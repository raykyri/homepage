## Stateless Software

Input is a document editor I've been working on — it's like if Obsidian were in your browser, or HackMD used GitHub as a backend.

Every file on Input is backed by a Git repo. The URL raykyri.input.md is automatically mapped to the public repo at `raykyri/homepage` [on GitHub](https://github.com/raykyri/homepage), and we fetch and render Markdown files as users visit the site.

Input implements the *stateless software* pattern: we don't introduce a new backend. GitHub is your backend. The app is just a thin caching layer.

This means a few things:

- No lock-in.
- You can easily fork the app, and/or add your own customizations.
- You can use Input with existing tools that connect to GitHub (e.g. Claude Code Web, Cursor Agents, or Obsidian).
- There's a strict schema for everything that gets stored (in this case Markdown), which works like a protocol.

### The past

Stateless software isn't new. [Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications to work this way, without a backend. They cobbled together a patchwork of APIs to give people persistence.

But I've never actually used Google Drive or Dropbox's APIs for serious persistence for third-party services, and I doubt that most people have either. They feel not quite like a home drive, even though they can work like one.

### The future

So why do I think this paradigm could work now? The first reason is that we've gotten used to connecting a long list of applications to GitHub: Cursor Agents, Claude, Codex, plus code review tools, test runners, and more.

As people start using applications like Claude Code for everything, Git repos suddenly start looking a lot more compelling as a system of record.

The second reason is that stateless software is a compelling progressive enhancement over local-first software. Local-first has gained momentum in the last few years, as people started to look for alternatives to popular online services that have started raising their prices.

But the model itself is limiting. I tried Obsidian and stopped using it because it wasn't helping me publish or get work out into the world... but writing documents in the browser feels like putting down words for other people to read.

### Beyond local-first

I want a web app! I want to be able to access my words from any computer, and to publish pages easily without having to set up Obsidian Sync or Obsidian Wikis.

Using a tool like Input, I don't have to think about that. I just write and it syncs to my personal Git repos. I have separate repos for public and private work, and I can switch quickly between drafts and published work. The tighter feedback loop seems to make my writing better, because the writing feels realistic - more like I'm writing for someone else to read, not editing a "second brain" or "tool for thought".

I like the ideals of local-first software, but stateless backends are much more appealing to me when I think about the kinds of software that people want to use.

### Behind the scenes

Why haven't people built software this way before?

One reason is it involves a surprising amount of complexity. For example, GitHub's APIs don't give you consistency, which means that naively using the API will break in a bunch of different ways. If the backend isn't configured properly, you'll edit a file and find some edits are lost, or that changes don't stick.

Developers also have to deal with rate limits, 409 Conflict errors, and handling 99th percentile load scenarios — what happens if a million people show up one day when a blog post goes viral?.

The backing API for a service like GitHub is designed to serve a much smaller number of users, so we have to design aggressive caching policies that kick in when load goes over a certain limit.

And yet, Claude and Codex have made it possible to address many of these issues. (Personally, it's been enough that Input has replaced Obsidian and other editors as a piece of software that I use every day.)

### Quality stateless software

Before this year, stateless software couldn't compete with walled-garden, siloed software. It didn't make sense to go through the effort of building a complex text editor, productivity app, etc., if a corporate competitor could outspend and outpace you.

And so people ended up using tools like Asana and Monday.com, and the successful ones would charge enterprises tens of thousands of dollars a year.

With Claude Code and Codex, one designer or engineer can now recreate an app like Monday.com in a week. Deep down, I think people understand that there's been a shift, but we don't know what it means. Most "vibe coded" software isn't yet the quality that it needs to be to compete.

I think in the next few years we'll start seeing much higher quality software that's built this way. Most vibe coded apps that ask you to entrust data to their own databases will fade, while apps that plug into your own data stores will survive.

There's a model here that should be appealing to enterprises, who intuitively understand the value of "on-prem", who can easily deploy an engineer with a coding agent if they need to make changes or fixes.

### New models

For individuals, the sell is that stateless software can actually be faster, easier to use, and more customizable than off-the-shelf software. A benevolent dictator can have a higher quality bar than a profit-motivated corporation, especially if they come from a design engineering background.

Independent developers building these kinds of tools don't need to close five- and six-figure contracts; they can subsist via sponsorships and subscriptions, serving hundreds of thousands of users using modern tech.

It also opens the door to playful, artistic applications that help people develop new kinds of capabilities. If I were working on communal software, malleable software, or decentralized networks today, I'd seriously consider taking this approach.

Many people have tried to call the future of coding by saying that "software is dead", or that everyone will have personal software that they customize to their heart's content. I find both of those positions to be a bit implausible; instead, I think this is a far more compelling vision for the democratization of software.
