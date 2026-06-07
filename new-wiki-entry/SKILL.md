---
name: new-wiki-entry
description: Create a new wiki entry in the vault with correct YAML frontmatter. Use when adding a goal, pattern, or knowledge entry to vault/wiki/.
---

When creating a wiki entry:
1. Ask for: title, type (goal/pattern/context/place), and any tags
2. Derive a kebab-case slug from the title (matching the slugify() behavior in server/src/wiki/manager.ts)
3. Write the file to vault/wiki/<slug>.md with this frontmatter:

```yaml
---
title: <title>
type: <type>
tags: [<tags>]
created: <ISO date>
updated: <ISO date>
---
```

4. Add a brief content section below the frontmatter
5. Remind the user that the server will pick up the new file via vault hot-reload
