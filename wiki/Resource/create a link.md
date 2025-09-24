---
날짜: 2025-04-28
tags:
  - 🦜Resource/Obsidian
---


<select id="mySelect" onchange="updateDataView()"> 
<option value="computer">computer</option> 
<option value="house">house</option>
<option value="keyboard">keyboard</option>
</select>

<input id="mySelect" onchange="updateDataView()" style="height:30px; width:400px;"> <button  style="height:30px; width:40px; "> </button>

input[type=text] {  width: 100%;  
  padding: 12px 20px;  
  margin: 8px 0;  
  box-sizing: border-box;}


<script>
function updateDataView() { var combo = document.getElementById("mySelect"); var selectedOption = combo.options[combo.selectedIndex].value; var dataViewCode = "```myDataView\n" + "table from #Enlaces where contains(topics, \"" + selectedOption + "\")\n" + "```"; 
						   
// Actualizamos el contenido del DataView en el editor de texto 
var editor = document.querySelector('.CodeMirror').CodeMirror; var currentText = editor.getValue(); var newText = currentText.replace(/```dataview myDataView[\s\S]*?```/, dataViewCode); editor.setValue(newText); 
						   
// Forzamos a Obsidian a renderizar la nota nuevamente 
var event = new Event('input', { bubbles: true, cancelable: true, }); editor.getInputField().dispatchEvent(event); }
</script>

```dataview myDataView
table from #Links where contains(topics, "computer")