---
toc: true
comments: true
layout: post
type: hacks
title: APCSP JS Hacks 2
description: Part 2 of the 5 things we had to learn for APCSP 
courses: { csse: {week: 1}, csp: {week: 5, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

<table>
    <tr>
        <td>
<input id = "First">FirstName</input>
<input id = "Last">LastName</input>
        </td>
    </tr>
    <tr>
        <td>
            <button onclick="js:addPerson();">Submit Person</button>
            <button onclick="js:renderGreeting();">Show Grettings</button>
        </td>
    </tr>
    <tr>
        <td>
            <p id = "output"></p>
        </td>
    </tr>
</table>

<script>
var personInfo = []
function addPerson(){
    var firstName = document.getElementById("First").value;
    var lastName = document.getElementById("Last").value;
    personInfo.push({
        "First Name" : firstName,
        "Last Name" : lastName
    })
    console.log(personInfo)
    return null
}
function renderGreeting(){
    var result = document.getElementById("output")
    var firstNames = ""
    var greetings = [
        "Hello",
        "Hi",
        "Greetings",
        "Good day"
    ]
    console.log(typeof(personInfo))
    console.log(Object.keys(personInfo).length)
    for(x = personInfo.length - 1; x >= 0; x--){
        firstNames += greetings[Math.floor(Math.random() * greetings.length)] + " " + personInfo[x]["First Name"] + "<br>"
    }
    result.innerHTML = firstNames
}
</script>