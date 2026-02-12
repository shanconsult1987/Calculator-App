# Calculator App Build Plan

## Steps

1. Initialize Vite + React + TypeScript project and install dependencies
2. Create reusable Button component with styling and click handler props
3. Create Display component to show current input/result
4. Build calculator logic utility (handle operations, state management, input validation)
5. Compose main Calculator component integrating display, buttons, and logic
6. Style with CSS using flexbox/grid for centered card layout and minimal design

## Project Setup

```bash
npm create vite@latest calculator-app -- --template react-ts
cd calculator-app
npm install
npm run dev

File Structure
```

src/
├── components/
│   ├── Calculator.tsx          # Main container component
│   ├── Display.tsx              # Display component (shows input/result)
│   └── Button.tsx               # Reusable button component
├── utils/
│   ├── calculator.ts            # Core calculator logic
│   └── types.ts                 # TypeScript interfaces/types
├── styles/
│   ├── Calculator.css           # Calculator layout styles
│   ├── Display.css              # Display styles
│   └── Button.css               # Button styles
├── App.tsx                      # Root app component
├── App.css                      # Global app styles (centering)
└── main.tsx                     # Entry point


Component Breakdown
Calculator.tsx
Manages calculator state (current value, previous value, operation)
Renders Display and 4×5 grid of Buttons
Handles button click events and delegates to calculator utility
Display.tsx
Props: value: string
Displays current input or result
Styled with right-aligned text
Button.tsx
Props: label: string, onClick: () => void, variant?: 'number' | 'operator' | 'function' | 'equals'
Reusable button with conditional styling based on variant
Grid cell item
utils/calculator.ts
handleNumberInput(current: string, digit: string): string
handleOperator(prev: string, current: string, operator: string): string
calculate(num1: string, num2: string, operator: string): string
handleSpecialFunction(current: string, func: 'AC' | '±' | '%' | 'backspace'): string
utils/types.ts

export type Operator = '+' | '−' | '×' | '÷';
export type SpecialFunction = 'AC' | '±' | '%' | '⌫';
export interface CalculatorState {
  display: string;
  previousValue: string;
  operator: Operator | null;
  waitingForOperand: boolean;
}

CSS Architecture
App.css: Center calculator card, dark background
Calculator.css: Card container (max-width, border-radius, shadow), 4×5 grid layout
Display.css: Top section, right-aligned text, large font
Button.css: Base button styles + variants (numbers: white, operators: orange, functions: gray, equals: orange)
Button Layout (4×5 Grid)

Row 1: AC  ⌫  %  ÷
Row 2: 7   8  9  ×
Row 3: 4   5  6  −
Row 4: 1   2  3  +
Row 5: ±   0  .  =

