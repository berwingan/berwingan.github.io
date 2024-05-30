---
title: Testing Room 🧪
---


<div> <input type="number" id="numberInput" placeholder="Enter a number"> <button onclick="displayNumber()">Submit</button> </div> <p id="output"></p> <script> function displayNumber() { var number = document.getElementById('numberInput').value; document.getElementById('output').innerText = 'Your number is: ' + number; } </script>
