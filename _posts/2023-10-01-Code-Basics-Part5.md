---
toc: true
comments: true
layout: post
type: hacks
title: APCSP JS Hacks 5
description: Part 5 of the 6 things we had to learn for APCSP 
courses: { csse: {week: 1}, csp: {week: 5, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

<button onclick = "players()">Hello</button>

<script>
var frame = 0;
var time = 0;
var xPlay = {
    "item" : "x",
    "x" : 0,
    "y" : 2
};
var yPlay = {
    "item" : "y",
    "x" : 1,
    "y" : 2
};
var dummy = {
    "item": "d",
    "x": 3,
    "y": 1
}
var objects = [xPlay, yPlay];
function drawScreen(){
    var lane = "";
    objCt = 0
    objects.sort((a, b) => {
        if(a["y"] < b["y"]){
            return -1
        }
        if(a["x"] < b["x"]){
            return -1
        }
        else{
            return 1
        }
    });
    for(var y = 0; y < 3; y++){
        for(var x = 0; x < 20; x++){
            if(objects[objCt]["x"] == x && objects[objCt]["y"] == y){
                lane += objects[objCt]["item"]
                if(objCt + 1 < objects.length){
                    objCt += 1
                }
            }
            else{
                lane += "."
            }
        }
        lane += "\n"
    }
    lane += "################oooo"
    return lane
}
function players(){
    console.log(frame)
    var toUpX = 0
    var toUpY = 0
    if(frame < 16){
        xPlay["x"] = frame
        if(frame % 2 == 1){
            toUpX = 1
        }
        else{
            toUpX = 0
        }
        xPlay["y"] = 2 - toUpX
        console.log("PlayerX X is", xPlay["x"])
        console.log("PlayerX Y is", xPlay["y"])
        if(frame > 1){
            yPlay["x"] = frame
            if(frame % 2 == 0 && frame != 0){
                toUpY = 1
            }
            else{
                toUpY = 0
            }
            yPlay["y"] = 2 - toUpY
            console.log("PlayerY X is", yPlay["x"])
            console.log("PlayerY Y is", yPlay["y"])
        }   
    }
    console.log("Time is", time)
    time += 1
    if(time >= 16 && time < 28){
        frame -= 1
    }
    else if (time < 20){
        frame += 1
    }
    theScreen = drawScreen()
    console.log(theScreen)
}
</script>