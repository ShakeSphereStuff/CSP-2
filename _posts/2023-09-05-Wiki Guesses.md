---
toc: true
comments: true
layout: post
title: Wiki Gusses
description: Wiki Gusses, things to do when you don't have friends
type: plans
courses: { csse: {week: 1}, csp: {week: 1, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---
<table id = "grid">
    <div id="scores"></div>
</table>
<script>
    var questions = ["ID for questions: "]
    var answer = ""
    var numOfQuests = 0
    console.log("Is this even running")
    function newData(text){
        if(String(text) == "undefined"){
                text = 0
            }
        console.log(text)
        var input = document.createElement("input");
        var newLine = document.createElement("br")
        var prompt = document.createElement("p")
        var grid = document.getElementById("grid") 
        input.onkeydown = data
        prompt.innerHTML = questions[text]
        input.id = "Input " + document.querySelectorAll("input").length
        grid.appendChild(prompt);
        prompt.appendChild(input);
        input.appendChild(newLine);
    }
    function processData(currentStr){
        var time = Date.now();
        time += 600000
        var userImportedMinutes = 0
        var toBeQuests = currentStr[2].split("& ")
        userTime = parseInt(currentStr[0])
        console.log("Current String is " + currentStr);
        console.log("Current Time is " + time)
        console.log("User's time is  " + userTime)
        // Adds time and sees if it's in a ten minnute range
        // console.log("User imputed time is " + userTime)
        // if(userTime < time && userTime > time - 600000){}
        for(questCt = 0; questCt < currentStr.length; questCt++){
            questions.push(toBeQuests[questCt])
        }
        numOfQuests = parseInt(currentStr[1]) + 1
        console.log("Questions is " + questions)
        answer = currentStr[currentStr.length - 1]
        return 2
    }
    function strAnswer(addOn){
        var text = questions[3]
        console.log("Text is " + questions)
        var newLine = document.createElement("br")
        var prompt = document.createElement("p")
        var grid = document.getElementById("grid") 
        prompt.innerHTML = addOn + String(answer) + "<br>" + "You got it in " + (document.querySelectorAll("input").length - 1) + " attempts"
        grid.appendChild(prompt);
        prompt.appendChild(newLine);
    }
    function data(event){
        if(event.key == "Enter"){
            console.log("Enter is Pressed")
            console.log(String(currentStr))
            event.preventDefault()
            var numOfInputs = document.querySelectorAll("input").length
            console.log("Num of Inputs is: " + numOfInputs)
            var currentStr = document.getElementById("Input " + String(numOfInputs - 1)).value
            var stripData = currentStr.split(";");
            var userTime = 0
            currentStr = String(currentStr)
            console.log("NumOfQuests: " + numOfQuests)
            console.log("Num of Data: " + stripData.length)
            if(numOfInputs != 1 && currentStr.toLowerCase() == answer.trim().toLowerCase()){
                console.log("Correct Answer")
                numOfInputs = 69
                strAnswer("You're correct it's ")
                return null
            }
            if(parseInt(numOfInputs) == 1){
                if(stripData.length != 4){
                    return null
                }
                var numData = processData(stripData)
                newData(numData)
            }
            else if(numOfInputs < numOfQuests){
                console.log("It passed through here")
                questions.push("Answer the Questions")
                newData(numOfInputs + 1)
            }
            else{
                strAnswer("It's ")
            }
        }
    }
    if(document.querySelectorAll("input").length == 0){
        newData()
    }
</script>