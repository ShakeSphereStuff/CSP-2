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

First Team teach, Developing algorithms: <button onclick = "javascript:getPythonCode(0)">Copy code</button> <br>
<p id = "codeCellOpen0" style = "display: none">
    students = [] <br>
    studentNamePos = [] <br>
    assignments = [] <br>
    assignmentNamePos = [] <br>
    totalGrades = 0.0 <br>
    def averageGrades(): <br>
        global totalGrades, students, assignments <br>
        for theStudent in students: <br>
            print(theStudent["Name"] + ":") <br>
            print("-"*10) <br>
            for theAssignment in assignments: <br>
                print(f'\t Assignment Name: {theAssignment["Name"]}') <br>
                print(f'\t Assignment Total: {theAssignment["Total"]}') <br>
                print(f'\t Student Score: {theStudent[theAssignment["Name"]]}') <br>
                if(theAssignment["Name"] != assignments[-1]["Name"]): <br>
                    print("-" * 10) <br>
                totalGrades += theStudent[theAssignment["Name"]] / theAssignment["Total"] <br>
        return totalGrades / (len(assignments) * len(students)) <br>
        <br>
    def addStudent(name): <br>
        global students, assignments, studentNamePos <br>
        newStudent = { <br>
            "Name": str(name) <br>
        } <br>
        studentNamePos.append(name) <br>
        for x in assignments: <br>
            newStudent[str(x["Name"])] = 0 <br>
        students.append(newStudent) <br>
        return students <br>
    <br>
    def makeAssignments(assignmentName, assignmentTotal): <br>
        global assignments, assignmentNamePos <br>
        newAssignment = {} <br>
        newAssignment["Name"] = assignmentName <br>
        newAssignment["Total"] = assignmentTotal <br>
        assignmentNamePos.append(assignmentName) <br>
        assignments.append(newAssignment) <br>
    <br>
    def gradeAssignment(studentName, assignmentName, grade): <br>
        global students, assignmentNamePos, assignments, studentNamePos <br>
        # If the assignment total is greater than the grade <br>
        assignmentTotal = assignments[assignmentNamePos.index(assignmentName)]["Total"] <br>
        if(assignmentTotal >= grade): <br>
            students[studentNamePos.index(studentName)][assignmentName] = grade / assignmentTotal <br>
            print(f'{studentName}\'s grade for {assignmentName} now at a {(grade / assignmentTotal)*100}%') <br>
        else: <br>
            print("\t Invalid Input, we only accept point values from 0 to " + str(assignmentTotal)) <br>
    <br>
    def startUp(): <br>
        global students <br>
        print("Welcome to Grader, the program to do everything with students grades, choose what you want to do;") <br>
        print("\tChoose A to average the class grades") <br>
        print("\tChoose B to add a student") <br>
        print("\tChoose C to make an Assignment") <br>
        print("\tChoose D to grade an Assignment") <br>
        print("\tChoose E to end this session") <br>
        userInput = "" <br>
        while 7 == 7: <br>
            if(userInput == ""): <br>
                print("Now, Choose another item from the list above") <br>
                userInput = input("What option do you want to choose? ") <br>
            if(userInput.upper() == "A"): <br>
                print(f"{averageGrades()} for a class of {len(students)} student(s)") <br>
                userInput = "" <br>
            elif(userInput.upper() == "B"): <br>
                userInput = input("\tWhat is the student's name? ") <br>
                currentStudents = addStudent(userInput) <br>
                print(currentStudents) <br>
                userInput = "" <br>
            elif(userInput.upper() == "C"): <br>
                assignmentName = input("What is the assignment name? ") <br>
                assignmentTotal = input("What is the assignment total? ") <br>
                try: <br>
                    if(assignmentTotal != float("nan") and float(assignmentTotal) > 0): <br>
                        makeAssignments(assignmentName, float(assignmentTotal)) <br>
                        userInput = "" <br>
                except: <br>
                    print("Invalid Point Score, please try again") <br>
                    userInput = "C" <br>
            elif(userInput.upper() == "D"): <br>
                global assignmentNamePos, studentNamePos <br>
                isValid = [False, False] <br>
                studentAssignment = input("\tWhat is the assignment your grading? ") <br>
                studentGrade = input("\tHow many points did they earn? ") <br>
                studentName = input("\tWhat is the student your grading? ") <br>
                for x in range(0, len(assignmentNamePos)): <br>
                    if(studentAssignment.upper() == assignmentNamePos[x].upper()): <br>
                        isValid[0] = True <br>
                if(isValid[0] == False): <br>
                    print("Invalid Assignment Name, please try again") <br>
                    userInput = "D" <br>
                for x in range(0, len(studentNamePos)): <br>
                    if(studentName.upper() == studentNamePos[x].upper()): <br>
                        isValid[1] = True <br>
                if(isValid[1] == False): <br>
                    print("Invalid Assignment Name, please try again") <br>
                    userInput = "D" <br>
                try: <br>
                    if(studentGrade != float("nan") and float(studentGrade) > 0 and int(isValid[0]) + int(isValid[1]) == 2): <br>
                        makeAssignments(assignmentName, float(studentGrade)) <br>
                        userInput = "" <br>
                        gradeAssignment(studentName, studentAssignment, float(studentGrade)) <br>
                except: <br>
                    print("Invalid Values, please try again") <br>
                    userInput = "D" <br>
            elif(userInput.upper() == "E"): <br> 
                print("\tHave a lovely day!") <br>
                break <br>
            else: <br>
                print("Invaid Input, please try again") <br>
                userInput = "" <br>
    startUp()
</p>

Second Team Teach, Data Abstraction: <button onclick = "javascript:getPythonCode(1)">Copy code</button>

<p id = "codeCellOpen1" style = "display: none">
import random <br>
name = input("What's your name?") <br>
continueGreet = True <br>
selectedGreeting = 0 <br>
result = "" <br>
Greetings = [["Hello", "State"], ["Hi there", "State"], ["How are you doing", "Quest"]] <br>
def greeting(): <br>
    global result, selectedGreeting, Greetings <br>
    selectedGreeting = random.randint(0, len(Greetings) - 1) <br>
    if(Greetings[selectedGreeting][1] == "Quest"): <br>
        print("\t" + Greetings[selectedGreeting][0] + " " + name + "?") <br>
        result = Greetings[selectedGreeting][0] + " " + name + "?" <br>
    elif(Greetings[selectedGreeting][1] == "State"): <br>
        print("\t" + Greetings[selectedGreeting][0] + " " + name) <br>
        result = Greetings[selectedGreeting][0] + " " + name <br>
    else: <br>
        print("INVALID GREETING") <br>
 <br>
greeting() <br>
 <br>
while(continueGreet == True): <br>
    global result, selectedGreeting, Greetings <br>
    isRight = input("Do you like this greeting? Y/N: ") <br>
    if(isRight.upper() == "N"): <br>
        del Greetings[selectedGreeting] <br>
    if(len(Greetings) == 0): <br>
        print("There are no more greetings, try adding 1 to the system, or pick one provided") <br>
        continueGreet = False <br>
    else: <br>
        greeting() <br>
        continueGreet = True <br>
    elif(isRight.upper() == "Y"): <br>
        continueGreet = False <br>
        print(result) <br>
    else: <br>
        print("Invalid") <br>
        continueGreet = True <br>
</p>



Third Team Teach, Developing Algorithms: <button onclick = "javascript:getPythonCode(2)">Copy code</button>

<p id = "codeCellOpen2" style = "display: none">

students = [] <br>
studentNamePos = [] <br>
assignments = [] <br>
assignmentNamePos = [] <br>
totalGrades = 0.0 <br>
def averageGrades(): <br>
    global totalGrades, students, assignments <br>
    for theStudent in students: <br>
        print(theStudent["Name"] + ":")  <br>
        print("-"*10) <br>
        for theAssignment in assignments: <br>
            print(f'\t Assignment Name: {theAssignment["Name"]}') <br>
            print(f'\t Assignment Total: {theAssignment["Total"]}') <br>
            print(f'\t Student Score: {theStudent[theAssignment["Name"]]}') <br>
            if(theAssignment["Name"] != assignments[-1]["Name"]): <br>
                print("-" * 10) <br>
            totalGrades += theStudent[theAssignment["Name"]] / theAssignment["Total"] <br>
 <br>
    return totalGrades / (len(assignments) * len(students)) <br>
def addStudent(name): <br>
    global students, assignments, studentNamePos <br>
    newStudent = { <br>
        "Name": str(name) <br>
    } <br>
    studentNamePos.append(name) <br>
    for x in assignments: <br>
        newStudent[str(x["Name"])] = 0 <br>
    students.append(newStudent) <br>
    return students <br>
 <br>
def makeAssignments(assignmentName, assignmentTotal): <br>
    global assignments, assignmentNamePos <br>
    newAssignment = {} <br>
    newAssignment["Name"] = assignmentName <br>
    newAssignment["Total"] = assignmentTotal <br>
    assignmentNamePos.append(assignmentName) <br>
    assignments.append(newAssignment) <br>
 <br>
def gradeAssignment(studentName, assignmentName, grade): <br>
    global students, assignmentNamePos, assignments, studentNamePos <br>
    # If the assignment total is greater than the grade <br>
    assignmentTotal = assignments[assignmentNamePos.index(assignmentName)]["Total"] <br>
    if(assignmentTotal >= grade): <br>
        students[studentNamePos.index(studentName)][assignmentName] = grade / assignmentTotal  <br>
        print(f'{studentName}\'s grade for {assignmentName} now at a {(grade / assignmentTotal)*100}%') <br>
    else: <br>
        print("\t Invalid Input, we only accept point values from 0 to " + str(assignmentTotal)) <br>
 <br>
def startUp(): <br>
    global students <br>
    print("Welcome to Grader, the program to do everything with students grades, choose what you want to do;") <br>
    print("\tChoose A to average the class grades") <br>
    print("\tChoose B to add a student") <br>
    print("\tChoose C to make an Assignment") <br>
    print("\tChoose D to grade an Assignment") <br>
    print("\tChoose E to end this session") <br>
    userInput = "" <br>
    while 7 == 7: <br>
        if(userInput == ""): <br>
            print("Now, Choose another item from the list above") <br>
            userInput = input("What option do you want to choose? ") <br>
 <br>
        if(userInput.upper() == "A"): <br>
            print(f"{averageGrades()} for a class of {len(students)} student(s)") <br>
            userInput = "" <br>
 <br>
        elif(userInput.upper() == "B"): <br>
            userInput = input("\tWhat is the student's name? ") <br>
            currentStudents = addStudent(userInput) <br>
            print(currentStudents) <br>
            userInput = "" <br>
<br>
        elif(userInput.upper() == "C"): <br>
            assignmentName = input("What is the assignment name? ") <br>
            assignmentTotal = input("What is the assignment total? ") <br>
            try: <br>
                if(assignmentTotal != float("nan") and float(assignmentTotal) > 0): <br>
                    makeAssignments(assignmentName, float(assignmentTotal)) <br>
                    userInput = "" <br>
            except: <br>
                print("Invalid Point Score, please try again") <br>
                userInput = "C" <br>
 <br>
        elif(userInput.upper() == "D"): <br>
            global assignmentNamePos, studentNamePos <br>
            isValid = [False, False] <br>
            studentAssignment = input("\tWhat is the assignment your grading? ") <br>
            studentGrade = input("\tHow many points did they earn? ") <br>
            studentName = input("\tWhat is the student your grading? ") <br>
            for x in range(0, len(assignmentNamePos)): <br>
                if(studentAssignment.upper() == assignmentNamePos[x].upper()): <br>
                    isValid[0] = True <br>
            if(isValid[0] == False): <br>
                print("Invalid Assignment Name, please try again") <br>
                userInput = "D" <br>
            for x in range(0, len(studentNamePos)): <br>
                if(studentName.upper() == studentNamePos[x].upper()): <br>
                    isValid[1] = True <br>
            if(isValid[1] == False): <br>
                print("Invalid Student Name, please try again") <br>
                userInput = "D" <br>
            try: <br>
                if(studentGrade != float("nan") and float(studentGrade) > 0 and int(isValid[0]) + int(isValid[1]) == 2): <br>
                    makeAssignments(assignmentName, float(studentGrade)) <br>
                    userInput = "" <br>
                    gradeAssignment(studentName, studentAssignment, float(studentGrade)) <br>
            except: <br>
                print("Invalid Values, please try again") <br>
                userInput = "D" <br>
 <br>
        elif(userInput.upper() == "E"): <br>
            print("\tHave a lovely day!") <br>
            break <br>
 <br>
        else: <br>
            print("Invaid Input, please try again") <br>
            userInput = "" <br>
startUp() <br>
</p>
Forth and Fifth, random Animal: <button onclick = "javascript:getPythonCode(3)">Copy code</button>

<p id = "codeCellOpen3" style = "display: none">

import time <br>
 <br>
currentMove = 0 <br>
player = { <br>
    "item":"x", <br>
    "x":5, <br>
    "y":5 <br>
} <br>
wall = { <br>
    "vertInfo":{ <br>
        "0":{ <br>
            "item":"#", <br>
            "x":6, <br>
            "y":6 <br>
        }, <br>
        "1":{ <br>
            "item":"#", <br>
            "x":7, <br>
            "y":6, <br>
        }, <br>
        "2":{ <br>
            "item":"#", <br>
            "x":9, <br>
            "y":6, <br>
        }, <br>
        "3":{ <br>
            "item":"#", <br>
            "x":10, <br>
            "y":6, <br>
        }, <br>
        "4":{ <br>
            "item":"#", <br>
            "x":10, <br>
            "y":5, <br>
        }, <br>
        "5":{ <br>
            "item":"#", <br>
            "x":10, <br>
            "y":4, <br>
        }, <br>
        "6":{ <br>
            "item":"#", <br>
            "x":10, <br>
            "y":3, <br>
        }, <br>
        "7":{ <br>
            "item":"#", <br>
            "x":10, <br>
            "y":2, <br>
        }, <br>
        "8":{ <br>
            "item":"#", <br>
            "x":9, <br>
            "y":2, <br>
        }, <br>
        "9":{ <br>
            "item":"#", <br>
            "x":8, <br>
            "y":2, <br>
        }, <br>
        "10":{ <br>
            "item":"#", <br>
            "x":7, <br>
            "y":2, <br>
        }, <br>
        "11":{ <br>
            "item":"#", <br>
            "x":6, <br>
            "y":2, <br>
        }, <br>
        "12":{ <br>
            "item":"#", <br>
            "x":6, <br>
            "y":3 <br>
        }, <br>
        "13":{ <br>
            "item":"#", <br>
            "x":6, <br>
            "y":4 <br>
        }, <br>
        "14":{ <br>
            "item":"#", <br>
            "x":6, <br>
            "y":5 <br>
        } <br>
    } <br>
} <br>
 <br>
toMove = [] <br>
theObjs = [wall, player] <br>
lane = "" <br>
width = 20 <br>
height = 20 <br>
thePixel = "" <br>
rec = [] <br>
 <br>
def createAnimals(): <br>
    global toMove <br>
    dog = {} <br>
    bird = {} <br>
    cat = {} <br>
    toMove = [2, 3, 4] <br>
    items = ["&", "^", "~"] <br>
    animals = [dog, bird, cat] <br>
    for beings in range(0, len(animals)): <br>
        animals[beings]["x"] = beings * 1 + 12 <br>
        animals[beings]["y"] = beings * 1 + 12 <br>
        animals[beings]["item"] = items[beings] <br>
        theObjs.append(animals[beings]) <br>
 <br>
def animalMoves(): <br>
    global toMove, display <br>
    couldMove = ["w", "a", "s", "d"] <br>
    for x in range(0, len(toMove)): <br>
        walk(couldMove[random.randint(0, 3)], theObjs[toMove[x]]) <br>
 <br>
    return screen() <br>
 <br>
def startUp(): <br>
    global display <br>
    createAnimals() <br>
    display = [["."]*20]*20 <br>
    movements() <br>
 <br>
def decompileVerts(): <br>
    objects = [] <br>
    for x in range(0, len(theObjs)): <br>
        if('vertInfo' in theObjs[x]): <br>
            for b in range(0, len(theObjs[x]["vertInfo"])): <br>
                if(theObjs[x]["vertInfo"][str(b)]["x"] > 0 and 20 > theObjs[x]["vertInfo"][str(b)]["x"] and theObjs[x]["vertInfo"][str(b)]["y"] > 0): <br>
                    objects.append(theObjs[x]["vertInfo"][str(b)]) <br>
        else: <br>
            objects.append(theObjs[x]) <br>
    return objects <br>
 <br>
def screen(): <br>
    global display, width, height, loadObjCt, thePixel <br>
    theObjs = decompileVerts() <br>
    thePixel = "" <br>
    theObjs.sort(key = lambda a: a["y"] * width + a["x"]) <br>
    loadObjCt = 0 <br>
    for y in range(0, height, 1): <br>
        if(y < 10): <br>
            thePixel += "0" <br>
        thePixel += str(y) <br>
        display[y] = [] <br>
        for x in range(0, width, 1): <br>
            if theObjs[loadObjCt]["x"] == x and theObjs[loadObjCt]["y"] == y: <br>
                display[y].append([theObjs[loadObjCt]["item"]]) <br>
                if(loadObjCt + 1 < len(theObjs)): <br>
                    loadObjCt += 1 <br>
            else: <br>
                display[y].append(["."]) <br>
            thePixel += str(display[y][x][0]) <br>
        thePixel += " "*300 <br>
        display[y] = display[y] <br>
    return thePixel <br>
 <br>
def walk(moves, currentObj): <br>
    global display, rec <br>
    theRec = "" <br>
    if(moves == "w" and (display[currentObj["y"] - 1][currentObj["x"]] == ["."]) and (currentObj["y"] - 1) >= 0): <br>
        currentObj["y"] -= 1 <br>
        theRec = "w" <br>
    elif(moves == "a" and display[currentObj["y"]][currentObj["x"] - 1] == ["."] and (currentObj["x"] - 1) >= 0): <br>
        currentObj["x"] -= 1 <br>
        theRec = "a" <br>
    elif(moves == "d" and (display[currentObj["y"] + 1][currentObj["x"]] == ["."]) and (currentObj["y"] - 1) >= 20): <br>
        currentObj["x"] += 1 <br>
        theRec = "d" <br>
    elif(moves == "s" and (display[currentObj["y"]][currentObj["x"] + 1] == ["."]) and (currentObj["x"] - 1) >= 20): <br>
        currentObj["y"] += 1 <br>
        theRec = "s" <br>
 <br>
    return screen() <br>
 <br>
def movements(): <br>
    global rec, thePixel <br>
    moves = [ <br>
        "a", <br>
        "a", <br>
        "s", <br>
        "s", <br>
        "s", <br>
        "d", <br>
        "d", <br>
        "d", <br>
        "w", <br>
        "w", <br>
        "a", <br>
    ] <br>
    newLine = " "*300 <br>
    movesRec = "" <br>
    for x in range(0, len(moves) - 0): <br>
        walk(moves[x], player) <br>
        view = animalMoves() <br>
        print(view, end = "\r") <br>
        movesRec += moves[x] + ", " <br>
 <br>
        if(moves[x - 1] == moves[x]): <br>
            time.sleep(.4) <br>
        else: <br>
            time.sleep(.6) <br>
    print("\n--------------------" + "\n" + "Moves were: " + str(movesRec)) <br>
 <br>
 <br>
startUp() <br>
</p>

Fifth One, Lists and search: <button onclick = "javascript:getPythonCode(4)">Copy code</button>

<p id = "codeCellOpen4" style = "display: none">
import random, math <br>
nums = [0, 2, 4, 7, 15, 21, 34, 36, 43, 48, 51, 60, 70, 71, 76, 77, 82, 94, 95, 99] <br>
 <br>
start = 0 <br>
end = len(nums) - 1 <br>
worstNums = 0 <br>
choosenNum = -1 <br>
for d in range(0, len(nums) - 1): <br>
    choosenNum += 1 <br>
    currentPos = (len(nums) - 1) // 2 <br>
    start = 0 <br>
    end = len(nums) - 1 <br>
 <br>
    for c in range(2, 10): <br>
        currentPos = (start + end) // 2  <br>
        if(nums[currentPos] > nums[choosenNum]): <br>
            end = currentPos - 1 <br>
            # currentPos += math.floor((len(nums) - currentPos) / 2 - 0.5) <br>
            #  <br>
        elif(nums[currentPos] < nums[choosenNum]): <br>
            start = currentPos + 1 <br>
            # currentPos -= math.floor((len(nums) - currentPos) / 2 - 0.5) <br>
        elif(nums[currentPos] == nums[choosenNum]): <br>
            print("Len is " + str(c - 2) + " at " + str(currentPos)) <br>
            if(worstNums < (c - 2)): <br>
                worstNums = c - 2 <br>
            break <br>
print("-"*20 + "\n" + "WorstNums is " + str(worstNums)) <br>
</p> 

Sixth one, procedures: <button onclick = "javascript:getPythonCode(5)">Copy code</button>

<p id = "codeCellOpen5" style = "display: none;"> 
# First one <br>
 <br>
def exponenchal(exponent, simTime): <br>
    count = "" <br>
    for x in range(0, simTime + 1): <br>
        count += f"Term {x}; {exponent ** x}:\n\t" <br>
        for y in range(1, (exponent ** x) + 1): <br>
            count += str(y%10) <br>
            if y%10 == 0: <br>
                count += f" {y}\'s " <br>
        count += "\n" <br>
    return count <br>
nums = exponenchal(2, 14) <br>
print(nums) <br>
 <br>
# Second One <br>
 <br>
import random <br>
nums = [] <br>
randomNums = [] <br>
for a in range(0, 100): <br>
    randomNums.append(a) <br>
for x in range(0, 20): <br>
    randNum = random.randint(0, (len(randomNums) - 1)) <br>
    nums.append(randomNums[randNum]) <br>
    randomNums.remove(randomNums[randNum]) <br>
print(sorted(nums)) <br>
 <br>
</p>

Seventh one, Boolean Operations and Conditions: <button onclick = "javascript:getPythonCode(6)">Copy code</button>

<p id = "codeCellOpen6" style = "display: none">
# Silly thing I made that made me Mad! <br>
print("Welcome to MegaCorp, please state your details") <br>
userFirstName = input("First Name: ") <br>
print("Input 'Null' if you don't have a prefered Name ") <br>
userPreferedName = input("Prefered Name: ") <br>
userLastName = input("Last Name: ") <br>
userAge = input("Age: ") <br>
 <br>
# What I used to bypass login, comment everything above and uncomment the comments below except for this line <br>
# userAge = 20 <br>
# userFirstName = "Fred" <br>
# userPreferedName = "Freddy" <br>
# userLastName = "Kilm" <br>
# userPay = 0 <br>
 <br>
def findPercent(userInput): <br>
    currentUserGrade = "" <br>
    currentUserClass = "" <br>
    classes = ["A", "B", "C", "D", "E", "F", "G"] <br>
    for x in userInput: <br>
        print(x) <br>
        if(x.isdigit()): <br>
            currentUserGrade += x <br>
            continue <br>
        for y in classes: <br>
            if x.upper() == y: <br>
                currentUserClass = y <br>
                continue <br>
    currentUserGrade = int(currentUserGrade) <br>
    return currentUserClass, currentUserGrade <br>
 <br>
def MegaCorpFinance(): <br>
    global userPreferedName, userPay <br>
    yearsOfEmployee = input(f"How many years have you served at the company {userPreferedName}? ") <br>
    jobPay = { # Per year <br>
        "Coder": 150000, <br>
        "Janitor": 30000 <br>
    } <br>
    for jobTitle in jobPay: <br>
        print("\t*" + str(jobTitle)) <br>
 <br>
    employeeTitle = input("Out of these, which is your job? ") <br>
 <br>
    for jobTitle in jobPay: <br>
        if(employeeTitle.upper() == jobTitle.upper()): <br>
            print("Valid Title") <br>
            employeeTitle = jobTitle <br>
 <br>
    if(userPay == 0): <br>
        userPay = jobPay[str(employeeTitle)] <br>
 <br>
 <br>
    if(int(yearsOfEmployee) > 5): <br>
        userPay *= 1.05  <br>
    print(userPay) <br>
 <br>
if(userPreferedName.upper() == "NULL"): <br>
    userPreferedName = userFirstName <br>
else:  <br>
    userPreferedName = userPreferedName <br>
 <br>
if(int(userAge) > 18): <br>
    print("Redirecting you to MegaCorpMain") <br>
    MegaCorpFinance() <br>
elif(int(userAge) < 18): <br>
    print(f"{userPreferedName}, we are redirecting you to MegaCollegeCorp") <br>
    print("\tType: A + grade for your last History") <br>
    print("\tType: B + grade for your last English") <br>
    print("\tType: C + grade for your last Math") <br>
    print("\tType: D + grade for your last Science") <br>
    print("\tType: E + grade for your last Forign Language") <br>
    print("\tType: F + grade for your last Fine Arts") <br>
    print("\tType: G + grade for your last Electives") <br>
    print("\tType Submit to submit your grades to us") <br>
    userGrade = { <br>
            "A": "F", # History <br>
            "B": "F", # English <br>
            "C": "F", # Math <br>
            "D": "F", # Science <br>
            "E": "F", # Forign Language <br>
            "F": "F", # Fine Arts <br>
            "G": "F" # Electives <br>
    } <br>
    while 7 == 7: <br>
        userInput = input("Input percents from your classes in base 10: ") <br>
        userInput = userInput.replace(" ", "") <br>
        print("User input is: " + str(userInput)) <br>
        classes = ["A", "B", "C", "D", "E", "F", "G"] <br>
        grades = ["A", "B", "C", "D", "E", "F"] <br>
        if(userInput.upper() == "SUBMIT"): <br>
            jobRequirements = { <br>
                "Coder": { <br>
                    "A": "C", <br>
                    "B": "B", <br>
                    "C": "A", <br>
                    "D": "A", <br>
                    "E": "C", <br>
                    "F": "C", <br>
                    "G": "C" <br>
                }, <br>
                "Jainitor": { <br>
                    "A": "D", <br>
                    "B": "D", <br>
                    "C": "D", <br>
                    "D": "D", <br>
                    "E": "D", <br>
                    "F": "D", <br>
                    "G": "D" <br>
                } <br>
            } <br>
            for currentJob in jobRequirements: <br>
                amountOfRequirements = 0  <br>
                print(f"Scanning Requirement for {currentJob}") <br>
                for currentClassCheck in classes: <br>
                    if(grades.index(jobRequiremets[currentJob][currentClassCheck]) >= grades.index(userGrade[currentClassCheck])): <br>
                        amountOfRequirements += 1 <br>
                if(amountOfRequirements > 4): <br>
                    print(f"You got the application for {currentJob}!") <br>
                    break <br>
 <br>
            break <br>
        percent = findPercent(userInput) <br>
        currentUserGrade = int(percent[1]) <br>
        currentUserClass = percent[0] <br>
        if(currentUserGrade > 80): <br>
            currentUserGrade = "A" <br>
        elif(currentUserGrade >= 60): <br>
            currentUserGrade = "B" <br>
        elif(currentUserGrade >= 50): <br>
            currentUserGrade = "C" <br>
        elif(currentUserGrade >= 45): <br>
            currentUserGrade = "D" <br>
        elif(currentUserGrade >= 25): <br>
            currentUserGrade = "E" <br>
        else: <br>
            currentUserGrade = "F" <br>
        userGrade[str(currentUserClass)] = currentUserGrade <br>
        print(f"Class type {currentUserClass} is now set to grade {currentUserGrade}") <br>
</p>
Seventh one, libaries: <button onclick = "javascript:getPythonCode(7)">Copy code</button>

<p id = "codeCellOpen7" style = "display: none;">
Here’s the HW for Libraries <br>
 <br>
from imdb import Cinemagoer <br>
import random <br>
 <br>
ia = Cinemagoer() <br>
 <br>
name = "Tarzan" <br>
 <br>
randMovieID = "0120855" <br>
 <br>
def callMovies(): <br>
    try: <br>
        movies = ia.get_movie(str(randMovieID)) <br>
        print(movies) <br>
        print(movies.current_info) <br>
        for x in movies.current_info: <br>
            print(x) <br>
            print(type(x)) <br>
            print(movies["plot"]) <br>
            print(movies[x]) <br>
    except: <br>
        print("Error, can't find Movie") <br>
         <br>
def parseMovie(dataSet): <br>
    dataSet = str(dataSet) <br>
    dataSet = dataSet[1: -2] <br>
    dataSet = dataSet.replace("<", "").replace(">", "", -1).replace("_", "", <br> -1).replace("[http]", "") <br>
    dataSet = dataSet.split("Movie id:") <br>
    dataSet = dataSet[1:-1] <br>
    return dataSet <br>
     <br>
print("Type 'result' to get the plot")  <br>
 <br>
terms = [] <br>
userTerms = [] <br>
     <br>
while 7 == 7: <br>
    userInput = input("What movies do you want to get the plot of?: ") <br>
    userTerms += [userInput] <br>
    if(userInput == "result"): <br>
        plotSums = [] <br>
        for x in range(0, len(terms)): <br>
            finalText = "" <br>
            plotSums += [[]] <br>
            try: <br>
                plotSums[x] += [str(ia.get_movie(terms[x])["plot"])] <br>
            except: <br>
                print("Can't get summery") <br>
                continue <br>
        # print(plotSums[0]) <br>
            banList = ["\n", "\'", "\\", "[", "]", "\""] <br>
            for y in plotSums[x][0]: <br>
                currentText = y <br>
                for z in banList: <br>
                    currentText = str(currentText).replace(z, "") <br>
                if(currentText != ""): <br>
                    finalText += str(currentText) <br>
            print(f"\n \nFinal Text for {userTerms[x]}: \n" + "-"*20 + "\n" + str(finalText)) <br>
     <br>

    results = ia.search_movie(userInput) <br>
    results = str(parseMovie(results)[0]) <br>
    terms.append(results[0:7]) <br>
    print("\nFinal Result: " + str(results[0:7])) <br>
  2.) Imdb api, allows for you to get an id from a movie title and get other terms, directors, genres, plot and more. <br>
 <br>
1.) Pygame API, allows for videogames to be played, favorite variables being get num_displays and pygame.font.quit <br>
 <br>
Imdb api, used to search for movies, favorite variables being tv kind ([‘kind’]) and filmography ([‘filmography’]) <br>
 <br>
Turtle API, used to make graphics, favorite variables being speed() and bye() <br>
</p> 

<!-- id = "codeCellOpen1" style = "display: none"-->
<script>
    function getPythonCode(num){
        console.log(num)
        if(document.getElementById("codeCellOpen" + String(num)) == null){
            var showText = document.getElementById("codeCellClose" + String(num));
            showText.style = "display:none"
            showText.id = "codeCellOpen" + String(num)
            return null
        }
        // var copyText = document.getElementById("#codeCellOpen" + String(num));
        // copyText = copyText.innerHTML
        var showText = document.getElementById("codeCellOpen" + String(num));
        console.log(showText.innerHTML)
        showText.style = "display:inline" 
        showText.id = "codeCellClose"  + String(num)
        // let text = copyText;
        // const copyContent = async () => {
        //     try {
        //         await navigator.clipboard.writeText(text);
        //         console.log('Content copied to clipboard');
        //     } catch (err) {
        //         console.error('Failed to copy: ', err);
        // }
        // }
    }
</script>

