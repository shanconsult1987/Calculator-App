# Test Suite Summary

## Overview

Comprehensive unit tests for the Calculator App using **Vitest** and **React Testing Library**. Tests cover all components, utilities, and main application logic with 100+ test cases.

## Test Files Structure

All test files are colocated with their corresponding source files using `.spec.ts` or `.spec.tsx` naming convention.

### Test Files

```
src/
├── utils/
│   ├── calculator.spec.ts         # 24 tests - Core calculation logic
│   └── format.spec.ts             # 13 tests - Number formatting utility
├── components/
│   ├── Button.spec.tsx            # 10 tests - Button component
│   ├── Display.spec.tsx           # 13 tests - Display component
│   └── Calculator.spec.tsx        # 45+ tests - Main calculator logic
└── App.spec.tsx                   # 3 tests - App root component
```

**Total: 100+ Tests**

---

## Test Coverage by Module

### 1. Calculator Utils (`src/utils/calculator.spec.ts`) - 24 Tests

**`handleNumberInput()`**
- ✅ Append digit to existing number
- ✅ Replace 0 with first digit
- ✅ Allow decimal point addition
- ✅ Prevent duplicate decimal points
- ✅ Allow zero before decimal
- ✅ Add decimal after 0

**`calculate()`**
- ✅ Add two numbers
- ✅ Subtract two numbers
- ✅ Multiply two numbers
- ✅ Divide two numbers
- ✅ Return Error on division by zero
- ✅ Handle decimal numbers
- ✅ Handle negative numbers
- ✅ Round floating point results
- ✅ Return 0 for invalid inputs

**`handleOperator()`**
- ✅ Return current value when no previous value
- ✅ Calculate result when chaining operations

**`handleSpecialFunction()`**
- ✅ Clear to 0 with AC
- ✅ Toggle sign with ±
- ✅ Convert to percentage with %
- ✅ Backspace with ⌫
- ✅ Handle edge cases (0, decimals, trailing dots)

---

### 2. Format Utils (`src/utils/format.spec.ts`) - 13 Tests

**`formatNumberDisplay()`**
- ✅ Format whole numbers with space thousands separator (1 234)
- ✅ Format large numbers with multiple separators (1 234 567)
- ✅ Handle decimal numbers (1 234.56)
- ✅ Handle negative numbers (-1 234 567)
- ✅ Preserve trailing decimal point (1 234.)
- ✅ Handle numbers starting with decimal (.5 → 0.5)
- ✅ Return Error as-is
- ✅ Handle very large numbers
- ✅ Handle numbers with many decimal places

---

### 3. Button Component (`src/components/Button.spec.tsx`) - 10 Tests

- ✅ Render button with label
- ✅ Call onClick handler when clicked
- ✅ Apply variant CSS classes (number, operator, function, equals)
- ✅ Apply base btn class
- ✅ Render special symbols correctly (÷, ±, ⌫, ×, −)

---

### 4. Display Component (`src/components/Display.spec.tsx`) - 13 Tests

- ✅ Render display value
- ✅ Format display with thousands separator
- ✅ Display decimal numbers
- ✅ Render hint message
- ✅ Hide/show hint based on provided value
- ✅ Apply show class to hint when provided
- ✅ Handle Error state
- ✅ Handle negative numbers and zero
- ✅ Check display-value class structure

---

### 5. Calculator Component (`src/components/Calculator.spec.tsx`) - 45+ Tests

**Display**
- ✅ Initialize with 0
- ✅ Display entered numbers
- ✅ Display multiple digits

**Number Input**
- ✅ Replace 0 with first digit
- ✅ Allow decimal input
- ✅ Prevent duplicate decimals
- ✅ Enforce 10-digit limit
- ✅ Allow backspace at digit limit

**Arithmetic Operations**
- ✅ Addition (5 + 3 = 8)
- ✅ Subtraction (10 − 3 = 7)
- ✅ Multiplication (6 × 7 = 42)
- ✅ Division (20 ÷ 4 = 5)
- ✅ Division by zero (returns Error)
- ✅ Multiple chained operations

**Special Functions**
- ✅ Clear with AC button
- ✅ Toggle sign with ± button
- ✅ Backspace with ⌫ button
- ✅ Percentage with % button

**Operator Chaining**
- ✅ Chain multiple operations correctly

**Decimal Operations**
- ✅ Handle decimal addition and complex calculations

**Button Layout**
- ✅ Render 20 buttons (4×5 grid)
- ✅ All required button labels present

**Display Formatting**
- ✅ Format large results with thousands separators

**Hint Messages**
- ✅ Auto-hide hint after 3 second timeout

---

### 6. App Component (`src/App.spec.tsx`) - 3 Tests

- ✅ Render Calculator component
- ✅ Render all 20 calculator buttons
- ✅ Render app container with proper class

---

## Running Tests

### Install Dependencies
```bash
npm install
```

### Run All Tests
```bash
npm test
```

### Run Tests in Watch Mode
```bash
npm test -- --watch
```

### Run Tests Once (CI Mode)
```bash
npm run test:run
```

### View Tests in UI
```bash
npm run test:ui
```

### Generate Coverage Report
```bash
npm run test:coverage
```

---

## Test Commands

| Command | Purpose |
|---------|---------|
| `npm test` | Run tests in watch mode (default Vitest behavior) |
| `npm run test:run` | Run tests once and exit |
| `npm run test:ui` | Interactive UI dashboard for running tests |
| `npm run test:coverage` | Generate coverage report |

---

## Configuration

### vitest.config.ts
```typescript
- Environment: happy-dom (lightweight DOM implementation)
- Globals: true (no need to import describe, it, expect)
- Coverage: v8 provider
- Path alias: @ → ./src
```

---

## Key Testing Patterns

### Component Testing
- Uses `@testing-library/react` for component rendering
- Tests user interactions with `fireEvent`
- Verifies output with `screen` queries

### Utils Testing
- Direct function calls with various inputs
- Boundary condition testing
- Edge case coverage

### Async Testing
- Uses `waitFor` for async assertions
- Tests hint auto-hide with fake timers

---

## Example Test

```typescript
it('should add two numbers', () => {
  render(<Calculator />);
  fireEvent.click(screen.getByRole('button', { name: '5' }));
  fireEvent.click(screen.getByRole('button', { name: '+' }));
  fireEvent.click(screen.getByRole('button', { name: '3' }));
  fireEvent.click(screen.getByRole('button', { name: '=' }));
  expect(screen.getByText('8')).toBeInTheDocument();
});
```

---

## Coverage Goals

- ✅ **Utilities**: 100% coverage
- ✅ **Components**: All user interactions covered
- ✅ **Edge Cases**: Decimals, negatives, limits, errors
- ✅ **State Management**: Calculator state transitions
- ✅ **UI**: Button rendering, display formatting, hints

---

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `vitest` | ^1.0.4 | Test runner |
| `@testing-library/react` | ^14.1.2 | Component testing |
| `@testing-library/jest-dom` | ^6.1.5 | Matchers |
| `happy-dom` | ^12.10.3 | DOM implementation |
| `@vitest/ui` | ^1.0.4 | Test UI dashboard |

---

## Continuous Integration

Tests can be integrated into CI/CD pipelines using:
```bash
npm run test:run
```

This runs all tests once and exits with appropriate status code for CI systems.

---

## Troubleshooting

**Tests not running?**
- Ensure `npm install` completed successfully
- Check Node.js version (16+)

**Import errors?**
- Clear `node_modules`: `rm -rf node_modules && npm install`
- Rebuild: `npm run build`

**Async test timeout?**
- Increase timeout in test: `{ timeout: 10000 }`

---

**Last Updated**: January 29, 2026  
**Status**: Complete ✓
