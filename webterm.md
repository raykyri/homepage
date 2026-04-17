---
fonts: Open Sans@400,700
css: li, p, h1, h2, h3, h4, h5 { font-family: Open Sans }
---

### Webterm

_April 2026_

There's a world of difference between "effectively free" and actually free. It's the difference between Facebook and email, or Notion and text files.

Today, getting a shell environment, which is required to do most interesting work using agents, is close to free. As a result, people building AI-enabled applications have to spend money on their own API keys, or write complex integrations and reimplement tools that already come with Claude Code and Codex.

Webterm is an environment for these agents that's actually free.

It's a WebAssembly shell that runs inside your browser tab, without an external server, and lets you launch agents like Claude Code, Gemini, and Pi as if you were on your local computer, so you can:

* Chat with any GitHub repo by opening Webterm to the repo, using your existing Claude or Codex subscription.
* Use any coding agent that runs on Node.js. You can use Claude Code for Anthropic models, and [Pi](https://pi.dev/) for Codex/Gemini. Gemini's CLI works too: `npm install -g @google/gemini-cli`.
* You can install any Node.js or Python package that doesn't depend on native binaries, or run `npx` command-line tools, all isolated in the browser environment.
* Your logins and sessions are automatically synced outside the terminal, so once you've logged into one Webterm with Claude Code or Pi, you won't have to do it again.

Want to try out a new [agent skill](https://skills.sh)? Or experiment with that new context management tool or agent orchestrator? There's a good chance that you can now do that without leaving your browser.

---

### Who's this for?

Ever wished [skills.sh](https://skills.sh/) was a live interactive social network, where you could play with every skill individually? Or that design tools in the browser like [Jam](https://jam.dev/) or [Agentation](https://www.agentation.com/) actually... had an agent in the browser?

Webterm might be useful for a range of developers -- anyone launching an agent skill, for example, could give users a playground. Using our sync layer, users could download and resume others' sessions.

Unlike a server-side sandbox or VM, terminals are gone as soon as you close your tab. As a developer, you should treat terminals as ephemeral sessions, keeping important artifacts (e.g. agent outputs, session logs) in the database.

If you want a persistent sandbox, there are a lot of great offerings for that; you should use one of those! But this terminal is a much lighter building block. You should use it when you want to add a coding agent to the frontend of your application, without rebuilding your application around an agent somewhere else.

---

### How it works

This version of Webterm is an early release, so I haven't separated it out into its own package yet. (If you're interested in using it, please send me a DM!)

The best way to use Webterm is through Input, a Markdown editor and alternative frontend to GitHub. It comes with the ability to retrieve repos, track commit history, and stage complex changes. I'm in the process of refactoring it so Input and Webterm each stand on their own.

But beyond that, Webterm is basically a "distro" built on WebContainers. It adds:

- A filesystem sync daemon that batches changes in/out of the terminal, and allows each terminal to be started with preconfigured tools like pi and claude
- A network bridge that translates network requests from inside the terminal to ones that can be made through CORS/a server
- A set of Node.js shims that route network requests through the bridge
- A set of shell tools, including reimplementations of `find`, `grep`, `nano`
- A terminal (ghostty-web) and interface tweaks to work around various bugs in WebContainers

Being based on WebContainers means that open-source projects are free to use us, as a wrapper around WebContainers. Signing up is pretty easy: go to [StackBlitz](https://stackblitz.com/), get an API key from the console, and drop it into our JS configuration.

The core idea behind WebContainers is to run any Node.js application, which is a massive scope, but when you scope it down to "run the top coding agents in the browser, plus the tools they call", it becomes much more manageable.

The one limitation is that WebContainers are entirely closed-source, where users are dependent on their hosted infrastructure. For terminals like these to become widely accessible, we need a more permissive Node.js in the browser. There are a few options there, that are interesting to pursue in the long term.

If this is interesting to you, or you'd like to follow along, find me at [@rei_v5](https://x.com/rei_v5) on X or [@raymond.bsky.social](https://bsky.app/profile/raymond.bsky.social) on Bluesky!

---

### References

- Webterm is partly inspired by just-bash, a Vercel Labs package which implements a shell in the browser using a very different approach.
- There are a few other Node.js reimplementations in the browser, like [AlmostNode](https://almostnode.dev/), [BrowserPod](https://browserpod.io/), [NodePod](https://scelar.com/blog/introducing-nodepod). Vercel also has [quickjs-wasi](https://github.com/vercel-labs/quickjs-wasi), which lacks Node's API surface.
- We also investigated using [EdgeJS](https://github.com/wasmerio/edgejs) with [WASIX](https://wasix.org/) as the POSIX compatibility layer, but EdgeJS isn't targeting the browser yet.
