---
description: Disk based database service
---

# 🗃 Sqlite3

SQLite is great when you want to prototype an application without necessarily investing in a database like PostgreSQL or Oracle. This is made possible because it offers a disk-based database that doesn't require a server.

### Connecting to a server

```python
import sqlite3
con = sqlite3.connect("mydatabase.db")
```

## Common challenges

## `sqlite3.OperationalError: attempt to write a readonly database`

This is because permissions for the `.db` have not been set. Fix this using `chmod`

```sh
chmod 777 database.db
```

## `sqlite3.OperationalError: table scheduler already exists`

This happens because you are attempting to create a table that already exists

Add `IF NOT EXISTS` to the SQL Query to resolve this.

