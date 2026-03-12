## Input: Stateless, Backendless Software

Input is a document editor — it's like Obsidian in the browser, or HackMD if it used GitHub as a backend. It's also a demonstration that AI applications can use GitHub for data portability and long-term persistence.

Every file on Input is backed by a Git repo. The server is just a caching proxy, and we fetch and render Markdown files fro GitHub as users open them. This means:

- There's no lock-in. The application can be used with any other Markdown-compatible editor.
- You can easily fork the app, or add your own customizations.
- Stored content follows well-defined, human-readable schemas.

[Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications without a backend, that worked this way. They cobbled together a patchwork of APIs to provide persistence, and let users choose from a menu that included services like Google Drive and Dropbox. But I suspect most of us have never actually used those APIs for serious persistence needs. In general, applications have been hostile to using third-party APIs for persistence, preferring at best a "file over app" philosophy of storing data locally.

That seems to be changing now. AI means people are now connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, code review tools, test runners, and more. Even non-technical users are starting to pick up Claude Code, and some are even teaching themselves to commit, push, and merge their code to Git.

And agents are changing the business of software. For the first time, it may be possible for an independent developer to build a complex piece of software with near-zero cost or maintenance burden. With so much software, Git might finally be a compelling system of record.

Why haven't people built software this way before?

One reason is that it introduces complex concerns around distributed data. GitHub's APIs don't give you consistency, which means that when using the API, you might edit a file and read back an older version. You have to build your own commits if you want to make atomic, multi-file updates. Without conflict resolution strategies, it's easy to lose data, or run into merge conflicts.

Also, the backing API for a service like GitHub is designed to serve a much smaller number of users, have to design aggressive caching policies that kick in when load goes over a certain limit. It's easy to go over rate limits when using an application aggressively, or in a 99th percentile scenarios, e.g. if a million people show up one day when a blog post goes viral -- exactly when you don't want to fail.

But assistants like Claude and Codex have made it possible to address many of these issues. In this project, I've used them to create a client-side caching layer that works as a local-first data store, so we don't have to hit GitHub on every request. Assistants have also been useful for dealing with more complex Git APIs, and identifying and patching the places where it's not possible to paper over errors. This has made the application smooth enough that I use it basically every day.

### The future of software

Before this year, stateless software couldn't compete with walled-garden, siloed software. It didn't make sense to go through the effort of building a complex text editor, productivity app, etc., if a corporate competitor could outspend and outpace you.

As a result, people ended up using tools like Asana and Monday.com, and the successful ones charged enterprises tens of thousands of dollars a year. Now one designer or engineer can create an app like Monday.com in a day... so what happens next?

A lot of business software is not very high quality - and people talk about antiquated user interfaces, slowness, and jankiness. People *want* to replace these systems, and the reason they haven't done so is mainly a coordination problem, i.e. most vibe coded software isn't very trustworthy or long-lasting.

There's a model here that should be appealing to enterprises, who intuitively understand the value of "on-prem", who can easily deploy an engineer with a coding agent if they need to make changes or fixes.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to their heart's content. I find both of those positions to be a bit implausible; and actually think this is a far more likely vision for the democratization of software.

Stateless software can be faster, easier to use, and more customizable than off-the-shelf software, especially when it's open source. It's a lot of fun to build, and it's fun to use too. As agents get more powerful, it will only get better. I'm excited to see where we can take it next.

