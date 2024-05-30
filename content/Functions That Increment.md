

<div> <input type="number" id="numberInput" placeholder="Enter a number"> <button onclick="displayNumber()">Submit</button> <button onclick="autoAdd()">Auto Increment</button> </div> 
<p id="output"></p> <script> 
function displayNumber() { 
var number = document.getElementById('numberInput').value; document.getElementById('output').innerText = 'Your number is: ' + number; 
} 

function autoAdd(){
var number = document.getElementById('numberInput').value;
for(var i =0;i<10000;i++){
document.getElementById('output').innerText = 'Your number is: ' + number+i;
setTimeout(function() {  }, 1000);	
	}
}
</script>




