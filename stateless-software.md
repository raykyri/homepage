## Input: Backendless software with persistence in Git

Input is a document editor — it's like Obsidian in the browser, or HackMD if it used GitHub as a backend.

It's also a demonstration that AI applications can use GitHub for data portability and long-term persistence. Every file on Input is backed by a Git repo. The server is just a caching proxy, and we fetch and render Markdown files from GitHub as users open them.

This means:

- The application has no lock-in.
- You can easily fork it, run it locally, or add your own customizations.
- You can use Input with existing tools that connect to GitHub (e.g. Claude Code, Cursor Agents, Obsidian).
- All stored content follows human-readable schemas, in this case Markdown with front matter and extensions. These extensions are enough to support features like sharing, comments, and wikilinks.

[Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications that worked this way, without a backend. They cobbled together a patchwork of APIs to provide persistence through services like Google Drive and Dropbox. But I suspect most of us have never actually used those APIs for serious persistence needs. Outside of a few limited enterprise use cases (e.g. Box, OneDrive), applications have generally been hostile to using third-party APIs for saving data, preferring at best a "file over app" philosophy of storing data locally.

That seems to be changing now. AI means people are now connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, code review tools, test runners, and more. Even non-technical users are starting to pick up Claude Code, and some are even teaching themselves to commit, push, and merge their code to Git.

Agents are also changing the business of software. For the first time, it may be possible for an independent developer to build a complex piece of software with near-zero cost or maintenance burden. With so much software, Git might finally be evolving into a compelling system of record.

Why haven't people built software this way before?

One reason is that it introduces complex concerns around distributed data. GitHub APIs don't give you consistency, which means that it's easy to edit a file and read back an older version. If you want to make atomic, multi-file updates, you have to use a more complex API that involves working with Git data structures. Either way, if multiple people edit the same files, it's easy to run into merge conflicts.

The backing API for a service like GitHub is also designed to serve a much smaller number of users than what you'd need for a public-facing application. That means it's easy to go over rate limits when using an application aggressively, or if you encounter a 99th-percentile scenario, e.g. if a million people show up one day when a blog post goes viral.

But assistants like Claude and Codex have made it possible to address many of these issues. In this project, I've used them to create a client-side, local-first data store, to avoid hitting GitHub on every request. Assistants have also made it easy to use complex Git APIs, and identify and patch the places where errors surface to users.

### The future of software

Before this year, stateless software couldn't compete with walled-garden, siloed software. It didn't make sense to go through the effort of building a complex productivity app, text editor, ticketing system, etc., if a corporate competitor could outspend and outpace you.

Now one designer or engineer can create a complex application in days. What these applications are missing is just a sense of permanence, since most vibe coded software isn't very trustworthy or long-lasting. This is where being open-source and storing data in portable containers like Git repos starts to make sense. Knowing that my data is backed up and will remain readable somewhere else gives me the assurances I need to take it seriously, both as a user and as a contributor. It sets up the right virtuous cycles for contributors to come together around a few trusted codebases.

There's plenty of opportunity here. A lot of business software is not very high quality; it's often slow, outdated, or janky. People *want* to replace these systems, and the reason they haven't done so is mainly a matter of finding quality alternatives they can trust.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to their heart's content. I think the real answer is somewhere in the middle. Certain kinds of software probably have their days numbered, but not everyone will write or prompt their own application. But there may be a thriving class that exists between the two extremes, of people coming together to build applications on top of portable data and shared stores.