---
fonts:
  - headings: Literata
css: h2 { font-size: 28px; font-family: Literata; font-weight: 300; border-bottom: none; padding-bottom: 6px; }
---

## Input: A backendless document editor backed by GitHub

For a long time, hackers and hobbyists have proposed different ways to create software that's independent of centralized services. A common feature in these systems is a neutral data-portability protocol that lets users reclaim their data, like Tim Berners-Lee's Solid or Bluesky's AT Protocol.

What if that protocol already existed?

Input is a document editor, like Obsidian, HackMD, or Notion, that uses GitHub as a backend. It's also a demonstration that AI era applications can use GitHub for data portability and long-term persistence.

Every file on Input is backed by GitHub, and the server is just a caching proxy, so we fetch and render Markdown files as users open them. This means:

- No lock-in: You can easily fork the application, run it locally, or apply custom modifications.
- Interoperability: Input works seamlessly with any tool connected to GitHub, such as Claude Code, Cursor Agents, or Obsidian.
- Human-readable data: All content follows open schemas, specifically Markdown with front matter and standard extensions.

### Backendless software

Applications like [Draw.io](https://draw.io) and [tldraw](https://tldraw.io) pioneered this approach, using a patchwork of APIs to provide persistence through services like Google Drive and Dropbox. Historically, however, these integrations remained niche. Most software has been inherently "hostile" to third-party APIs for primary storage, preferring a ["file over app"](https://stephango.com/file-over-app) philosophy that keeps data local.

This dynamic seems to be shifting now. AI means people are now connecting an ever-growing list of tools to GitHub: Cursor Agents, Claude, Codex, code review tools, test runners, and more. Even non-technical users are starting to pick up Claude Code, and some are even teaching themselves to commit, merge, and push to Git.

Simultaneously, AI agents are collapsing the cost of software development. An independent developer can now build and maintain a sophisticated application in a matter of days. This means we may have more freedom than ever to create high-quality software that doesn't require a traditional business model.

### Distributed data

One reason that people haven't built software this way before is the complexity of distributing data in different places. GitHub APIs don't give you consistency, which means that it's easy to edit a file and read back an older version. If you want to make atomic, multi-file updates, you have to use a more complex API that involves working with Git data structures. Either way, if multiple people edit the same files, it's easy to run into merge conflicts.

GitHub APIs are also designed to serve a much smaller number of users than what you'd need for a public-facing application. That means it's easy to go over rate limits when using an application aggressively, or if you encounter an unusual spike in traffic, e.g. if a million people show up one day when a blog post goes viral.

But assistants like Claude and Codex have made it possible to address many of these issues. In this project, I've used them to create a client-side, local-first data store, to avoid hitting GitHub on every request. Assistants have also made it easy to use complex Git APIs, and identify and patch the places where errors surface to users. Working with distributed data is easier than ever before.

### The future of software

Before this year, backendless software couldn't compete with walled-garden, siloed software. It wouldn't make sense to go through the effort of building a complex productivity app, text editor, ticketing system, etc., if a corporate competitor could outspend and outpace you. Now one designer or engineer can create a complex application in days. What's missing is trust and permanence, since most AI-generated software isn't very trustworthy or long-lasting. This is where being open-source and storing data in portable containers starts to make sense. Knowing that my data will remain accessible to me gives me the assurance I need to take a piece of software seriously, both as a user and as a contributor.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to be perfectly suited to themselves. Where we land will probably be somewhere in the middle. Walled-garden software-as-a-service won't be sustainable when anyone can generate a clone of the application with zero human effort, but that doesn't mean everyone is going to generate their own software, nor does it mean that software companies will stop existing. Software that provides the connectivity and infrastructure for people and AIs to build complex applications will do just fine.

If things go well, we may even see an entirely new class of software, neither one-off code generations, nor deep infrastructure, but open-source applications on shared data stores that actually look a lot more like software we use today, which we work together to build in the commons.
