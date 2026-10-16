Hi. I’ve been taking pretty diligent LaTeX notes on a variety of math and CS topics, and I’m interested in starting to publish notes on my GitHub Pages, which I can do easily with Obsidian Webpage Export. However, there is an issue I foresee with this workflow.

I like having one large vault with everything, so my “public-ready” notes are interspersed with lots of personal things that I would not want to publish. Even within the folders containing my technical notes, there’s lots of stuff that wouldn’t be helpful online. Manually picking these out every time seems burdensome, and I can see myself accidentally committing something private to my GitHub. Moreover, the structure I’d want for an online vault would not be exactly the same as how the notes are on my personal vault, and I might even want to include some additional pages as explanation.

In my mind, the ideal solution would be creating a subfolder of my vault for this public site, and then linking the notes that I’d like published into that subfolder. That way, I can simply publish the entire folder and get the latest versions of my vault, without worrying about consistency or affecting my personal vault. I think my alternative would be copying over the notes manually, which would be annoying. But I also haven't seen a straightforward way of doing this linking.

Any ideas how I could accomplish this or alternative suggestions? I’m curious how others have gone about this.

---

## Comments

> **artsbymat** · [2025-11-26](https://reddit.com/r/ObsidianMD/comments/1p73q2v/comment/nqv030e/) · 3 points
> 
> You could streamline this quite a bit without duplicating or restructuring your vault manually.
> 
> If you want to keep one master vault but only surface selected notes publicly, you might try using [Quartz](https://quartz.jzhao.xyz/plugins/ExplicitPublish). It supports an **ExplicitPublish** mode, where only notes containing a simple frontmatter flag like:
> 
> publish: true
> 
> get included in the final build. That means you can keep everything private drafts, personal notes, scratch work in the same vault, while only curated notes appear on your site. No need to maintain a second repo or copy files over, and you don’t risk accidentally pushing something you didn’t mean to publish.
> 
> > **BinyaminF** · [2025-11-26](https://reddit.com/r/ObsidianMD/comments/1p73q2v/comment/nqwou5l/) · 1 points
> > 
> > This looks quite good, thanks for the recommendation!

> **erikrelay** · [2025-11-26](https://reddit.com/r/ObsidianMD/comments/1p73q2v/comment/nquuxo5/) · 1 points
> 
> It's more on the techy side, but HUGO is a good option. It's a static site generator that takes your markdown files and turns them into html. There's a lot of premade themes online you can build from or make one from scratch. You could turn your entire vault into a Hugo site, and the ones you don't want published you mark as drafts. Then it generates a separate "public" folder you can publish.
> 
> It's what I've been using. I don't have as many notes as you tho, so I just copy paste them manually when I want to publish.

> **JorgeGodoy** · [2025-11-26](https://reddit.com/r/ObsidianMD/comments/1p73q2v/comment/nqv49g9/) · 1 points
> 
> I use the digital garden plugin. It will only publish notes with a property saying that the note should be published.
> 
> It will replicate the folders where the notes are. To create a workaround, you can create a new folder, as you mentioned, and create new notes there where you would embed the original note. The thing is that if you update the original note, it won't see the update (you need to test it, I think it doesn't see it from the very few cases I have) so you'll have to change something -- such as a property -- on the other file as well.
> 
> This is the link to the docs: [https://dg-docs.ole.dev/](https://dg-docs.ole.dev/)
> 
> You can take a look at it before trying it out. My notes are all mixed up with published and unpublished all living in the same folder, besides a folder of notes written for publishing.
> 
> As it uses 11ty, it is highly customizable. I publish from both the computer and from mobile. Many of the other options I saw required some local installation and processing, and I didn't want to maintain all that at Termux.