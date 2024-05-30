---
title: Testing Room 🧪 123
---


<div> <input type="number" id="numberInput" placeholder="Enter a number">
<button onclick="displayNumber()">Submit</button> </div> 

<table border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;"> <tr> <td id="cell1"></td> <td></td> </tr> <tr> <td></td> <td id="cell2"></td> </tr> </table>


<script> function displayNumber() { var number = document.getElementById('numberInput').value; document.getElementById('cell1').innerText = number; document.getElementById('cell2').innerText = number; } </script>


<table border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;"> <tr> <td style="background-color: white;"></td> <td></td> </tr> <tr> <td></td> <td style="background-color: white;"></td> </tr> </table>






<head>
<style> table { border-collapse: collapse; width: 100%; } td { width: 10px; height: 10px; } .white { background-color: white; } .gray { background-color: gray; } </style> 

</head> <body> <table id="colorTable"></table>

<script> function createTable() { var table = document.getElementById('colorTable'); for (var i = 0; i < 100; i++) { var row = table.insertRow(); for (var j = 0; j < 100; j++) { var cell = row.insertCell(); if ((i + j) % 2 == 0) { cell.className = 'white'; } else { cell.className = 'gray'; } } } } createTable(); </script>