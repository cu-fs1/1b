# Simple Banking UI

A responsive banking application with deposit and withdrawal functionality. This project demonstrates HTML structure, CSS styling, and JavaScript event handling.

---

## File Explanations

### index.html

The HTML file provides the structure for the banking interface:

- **Document Setup**: Uses HTML5 DOCTYPE and UTF-8 charset for proper character encoding
- **Meta Tags**: Includes viewport meta tag for responsive design on mobile devices
- **Title**: "Simple Banking UI" displayed in the browser tab
- **Stylesheet**: Links to `styles.css` for styling

**Main Elements**:
- **Balance Display**: An `<h1>` element with id `balance-display` that shows the current account balance (initialized at $1000)
- **Banking Form**: A form with id `banking-form` containing:
  - **Amount Input**: A number input field (id: `amount`) that accepts decimal values with step="0.01" for currency precision
  - **Deposit Button**: A button with id `deposit-btn` that uses `onclick="handleDeposit()"` to trigger the deposit function
  - **Withdraw Button**: A button with id `withdraw-btn` with an event listener for withdrawal functionality
  - **Error Message**: A paragraph element (id: `error-message`) that displays validation errors
- **Script**: Links to `script.js` for JavaScript functionality

---

### styles.css

The CSS file handles all visual styling and layout:

**Theme Colors**:
- Primary Blue (`#1e40ff`): Used for deposit button
- Error Red (`#dc3545`): Used for error messages and withdraw button

**Layout Structure**:
- **Body**: Uses flexbox to center the container vertically and horizontally on the page
- **Banking Container**: A white card with 400px width, rounded corners (8px), and padding (40px)

**Typography**:
- Imports "Inter" and "Poppins" fonts from Google Fonts
- Default system font stack as fallback: `-apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto"`
- Balance display is 36px bold text centered
- Input label is 18px regular text

**Input Field Styling**:
- Default state: Red border indicating invalid/empty state
- Valid state: Green border (`#22c55e`) when valid amount is entered
- Focus state: Green outline when focused with valid input
- Full width with 12px padding

**Button Styling**:
- Both buttons have 14px padding, rounded corners, and cursor pointer
- Deposit button: Blue background
- Withdraw button: Red background
- Both buttons have hover effect with 0.9 opacity

**Error Message**:
- Red text, 18px font size, centered alignment
- Can be toggled visible/hidden via JavaScript

**Responsive Design**:
- Mobile view: Full width with adjusted container padding, smaller balance text, single-column button layout
- Applies at 480px minimum width breakup

---

### script.js

The JavaScript file handles all functionality and data persistence:

**Data Storage**:
- **Balance Variable**: Loads from browser's localStorage with key "bankBalance" or defaults to $1000
- Updates localStorage whenever balance changes to persist data across browser sessions

**DOM References**:
- Caches references to all interactive elements: balance display, input field, buttons, error message, and form

**Utility Functions**:
- **updateBalance()**: Updates the balance display text and saves to localStorage
- **showError()**: Makes the error message visible (display: block)
- **hideError()**: Hides the error message (display: none)
- **validateAmount()**: Checks if amount is positive and a valid number

**Deposit Functionality** (`handleDeposit()`):
- Called via `onclick` attribute on the deposit button
- Validates the amount input
- If valid: Adds amount to balance, updates display, clears input, hides error
- If invalid: Shows error message

**Withdraw Functionality**:
- Event listener on withdraw button
- Validates amount is positive
- Checks if sufficient funds exist
- If insufficient: Shows "Insufficient funds!" error message
- If valid: Subtracts amount from balance, updates display, clears input, hides error

**Input Validation**:
- Real-time input listener that validates on each keystroke
- Valid amount adds "valid" class to input (green border)
- Invalid amount removes "valid" class and shows error
- Provides instant visual feedback to the user

**Form Submission Prevention**:
- Prevents default form submission behavior to avoid page reload

---

## Glossary of Abbreviations

| Abbreviation | Full Form |
|--------------|-----------|
| **HTML** | HyperText Markup Language |
| **CSS** | Cascading Style Sheets |
| **DOM** | Document Object Model |
| **API** | Application Programming Interface |
| **JSON** | JavaScript Object Notation |
| **UTF-8** | 8-bit Unicode Transformation Format |
| **DOCTYPE** | Document Type Declaration |
| **SVG** | Scalable Vector Graphics |
| **PNG** | Portable Network Graphics |
| **px** | Pixels |
| **rem** | Root Element |
| **em** | Element |
| **RGB** | Red, Green, Blue |
| **RGBA** | Red, Green, Blue, Alpha |
| **NaN** | Not a Number |
