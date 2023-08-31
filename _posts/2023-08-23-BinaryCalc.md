---
layout: default
title: Calculators
permalink: /calculators
description: Personally made calculators to perform simple computations
type: hacks
courses: { csa: {week: 0} }
---

<script>
function add() {
    var num1 = parseFloat(document.getElementById("num1").value);
    var num2 = parseFloat(document.getElementById("num2").value);
    var answer = num1 + num2;
    document.getElementById("answer").innerHTML = "Result: " + answer;
}
function subtract() {
    var num1 = parseFloat(document.getElementById("num1").value);
    var num2 = parseFloat(document.getElementById("num2").value);
    var answer = num1 - num2;
    document.getElementById("answer").innerHTML = "Result: " + answer;
}
function multiply() {
    var num1 = parseFloat(document.getElementById("num1").value);
    var num2 = parseFloat(document.getElementById("num2").value);
    var answer = num1 * num2;
    document.getElementById("answer").innerHTML = "Result: " + answer;
}
function divide() {
    var num1 = parseFloat(document.getElementById("num1").value);
    var num2 = parseFloat(document.getElementById("num2").value);
    if (num2 !== 0) {
        var answer = num1 / num2;
        document.getElementById("answer").innerHTML = "Result: " + answer;
    } else {
        document.getElementById("answer").innerHTML = "Cannot divide by zero.";
    }
}
</script>
<body>
    <h2>Simple Calculator</h2>
    <input type="number" id="num1" placeholder="Enter first #">
    <input type="number" id="num2" placeholder="Enter second #">
    <br>
    <button class="number" onclick="add()">+</button>
    <button class="number" onclick="subtract()">-</button>
    <button class="number" onclick="multiply()">×</button>
    <button class="number" onclick="divide()">÷</button>
    <p id="answer"></p>
</body>


<style>
    button.number{
        width: 130.5px;
        background-color: #333;
        font-size: 28px;
        color: #ff8200;
        display:block;
        margin-left: auto;
        margin-right: auto;
    }
    h2{
        padding:10px 142px;
        font-size: 30px;
    }
    p#answer{
        color: #ff8200;
        margin: 0px 210px;
        font-size:25px;
        padding: 5px 0px;
        text-align: center;
    }
    input#num1,input#num2{
        background-color:#ff8200;
        text-align:center;
        font-size:25px;
        height:60px;
        width: 264.5px;
        display:block;
        margin-left: auto;
        margin-right: auto;
    }

</style>

<head>
    <title>Binary Calculator</title>
    <script>
        function binaryAdd() {
            var bin1 = document.getElementById("bin1").value;
            var bin2 = document.getElementById("bin2").value;
            var dec1 = parseInt(bin1, 2);
            var dec2 = parseInt(bin2, 2);
            var resultDec = dec1 + dec2;
            var resultBin = resultDec.toString(2);
            document.getElementById("result").innerHTML = "Result: " + resultBin;
        }
        function binarySubtract() {
            var bin1 = document.getElementById("bin1").value;
            var bin2 = document.getElementById("bin2").value;
            var dec1 = parseInt(bin1, 2);
            var dec2 = parseInt(bin2, 2);
            var resultDec = dec1 - dec2;
            var resultBin = resultDec.toString(2);
            document.getElementById("result").innerHTML = "Result: " + resultBin;
        }
    </script>
</head>
<body>
    <h2>Binary Calculator</h2>
    <input type="text" id="bin1" placeholder="Enter 1st Binary #">
    <input type="text" id="bin2" placeholder="Enter 2nd Binary #">
    <br>
    <button class="binary" onclick="binaryAdd()">+</button>
    <button class="binary" onclick="binarySubtract()">-</button>
    <p id="result"></p>
</body>
<style>
    button.binary{
        width: 265px;
        padding: 10px;
        background-color: #333;
        font-size: 28px;
        color: #ff8200;
        display:block;
        margin-left: auto;
        margin-right: auto;
    }
    h2{
        padding:10px 142px;
        font-size: 30px;
        color:#ff8200;
        text-align: center;
    }
    p#result{
        color: #ff8200;
        margin: 0px 200px;
        font-size:25px;
        padding: 5px 0px;
        text-align: center;
    }
    input#bin1,input#bin2{
        background-color:#ff8200;
        text-align:center;
        font-size:25px;
        height:60px;
        display:block;
        margin-left: auto;
        margin-right: auto;
    }
</style>