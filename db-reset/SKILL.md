---
name: db-reset
description: Reset the NextTurn SQLite database to a clean seeded state (deletes data/nextturn.db, re-initializes schema, runs demo seed)
disable-model-invocation: true
---

Run the following to reset the database to demo state:

```bash
rm -f data/nextturn.db && npm run init-db && npm run seed
```
