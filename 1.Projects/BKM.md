
为了让你能够完全看清整个系统的全貌，我们把这套架构拆解为**两个独立的文件夹**：

1. **「用户维护目录」**：这是你（作者）在本地唯一需要用“人话”写和维护的内容（场景一）。
    
2. **「系统运行目录（生成物）」**：这是你的元智能体（Meta-Agent）自动编译出来的、符合 2026 年行业标准的 **AKU 技能包与拓扑图**（直接提供给后台常驻的 Codex 智能体执行，对应场景二） 。
    

以下是完整的目录结构和每一个文件的具体样例。

---

## 📁 目录结构总览

Plaintext

```
├── 📁 1_user_maintenance/                 # 一、用户维护目录（你负责写的纯人话）
│   ├── 📄 00_capabilities.md               # 你的底层工具能力清单
│   └── 📄 01_business_flows.md             # 你的核心经营与营销流程逻辑
│
└── 📁 2_system_registry/                  # 二、系统运行目录（元智能体自动生成的 AKU 资产库）
    ├── 📄 topology_config.json             # 整个网站的【知识拓扑图】连线规则
    ├── 📁 skills/                          # 具体的【原子能力 SKILL】规范定义
    │   ├── 📄 sku_01_paywall_enforce.md
    │   ├── 📄 sku_02_dynamic_bundle.md
    │   └── 📄 sku_03_omnichannel_deliver.md
    └── 📁 validators/                      # 确定性代码验证器（硬合规熔断脚本）
        └── 📄 check_discount_limit.py
```

---

## 一、 用户维护目录（User Maintenance）

### 📄 1. `00_capabilities.md` （你用人话定义的系统能力）

Markdown

```
# 平台底层系统工具资产

我已经通过 MCP 协议将网站的底层系统封装成了以下工具能力：
- 数据库工具：可以读取或修改用户的画像、国家（region）、活跃度评分（active_score），也可以给用户打标签，或者给用户账户增加免费试用天数。
- 海外支付（Stripe）：可以为特定用户生成限时优惠券折扣。
- 海外邮件（SendGrid）：可以给指定的邮箱发送定制的通知邮件。
- 国内微信（WeChat）：可以通过微信机器人向国内用户的微信发送模板消息通知。
```

### 📄 2. `01_business_flows.md` （你用人话定义的经营流程）

Markdown

```
# 付费内容商业变现与流失挽回流程

流程 1【付费墙动态拦截】：
当一个还没付钱的用户，在网站上点开标记为 Premium 的付费文章时，必须触发拦截。如果这个人累计试读已经超过 3 篇了，说明他是个高意向流失风险用户，必须立刻把他带入下面的「挽回流程」。

流程 2【智能化流失挽回】：
AI 运营官接到高意向流失用户后，根据他的国家和活跃度自动做个变现决定：
- 规定 A（针对国内用户）：如果用户是中国区（CN）的，不要调用 Stripe 生成折扣码，直接在数据库里为他的账户免费延长 3 到 7 天的试用期。
- 规定 B（针对海外用户）：如果是海外的，AI 你自己算个合理的折扣。但本站不能打骨折，所以你的折扣绝对不能低于 5折（0.50）。算好后去调用 Stripe 生成优惠券。

流程 3【全渠道交付】：
决定做完、资产生成后，如果上一步是发券且对方有邮箱，用 SendGrid 发邮件通知他；如果是延长了试用且对方是中国区，用微信给他推一个精美的体验到账通知。最后，在数据库里给用户打上 [挽回成功] 的标签，记录审计日志，清空会话准备接待下一个人。
```

---

## 二、 系统运行目录（System Registry - 元智能体生成产物）

当你保存上面的人话文件并运行本地构建时，元智能体（Meta-Agent）会精准捕捉你提到的逻辑，并自动转化为以下机器可直接执行的标准资产 ：

### 📄 1. `topology_config.json` （【知识拓扑图】——定义节点如何连线）

> **技术原理**：它将孤立的 Skill 串联成了有向图路由网，LLM 通过读取它，在运行时根据前一步的退出状态动态“寻路” 。

JSON

```
{
  "topology_name": "Knowledge_Platform_Core_Business_Graph",
  "version": "2026.1.0",
  "start_node": "sku_01_paywall_enforce",
  "edges": [
    {
      "from": "sku_01_paywall_enforce",
      "condition": "exit_status == 'TRIGGER_LOSS_MITIGATION'",
      "to": "sku_02_dynamic_bundle"
    },
    {
      "from": "sku_02_dynamic_bundle",
      "condition": "exit_status == 'SUCCESS'",
      "to": "sku_03_omnichannel_deliver"
    },
    {
      "from": "sku_02_dynamic_bundle",
      "condition": "exit_status == 'VALIDATOR_FAILED'",
      "to": "sku_human_review_gate"
    }
  ]
}
```

📁 2. `skills/` 目录下的具体文件（满足论文 7 组件 Schema）

#### 📄 `sku_01_paywall_enforce.md` （触发场景与初筛）

Markdown

```
---
id: sku_01_paywall_enforce
name: Paywall Dynamic Enforcement
description: 拦截未订阅用户访问付费内容，并初筛高活跃流失风险用户。
trigger_conditions:
  - action == "read_premium_article"
---

# 过程知识
1. 调用 `mcp::db::get_user_profile` 获取用户的 `user_status` 和 `trial_articles_viewed`。
2. 逻辑分支：
   - 若 `user_status == "subscribed"` -> 允许通行。
   - 若 `user_status == "non_subscribed"` 且 `trial_articles_viewed >= 3` -> 设置 `exit_status = "TRIGGER_LOSS_MITIGATION"`，引导 AI 转向拓扑下一步。

# 工具绑定
- mcp::db::get_user_profile
```

#### 📄 `sku_02_dynamic_bundle.md` （自适应商业决策与硬合规）

Markdown

```
---
id: sku_02_dynamic_bundle
name: Intelligent Loss Mitigation
description: 动态判断商业对策（国内加天数，海外算折扣并发券）。
---

# 过程知识
1. 读取上游事件传来的小明画像：`region` 和 `active_score`。
2. 运行运行时自适应决策：
   - 若 `region == "CN"` -> 决定发放免费试用，计算天数，调用 `mcp::db::extend_free_trial`。
   - 若 `region != "CN"` -> 决定发放折扣，基于 `active_score` 生成变量 `proposed_discount`，调用 `mcp::stripe::create_coupon`。

# 治理约束
- [cite_start]核心红线：`proposed_discount` 必须 $\ge 0.50$ [cite: 594]。

# 确定性验证器 (Validators)
- [cite_start]pre_execution_script: validators/check_discount_limit.py [cite: 594]

# 工具绑定
- mcp::db::extend_free_trial
- mcp::stripe::create_coupon
```

#### 📄 `sku_03_omnichannel_deliver.md` （多渠道触达交付与清空）

Markdown

```
---
id: sku_03_omnichannel_deliver
name: Omnichannel Campaign Delivery
description: 根据用户生态渠道进行精准送达，写入审计并清空上下文。
---

# 过程知识
1. 检查上游交付资产元数据。
2. 渠道分发逻辑：
   - 若产生优惠券且 `region != "CN"` -> 调用 `mcp::sendgrid::send_email` 发送促销邮件。
   - 若产生天数延长且 `region == "CN"` -> 调用 `mcp::wechat::send_template_msg` 发送微信通知。
3. 执行成功后，调用 `mcp::db::add_user_tag` 为用户标记 `[Loss_Mitigated]`，记录审计日志。

# 工具绑定
- mcp::sendgrid::send_email
- mcp::wechat::send_template_msg
- mcp::db::add_user_tag
```

---

### 📁 3. `validators/` 目录下的核心硬拦截文件

#### 📄 `check_discount_limit.py` （代码化治理防火墙）

> **技术原理**：当常驻后台的 Codex 智能体因为逻辑产生幻觉，试图发出一个“4折（0.40）”的违规折扣时，这个嵌入脚本会拦截它，逼迫 AI 进行“自反思自我修正”，从而保护你的财务资产安全 。

Python

```
# path: ./validators/check_discount_limit.py
import sys
import json

def validate_action():
    # 从常驻智能体当前的运行时上下文中提取其提议的值
    runtime_data = json.loads(sys.argv[1])
    proposed_discount = runtime_data.get("proposed_discount", 1.0)
    
    # 执行你（站长）在人话里声明的硬性红线
    if proposed_discount < 0.5:
        print(f"[熔断异常] AI 决策折扣为 {proposed_discount}，低于5折底线！硬性阻断该操作。")
        sys.exit(1) # 返回非0，Codex智能体将收到拒绝信号，触发自反思
        
    print("[验证通过] 折扣率合规。")
    sys.exit(0) # 放行

if __name__ == "__main__":
    validate_action()
```

---

## 💡 它们之间是怎么对应上的？

1. 当你在人话里写下：_“折扣绝对不能低于 5折（0.50）”_。 元智能体在静态编译时，会将其翻译为 `sku_02_dynamic_bundle.md` 里的 `# 治理约束` ，并自动为你生成 `check_discount_limit.py` 验证脚本 。
    
2. 当你在人话里写下：_“拦截之后，AI 运营官应该去后台看这个人的活跃度……累计试读超过 3 篇，进入挽回流程”_。 元智能体自动在 `topology_config.json` 里画了一条从 `sku_01` 指向 `sku_02` 的连线（Edge） 。
    

这样一来，你作为创作者，**你的数字资产库的全部维护工作就退回到了 `1_user_maintenance/` 文件夹下。你改动一句人话，线上的 AI 行为逻辑、验证机制和拓扑图连线就会发生自适应的技术重构** 。