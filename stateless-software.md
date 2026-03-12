## Input: Stateless, Backendless Software

Input is a document editor — it's like Obsidian in the browser, or HackMD if it used GitHub as a backend. It's also a demonstration that AI applications can use GitHub for data portability and long-term persistence.

Every file on Input is backed by a Git repo. The server is just a caching proxy, and we fetch and render Markdown files fro GitHub as users open them. This means:

- There's no lock-in. The application can be used with any other Markdown-compatible editor.
- You can easily fork the app, or add your own customizations.
- Stored content follows well-defined, human-readable schemas.

[Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications without a backend that worked this way. They cobbled together a patchwork of APIs to provide persistence, and let users choose from a menu that included services like Google Drive and Dropbox. But I suspect most of us have never actually used those APIs for serious persistence needs. In general, applications have been hostile to using third-party APIs for persistence, preferring at best a "file over app" philosophy of storing data locally.

That seems to be changing now. AI means people are now connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, code review tools, test runners, and more. Even non-technical users are starting to pick up Claude Code, and some are even teaching themselves to commit, push, and merge their code to Git.

And agents are changing the business of software. For the first time, it may be possible for an independent developer to build a complex piece of software with little cost and near-zero maintenance burden. With the convergence of all these factors, Git might finally become a compelling system of record.

Why haven't people built software this way before?

One reason is that it introduces complex concerns around distributed data. GitHub's APIs don't give you consistency, which means that when using the API, you might edit a file and read back an older version. You have to build your own commits if you want to make atomic, multi-file updates. Without conflict resolution strategies, it's easy to lose data, or run into merge conflicts.

Also, the backing API for a service like GitHub is designed to serve a much smaller number of users. As a result, developers following this model have to design aggressive caching policies that kick in when load goes over a certain limit. Handling cases where a user refreshes an application aggressively, or if a blog post goes viral, are actually difficult and require careful thought about fallbacks and how to degrade gracefully.

But assistants like Claude and Codex have made it possible to address many of these issues. I've used them to create a client-side caching layer that works as a local-first data store, to avoid hitting GitHub on every request. Assistants have made it possible to use complex Git Data APIs, and identify and patch places where data errors inevitably surface up to the user.

### The future of software

Before this year, stateless software couldn't compete with walled-garden, siloed software. But now one designer or engineer can create an app like Monday.com in a day.

A lot of business software is not very high quality - and people talk about antiquated user interfaces, slowness, and jankiness. People *want* to replace these systems, and the reason they haven't done so is mainly a coordination problem, i.e. most vibe coded software isn't very trustworthy or long-lasting.

There's a model here that should be appealing to enterprises, who intuitively understand the value of "on-prem", who can easily deploy an engineer with a coding agent if they need to make changes or fixes.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to their heart's content. I find both of those positions to be a bit implausible; and actually think this is a far more likely vision for the democratization of software.

Stateless software can be faster, easier to use, and more customizable than off-the-shelf software, especially when it's open source. It's a lot of fun to build, and it's fun to use too. As agents get more powerful, it will only get better. I'm excited to see where we can take it next.

