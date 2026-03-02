## Stateless Software

Input is a document editor — it's like Obsidian if it worked in your browser. Or HackMD, if it were built on Github.

Input implements the *stateless software* pattern: we don't introduce a new backend. Github is your backend; we are just a thin caching layer on top of Github.

Importantly, this means a few things:

- No lock-in.
- You can easily fork it and build your own version.
- You can use Input with your existing tools, which probably already connect to Github (e.g. use Claude Code Web, or Cursor Agents, to update your site)
- Data-oriented design. We have to define a strict schema for everything we store.

Stateless software isn't new. [Draw.io](https://draw.io) and [tldraw](https://tldraw.io) were some of the first popular applications to work this way, without a backend. They cobbled together a patchwork of APIs to give people persistence.

I actually think of draw.io as "that app with the Google Drive filepicker" because it's so rare to see one. And I've never actually used Google Drive or Dropbox's APIs for serious persistence. It's just such an unusual design pattern.

But why do I think it could work now? The first is that I have already connected a long list of applications to Github: Cursor Agents, Claude Code Web, Codex, and so on.

The second is the local-first software movement - and that stateless web software is a strict progressive enhancement over local-first software. I tried Obsidian and stopped using it because it wasn't helping me publish or get work out into the world... but writing documents in the browser feels like putting down words for other people to read.

So using a tool like Input, I don't have to think about Obsidian Sync or Obsidian Wikis or another plugin like that. And having a tighter feedback loop seems to make the quality of my writing better, which in turn makes me want to use the tool more.

Before, stateless software couldn't compete with walled garden, siloed software. There were a million Asanas, and Monday.coms, that sold the same simple app, each a silo with its own complex enterprise backend. And they charged companies tens of thousands of dollars a year.

I wonder if, with Claude Code and Codex, more people will start building stateless software. Since agents have leveled the playing field in building complex features, one designer or engineer could recreate not just a functional, but also high-quality version of those applications, served to hundreds of thousands of users.

That person could serve as a benevolent dictator, and actually maintain a higher bar for quality than the average software-as-a-service company.

Many people have talked about vibe coding, or personal software, but I think this is a far more compelling vision of the future of software after automated coding and agentic engineering become something that everyone has access to.

