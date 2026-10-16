Hi all! Full disclosure: I'm building in the Obsidian/Markdown publishing space, so I'm not just a neutral observer.

I'm trying to understand people's workflows, without assuming a product answer.

For people who keep notes for different projects or audiences in the same vault or folder tree: how do you decide what gets published or shared?

I am especially interested in cases where one of your notes links to other notes that may or may not be meant for the same audience. Do you use tags, folders, a separate vault, manual review, scripts, Obsidian Publish's "Add linked" flow, or something else?

When you publish or share from your notes, is it usually one long-lived public site, occasional one-off shares, or separate outputs for different projects/audiences?

Has anything been annoying, risky, or surprisingly workable about your current setup?

Thanks for any experiences or examples you’re willing to share.

---

## Comments

> **JorgeGodoy** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo8hxa8/) · 1 points
> 
> I flag the notes I want to publish and use the digital garden plugin. What isn't published becomes a 404 error. This is ok and it is part of my writing process, as not every link in my vault exists, so there's no problem if it doesn't exist in my site.
> 
> > **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo8k48i/) · 1 points
> > 
> > That's helpful, thanks! Do you use tags in the notes you want to publish, something in frontmatter, or some other mechanism? Do you publish multiple sites, and if so, how do you distinguish which sites it is included in?
> > 
> > \> What isn't published becomes a 404 error
> > 
> > That makes sense. Assuming you publish multiple sites, do you manually traverse through your notes and mark them to ensure it's roughly what you want to publish (and stuff outside that 404s?). If it's just one site, I can see how it would just organically grow over time as you flag stuff for inclusion.
> > 
> > > **JorgeGodoy** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo9407c/) · 1 points
> > > 
> > > Digital Garden uses a property. It is a boolean value. If true, publish. If something else (false, inexistent, etc.) don't publish.
> > > 
> > > As I only have a single vault, I only have a single site.
> > > 
> > > I mark my notes when I create them. It is part of the process of writing. The audience has to be defined at the beginning of the writing process.
> > > 
> > > > **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo94sqf/) · 1 points
> > > > 
> > > > Thanks so much for your insight!

> **jsifalda** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo8r1kz/) · 1 points
> 
> i only use yourpulse.cc plugin, which allows you tu publish only specific notes via frontmatter property via configured url, zero hosting, or setup 
> 
> (disclaimer: i created that plugin for that purpose) 
> 
> > **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo8y00v/) · 2 points
> > 
> > Nice! I see you do linked note resolution. For those linked notes, you would just need to add \`yp-publish: true\` to the frontmatter of those linked notes, too?
> > 
> > Is this aimed primarily at publishing a single site containing any notes that have \`yp-publish: true\` in the frontmatter?
> > 
> > > **jsifalda** · [2026-05-28](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oofwnsf/) · 1 points
> > > 
> > > exactly : )

> **seashoreandhorizon** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo93nhj/) · 1 points
> 
> I have a user script that I run using QuickAdd that sets the publish flag to Y in the frontmatter, queries an LLM to populate SEO data for the note, and finally pushes the resulting file to my git repo. My CI/CD pipeline picks it up from there and rebuilds my site in Astro, pushing the result to Cloudflare using Wrangler.
> 
> > **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo97iye/) · 1 points
> > 
> > That sounds like a pretty advanced workflow with some very compelling automation. I hadn't heard of either QuickAdd or Astro, but they look nice!
> > 
> > When a published note links to another note that does not have the publish flag, what happens? Does Astro leave a broken link, exclude it cleanly, or do you have some kind of preflight check before pushing? Or maybe you just know that you shouldn't publish any pages with links for this workflow?
> > 
> > Also curious whether this setup now feels basically solved for you. Anything you wish it had, or are you pretty satisfied?
> > 
> > > **seashoreandhorizon** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo99avc/) · 1 points
> > > 
> > > I just don't link to notes I haven't published. It would be fairly trivial to add a step in the pipeline that checked for this scenario though, if it ever becomes an issue.
> > > 
> > > No, I'm petty happy with it. Any changes I want can be implemented in the CI/CD pipeline or as part of my user script.
> > > 
> > > > **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo9c04k/) · 1 points
> > > > 
> > > > Cool, sounds good. Thanks for taking the time to reply. I appreciate it!

> **Acrobatic-Window5364** · [2026-05-27](https://reddit.com/r/ObsidianMD/comments/1tpaw6d/comment/oo9vjkn/) · 1 points
> 
> One thing I am noticing from the replies is that most setups seem to have a single publish boundary: a note is in or out of one public site.
> 
> Do you ever have notes that are publishable in one context but not another? For example: different projects, clients, audiences, courses, documentation sets, or public/private personas.
> 
> Or is “one vault -> one public site” basically the shape of the problem for most of you?