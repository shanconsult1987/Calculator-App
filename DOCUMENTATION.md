# Calculator App - Developer Documentation

## Project Overview

A modern, interactive calculator application built with **React**, **TypeScript**, and **Vite**. Features a clean, minimal UI with a dark calculator card on a light background, circular buttons, and formatted number display with thousands separators.

### Key Features

- **4×5 Button Grid**: Complete calculator layout with operations (+, −, ×, ÷), functions (AC, %, ±, backspace), and decimal support
- **Smart Display**: Numbers formatted with space thousands separators (e.g., 1 234 567.89)
- **Input Validation**: Maximum 10-digit limit with auto-hide hint message
- **Smooth Interactions**: Hover effects on buttons (color-coded by type), responsive transitions
- **Modern Design**: Light page background, dark card, circular buttons, soft shadows
- **Error Handling**: Division by zero detection and display

---

## Technical Stack

| Technology | Purpose |
|-----------|---------|
| **React 18** | UI component framework |
| **TypeScript** | Type-safe JavaScript |
| **Vite 7.3** | Lightning-fast build tool and dev server |
| **CSS3** | Styling with flexbox and grid |
| **Intl.NumberFormat** | Locale-aware number formatting (no external deps) |

---

## Project Structure

```
src/
├── components/
│   ├── Calculator.tsx          # Main calculator container & state
│   ├── Calculator.css          # Grid layout and card styling
│   ├── Display.tsx             # Number/hint display
│   ├── Display.css             # Display styling
│   ├── Button.tsx              # Reusable button component
│   └── Button.css              # Button styling (circular, colors)
├── utils/
│   ├── calculator.ts           # Core calculation logic
│   ├── format.ts               # Number formatting utility
│   └── types.ts                # TypeScript interfaces
├── App.tsx                      # Root component
├── App.css                      # App layout (centering)
├── index.css                    # Global styles
└── main.tsx                     # Entry point
```

---

## Setup Instructions

### Prerequisites
- **Node.js** 16+ and **npm** (or yarn/pnpm)

### Install Dependencies

```bash
cd Calculator-App
npm install
```

### Development Server

Start the dev server with hot module replacement (HMR):

```bash
npm run dev
```

Opens at `http://localhost:5173/`

### Build for Production

```bash
npm run build
```

Outputs optimized files to `dist/`

### Preview Production Build

```bash
npm run preview
```

Serves the production build locally for testing.

### Linting (Optional)

If ESLint is configured:

```bash
npm run lint
```

---

## Usage Guide

### Basic Calculator Operations

1. **Enter Numbers**: Click digit buttons (0-9) to input numbers
2. **Decimal Point**: Click `.` to add a decimal separator
3. **Operations**: Click `+`, `−`, `×`, `÷` to perform arithmetic
4. **Calculate Result**: Click `=` to compute
5. **Clear**: Click `AC` to reset display and state

### Special Functions

| Button | Action |
|--------|--------|
| **AC** | Clear all (reset to 0) |
| **⌫** | Backspace (remove last digit) |
| **%** | Convert to percentage (÷ 100) |
| **±** | Toggle sign (positive/negative) |

### Display Features

- **Thousands Separator**: Automatically adds spaces every 3 digits (e.g., 1 234 567)
- **Decimal Support**: Maintains decimal places with dot separator
- **Input Hint**: Shows "Max 10 digits" when limit is reached, auto-hides in 3 seconds
- **Error Display**: Shows "Error" for invalid operations (e.g., divide by zero)

### Example Calculations

```
Input: 12345 + 67890 =
Display: 80 235

Input: 1000000 × 2 =
Display: 2 000 000

Input: 100 / 3 =
Display: 33.333333333
```

---

## Key Components

### Calculator.tsx
- Manages calculator state (display, previousValue, operator, waitingForOperand)
- Handles number input with 10-digit limit validation
- Routes button clicks to appropriate handlers
- Manages hint auto-hide timer

### Display.tsx
- Renders current display value and hint messages
- Uses `formatNumberDisplay()` utility for formatting

### Button.tsx
- Reusable button with variants: `number`, `operator`, `function`, `equals`
- Color-coded styling per variant
- Hover effects with smooth transitions

### Utilities

**calculator.ts**
- `handleNumberInput()`: Add digit, prevent duplicate decimals
- `handleOperator()`: Chain calculations
- `calculate()`: Perform arithmetic operations
- `handleSpecialFunction()`: AC, ±, %, backspace

**format.ts**
- `formatNumberDisplay()`: Uses Intl.NumberFormat with fr-FR locale for space separators

**types.ts**
- TypeScript interfaces for operators and calculator state

---

## Development Tips

### Adding a New Operation

1. Add operator type to `types.ts`
2. Implement logic in `calculator.ts` `calculate()` function
3. Add button in `Calculator.tsx` buttons array
4. Test with various inputs

### Customizing Styles

- **Button size**: Edit `.btn` width/height in `Button.css`
- **Card width**: Adjust `.calculator` width in `Calculator.css`
- **Colors**: Modify background-color values in respective CSS files
- **Font**: Update `font-size` in `Display.css`

### Extending Functionality

- **Keyboard Support**: Add keydown handlers in `Calculator.tsx`
- **History**: Store calculations in state array
- **Scientific Mode**: Add trigonometric/logarithmic functions
- **Dark Mode**: Toggle CSS classes based on theme state

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Build fails with TypeScript errors | Run `npm install` and check tsconfig.json |
| Dev server won't start | Kill existing process on port 5173, restart npm run dev |
| Button clicks unresponsive | Check browser console for JavaScript errors |
| Numbers not formatting correctly | Verify `Intl.NumberFormat` locale in `format.ts` |

---

## Performance Notes

- **Zero External Formatting Libraries**: Uses native `Intl.NumberFormat`
- **Minimal Bundle**: ~60KB gzipped (typical Vite + React bundle)
- **No Redux/State Management**: Simple React hooks suffice
- **CSS Grid**: Efficient button layout rendering

---

## Browser Support

- Chrome/Edge 88+
- Firefox 78+
- Safari 14+
- (Intl.NumberFormat widely supported in modern browsers)

---

## License

MIT - Feel free to use and modify as needed.

---

## Quick Reference

```bash
# Install
npm install

# Dev
npm run dev

# Build
npm run build

# Preview build
npm run preview
```

---

**Last Updated**: January 29, 2026  
**Version**: 1.0.0
