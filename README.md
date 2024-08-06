<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: linear-gradient(to right, #a8c0ff, #3f2b96);
            color: #fff;
            margin: 0;
            padding: 20px;
            position: relative;
        }

        #container {
            margin: 0 auto;
            max-width: 350px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
            position: relative;
        }

        #display {
            width: 100%;
            margin-bottom: 10px;
            padding: 10px;
            font-size: 24px;
            text-align: right;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        #switch {
            margin-bottom: 20px;
        }

        #switch button {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
            border-radius: 5px;
        }

        .calculator-mode {
            display: none;
        }

        .calculator-mode.active {
            display: block;
        }

        .buttons button {
            width: 60px;
            height: 60px;
            font-size: 18px;
            margin: 5px;
            background: #f1f1f1;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .buttons button:hover {
            background: #ddd;
        }

        #watermark-top, #watermark-bottom {
            position: absolute;
            font-size: 12px;
            color: gray;
            opacity: 0.5;
            pointer-events: none;
            padding: 10px;
        }

        #watermark-top {
            top: 10px;
            left: 10px;
        }

        #watermark-bottom {
            bottom: 10px;
            right: 10px;
        }
    </style>
</head>
<body>
    <div id="watermark-top">M_RIFAT_JR</div>
    <div id="container">
        <div id="calculator">
            <input type="text" id="display" disabled>
            <div id="switch">
                <button onclick="toggleCalculator()">Switch to Scientific</button>
            </div>
            <div id="basic" class="calculator-mode active">
                <!-- Basic Calculator Buttons -->
                <div class="buttons">
                    <button onclick="appendValue('7')">7</button>
                    <button onclick="appendValue('8')">8</button>
                    <button onclick="appendValue('9')">9</button>
                    <button onclick="appendValue('/')">/</button>
                    <button onclick="appendValue('4')">4</button>
                    <button onclick="appendValue('5')">5</button>
                    <button onclick="appendValue('6')">6</button>
                    <button onclick="appendValue('*')">*</button>
                    <button onclick="appendValue('1')">1</button>
                    <button onclick="appendValue('2')">2</button>
                    <button onclick="appendValue('3')">3</button>
                    <button onclick="appendValue('-')">-</button>
                    <button onclick="appendValue('0')">0</button>
                    <button onclick="appendValue('.')">.</button>
                    <button onclick="appendValue('+')">+</button>
                    <button onclick="calculate()">=</button>
                    <button onclick="clearDisplay()">C</button>
                </div>
            </div>
            <div id="scientific" class="calculator-mode">
                <!-- Scientific Calculator Buttons -->
                <div class="buttons">
                    <button onclick="appendValue('Math.sqrt(')">√</button>
                    <button onclick="appendValue('Math.pow(')">^</button>
                    <button onclick="appendValue('Math.sin(')">sin</button>
                    <button onclick="appendValue('Math.cos(')">cos</button>
                    <button onclick="appendValue('Math.tan(')">tan</button>
                    <button onclick="appendValue('Math.log(')">log</button>
                    <button onclick="appendValue('Math.exp(')">exp</button>
                    <button onclick="appendValue('Math.PI')">π</button>
                    <button onclick="clearDisplay()">C</button>
                    <button onclick="appendValue('/')">/</button>
                    <button onclick="appendValue('*')">*</button>
                    <button onclick="appendValue('-')">-</button>
                    <button onclick="appendValue('+')">+</button>
                    <button onclick="appendValue('.')">.</button>
                    <button onclick="calculate()">=</button>
                </div>
            </div>
        </div>
    </div>
    <div id="watermark-bottom">M_RIFAT_JR</div>
    <script>
        function appendValue(value) {
            const display = document.getElementById('display');
            display.value += value;
        }

        function calculate() {
            const display = document.getElementById('display');
            try {
                // Replace math functions with their respective JavaScript functions
                const expression = display.value
                    .replace(/Math.sqrt\(/g, 'Math.sqrt(')
                    .replace(/Math.pow\(/g, 'Math.pow(')
                    .replace(/Math.sin\(/g, 'Math.sin(')
                    .replace(/Math.cos\(/g, 'Math.cos(')
                    .replace(/Math.tan\(/g, 'Math.tan(')
                    .replace(/Math.log\(/g, 'Math.log(')
                    .replace(/Math.exp\(/g, 'Math.exp(')
                    .replace(/Math.PI/g, 'Math.PI');
                display.value = eval(expression);
            } catch {
                display.value = 'Error';
            }
        }

        function clearDisplay() {
            const display = document.getElementById('display');
            display.value = '';
        }

        function toggleCalculator() {
            const basic = document.getElementById('basic');
            const scientific = document.getElementById('scientific');
            const switchButton = document.getElementById('switch').querySelector('button');

            if (basic.style.display === 'none') {
                basic.style.display = 'block';
                scientific.style.display = 'none';
                switchButton.textContent = 'Switch to Scientific';
            } else {
                basic.style.display = 'none';
                scientific.style.display = 'block';
                switchButton.textContent = 'Switch to Basic';
            }
        }
    </script>
</body>
</html>

