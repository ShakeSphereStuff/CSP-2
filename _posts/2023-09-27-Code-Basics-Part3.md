---
toc: true
comments: true
layout: post
type: hacks
title: APCSP JS Hacks 3
description: Part 3 of the 5 things we had to learn for APCSP 
courses: { csse: {week: 1}, csp: {week: 5, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

This is running a for loop for what was suppost to be a loading simulation, now, I know from 0 - 5 the text is suppost to be 
\/\/\/\/\/\/\/\/\/\/

<p id="Load">Loading</p>
<script>
    var loadingScreen = document.getElementById("Load").innerHTML;
    var time = new Date(); 
    var wait = time.getTime();
    for(x = 0; x < 10; x++){
        if(wait + 1000000 > new Date().getTime()){
            console.log("Starts with", loadingScreen)
            if(loadingScreen != "Loading..."){
                loadingScreen += ".";
            }
            else{
                loadingScreen = "Loading";
            }   
        }
    }
    document.getElementById("Load").innerHTML = loadingScreen
    console.log("Ends with", loadingScreen)
</script> 

Found out that I had to redefine .innerHTML because for some reason it wasn't working just once.