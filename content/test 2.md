

<table id="colorTable" style="border-collapse: collapse; width: 100%;"> </table>


<script> function createTable() { var table = document.getElementById('colorTable'); for (var i = 0; i < 100; i++) { var row = table.insertRow(); for (var j = 0; j < 100; j++) { var cell = row.insertCell(); cell.style.width = '10px'; cell.style.height = '10px'; cell.style.backgroundColor = (i + j) % 2 == 0 ? 'white' : 'gray'; } } } createTable(); </script>