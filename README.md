# Simple Banking UI

A simple banking application that allows users to deposit and withdraw money with real-time balance updates. The application uses local storage to persist balance data across browser sessions.

## Code Explanation

### index.html

The HTML file provides the structure for the banking interface:

**Document Structure:**
- `<!DOCTYPE html>` - Declares this as an HTML5 document
- `<html lang="en">` - Root element with English language attribute
- `<head>` section contains metadata:
  - `<meta charset="UTF-8">` - Sets character encoding to UTF-8 for international character support
  - `<meta name="viewport">` - Ensures responsive design on mobile devices
  - `<title>` - Sets the page title shown in browser tabs
  - `<link rel="stylesheet">` - Links to the external CSS file for styling

**Body Content:**
- `<main class="banking-container">` - Main container for the banking interface
- `<h1 id="balance-display">` - Displays the current balance with an ID for JavaScript access
- `<form id="banking-form">` - Contains the banking operations form
  - `<input type="number">` - Number input field for entering amounts with:
    - `step="0.01"` - Allows decimal values (cents)
    - `id="amount"` - Identifier for JavaScript manipulation
  - `<button id="deposit-btn">` - Deposit button with inline `onclick` event handler
  - `<button id="withdraw-btn">` - Withdraw button (event listener added in JavaScript)
  - `<p id="error-message">` - Error message container (initially hidden via CSS)
- `<script src="script.js">` - Links to external JavaScript file

### styles.css

The CSS file handles all visual styling and layout:

**CSS Variables:**
- `:root` selector defines reusable color variables:
  - `--primary-blue: #1e40ff` - Blue color for deposit button
  - `--error-red: #dc3545` - Red color for errors and withdraw button

**Global Styles:**
- `* { ... }` - Universal selector resets margins and padding, applies border-box sizing
- `body` - Centers content using flexbox, sets background color and typography

**Component Styles:**
- `.banking-container` - White card with rounded corners (8px radius) and 40px padding
- `.balance-display` - Large (36px), bold text centered for balance visibility
- `.input-field` - Styled input with red border by default, green border when valid
- `.input-field:focus` - Removes default outline and adds custom focus styles
- `.actions` - Grid layout with 2 columns for side-by-side buttons
- `.btn` - Base button styling with padding, border-radius, and white text
- `.btn-deposit` - Blue background using CSS variable
- `.btn-withdrawal` - Red background using CSS variable
- `.error-message` - Red, centered error text

**Responsive Design:**
- `@media (min-width: 480px)` - Adjusts layout for smaller screens:
  - Reduces padding and container width
  - Changes button grid to single column
  - Reduces balance font size

### script.js

The JavaScript file implements the banking logic and interactivity:

**State Management:**
- `localStorage.getItem("bankBalance")` - Retrieves saved balance from browser storage
- `parseFloat()` - Converts string to decimal number
- `|| 1000` - Uses default value of 1000 if no saved balance exists

**DOM References:**
- Multiple `document.getElementById()` calls store references to HTML elements for efficient access

**Core Functions:**

1. `updateBalance()` - Updates display and saves to localStorage
   - Uses template literal to format balance text
   - `localStorage.setItem()` persists data across sessions

2. `showError()` / `hideError()` - Toggle error message visibility by changing CSS display property

3. `validateAmount(amount)` - Validates user input:
   - Checks if amount is positive
   - Uses `isNaN()` to verify it's a valid number

4. `handleDeposit()` - Processes deposit transactions:
   - Parses input value to float
   - Validates amount
   - Adds to balance using `+=` operator
   - Clears input field after successful deposit

**Event Listeners:**

1. **Withdraw Button** - `addEventListener("click", ...)`:
   - Validates amount
   - Checks for sufficient funds
   - Subtracts from balance using `-=` operator
   - Shows custom error message for insufficient funds

2. **Amount Input** - `addEventListener("input", ...)`:
   - Real-time validation as user types
   - Adds/removes "valid" CSS class for visual feedback
   - Shows/hides error messages dynamically

3. **Form Submit** - `addEventListener("submit", ...)`:
   - `e.preventDefault()` prevents page reload on form submission

**Initial Load:**
- `updateBalance()` is called immediately to display loaded balance

## Glossary of Terms

### HTML Abbreviations
- **HTML** - HyperText Markup Language
- **DOCTYPE** - Document Type Declaration
- **UTF** - Unicode Transformation Format
- **UI** - User Interface
- **SVG** - Scalable Vector Graphics
- **ID** - Identifier

### CSS Abbreviations
- **CSS** - Cascading Style Sheets
- **URL** - Uniform Resource Locator
- **RGB/RGBA** - Red Green Blue / Red Green Blue Alpha
- **PX** - Pixels
- **VH** - Viewport Height
- **FR** - Fractional Unit (CSS Grid)
- **REM** - Root Em (relative unit)

### JavaScript Abbreviations
- **JS** - JavaScript
- **DOM** - Document Object Model
- **NaN** - Not a Number
- **API** - Application Programming Interface
- **JSON** - JavaScript Object Notation

### General Programming Terms
- **localStorage** - Browser API for storing key-value pairs persistently
- **parseFloat** - Function to convert strings to floating-point numbers
- **addEventListener** - Method to attach event handlers to DOM elements
- **getElementById** - Method to select HTML elements by their ID attribute
- **preventDefault** - Method to stop default browser behavior
- **Template Literal** - String syntax using backticks (`) for variable interpolation
- **CSS Variable** - Custom property defined with -- prefix for reusable values
- **Event Handler** - Function that responds to user interactions
- **Flexbox** - CSS layout model for flexible responsive design
- **Grid** - CSS layout system for two-dimensional layouts
- **Responsive Design** - Approach to make web pages adapt to different screen sizes
- **Media Query** - CSS technique to apply styles based on device characteristics