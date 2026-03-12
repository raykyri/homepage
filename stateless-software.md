## Input: A backendless document editor with Git persistence

Input is a document editor, like Obsidian or HackMD, with GitHub as a backend.

It's also a demonstration that applications in the AI era can use GitHub for data portability and long-term persistence. Every file on Input is backed by GitHub. The server is just a caching proxy, and we fetch and render Markdown files as users open them.

This means:

- The application has no lock-in. You can easily fork it, run it locally, or add your own customizations.
- You can use Input with existing tools that connect to GitHub (e.g. Claude Code, Cursor Agents, Obsidian).
- All stored content follows human-readable schemas, in this case Markdown with front matter and extensions, to support features like share links, private document permissioning, and comments.

### Backendless software

[Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications that worked this way, without a backend. They used a patchwork of APIs to provide persistence through services like Google Drive and Dropbox. But I suspect most of us have never actually used those APIs for serious persistence needs. Outside of a few limited enterprise use cases (e.g. Box, OneDrive), applications have generally been hostile to using third-party APIs for saving data, preferring at best a ["file over app"](https://stephango.com/file-over-app) philosophy of storing data locally.

That seems to be changing now. AI means people are now connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, code review tools, test runners, and more. Even non-technical users are starting to pick up Claude Code, and some are even teaching themselves to commit, merge, and push to Git.

Agents are also changing the costs of creating software. For the first time, it may be possible for an independent developer to build a complex piece of software in days of work, and maintain it without significant resources or effort. That means more freedom to create applications that have no particular business model, that are still highly technically sophisticated.

### Distributed data

One reason that people haven't built software this way before is the complexity of distributing data in different places. GitHub APIs don't give you consistency, which means that it's easy to edit a file and read back an older version. If you want to make atomic, multi-file updates, you have to use a more complex API that involves working with Git data structures. Either way, if multiple people edit the same files, it's easy to run into merge conflicts.

GitHub APIs are also designed to serve a much smaller number of users than what you'd need for a public-facing application. That means it's easy to go over rate limits when using an application aggressively, or if you encounter an unusual spike in traffic, e.g. if a million people show up one day when a blog post goes viral.

But assistants like Claude and Codex have made it possible to address many of these issues. In this project, I've used them to create a client-side, local-first data store, to avoid hitting GitHub on every request. Assistants have also made it easy to use complex Git APIs, and identify and patch the places where errors surface to users. Working with distributed data is easier than ever before.

### The future of software

Before this year, backendless software couldn't compete with walled-garden, siloed software. It wouldn't make sense to go through the effort of building a complex productivity app, text editor, ticketing system, etc., if a corporate competitor could outspend and outpace you. Now one designer or engineer can create a complex application in days. What's missing is trust and permanence, since most AI-generated software isn't very trustworthy or long-lasting. This is where being open-source and storing data in portable containers starts to make sense. Knowing that my data will remain accessible to me gives me the assurance I need to take a piece of software seriously, both as a user and as a contributor.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to be perfectly suited to themselves. Where we land will probably be somewhere in the middle. Walled-garden software-as-a-service won't be sustainable when anyone can generate a clone of the application with zero human effort, but that doesn't mean everyone is going to generate their own software, nor does it mean that software companies will stop existing. Software that provides the connectivity and infrastructure for people and AIs to build complex applications will do just fine.

If things go well, we may even see an entirely new class of software, neither one-off code generations, nor deep infrastructure, but open-source applications on shared data stores that actually look a lot more like software we use today, which we work together to build in the commons.
