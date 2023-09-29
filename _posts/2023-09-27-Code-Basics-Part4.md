---
toc: true
comments: true
layout: post
type: hacks
title: APCSP JS Hacks 4
description: Part 4 of the 5 things we had to learn for APCSP 
courses: { csse: {week: 1}, csp: {week: 5, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

%%html
<table id = "Hello">
    <tr id = "What the text is">
    </tr>
    <tr id = "What I know">
    </tr>
    <tr id = "To ask for help">
    </tr>
</table>
<script>
    var table = document.getElementById("Hello")
    var code = document.getElementById("What the text is")
    var iKnow = document.getElementById("What I know")
    var toLearn = document.getElementById("To ask for help")
    var theContent = [
        "Code presented in JS",
        "thead",
        "object.this",
        "Definitions"
    ]
    var contentIKnow = [
        "What I know of Code",
        "Know that it represents the table head",
        "I know it represents the something about the object",
        "They give meaning to a certin term"
    ]
    var contentToLearn = [
        "Questions abount Code",
        "When should I use this?",
        "Confirm: Is used for returning Data abt the object",
        "Learn what in means in APCSP"
    ]
    console.log(theContent)
    for(x = 0; x <theContent.length; x++){
        var cell = document.createElement("td")
        cell.innerHTML = "<code>" + theContent[x] + "<code>"
        code.appendChild(cell)
    }
    console.log(contentIKnow)
    for(x = 0; x <contentToLearn.length; x++){
        var cell2 = document.createElement("td")
        cell2.innerHTML = contentToLearn[x]
        toLearn.appendChild(cell2)
    }
    console.log(contentToLearn)
    for(x = 0; x <contentIKnow.length; x++){
        var cell = document.createElement("td")
        cell.innerHTML = contentIKnow[x]
        iKnow.appendChild(cell) 
    }
</script> 

What I've learned:
- 1  Uses raw HTML, can be used to customize it to what I want
- 2. To look over what variables are named, happened to me multiple times over.