# 📝 Text Diff Comparison Tool

A simple, single-page HTML tool for comparing text differences with special support for `.env` file comparisons.

## Features

### Three Comparison Modes

| Mode | Description |
|------|-------------|
| **Line by Line** | Traditional diff view showing added (+), removed (-), and unchanged lines |
| **Inline** | Character-level diff highlighting changes within modified lines |
| **.env Mode** | Order-independent comparison of key=value pairs |

### General Features

- 🔄 **Swap** - Quickly swap original and modified text
- 🗑️ **Clear All** - Reset both input panels
- ⌨️ **Keyboard Shortcut** - Press `Ctrl+Enter` (or `Cmd+Enter` on Mac) to compare
- 📊 **Statistics** - Real-time count of added, removed, and unchanged items
- 📱 **Responsive** - Works on desktop and mobile devices

## Usage

### Basic Text Comparison

1. Open `index.html` in your browser
2. Paste your original text in the left panel
3. Paste your modified text in the right panel
4. Click **Compare Texts** or press `Ctrl+Enter`

### .env File Comparison

The `.env Mode` is specifically designed for comparing environment files where:
- Key order doesn't matter
- You want to see which keys have different values
- You need to identify missing or new keys

#### How to use:

1. Click the **`.env Mode`** button
2. Paste your first `.env` content in "Original Text"
3. Paste your second `.env` content in "Modified Text"
4. Click **Compare Texts**

#### Results are grouped into:

| Section | Icon | Description |
|---------|------|-------------|
| **Modified Values** | ⚡ | Same key exists in both files but with different values |
| **Only in Original** | 🔴 | Keys present only in the first file (missing from second) |
| **Only in Modified** | 🟢 | Keys present only in the second file (new keys) |
| **Identical Keys** | ✓ | Keys with the same values in both files |

## Example

### .env Mode Example

**Original (.env.local):**
```env
DATABASE_URL=postgres://localhost:5432/mydb
API_KEY=abc123
DEBUG=true
PORT=3000
```

**Modified (.env.production):**
```env
PORT=8080
API_KEY=xyz789
DATABASE_URL=postgres://prod-server:5432/mydb
NEW_FEATURE=enabled
```

**Result:**
- ⚡ **Modified**: `DATABASE_URL`, `API_KEY`, `PORT` (values changed)
- 🔴 **Only in Original**: `DEBUG` (missing in production)
- 🟢 **Only in Modified**: `NEW_FEATURE` (new key)

## Color Coding

| Color | Meaning |
|-------|---------|
| 🟢 Green | Added lines/new keys |
| 🔴 Red | Removed lines/missing keys |
| 🟡 Yellow | Modified values |
| ⚪ Gray | Unchanged |

## Technical Details

- **No dependencies** - Pure HTML, CSS, and JavaScript
- **Client-side only** - All processing happens in the browser
- **No data sent anywhere** - Your text never leaves your machine
- **Algorithm** - Uses Longest Common Subsequence (LCS) for accurate diff computation

## Browser Support

Works in all modern browsers:
- Chrome
- Firefox
- Safari
- Edge

## Installation

No installation required! Simply:

```bash
# Open in browser
open index.html

# Or on Linux
xdg-open index.html

# Or on Windows
start index.html
```

## License

MIT License - Free to use and modify.
