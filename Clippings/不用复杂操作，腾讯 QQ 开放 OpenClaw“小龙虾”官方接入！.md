---
title: "不用复杂操作，腾讯 QQ 开放 OpenClaw“小龙虾”官方接入！"
source: "https://zhuanlan.zhihu.com/p/2014462185804427806"
author:
  - "[[追逐时光者​互联网行业 从业人员]]"
published:
created: 2026-04-23
description: "前言你养“龙虾”了吗？这句看似玩笑的问候，正成为 2026 年科技圈最火热的社交暗号。过去几个月，OpenClaw 以势不可挡的姿态席卷全球，不仅在 GitHub 狂揽 270K+ Star，登顶史上最受欢迎开源项目，更催生了“赛博…"
tags:
  - "clippings"
---
[收录于 · AIGC&AI赋能](https://www.zhihu.com/column/c_1872399802895044608)

1 人赞同了该文章

目录

收起

前言

OpenClaw 是什么？

快速搭建AI私人QQ助理

支持的消息类型

OpenClaw原生接入流程

一、安装OpenClaw开源社区QQBot插件

二、配置绑定当前QQ机器人

三、重启本地OpenClaw服务

腾讯云部署 OpenClaw 教程

## 前言

你养“龙虾”了吗？这句看似玩笑的问候，正成为 2026 年科技圈最火热的社交暗号。过去几个月，OpenClaw 以势不可挡的姿态席卷全球，不仅在 [GitHub](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=GitHub&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiJHaXRIdWIiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNzEyMTEyNjcsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.Xr3AnDnBjtFbhupQ-MwOptYsUbNFcIgsbqird9tKTh8&zhida_source=entity) 狂揽 270K+ Star，登顶史上最受欢迎开源项目，更催生了“ [赛博养虾](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=%E8%B5%9B%E5%8D%9A%E5%85%BB%E8%99%BE&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiLotZvljZrlhbvomb4iLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNzEyMTEyNjcsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.SJrb7nOe6rq2c6g0G_4wcVcp_rjLpJaz8YWsMdkdXhI&zhida_source=entity) ”的新兴文化。从开发者论坛到街头巷尾，从499/999元的上门部署服务到闲鱼爆火的“龙虾驯养指南”，这场由 [AI智能体](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=AI%E6%99%BA%E8%83%BD%E4%BD%93&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiJBSeaZuuiDveS9kyIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTIxMTI2NywiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.zF_bahVz1le0nGracOLOmHqOrRBgqs9q5sSyFqBysHo&zhida_source=entity) 掀起的生产力革命，正在重塑人与机器的协作方式。

现如今腾讯 QQ 重磅推出官方接入通道，无需复杂配置，无需代码基础，只需一键绑定，你的 QQ 就能化身“龙虾饲养员”。

## OpenClaw 是什么？

OpenClaw 是一款本地优先、完全开源的新一代 AI 助手。它直接部署在你的 [macOS](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=macOS&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiJtYWNPUyIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTIxMTI2NywiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.v4uWgsyTj52W8Z5cZ1zgWFUCEww_D-putUIqg0_CePU&zhida_source=entity) 、 [Windows](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=Windows&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiJXaW5kb3dzIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjcxMjExMjY3LCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.CMqjz7w732zvDeOhw3tgDFPFes3wOACI2iqZBb7W1vI&zhida_source=entity) 或 [Linux](https://zhida.zhihu.com/search?content_id=271211267&content_type=Article&match_order=1&q=Linux&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzcxMDU5NzAsInEiOiJMaW51eCIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTIxMTI2NywiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.XbRt0Hn-07xt1yPC8-C1PnZKap72DcP2pVOQOHrkRCc&zhida_source=entity) 设备（及服务器）上，将大模型的智慧与您的操作系统深度融合。它不仅能理解上下文，更拥有长时记忆与系统级权限，能真正“动手”执行文件管理、数据抓取、应用操控等真实任务。

- openclaw 开源地址： [github.com/openclaw/ope](https://link.zhihu.com/?target=https%3A//github.com/openclaw/openclaw)
![](https://picx.zhimg.com/v2-65b2819d6663b8f715f16492a6e9926f_1440w.jpg)

## 快速搭建AI私人QQ助理

- 登录地址： [q.qq.com/qqbot/openclaw](https://link.zhihu.com/?target=https%3A//q.qq.com/qqbot/openclaw/login.html)

https://q.qq.com/qqbot/openclaw/entity-picker.html?session\_id=7bfd6887-788b-400f-804c-3e4dffef8b47&\_wv=16777218 (二维码自动识别)

登录后，点击创建机器人，每个 QQ 账号可以注册 5 只独立 AI 机器人，创建的机器人昵称、头像、简介可以自由修改。

![](https://pic1.zhimg.com/v2-beebebfbef711f45956eaddd150c1fce_1440w.jpg)

![](https://picx.zhimg.com/v2-087b65300082e2599fb1a0f5aa2d50cb_1440w.jpg)

![](https://pic4.zhimg.com/v2-e0f80f5317546598fed87af71ba3f933_1440w.jpg)

![](https://pica.zhimg.com/v2-f90550741a74df9185725f6f2a1c2614_1440w.jpg)

## 支持的消息类型

![](https://pic1.zhimg.com/v2-ac32c3f31bf939d1dab68935e71dc182_1440w.jpg)

## OpenClaw原生接入流程

### 一、安装OpenClaw开源社区QQBot插件

```
openclaw plugins install @sliverp/qqbot@latest
```

### 二、配置绑定当前QQ机器人

```
openclaw channels add --channel qqbot --token "xxx:xxxx"
```

### 三、重启本地OpenClaw服务

```
openclaw gateway restart
```

## 腾讯云部署 OpenClaw 教程

腾讯云提供可视化配置面板，只需几步即可快速完成操作，极简接入！

- [cloud.tencent.com/devel](https://link.zhihu.com/?target=https%3A//cloud.tencent.com/developer/article/2626045)
![](https://pic4.zhimg.com/v2-282b6a5a08c4bb2dc9ba7734b688979f_1440w.jpg)

![](https://pic2.zhimg.com/v2-0759d7f17cf39166732ee1e3c7072a03_1440w.jpg)

发布于 2026-03-09 22:09・广东