---
title: Videos on a Static Site 📺
tags:
  - experiment
  - "#html"
  - underconstruction
---
# Chicken Rice
The idea for this exploration came from the chicken rice shop near my work in which a QR code is required in order to obtain a menu and place an order. A piece of paper with the verification code is stuck on the table and changed daily. The QR code directs my phone to a dynamic link based on the exact table I'm sitting on which then uses the verification code to ensure the order is fresh from the day. One of the great thing about obsidian, which is the tool I am using to manage this site, is that the file is in mark-up which allows html to be included using tags.

Hence writing the following inline will result in a button similar to writing on a .html file.
```
<button type="button">Decepticons</button>
```
<button type="button">Decepticons</button>

As such, I first set out to create a static page on this site that will take a site and convert it into a QR code. My first worry was that the QR code would be too big and would require too many cells to fit on screen and hence would require scrolling. As such to make sure a QR code was even able to be displayed on the screen of the site I first had to check that I could even fit a bunch of cells on screen using a table tag without scrolling for urls that are more complex.

After an afternoon of search on the basics of html, I learn that the two properties that are important here is ==min-width== (also min-height) which controls the minimum size a cell of a table can get and ==padding== which separates the content and the border. Since the only use for the table was to fill in its background color to either white or black for the QR code, the padding was mandatory. Leaving it at 0px will result in the table disappearing as there will be no space between the borders as there are no actual content in the cells.

```
<style> 
.table-container table td { 
	min-width: 1px; 
	min-height:1px;
	padding: 1px 1px; 
	} 
</style>
```

# Basic QR Table Code
First off, I want to test that the table can actually redirect my phone. As such, I tried manually creating a 21 by 21 QR code that will redirect my phone to a link. After many trials and experiments, I discovered that the important thing in a QR code is that it has some contrasting background for example the white margins to distinguish the three squares (top left, top right and bottom left) and the squareness of each individual cell does not play that big of a role in detection. As such, I left my cells as it is even though they are not in a 1 to 1 ratio of height to width.

<style> 
.example-table table td { 
min-width: 1px; 
min-height:1px;
border: 0;
width:4%;
padding-top: 4%;
height: 0;
}
.example-table table tr{
border:0;
}
.example-table table{
width: 90%;
border: 5px solid; 
border-color: red;
}
</style>
### Example QR Code
<div class="example-table">
<table>  
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
</tr>
<tr>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
</table>
</div>

### Code for Inserting Into Table Tag
```Javascript
qr=["111111101011101111111","100000100011001000001","101110101101001011101",
    "101110101100101011101","101110101001001011101","100000100111101000001",
    "111111101010101111111","000000000001100000000","111100101111110011101",
   "010011010101111111101","001101101111010100011","110110011011000101010",
   "001010100100111000001","000000001001001110101","111111100011111110000",
   "100000100110010101111","101110100110100001100","101110101100001001110",
   "101110101010100100100","100000101011011110001","111111101111011100100"]

for(var i =0;i<qr.length;i++){
  temp_string = qr[i];
  console.log("<tr>");
  for(var j=0;j<temp_string.length;j++){
    if(temp_string[j] == "1"){
      console.log("<td style='background-color:black;'></td>");
    }else{
      console.log("<td style='background-color:white;'></td>");
    }
  }
  console.log("</tr>");
}
```


## Loops in Script
For some reason, whenever a loop of any kind is added into a script tag, it ceases to work. After trawling the web and various forums, I still have no idea why this is the case. Hence, any form of Document Object Model manipulation or change to the table using loops is impossible.

# Encoding Algorithm
Now that I have gotten a table setup, the next focus will be on figuring out how to turn a string which represents a url into a QR code. 

1) Position and Rotation markers
2) Timing Structure (Version of Code, Timing)
3) Level of Error Correction
	1) 7%
	2) 15%
	3) 25%
	4) 30%
4) Mask
5) Error Correction for Mask and Level of Error Correction
6) Single Bit ?
7) Type of Encoding
	1) Numeric 
	2) Alpha Numeric
	3) Kanji
	4) Bytes
8) Message Length
9) Message -> ASCII in bits
10) End of Message Indicator
11) Error correction data for message

<style> 
.informatics table td { 
	min-width: 1px; 
	min-height:1px;
	padding: 1px 1px; 
	width: 20px;
	height: 20px;
	border: 1px solid;
	border-color: black;
	} 
.informatics table{
border: 5px solid; 
border-color: white;
}
.informatics table tr{
	border: 0;
}
</style>
# Explainer Table for 21x21
<div class='informatics'>
<table>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:green;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
</tr>
<tr>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:green;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:blue;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:green;'></td>
<td style='background-color:white;'></td>
<td style='background-color:black;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
<tr>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:red;'></td>
<td style='background-color:white;'></td>
<td style='background-color:blue;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
<td style='background-color:white;'></td>
</tr>
</table>
</div>

# code for informatics
```Javascript
qr=["111111112000011111111",
	"111111112000011111111",
	"111111112000011111111",
	"111111112000011111111",
	"111111112000011111111",
	"111111112000011111111",
	"111111133333331111111",
	"111111112000011111111",
	"222222322000002222222",
	"000000300000000000000",
	"000000300000000000000",
	"000000300000000000000",
	"000000300000000000000",
	"111111314000000000000",
	"111111112000000000000",
	"111111112000000000000",
	"111111112000000000000",
	"111111112000000000000",
	"111111112000000000000",
	"111111112000000000000",
	"111111112000000000000",
    ]
```


# Loops in Script 2
After spending some time on the following resources, I learn that without loops, making an in-page html script to turn a string in to QR code is not possible. Some part of QR code requires dynamic data handling depending on the particular mask and data type. It would not have made sense to try and hardcore every possible scenario into a script.

- [Python Library for QR Code](https://github.com/lincolnloop/python-qrcode)
- [How to Decode a QR Code by Hand](https://www.youtube.com/watch?v=KA8hDldvfv0)
- [Wikipedia on QR Code](https://en.wikipedia.org/wiki/QR_code)

If you have the time and are interested,  I highly recommend these links, especially the second one, which is a step by step guid on reconstructing a string from a QR code by hand. 

# Getting on to Videos


