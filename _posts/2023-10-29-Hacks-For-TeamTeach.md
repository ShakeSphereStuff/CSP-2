---
toc: true
comments: true
layout: post
type: hacks
title: Compolation of Team Teaches
description: 5 of the 6 team teaches on NightHawkCoders 
courses: { csse: {week: 1}, csp: {week: 9, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

If the copy code button doesn't work, try opening the console to copy the python code

First Team teach, algorithms:
<button onclick = "javascript:getPythonCode(0)">Copy code</button>
<p id = "codeCell" hidden>
    students = []
    studentNamePos = []
    assignments = []
    assignmentNamePos = []
    totalGrades = 0.0
    def averageGrades():
        global totalGrades, students, assignments
        for theStudent in students:
            print(theStudent["Name"] + ":") 
            print("-"*10)
            for theAssignment in assignments:
                print(f'\t Assignment Name: {theAssignment["Name"]}')
                print(f'\t Assignment Total: {theAssignment["Total"]}')
                print(f'\t Student Score: {theStudent[theAssignment["Name"]]}')
                if(theAssignment["Name"] != assignments[-1]["Name"]):
                    print("-" * 10)
                totalGrades += theStudent[theAssignment["Name"]] / theAssignment["Total"]

        return totalGrades / (len(assignments) * len(students))
    def addStudent(name):
        global students, assignments, studentNamePos
        newStudent = {
            "Name": str(name)
        }
        studentNamePos.append(name)
        for x in assignments:
            newStudent[str(x["Name"])] = 0
        students.append(newStudent)
        return students

    def makeAssignments(assignmentName, assignmentTotal):
        global assignments, assignmentNamePos
        newAssignment = {}
        newAssignment["Name"] = assignmentName
        newAssignment["Total"] = assignmentTotal
        assignmentNamePos.append(assignmentName)
        assignments.append(newAssignment)

    def gradeAssignment(studentName, assignmentName, grade):
        global students, assignmentNamePos, assignments, studentNamePos
        # If the assignment total is greater than the grade
        assignmentTotal = assignments[assignmentNamePos.index(assignmentName)]["Total"]
        if(assignmentTotal >= grade):
            students[studentNamePos.index(studentName)][assignmentName] = grade / assignmentTotal 
            print(f'{studentName}\'s grade for {assignmentName} now at a {(grade / assignmentTotal)*100}%')
        else:
            print("\t Invalid Input, we only accept point values from 0 to " + str(assignmentTotal))

    def startUp():
        global students
        print("Welcome to Grader, the program to do everything with students grades, choose what you want to do;")
        print("\tChoose A to average the class grades")
        print("\tChoose B to add a student")
        print("\tChoose C to make an Assignment")
        print("\tChoose D to grade an Assignment")
        print("\tChoose E to end this session")
        userInput = ""
        while 7 == 7:
            if(userInput == ""):
                print("Now, Choose another item from the list above")
                userInput = input("What option do you want to choose? ")

            if(userInput.upper() == "A"):
                print(f"{averageGrades()} for a class of {len(students)} student(s)")
                userInput = ""

            elif(userInput.upper() == "B"):
                userInput = input("\tWhat is the student's name? ")
                currentStudents = addStudent(userInput)
                print(currentStudents)
                userInput = ""

            elif(userInput.upper() == "C"):
                assignmentName = input("What is the assignment name? ")
                assignmentTotal = input("What is the assignment total? ")
                try:
                    if(assignmentTotal != float("nan") and float(assignmentTotal) > 0):
                        makeAssignments(assignmentName, float(assignmentTotal))
                        userInput = ""
                except:
                    print("Invalid Point Score, please try again")
                    userInput = "C"

            elif(userInput.upper() == "D"):
                global assignmentNamePos, studentNamePos
                isValid = [False, False]
                studentAssignment = input("\tWhat is the assignment your grading? ")
                studentGrade = input("\tHow many points did they earn? ")
                studentName = input("\tWhat is the student your grading? ")
                for x in range(0, len(assignmentNamePos)):
                    if(studentAssignment.upper() == assignmentNamePos[x].upper()):
                        isValid[0] = True
                if(isValid[0] == False):
                    print("Invalid Assignment Name, please try again")
                    userInput = "D"
                for x in range(0, len(studentNamePos)):
                    if(studentName.upper() == studentNamePos[x].upper()):
                        isValid[1] = True
                if(isValid[1] == False):
                    print("Invalid Assignment Name, please try again")
                    userInput = "D"
                try:
                    if(studentGrade != float("nan") and float(studentGrade) > 0 and int(isValid[0]) + int(isValid[1]) == 2):
                        makeAssignments(assignmentName, float(studentGrade))
                        userInput = ""
                        gradeAssignment(studentName, studentAssignment, float(studentGrade))
                except:
                    print("Invalid Values, please try again")
                    userInput = "D"

            elif(userInput.upper() == "E"):
                print("\tHave a lovely day!")
                break

            else:
                print("Invaid Input, please try again")
                userInput = ""
    startUp()

</p>

Second Team Teach, Data Abstraction:

<button onclick = "javascript:getPythonCode(1)">Copy code</button>

<p id = "codeCell" hidden>
import random
name = input("What's your name?")
continueGreet = True
selectedGreeting = 0
result = ""
Greetings = [["Hello", "State"], ["Hi there", "State"], ["How are you doing", "Quest"]]
def greeting():
    global result, selectedGreeting, Greetings
    selectedGreeting = random.randint(0, len(Greetings) - 1)
    if(Greetings[selectedGreeting][1] == "Quest"):
        print("\t" + Greetings[selectedGreeting][0] + " " + name + "?")
        result = Greetings[selectedGreeting][0] + " " + name + "?"
    elif(Greetings[selectedGreeting][1] == "State"):
        print("\t" + Greetings[selectedGreeting][0] + " " + name)
        result = Greetings[selectedGreeting][0] + " " + name
    else:
        print("INVALID GREETING")

greeting()

while(continueGreet == True):
    global result, selectedGreeting, Greetings
    isRight = input("Do you like this greeting? Y/N: ")
    if(isRight.upper() == "N"):
        del Greetings[selectedGreeting]
    if(len(Greetings) == 0):
        print("There are no more greetings, try adding 1 to the system, or pick one provided")
        continueGreet = False
    else:
        greeting()
        continueGreet = True
    elif(isRight.upper() == "Y"):
        continueGreet = False
        print(result)
    else:
        print("Invalid")
        continueGreet = True
</p>



Third Team Teach, Developing Algorithms

<button onclick = "javascript:getPythonCode(2)">Copy code</button>

<p id = "codeCell" hidden>

students = []
studentNamePos = []
assignments = []
assignmentNamePos = []
totalGrades = 0.0
def averageGrades():
    global totalGrades, students, assignments
    for theStudent in students:
        print(theStudent["Name"] + ":") 
        print("-"*10)
        for theAssignment in assignments:
            print(f'\t Assignment Name: {theAssignment["Name"]}')
            print(f'\t Assignment Total: {theAssignment["Total"]}')
            print(f'\t Student Score: {theStudent[theAssignment["Name"]]}')
            if(theAssignment["Name"] != assignments[-1]["Name"]):
                print("-" * 10)
            totalGrades += theStudent[theAssignment["Name"]] / theAssignment["Total"]

    return totalGrades / (len(assignments) * len(students))
def addStudent(name):
    global students, assignments, studentNamePos
    newStudent = {
        "Name": str(name)
    }
    studentNamePos.append(name)
    for x in assignments:
        newStudent[str(x["Name"])] = 0
    students.append(newStudent)
    return students

def makeAssignments(assignmentName, assignmentTotal):
    global assignments, assignmentNamePos
    newAssignment = {}
    newAssignment["Name"] = assignmentName
    newAssignment["Total"] = assignmentTotal
    assignmentNamePos.append(assignmentName)
    assignments.append(newAssignment)

def gradeAssignment(studentName, assignmentName, grade):
    global students, assignmentNamePos, assignments, studentNamePos
    # If the assignment total is greater than the grade
    assignmentTotal = assignments[assignmentNamePos.index(assignmentName)]["Total"]
    if(assignmentTotal >= grade):
        students[studentNamePos.index(studentName)][assignmentName] = grade / assignmentTotal 
        print(f'{studentName}\'s grade for {assignmentName} now at a {(grade / assignmentTotal)*100}%')
    else:
        print("\t Invalid Input, we only accept point values from 0 to " + str(assignmentTotal))

def startUp():
    global students
    print("Welcome to Grader, the program to do everything with students grades, choose what you want to do;")
    print("\tChoose A to average the class grades")
    print("\tChoose B to add a student")
    print("\tChoose C to make an Assignment")
    print("\tChoose D to grade an Assignment")
    print("\tChoose E to end this session")
    userInput = ""
    while 7 == 7:
        if(userInput == ""):
            print("Now, Choose another item from the list above")
            userInput = input("What option do you want to choose? ")

        if(userInput.upper() == "A"):
            print(f"{averageGrades()} for a class of {len(students)} student(s)")
            userInput = ""

        elif(userInput.upper() == "B"):
            userInput = input("\tWhat is the student's name? ")
            currentStudents = addStudent(userInput)
            print(currentStudents)
            userInput = ""

        elif(userInput.upper() == "C"):
            assignmentName = input("What is the assignment name? ")
            assignmentTotal = input("What is the assignment total? ")
            try:
                if(assignmentTotal != float("nan") and float(assignmentTotal) > 0):
                    makeAssignments(assignmentName, float(assignmentTotal))
                    userInput = ""
            except:
                print("Invalid Point Score, please try again")
                userInput = "C"

        elif(userInput.upper() == "D"):
            global assignmentNamePos, studentNamePos
            isValid = [False, False]
            studentAssignment = input("\tWhat is the assignment your grading? ")
            studentGrade = input("\tHow many points did they earn? ")
            studentName = input("\tWhat is the student your grading? ")
            for x in range(0, len(assignmentNamePos)):
                if(studentAssignment.upper() == assignmentNamePos[x].upper()):
                    isValid[0] = True
            if(isValid[0] == False):
                print("Invalid Assignment Name, please try again")
                userInput = "D"
            for x in range(0, len(studentNamePos)):
                if(studentName.upper() == studentNamePos[x].upper()):
                    isValid[1] = True
            if(isValid[1] == False):
                print("Invalid Student Name, please try again")
                userInput = "D"
            try:
                if(studentGrade != float("nan") and float(studentGrade) > 0 and int(isValid[0]) + int(isValid[1]) == 2):
                    makeAssignments(assignmentName, float(studentGrade))
                    userInput = ""
                    gradeAssignment(studentName, studentAssignment, float(studentGrade))
            except:
                print("Invalid Values, please try again")
                userInput = "D"

        elif(userInput.upper() == "E"):
            print("\tHave a lovely day!")
            break

        else:
            print("Invaid Input, please try again")
            userInput = ""
startUp()
</p>

Forth and Fifth, random Animal:

<button onclick = "javascript:getPythonCode(3)">Copy code</button>

<p id = "codeCell" hidden>

```python
import time

currentMove = 0
player = {
    "item":"x",
    "x":5,
    "y":5
}
wall = {
    "vertInfo":{
        "0":{
            "item":"#",
            "x":6,
            "y":6
        },
        "1":{
            "item":"#",
            "x":7,
            "y":6,
        },
        "2":{
            "item":"#",
            "x":9,
            "y":6,
        },
        "3":{
            "item":"#",
            "x":10,
            "y":6,
        },
        "4":{
            "item":"#",
            "x":10,
            "y":5,
        },
        "5":{
            "item":"#",
            "x":10,
            "y":4,
        },
        "6":{
            "item":"#",
            "x":10,
            "y":3,
        },
        "7":{
            "item":"#",
            "x":10,
            "y":2,
        },
        "8":{
            "item":"#",
            "x":9,
            "y":2,
        },
        "9":{
            "item":"#",
            "x":8,
            "y":2,
        },
        "10":{
            "item":"#",
            "x":7,
            "y":2,
        },
        "11":{
            "item":"#",
            "x":6,
            "y":2,
        },
        "12":{
            "item":"#",
            "x":6,
            "y":3
        },
        "13":{
            "item":"#",
            "x":6,
            "y":4
        },
        "14":{
            "item":"#",
            "x":6,
            "y":5
        }
    }
}

toMove = []
theObjs = [wall, player]
lane = ""
width = 20
height = 20
thePixel = ""
rec = []

def createAnimals():
    global toMove
    dog = {}
    bird = {}
    cat = {}
    toMove = [2, 3, 4]
    items = ["&", "^", "~"]
    animals = [dog, bird, cat]
    for beings in range(0, len(animals)):
        animals[beings]["x"] = beings * 1 + 12
        animals[beings]["y"] = beings * 1 + 12
        animals[beings]["item"] = items[beings]
        theObjs.append(animals[beings])

def animalMoves():
    global toMove, display
    couldMove = ["w", "a", "s", "d"]
    for x in range(0, len(toMove)):
        walk(couldMove[random.randint(0, 3)], theObjs[toMove[x]])

    return screen()

def startUp():
    global display
    createAnimals()
    display = [["."]*20]*20
    movements()

def decompileVerts():
    objects = []
    for x in range(0, len(theObjs)):
        if('vertInfo' in theObjs[x]):
            for b in range(0, len(theObjs[x]["vertInfo"])):
                if(theObjs[x]["vertInfo"][str(b)]["x"] > 0 and 20 > theObjs[x]["vertInfo"][str(b)]["x"] and theObjs[x]["vertInfo"][str(b)]["y"] > 0):
                    objects.append(theObjs[x]["vertInfo"][str(b)])
        else:
            objects.append(theObjs[x])
    return objects

def screen():
    global display, width, height, loadObjCt, thePixel
    theObjs = decompileVerts()
    thePixel = ""
    theObjs.sort(key = lambda a: a["y"] * width + a["x"])
    loadObjCt = 0
    for y in range(0, height, 1):
        if(y < 10):
            thePixel += "0"
        thePixel += str(y)
        display[y] = []
        for x in range(0, width, 1):
            if theObjs[loadObjCt]["x"] == x and theObjs[loadObjCt]["y"] == y:
                display[y].append([theObjs[loadObjCt]["item"]])
                if(loadObjCt + 1 < len(theObjs)):
                    loadObjCt += 1
            else:
                display[y].append(["."])
            thePixel += str(display[y][x][0])
        thePixel += " "*300
        display[y] = display[y]
    return thePixel

def walk(moves, currentObj):
    global display, rec
    theRec = ""
    if(moves == "w" and (display[currentObj["y"] - 1][currentObj["x"]] == ["."]) and (currentObj["y"] - 1) >= 0):
        currentObj["y"] -= 1
        theRec = "w"
    elif(moves == "a" and display[currentObj["y"]][currentObj["x"] - 1] == ["."] and (currentObj["x"] - 1) >= 0):  
        currentObj["x"] -= 1
        theRec = "a"
    elif(moves == "d" and (display[currentObj["y"] + 1][currentObj["x"]] == ["."]) and (currentObj["y"] - 1) >= 20):
        currentObj["x"] += 1
        theRec = "d"
    elif(moves == "s" and (display[currentObj["y"]][currentObj["x"] + 1] == ["."]) and (currentObj["x"] - 1) >= 20):
        currentObj["y"] += 1
        theRec = "s"

    return screen()

def movements():
    global rec, thePixel
    moves = [
        "a",
        "a",
        "s",
        "s",
        "s",
        "d",
        "d",
        "d",
        "w",
        "w",
        "a",
    ]
    newLine = " "*300
    movesRec = ""
    for x in range(0, len(moves) - 0):
        walk(moves[x], player)
        view = animalMoves()
        print(view, end = "\r")
        movesRec += moves[x] + ", "

        if(moves[x - 1] == moves[x]):
            time.sleep(.4)
        else:
            time.sleep(.6)
    print("\n--------------------" + "\n" + "Moves were: " + str(movesRec))


startUp()
</p>

Fifth One: <button onclick = "javascript:getPythonCode(4)">Copy code</button>

<p id = "codeCell" hidden>

</p>

<script>
    function getPythonCode(num){
        var copyText = document.querySelectorAll("#codeCell");
        copyText = copyText[num].innerHTML
        console.log(copyText)
        let text = copyText;
        const copyContent = async () => {
            try {
                await navigator.clipboard.writeText(text);
                console.log('Content copied to clipboard');
            } catch (err) {
                console.error('Failed to copy: ', err);
        }
        }
    }
</script>

