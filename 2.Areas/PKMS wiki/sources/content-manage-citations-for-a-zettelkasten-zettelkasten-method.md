---
title: Manage Citations for a Zettelkasten • Zettelkasten Method.md
type: source
path: /Users/weisun/github/mdfriday/sunwei/.obsidian/plugins/mdfriday/workspace/projects/2.Areas/PKMS-wiki/content/Manage Citations for a Zettelkasten • Zettelkasten Method.md
date: 2026-05-08T10:27:19.071Z
---

# Manage Citations for a Zettelkasten • Zettelkasten Method.md

**Path**: `/Users/weisun/github/mdfriday/sunwei/.obsidian/plugins/mdfriday/workspace/projects/2.Areas/PKMS-wiki/content/Manage Citations for a Zettelkasten • Zettelkasten Method.md`

**Summary**: 

## Entities

- [[Zotero]] (tool)
- [[Christian]] (person)
- [[Marked 2]] (tool)
- [[Cal Newport]] (person)
- [[BibDesk]] (tool)
- [[Scrivener]] (tool)
- [[MultiMarkdown]] (tool)
- [[nvALT]] (tool)
- [[TextExpander]] (tool)
- [[Typinator]] (tool)
- [[KeyboardMaestro]] (tool)
- [[LaTeX]] (tool)
- [[BibTeX]] (tool)

## Concepts

- [[Zettelkasten]]
- [[Getting Things Done]]
- [[Citation Management]]
- [[Collection Phase]]
- [[Research Database]]

## Original Content

---
title: "Manage Citations for a Zettelkasten • Zettelkasten Method"
source: "https://zettelkasten.de/posts/bibliography-zettelkasten/"
author:
  - "[[christian]]"
published: 2013-10-08
created: 2026-05-08
description: "How to enter literature references into your notes, and how to configure BibDesk for Mac to do the job in a minimal way."
tags:
  - "clippings"
---
Today, we’ll talk about tools for a change. Managing a reference file is part of the **collection** phase of maintaining a *[[Zettelkasten]].* It’s of special importance if you’re [[Writing]] a research paper or a book because without proper [[Citation Management]] [[Things]] are going to be a mess for you, soon. I’ll show you how I do it and tell you about possible alternatives briefly.

In short, I suggest you:

- use [[MultiMarkdown]] citations,
- add the full citation to every Zettel once,
- use a [[Reference Manager]] and
- add [[TextExpander]] shortcuts for frequently cited works.

## Why I add full citations to every Zettel

![Screenshot of a Zettel](https://[[zettelkasten.de]]/posts/bibliography-zettelkasten/zettel.png)

Zettel with full citation at the bottom

I always include a full citation in a *Zettel.* This redundant storage gives me a safe feeling:

- Every *Zettel* I write is self-contained: [[nvALT]] and [Marked](http://[[Marked 2]]/) preview know what to do without additional effort.
- I could re-create a bibliography from most of the references stored in my notes did I ever lose my precious digital library.
- Since I only add references to notes from my bibliography manager, I’ve still got a fully working bibliography or digital library at my fingertips.

The references are copied over from my bibliography manager of choice, [[[BibDesk]]](http://[[BibDesk]]/). I made this process as easy as I could. [TextExpander](http://[[TextExpander]]) and the like will help you safe tons of [[Time (magazine)]]. Whenever I’m about to create lots of notes for a book, I add two shortcuts:

1. A shortcut to the full citation which I put at the end of a note. For example `,,evans` expands to:
	```[[Markdown]]
	[#evans2006ddd]: Eric Evans (2006): _Domain-Driven Design. Tackling complexity in the heart of software_, Upper Saddle River, NJ: Addison-Wesley.
	```
2. Another shortcut is needed for inline citations. For example, `°evans` expands to `[{^}][#evans2006ddd]`, where `{^}` denotes the cursor position.

If you’re doing lots of research, do yourself a favor and get at least a trial version of [TextExpander](http://smile.7eer.net/c/176775/161942/2936) [^1], [Typinator](http://www.ergonis.com/products/typinator/), or [KeyboardMaestro](http://www.keyboardmaestro.com/) and see for yourself how much faster you can be.

**Update 2015-09-01**: TextExpander 5 will now suggest new snippets and remind you of existing ones which you tend not to use.

## Benefits of MultiMarkdown citations

When I write anything, I capture ideas in my *Zettelkasten* in [MultiMarkdown](http://fletcherpenney.net/multimarkdown/). I compose drafts for longer pieces in MultiMarkdown as well. When I need to hand in a paper, I convert MultiMarkdown to LaTeX to PDF.

Since MultiMarkdown has its own [citations syntax](http://fletcher.github.io/peg-multimarkdown/#citations), every citation in my *Zettelkasten* is done in this format.

```
Something something.[p 123][#citekey]

[#citekey]: (full-blown reference like in the example above)
```

When I put Markdown preview in nvALT [exactly three years ago](http://christiantietze.de/posts/2010/10/markdown-hud-nv/), I deliberately chose MultiMarkdown to support citations for acamedic writing. It served me well all these years and I’m glad Brett & David sticked to it when NV became nvALT.

It’s easy to go from `.mmd` to `.tex` and clean things up afterwards. LaTeX utilizes the BibTeX format to read bibliography information and generate manageable citations and a well-formed bibliography.

## BibDesk bibliography manager

![BibDesk](https://zettelkasten.de/img/blog/201310071817_bibdesk.png)

The software which fits like a glove when managing references seems to be [BibDesk](http://bibdesk.sourceforge.net/) (Mac only). It’s storing everything in a `.bib` BibTeX file, hence everything is fully compatible with LaTeX.

The sweet part is how easily you can create your own **export templates** which in turn can be bound to the “copy” action at ⌘C (Cmd+C). Select the items in the library, hit “copy”, switch to nvALT, paste, done.

You can [find the full citation template on GitHub](https://gist.github.com/DivineDominion/6870769) and propose changes there.

```
<$publications>

[#<$citeKey/>]: <$authors.name?>

<$authors.name.stringByRemovingTeX.@componentsJoinedByCommaAndAnd/><?$authors.name?><$editors.name.stringByRemovingTeX.@componentsJoinedByCommaAndAnd/> (Hrsg.)

</$authors.name?>

<$fields.Year?> (<$fields.Year/>)</$fields.Year?>:  _<$fields.Title.stringByRemovingTeX/><$fields.Subtitle?>. <$fields.Subtitle.stringByRemovingTeX/></$fields.Subtitle?>_<$pubType=article?>

, <$fields.Journal/><$fields.Number?> <$fields.Number/></$fields.Number?>, <$fields.Year/>, Vol. <$fields.Volume/>, S. <$fields.Pages/><?$pubType=incollection?>

, in: <$fields.Booktitle/><$fields.Address?>, <$fields.Address/>: <$fields.Publisher?><$fields.Publisher/></$fields.Publisher?><?$fields.Address?>

  <$fields.Publisher?>, <$fields.Publisher/></$fields.Publisher?>

</$fields.Address?>

<?$pubType?>

<$fields.Address?>, <$fields.Address/>: <$fields.Publisher?><$fields.Publisher/></$fields.Publisher?><?$fields.Address?>

  <$fields.Publisher?>, <$fields.Publisher/></$fields.Publisher?>

</$fields.Address?>

</$pubType?>.

</$publications>
```

You can find the other BibDesk templates in `~/Library/Application Support/BibDesk/Templates/`. This is where I put mine, too. You have to add the template file to BibDesk’s preferences afterwards. They are overwhelmingly complex at first, but you only need worry about the setting panes called “Template Files” and “Citation Behavior” ([see image](https://zettelkasten.de/posts/bibliography-zettelkasten/config.png)).

### Automatic citekey generation

![](https://zettelkasten.de/posts/bibliography-zettelkasten/bibdesk-citekey.png)

Recommended citekey format setting in BibDesk

BibDesk allows you to specify the citekey format that will be used when you e.g. import items or enter all required fields manually.

I like my “author + year + short title” (short being 4 characters), so the format string I use is this: `%a1%Y%t4`

That produces `mccracken2004bibd` from first [[Christian]] being McCracken, year being 2004, and title being “BibDesk, a great application to manage your bibliographies”.

### Software Alternatives

Your reference manager should get out of your way and export references in a MultiMarkdown-friendly format if you’re like me. The more you cite your sources in notes the more you will want to have a shortcut to generate the citations quickly.

I’ve had my hands on various alternatives you might want to try for yourself:

- [[[Zotero]]](http://www.[[Zotero]]/) is nice and platform independent but the export templates give me nightmares. Zotero is more useful if loathe [[LaTeX]] and prefer to write articles in Word or Pages since it can export bibliographies as rich text.
- [[[JabRef]]](http://jabref.sourceforge.net/) is a platform independent [[BibTeX]] database manager a friend of mine used for years. It’s ugly, but it does its job. Even on Windows.
- Then there’s [Mendeley](http://www.mendeley.com/), which has a unique spin: it incorporates social network features and stores attachments in its cloud service. You can share citations and cooperate on bibliographies with others, think *collaborative research.* Also, it totally turns me off because I don’t need any of this.

In the end, you could totally use a spreadsheet to keep track of author, title and year and a column with pre-formatted Markdown output. [[Cal Newport]] wrote a great introduction on how to use a lo-fi [“[[Research Database]]” spreadsheet](http://[[Cal Newport]]/blog/2007/10/01/monday-master-class-how-to-build-a-paper-research-database/) way back in 2007. His principles of organizing the database are well worth a read.

## Outlook

Chances are you write a lot. Since I’m covering [[macOS]] applications a great deal, you probably have heard of [[[Scrivener]]](http://www.[[Scrivener]]). When you collect your notes and ideas in your *Zettelkasten,* you may want to write your paper or your book with Scrivener. Since Scrivener utilizes MultiMarkdown, it’s a fully compatible extension to the note-taking workflow I’ve sketched. There’s a great article by Tim Brandes about [writing and citing in Scrivener 2](http://timbrandes.com/blog/2012/02/28/howto-write-your-thesis-in-latex-using-scrivener-2-multimarkdown-3-and-bibdesk/) which I enjoyed reading.

I picked my tools so they can be easily exchanged. A BibTeX database can be edited with any text editor. The popular MultiMarkdown syntax won’t go anywhere soon. What are your principles?

[^1]: Affiliate link; we get a small kickback to suppor this site from the vendor if you buy from our link but it won’t cost you anything.

