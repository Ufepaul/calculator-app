<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic Calculator</title>
  <style>
    /* CSS Styling */
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      width: 320px;
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }

    #display {
      width: 100%;
      height: 60px;
      background: #e6e6e6;
      border-radius: 5px;
      margin-bottom: 10px;
      text-align: right;
      line-height: 60px;
      font-size: 28px;
      padding: 0 10px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 10px;
    }

    button {
      font-size: 18px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background-color: #f9f9f9;
      transition: background-color 0.3s ease;
      height: 50px;
    }

    button:hover {
      background-color: #e0e0e0;
    }

    /* The clear (C) button spans two columns */
    button:first-child {
      grid-column: span 2;
    }

    /* Optionally, the 0 button spans two columns */
    button.zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <!-- Display Area -->
    <div id="display">0</div>

    <!-- Calculator Buttons -->
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="appendOperator('/')">÷</button>
      <button onclick="appendOperator('*')">×</button>
      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button onclick="appendOperator('-')">-</button>
      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button onclick="appendOperator('+')">+</button>
      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button onclick="calculate()">=</button>
      <button onclick="appendNumber('0')" class="zero">0</button>
      <button onclick="appendNumber('.')">.</button>
    </div>
  </div>

  <script>
    // JavaScript Functionality
    let displayValue = ""; // Stores the current expression

    // Update the display with the current expression or defaults to "0"
    function updateDisplay() {
      const display = document.getElementById("display");
      display.textContent = displayValue || "0";
    }

    // Clears the current display value
    function clearDisplay() {
      displayValue = "";
      updateDisplay();
    }

    // Appends a number or a decimal point to the expression
    function appendNumber(number) {
      displayValue += number;
      updateDisplay();
    }

    // Appends an operator to the expression, ensuring no consecutive operators
    function appendOperator(operator) {
      if (displayValue === "") return; // Prevents adding an operator at start
      const lastChar = displayValue.slice(-1);
      if ("+-*/".includes(lastChar)) return; // Prevent consecutive operators
      displayValue += operator;
      updateDisplay();
    }

    // Evaluates the expression using eval() and updates the display
    function calculate() {
      try {
        displayValue = eval(displayValue).toString();
        updateDisplay();
      } catch (error) {
        alert("Invalid operation!");
      }
    }
  </script>
</body>
</html>
