index.html

# Mainflow
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="appendOperator('/')">/</button>
            <button onclick="appendOperator('*')">x</button>
            <button onclick="appendOperator('-')">-</button>
            <button onclick="appendNumber('7')">7</button>
            <button onclick="appendNumber('8')">8</button>
            <button onclick="appendNumber('9')">9</button>
            <button onclick="appendOperator('+')">+</button>
            <button onclick="appendNumber('4')">4</button>
            <button onclick="appendNumber('5')">5</button>
            <button onclick="appendNumber('6')">6</button>
            <button onclick="calculate()">=</button>
            <button onclick="appendNumber('1')">1</button>
            <button onclick="appendNumber('2')">2</button>
            <button onclick="appendNumber('3')">3</button>
            <button onclick="appendNumber('0')">0</button>
            <button onclick="appendDecimal('.')">.</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>

style.css

body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    font-family: Arial, sans-serif;
}

.calculator {
    width: 250px;
    background-color: #333;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
}

#display {
    width: 100%;
    height: 50px;
    font-size: 24px;
    text-align: right;
    margin-bottom: 10px;
    padding: 10px;
    border: none;
    background-color: #222;
    color: #fff;
    border-radius: 5px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 50px;
    font-size: 20px;
    background-color: #444;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #555;
}



script.js
let display = document.getElementById('display');

function clearDisplay() {
    display.value = '';
}

function appendNumber(number) {
    display.value += number;
}

function appendOperator(operator) {
    const lastChar = display.value.slice(-1);
    if (['+', '-', '*', '/'].includes(lastChar)) {
        display.value = display.value.slice(0, -1) + operator;
    } else {
        display.value += operator;
    }
}

function appendDecimal(decimal) {
    const lastNumber = display.value.split(/[\+\-\*\/]/).pop();
    if (!lastNumber.includes('.')) {
        display.value += decimal;
    }
}

function calculate() {
    try {
        display.value = eval(display.value);
    } catch (error) {
        display.value = 'Error';
    }
}


