---
title: Testing Room 🧪
---


<div> <input type="number" id="numberInput" placeholder="Enter a number"> <button onclick="displayNumber()">Submit</button> </div> <p id="output"></p> <script> function displayNumber() { var number = document.getElementById('numberInput').value; document.getElementById('output').innerText = 'Your number is: ' + number; } </script>

<div> <input type="number" id="numberInput" placeholder="Enter a number">
<button onclick="displayNumber()">Submit</button> </div> 

<table border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;"> <tr> <td id="cell1"></td> <td></td> </tr> <tr> <td></td> <td id="cell2"></td> </tr> </table>


<script> function displayNumber() { var number = document.getElementById('numberInput').value; document.getElementById('cell1').innerText = number; document.getElementById('cell2').innerText = number; } </script>
