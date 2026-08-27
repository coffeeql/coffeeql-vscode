# CoffeeQL for VS Code

[![Version](https://img.shields.io/visual-studio-marketplace/v/coffeeql.coffeeql?color=blue&label=VS%20Code%20Marketplace)](https://marketplace.visualstudio.com/items?itemName=coffeeql.coffeeql)
[![Installs](https://img.shields.io/visual-studio-marketplace/i/coffeeql.coffeeql)](https://marketplace.visualstudio.com/items?itemName=coffeeql.coffeeql)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

Syntax highlighting, snippets, and hover documentation for [CoffeeQL](https://coffeeql.dev) — the universal query language for any database.

---

## What is CoffeeQL?

CoffeeQL is a single query syntax that works across PostgreSQL, MongoDB, MySQL, and Redis — available on npm, PyPI

```coffeeql
// Same syntax. Every database. Every runtime.
users[].where(plan = "pro", active = true).give(name, email).cup(10)
```

---

## Features

### Syntax Highlighting

Full highlighting for `.cql` files including:

- **Chain operations** — `.where` `.give` `.sort` `.cup` `.blend` `.mix` `.pour` `.refill` `.spill` `.stream`
- **Collection types** — `users[]` (relational), `products{}` (document), `session:key{}` (key-value)
- **Aggregates** — `COUNT()` `SUM()` `AVG()` `MAX()` `MIN()`
- **Special methods** — `.near()` `.like()` `.has()` `.last()`
- **Built-in functions** — `uuid()` `now()` `today()`
- **Data types** — `UUID` `TEXT` `INT` `FLOAT` `BOOL` `DATETIME` `GEOPOINT` `VECTOR`
- **Constraints** — `PRIMARY` `UNIQUE` `NOT NULL`
- **Comments** — `//`

### Snippets

Type a prefix and press `Tab` to expand:

| Prefix | Description |
|--------|-------------|
| `query` | Basic query with `.where` and `.cup` |
| `queryg` | Query with `.give` |
| `querys` | Query with `.sort` |
| `pour` | Insert a new record |
| `refill` | Update matching records |
| `spill` | Delete matching records |
| `mix` | Join two collections |
| `blend` | Group by with aggregate |
| `stream` | Streaming query (v0.5.0+) |
| `grind` | Define a collection schema |
| `shot` | Batch multiple queries |
| `near` | Geolocation proximity query |
| `like` | Vector similarity search |
| `last` | Time-based filter |
| `count` | Count with group by |
| `menu` | Inspect collection schema |
| `raw` | Raw query passthrough |

### Hover Documentation

Hover over any CoffeeQL keyword to see:
- What it does
- Valid usage examples
- Supported operators and options
- Tips and warnings

Supported keywords: `.where` `.give` `.sort` `.cup` `.blend` `.mix` `.pour` `.refill` `.spill` `.stream` `shot` `grind` `menu` `.near` `.like` `.last` `COUNT` `SUM` `AVG` `MAX` `MIN`

---

## Installation

### From VS Code

1. Open VS Code
2. Press `Ctrl+Shift+X` to open Extensions
3. Search for **CoffeeQL**
4. Click **Install**

### From Marketplace

[Install from VS Code Marketplace →](https://marketplace.visualstudio.com/items?itemName=coffeeql.coffeeql)

### From VSIX

```bash
code --install-extension coffeeql-0.1.0.vsix
```

---

## File Association

CoffeeQL highlighting applies automatically to `.cql` files.

To enable CoffeeQL highlighting in other file types, add this to your VS Code `settings.json`:

```json
{
  "files.associations": {
    "*.coffeeql": "coffeeql",
    "*.coffeeql": "coffeeql"
  }
}
```

---

## Quick Start

Create a file called `queries.cql` and start writing:

```coffeeql
// Fetch pro users
users[].where(plan = "pro", active = true).give(name, email).cup(10)

// Insert a record
users[].pour({ id: uuid(), name: "Khushvi", plan: "pro", active: true })

// Update a record
users[].where(id = "usr_001").refill({ plan: "enterprise" })

// Delete records
users[].where(active = false).spill()

// Join collections
users[]
  .mix(orders[] ON users[].id = orders[].user_id)
  .give(users[].name, orders[].amount)
  .cup(20)
```

---

## Install CoffeeQL

```bash
# Python
pip install coffeeql

# JavaScript / Node.js
npm install coffeeql

# Dart / Flutter
dart pub add coffeeql
```

---

## Links

- [coffeeql.dev](https://coffeeql.dev) — documentation
- [GitHub](https://github.com/coffeeql) — source code
- [npm](https://npmjs.com/package/coffeeql) — JavaScript package
- [PyPI](https://pypi.org/project/coffeeql) — Python package
---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to contribute to the extension.

## License

MIT — see [LICENSE](LICENSE)
