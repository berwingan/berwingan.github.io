---
title: Testing Room 🧪 1232
---

<table id="colorTable" border="1" style="width: 200px; height: 100px; text-align: center; margin-top: 20px;">   <tr>     <td id="cell1" style="background-color: white;"></td>     <td id="cell2"></td>   </tr>   <tr>     <td id="cell3"></td>     <td id="cell4" style="background-color: white;"></td>   </tr> </table> <button onclick="switchColors()">Switch Colors</button>  

<script>   function switchColors() {     document.getElementById('cell1').style.backgroundColor = '';     document.getElementById('cell2').style.backgroundColor = 'white';     document.getElementById('cell3').style.backgroundColor = 'white';     document.getElementById('cell4').style.backgroundColor = '';   } </script>