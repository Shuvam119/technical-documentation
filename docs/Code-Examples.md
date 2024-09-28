# How to Create a Calculator?

We have used simple `html`, `css `, and `javascript` to create this calculator.

Copy and paste this sample code in your text editor and see the magic.

---

```js title="calculator.js" linenums="1" hl_lines="84-116"
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .calculator {
            width: 200px;
            margin: 100px auto;
            padding: 20px;
            background-color: #f4f4f4;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
        }
        .display {
            width: 100%;
            height: 40px;
            text-align: right;
            padding: 10px;
            background-color: #222;
            color: white;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            margin-bottom: 10px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        .buttons button {
            padding: 15px;
            font-size: 18px;
            border-radius: 5px;
            border: none;
            background-color: #444;
            color: white;
            cursor: pointer;
        }
        .buttons button:hover {
            background-color: #666;
        }
        .buttons .equal {
            grid-column: span 4;
            background-color: #f90;
        }
        .buttons .equal:hover {
            background-color: #fa0;
        }
    </style>
</head>
<body>

<div class="calculator">
    <input type="text" class="display" id="display" disabled>
    <div class="buttons">
        <button onclick="appendNumber('7')">7</button>
        <button onclick="appendNumber('8')">8</button>
        <button onclick="appendNumber('9')">9</button>
        <button onclick="setOperation('/')">/</button>

        <button onclick="appendNumber('4')">4</button>
        <button onclick="appendNumber('5')">5</button>
        <button onclick="appendNumber('6')">6</button>
        <button onclick="setOperation('*')">*</button>

        <button onclick="appendNumber('1')">1</button>
        <button onclick="appendNumber('2')">2</button>
        <button onclick="appendNumber('3')">3</button>
        <button onclick="setOperation('-')">-</button>

        <button onclick="appendNumber('0')">0</button>
        <button onclick="clearDisplay()">C</button>
        <button onclick="setOperation('+')">+</button>
        <button onclick="calculateResult()">=</button>
    </div>
</div>

<script>
    let currentInput = '';
    let previousInput = '';
    let operator = '';

    function appendNumber(number) {
        currentInput += number;
        document.getElementById('display').value = currentInput;
    }

    function setOperation(op) {
        if (currentInput === '') return;
        operator = op;
        previousInput = currentInput;
        currentInput = '';
    }

    function calculateResult() {
        if (currentInput === '' || previousInput === '' || operator === '') return;
        const result = eval(`${previousInput} ${operator} ${currentInput}`);
        document.getElementById('display').value = result;
        currentInput = result;
        operator = '';
        previousInput = '';
    }

    function clearDisplay() {
        currentInput = '';
        previousInput = '';
        operator = '';
        document.getElementById('display').value = '';
    }
</script>

</body>
</html>

```