---
title: Testing Room 🧪 11
---
currently playing with some html script to see what i can do here
<table id="colorTable" border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;"> <tr> <td id="cell1" style="background-color: white;"></td> <td id="cell2"></td> </tr> <tr> <td id="cell3"></td> <td id="cell4" style="background-color: white;"></td> </tr> </table>
<button onclick="callSwitchColors()">Switch Colors</button> 

<script> function switchColors() { var cell1Color = document.getElementById('cell1').style.backgroundColor; var cell2Color = document.getElementById('cell2').style.backgroundColor; var cell3Color = document.getElementById('cell3').style.backgroundColor; var cell4Color = document.getElementById('cell4').style.backgroundColor; document.getElementById('cell1').style.backgroundColor = cell1Color === 'white' ? '' : 'white'; document.getElementById('cell2').style.backgroundColor = cell2Color === 'white' ? '' : 'white'; document.getElementById('cell3').style.backgroundColor = cell3Color === 'white' ? '' : 'white'; document.getElementById('cell4').style.backgroundColor = cell4Color === 'white' ? '' : 'white'; } 

function callSwitchColors() { var count = 0; var intervalId = setInterval(function() { switchColors(); count++; if (count === 1000) { clearInterval(intervalId); } }, 10); // Call switchColors() every 10 milliseconds }
</script>