# Calculator App

A modern, interactive calculator application built with **React**, **TypeScript**, and **Vite**.

## Overview

This project provides a clean, fully-functional calculator with a dark card UI on a light background. It supports all standard arithmetic operations, formatted number display, input validation, and error handling.

## Features

- **4×5 Button Grid** — full calculator layout with operations (+, −, ×, ÷), functions (AC, %, ±, ⌫), and decimal support
- **Smart Display** — numbers formatted with space thousands separators (e.g., `1 234 567.89`)
- **Input Validation** — maximum 10-digit limit with an auto-hiding hint message
- **Error Handling** — detects and displays division-by-zero errors
- **Modern Design** — circular buttons color-coded by type, soft shadows, smooth hover transitions

## Tech Stack

| Technology | Purpose |
|---|---|
| React 19 | UI component framework |
| TypeScript | Type-safe JavaScript |
| Vite 7 | Fast build tool and dev server |
| CSS3 | Flexbox/grid layout and styling |
| `Intl.NumberFormat` | Locale-aware number formatting (no external deps) |

## Getting Started

```bash
# Install dependencies
npm install

# Start development server (http://localhost:5173)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Run tests
npm test
```

## Project Structure

```
src/
├── components/
│   ├── Calculator.tsx   # Main container & state management
│   ├── Display.tsx      # Number/hint display
│   └── Button.tsx       # Reusable button component
├── utils/
│   ├── calculator.ts    # Core arithmetic logic
│   ├── format.ts        # Number formatting utility
│   └── types.ts         # TypeScript interfaces
├── App.tsx              # Root component
└── main.tsx             # Entry point
```

## Button Layout

```
AC   ⌫   %   ÷
7    8   9   ×
4    5   6   −
1    2   3   +
±    0   .   =
```

## Usage

1. Click digit buttons (0–9) to enter numbers
2. Click an operator (+, −, ×, ÷) to choose an operation
3. Click `=` to compute the result
4. Click `AC` to reset, `⌫` to delete the last digit, `%` for percentage, `±` to toggle sign

See [DOCUMENTATION.md](./DOCUMENTATION.md) for full developer documentation.

## License

MIT
