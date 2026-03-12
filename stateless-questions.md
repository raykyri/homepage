### Backendless Software: Questions

- How are documents named?
  - Currently just by filename. In the future, possibly by title + slug, where the slug is a filename without extension.
- How do you store share links?
  - Front matter, as `share_links: [hash]` for share links, and `share_users: [handle]` for sharing with users
- How do you store wiki links?
  - Inline, as `[[file-name]]`. Wiki links are references to .md files, including in /.concepts
- How do you create directories or nested documents?
  - As directories in Git. Empty directories are not supported.
- How do you store comments?
  - As a .comments.md file, stateless-questions.comments.md. Comment identities cannot be verified without creating an index of GitHub users and assigning Keybase-style public keys to them.
- Rich text editing?
  - Yes please