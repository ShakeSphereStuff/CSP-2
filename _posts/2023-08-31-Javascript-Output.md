---
toc: true
comments: true
layout: post
title: JavaScript Output
description: Suppost to be for a table
courses: { csse: {week: 1}, csp: {week: 1, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---
<table id = "anchor">
    <div id = "Grid"></div>
</table>
<script>
    var cellCt = -1;
    var xMax = 0;
    var yMax = 0;
    var xRandom = 0;
    var yRandom = 0;
    function generate(){
        console.log("Is called");
        if(cellCt > 0){
            var preGrid = document.getElementById("Grid");
            preGrid.remove();
            var table = document.createElement("div");
            table.id = "Grid";
            var anchor = document.getElementById("anchor")
            anchor.appendChild(table);
        }
        console.log("Is called through here");
        xMax = parseInt(document.getElementById("xMax").value);
        yMax = parseInt(document.getElementById("yMax").value);
        xRandom = Math.floor(Math.random() * (xMax - 1));
        yRandom = Math.floor(Math.random() * (yMax - 1));
        console.log("Made through these variables");
        console.log("Cell Ct: " + cellCt);
        for(var x = 0; x < xMax; x++){
            for(var y = 0; y < yMax; y++){
                screen(x, y);
            }
        }
        document.getElementById("xMax").remove();
        document.getElementById("yMax").remove();
        document.getElementById("generator").remove();      
        cellCt = 0;
    };      
    function screen(row, col){
        if(col > cellCt){
            console.log("Cell Ct " + cellCt)
            cellCt += 1
            var grid = document.getElementById("Grid");
            console.log("Grid Id = " + document.getElementById("Grid").id)
            var cell = document.createElement("tr");
            cell.id = "Cols; " + col;
            grid.appendChild(cell)
        }
        console.log("Got Called");
        var state = "-";
        if(row == xRandom && col == yRandom){
            console.log(xMax - 1)
            console.log(yMax - 1)
            state = "x"
        }
        // var string = "Row; " + row + " Col; " + col + " State; " + state;
        console.log("Cols; " + col)
        var string = state
        var trCol = document.getElementById("Cols; " + col);
        var button = document.createElement("td");
        button.id = "(" + String(row) + ", "+ String(col) + ")";
        button.innerHTML = string;
        trCol.appendChild(button);
    };
</script>

<input id = "xMax" type = "number" value = "6"> 
<input id = "yMax" type = "number" value = "6">
<button onclick = "generate()" id = "generator"> Create Grid </button>