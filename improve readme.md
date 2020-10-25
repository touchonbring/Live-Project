
<!doctype html>
<html>
<head>
<style>
table{width: 70%;}
table,th,td{border: solid 1px black;
border-collapse: collapse;
padding: 2px 3px;
text-align: center;
}
</style>
<meta charset="utf-8">
<title>Untitled Document</title>
</head>

<body onLoad="createTable()">
<p>
<input type="button" id="addrow()" value="Add new Row" onClick="addrow()">
</p>
<div id="cont"></div><!-- this container is for table -->
<p><input type="button" id="bt" value="submit data" onClick="submit()"></p>

</body>
<script>
//debugger;
var arrhead=new Array();
arrhead=['','emp. Name','Designation','Age'];
//function to create table
function createTable()
{
var empTable=document.createElement('table');
empTable.setAttribute('id','empTable'); //table id
var tr=empTable.insertRow(-1);
for(var h=0;h<arrhead.length;h++)
{
var th=document.createElement('th');
th.innerHTML=arrhead[h];
tr.appendChild(th);
}
var div=document.getElementById('cont');
div.appendChild(empTable);
}
//new row addtion function
function addrow()
{
var empTab=document.getElementById('empTable');
var rowCnt=empTab.rows.length; //get num of row
var tr=empTab.insertRow(rowCnt);
tr=empTab.insertRow(rowCnt);
for(var c=0;c<arrhead.length;c++)
{
var td=document.createElement('td');
td=tr.insertCell(c);
if(c==0)//if it is first columne of table
{
//add button
var button=document.createElement('input');
button.setAttribute('type','button');
button.setAttribute('value','Remove');
// add button click event
button.setAttribute('onClick','removeRow(this)');
td.appendChild(button);
}
else
{
// 2nd ,3rd and 4th column will have text
var ele =document.createElement('input');
ele.setAttribute('type','text');
ele.setAttribute('value','');
td.appendChild(ele);
}
}
}
//remove row
function removeRow(oButton)
{
var empTab=document.getElementById('empTable');
empTab.deleteRow(oButton.parentNode.parentNode.rowIndex);
}
function submit()
{
var myTab=document.getElementById('empTable');
var arrValues=new Array();
// loop through each row of the table
for (var row=1;row<myTab.rows.length-1;row++)
{
// for each cell of table
for(c=0; c<myTab.rows[row].cells.length;c++)
{
var element =myTab.rows.item(row).cells[c];
if(element.childNodes[0].getAttribute('type')=='text')
{
arrValues.push(","+element.childNodes[0].value+",");
}
}
}
console.log(arrValues);
}
</script>
</html>
