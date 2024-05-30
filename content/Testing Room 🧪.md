---
title: Testing Room 🧪 1232
---


<div> <input type="number" id="numberInput" placeholder="Enter a number">
<button onclick="displayNumber()">Submit</button> </div> 

<table border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;"> <tr> <td id="cell1"></td> <td></td> </tr> <tr> <td></td> <td id="cell2"></td> </tr> </table>


<table id="colorTable" style="border-collapse: collapse; width: 100%;"> </table> <script> function createTable() { var table = document.getElementById('colorTable'); for (var i = 0; i < 100; i++) { var row = table.insertRow(); for (var j = 0; j < 100; j++) { var cell = row.insertCell(); cell.style.width = '10px'; cell.style.height = '10px'; cell.style.backgroundColor = (i + j) % 2 == 0 ? 'white' : 'gray'; } } } createTable(); </script>





<head>
<style> table { border-collapse: collapse; width: 100%; } td { width: 10px; height: 10px; } .white { background-color: white; } .gray { background-color: gray; } </style> 

</head> <body> <table id="colorTable"></table>

<script> function createTable() { var table = document.getElementById('colorTable'); for (var i = 0; i < 100; i++) { var row = table.insertRow(); for (var j = 0; j < 100; j++) { var cell = row.insertCell(); if ((i + j) % 2 == 0) { cell.className = 'white'; } else { cell.className = 'gray'; } } } } createTable(); </script>