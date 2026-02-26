# Calculator App

A modern, interactive calculator built with **React**, **TypeScript**, and **Vite**.

## Features

- **4×5 button grid** — digits, operators (`+` `−` `×` `÷`), and functions (`AC`, `±`, `%`, `⌫`)
- **Smart number formatting** — space thousands separators (e.g. `1 234 567.89`) via `Intl.NumberFormat`
- **Input validation** — 10-digit limit with an auto-hiding hint message
- **Error handling** — detects and displays division-by-zero errors
- **Clean UI** — dark calculator card on a light page, circular buttons, smooth hover transitions

## Tech Stack

| Technology | Role |
|---|---|
| React 19 | UI component framework |
| TypeScript | Type-safe JavaScript |
| Vite | Dev server & production bundler |
| CSS3 (Grid / Flexbox) | Layout and styling |
| `Intl.NumberFormat` | Locale-aware number formatting (no external deps) |

## Quick Start

```bash
# Install dependencies
npm install

# Start development server (http://localhost:5173)
npm run dev

# Run tests
npm test

# Build for production
npm run build
```

## Project Structure

```
src/
├── components/
│   ├── Calculator.tsx   # Main container & state management
│   ├── Display.tsx      # Number / hint display
│   └── Button.tsx       # Reusable button component
├── utils/
│   ├── calculator.ts    # Core arithmetic logic
│   ├── format.ts        # Number formatting helper
│   └── types.ts         # Shared TypeScript interfaces
├── App.tsx              # Root component
└── main.tsx             # Entry point
```

## Button Layout

```
AC   ⌫   %   ÷
 7   8   9   ×
 4   5   6   −
 1   2   3   +
 ±   0   .   =
```

> Rows 2–5 are indented one space so the single-character digits line up visually with the two-character labels in row 1.

## Documentation

See [DOCUMENTATION.md](./DOCUMENTATION.md) for full developer documentation, including component breakdowns, utility API, styling guide, and troubleshooting tips.

## License

MIT
