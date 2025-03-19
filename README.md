<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        body {
            display: flex;
            height: 100vh;
            justify-content: center;
            align-items: center;
            background-color: #b0b5bd;
        }
        .calculator {
            background-color: #383737;
            padding: 22px;
            border-radius: 13px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            display: grid;
            grid-template-columns: repeat(4, 70px);
            gap: 10px;
        }
        .display {
            grid-column: span 4;
            height: 60px;
            background-color: #222;
            color: #fff;
            text-align: right;
            padding: 10px;
            font-size: 24px;
            border-radius: 8px;
            margin-bottom: 10px;
        }
        .history {
            grid-column: span 4;
            height: 60px;
            background-color: #444;
            color: #fff;
            text-align: right;
            padding: 10px;
            font-size: 18px;
            border-radius: 8px;
            margin-bottom: 10px;
            overflow: auto;
        }
        button {
            height: 60px;
            background-color: #666;
            color: #fff;
            border: none;
            border-radius: 8px;
            font-size: 20px;
            cursor: pointer;
        }
        button.operator {
            background-color: #ff9d00;
        }
        button.equal {
            background-color: #2bd070;
            grid-column: span 2;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="history" id="history"></div>
        <button onclick="clearDisplay()">C</button>
        <button onclick="appendValue('/')" class="operator">/</button>
        <button onclick="appendValue('*')" class="operator">*</button>
        <button onclick="deleteLast()">DEL</button>

        <button onclick="appendValue('7')">7</button>
        <button onclick="appendValue('8')">8</button>
        <button onclick="appendValue('9')">9</button>
        <button onclick="appendValue('-')" class="operator">-</button>

        <button onclick="appendValue('4')">4</button>
        <button onclick="appendValue('5')">5</button>
        <button onclick="appendValue('6')">6</button>
        <button onclick="appendValue('+')" class="operator">+</button>

        <button onclick="appendValue('1')">1</button>
        <button onclick="appendValue('2')">2</button>
        <button onclick="appendValue('3')">3</button>
        <button onclick="calculateResult()" class="equal">=</button>

        <button onclick="appendValue('0')">0</button>
        <button onclick="appendValue('.')">.</button>
    </div>

    <script>
        let display = document.getElementById('display');
        let history = document.getElementById('history');

        function clearDisplay() {
            display.textContent = '0';
        }

        function appendValue(value) {
            if (display.textContent === '0') {
                display.textContent = value;
            } else {
                display.textContent += value;
            }
        }

        function deleteLast() {
            display.textContent = display.textContent.slice(0, -1) || '0';
        }

        function calculateResult() {
            try {
                const result = eval(display.textContent);
                history.textContent += display.textContent + ' = ' + result + '\n';
                display.textContent = result;
            } catch {
                display.textContent = 'Error';
            }
        }
    </script>
</body>
</html>
