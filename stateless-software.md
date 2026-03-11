## Input: Stateless, Backendless Softwware

Input is a document editor — it's like Obsidian in the browser, or HackMD using GitHub as a backend.

Every file on Input is backed by a Git repo. The URL raykyri.input.md is automatically mapped to the public repo at `raykyri/homepage` [on GitHub](https://github.com/raykyri/homepage). We fetch and render Markdown files as users visit the site.

This means:

- No lock-in.
- You can easily fork the app, and/or add your own customizations.
- You can use Input with existing tools that connect to GitHub (e.g. Claude Code Web, Cursor Agents, or Obsidian).
- All stored content follows pre‑declared schemas, in this case Markdown.

[Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications to work without a backend this way. They cobbled together a patchwork of APIs to provide persistence. But I suspect most of us have never actually used Google Drive or Dropbox's APIs along with linked applications. Third-party persistence has never seen serious adoption, for either end users or enterprises.

That seems to be changing now. One reason is we've finallly gotten used to connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, plus code review tools, test runners, and more. As people started using applications like Claude Code for everything, Git repos suddenly start looking a lot more compelling as a system of record.

### Beyond local-first

You can think of this kind of persistence as a progressive enhancement over local-first software, which has gained momentum in the last few years, as people started looking for alternatives to popular online services.

But the local-first model itself is limiting. In general, I want a web app! I want to be able to access the app from any computer, and to publish easily, without `git push` or running static site generators.

Why haven't people built software this way before?

One reason is it involves a lot of complexity. GitHub's APIs don't give you consistency, which means that naively using the API breaks in surprisingly ways. You might edit a file and find some edits are lost, or that changes don't stick.

You have to deal with rate limits, 409 Conflict errors, and 99th percentile scenarios, e.g. if a million people show up one day when a blog post goes viral. The backing API for a service like GitHub is designed to serve a much smaller number of users, so you have to design aggressive caching policies that kick in when load goes over a certain limit.

Claude and Codex have made it possible to address many of these issues. Personally, this app has already replaced several tools that I used day-to-day.

### The future of software

Before this year, stateless software couldn't compete with walled-garden, siloed software. It didn't make sense to go through the effort of building a complex text editor, productivity app, etc., if a corporate competitor could outspend and outpace you.

As a result, people ended up using tools like Asana and Monday.com, and the successful ones charged enterprises tens of thousands of dollars a year. Now one designer or engineer can create an app like Monday.com in a day... so what happens next?

A lot of business software is not very high quality - and people talk about antiquated user interfaces, slowness, and jankiness. People *want* to replace these systems, and the reason they haven't done so is mainly a coordination problem, i.e. most vibe coded software isn't very trustworthy or long-lasting.

There's a model here that should be appealing to enterprises, who intuitively understand the value of "on-prem", who can easily deploy an engineer with a coding agent if they need to make changes or fixes.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to their heart's content. I find both of those positions to be a bit implausible; and actually think this is a far more likely vision for the democratization of software.

Stateless software can be faster, easier to use, and more customizable than off-the-shelf software, especially when it's open source. It's a lot of fun to build, and it's fun to use too. As agents get more powerful, it will only get better. I'm excited to see where we can take it next.

