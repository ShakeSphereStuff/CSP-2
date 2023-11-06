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

First Team teach, Developing algorithms: <button onclick = "javascript:getPythonCode(0)">Copy code</button> 
<pre id = "codeCellOpen0" style = "display: none">
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
</pre>

Second Team Teach, Data Abstraction: <button onclick = "javascript:getPythonCode(1)">Copy code</button>

<pre id = "codeCellOpen1" style = "display: none">
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
</pre>



Third Team Teach, Algorithms, the earlier one: <button onclick = "javascript:getPythonCode(2)">Copy code</button>

<pre id = "codeCellOpen2" style = "display: none">
import math
text = input("What text do you think in a palindrome: ")
score = 0
for x in range(0, math.floor(len(text) / 2)):
    if text[x].upper() == text[-(x + 1)].upper():
        score += 1
    if score == math.floor(len(text) / 2):
        print("It's a palindrome")
    else:
        print("It's not a palindrome")

Pratical Algorithm:
import math, time
screen = [
["@", "%", " ", " ", " "],
["#", "#", "#", "#", " "],
[" ", "@", "%", " ", " "],
["#", "#", "#", "#", " "],
[" ", " ", "@", "%", " "],
["#", "#", "#", "#", " "],
[" ", " ", " ", "@", "%"],
["#", "#", "#", "#", " "],
[" ", " ", " ", "@", " "],
["#", "#", "#", "#", "%"],
[" ", " ", " ", "@", " "],
["#", "#", "#", "#", " "],
[" ", " ", " ", "@", " "],
["#", "#", "#", "#", " "],
[" ", " ", "@", " ", " "],
["#", "#", "#", "#", " "],
[" ", "@", " ", " ", " "],
["#", "#", "#", "#", " "],
["@", " ", " ", " ", " "],
["#", "#", "#", "#", " "],
[" ", " ", " ", " ", " "],
["#", "#", "#", "#", " "],
]
print(len(screen) // 2)
displayA = ""
displayB = ""
display = ""
for y in range(0, len(screen), 2):
    displayA = ""
    displayB = ""
    display = ""
    for x in range(0, len(screen[0]), 1):
        # print(y, x)
        displayA += screen[y][x]
        displayB += screen[y + 1][x]
        display = displayA + " "*300 + displayB
        print(display, end = "\r")
        time.sleep(0.8)
</pre>
Forth and Fifth, random Animal: <button onclick = "javascript:getPythonCode(3)">Copy code</button>

<pre id = "codeCellOpen3" style = "display: none">

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
</pre>

Fifth One, Lists and search: <button onclick = "javascript:getPythonCode(4)">Copy code</button>

<pre id = "codeCellOpen4" style = "display: none">
import random, math 
nums = [0, 2, 4, 7, 15, 21, 34, 36, 43, 48, 51, 60, 70, 71, 76, 77, 82, 94, 95, 99] 
 
start = 0 
end = len(nums) - 1 
worstNums = 0 
choosenNum = -1 
for d in range(0, len(nums) - 1): 
    choosenNum += 1 
    currentPos = (len(nums) - 1) // 2 
    start = 0 
    end = len(nums) - 1 
 
    for c in range(2, 10): 
        currentPos = (start + end) // 2  
        if(nums[currentPos] > nums[choosenNum]): 
            end = currentPos - 1 
            # currentPos += math.floor((len(nums) - currentPos) / 2 - 0.5) 
            #  
        elif(nums[currentPos] < nums[choosenNum]): 
            start = currentPos + 1 
            # currentPos -= math.floor((len(nums) - currentPos) / 2 - 0.5) 
        elif(nums[currentPos] == nums[choosenNum]): 
            print("Len is " + str(c - 2) + " at " + str(currentPos)) 
            if(worstNums < (c - 2)): 
                worstNums = c - 2 
            break 
print("-"*20 + "\n" + "WorstNums is " + str(worstNums)) 
</pre> 

Sixth one, procedures: <button onclick = "javascript:getPythonCode(5)">Copy code</button>

<pre id = "codeCellOpen5" style = "display: none;"> 
# First one 
 
def exponenchal(exponent, simTime): 
    count = "" 
    for x in range(0, simTime + 1): 
        count += f"Term {x}; {exponent ** x}:\n\t" 
        for y in range(1, (exponent ** x) + 1): 
            count += str(y%10) 
            if y%10 == 0: 
                count += f" {y}\'s " 
        count += "\n" 
    return count 
nums = exponenchal(2, 14) 
print(nums) 
 
# Second One 
 
import random 
nums = [] 
randomNums = [] 
for a in range(0, 100): 
    randomNums.append(a) 
for x in range(0, 20): 
    randNum = random.randint(0, (len(randomNums) - 1)) 
    nums.append(randomNums[randNum]) 
    randomNums.remove(randomNums[randNum]) 
print(sorted(nums)) 
 
</pre>

Seventh one, Boolean Operations and Conditions: <button onclick = "javascript:getPythonCode(6)">Copy code</button>

<pre id = "codeCellOpen6" style = "display: none">
# Silly thing I made that made me Mad! 
print("Welcome to MegaCorp, please state your details") 
userFirstName = input("First Name: ") 
print("Input 'Null' if you don't have a prefered Name ") 
userPreferedName = input("Prefered Name: ") 
userLastName = input("Last Name: ") 
userAge = input("Age: ") 
 
# What I used to bypass login, comment everything above and uncomment the comments below except for this line 
# userAge = 20 
# userFirstName = "Fred" 
# userPreferedName = "Freddy" 
# userLastName = "Kilm" 
# userPay = 0 
 
def findPercent(userInput): 
    currentUserGrade = "" 
    currentUserClass = "" 
    classes = ["A", "B", "C", "D", "E", "F", "G"] 
    for x in userInput: 
        print(x) 
        if(x.isdigit()): 
            currentUserGrade += x 
            continue 
        for y in classes: 
            if x.upper() == y: 
                currentUserClass = y 
                continue 
    currentUserGrade = int(currentUserGrade) 
    return currentUserClass, currentUserGrade 
 
def MegaCorpFinance(): 
    global userPreferedName, userPay 
    yearsOfEmployee = input(f"How many years have you served at the company {userPreferedName}? ") 
    jobPay = { # Per year 
        "Coder": 150000, 
        "Janitor": 30000 
    } 
    for jobTitle in jobPay: 
        print("\t*" + str(jobTitle)) 
 
    employeeTitle = input("Out of these, which is your job? ") 
 
    for jobTitle in jobPay: 
        if(employeeTitle.upper() == jobTitle.upper()): 
            print("Valid Title") 
            employeeTitle = jobTitle 
 
    if(userPay == 0): 
        userPay = jobPay[str(employeeTitle)] 
 
 
    if(int(yearsOfEmployee) > 5): 
        userPay *= 1.05  
    print(userPay) 
 
if(userPreferedName.upper() == "NULL"): 
    userPreferedName = userFirstName 
else:  
    userPreferedName = userPreferedName 
 
if(int(userAge) > 18): 
    print("Redirecting you to MegaCorpMain") 
    MegaCorpFinance() 
elif(int(userAge) < 18): 
    print(f"{userPreferedName}, we are redirecting you to MegaCollegeCorp") 
    print("\tType: A + grade for your last History") 
    print("\tType: B + grade for your last English") 
    print("\tType: C + grade for your last Math") 
    print("\tType: D + grade for your last Science") 
    print("\tType: E + grade for your last Forign Language") 
    print("\tType: F + grade for your last Fine Arts") 
    print("\tType: G + grade for your last Electives") 
    print("\tType Submit to submit your grades to us") 
    userGrade = { 
            "A": "F", # History 
            "B": "F", # English 
            "C": "F", # Math 
            "D": "F", # Science 
            "E": "F", # Forign Language 
            "F": "F", # Fine Arts 
            "G": "F" # Electives 
    } 
    while 7 == 7: 
        userInput = input("Input percents from your classes in base 10: ") 
        userInput = userInput.replace(" ", "") 
        print("User input is: " + str(userInput)) 
        classes = ["A", "B", "C", "D", "E", "F", "G"] 
        grades = ["A", "B", "C", "D", "E", "F"] 
        if(userInput.upper() == "SUBMIT"): 
            jobRequirements = { 
                "Coder": { 
                    "A": "C", 
                    "B": "B", 
                    "C": "A", 
                    "D": "A", 
                    "E": "C", 
                    "F": "C", 
                    "G": "C" 
                }, 
                "Jainitor": { 
                    "A": "D", 
                    "B": "D", 
                    "C": "D", 
                    "D": "D", 
                    "E": "D", 
                    "F": "D", 
                    "G": "D" 
                } 
            } 
            for currentJob in jobRequirements: 
                amountOfRequirements = 0  
                print(f"Scanning Requirement for {currentJob}") 
                for currentClassCheck in classes: 
                    if(grades.index(jobRequiremets[currentJob][currentClassCheck]) >= grades.index(userGrade[currentClassCheck])): 
                        amountOfRequirements += 1 
                if(amountOfRequirements > 4): 
                    print(f"You got the application for {currentJob}!") 
                    break 
 
            break 
        percent = findPercent(userInput) 
        currentUserGrade = int(percent[1]) 
        currentUserClass = percent[0] 
        if(currentUserGrade > 80): 
            currentUserGrade = "A" 
        elif(currentUserGrade >= 60): 
            currentUserGrade = "B" 
        elif(currentUserGrade >= 50): 
            currentUserGrade = "C" 
        elif(currentUserGrade >= 45): 
            currentUserGrade = "D" 
        elif(currentUserGrade >= 25): 
            currentUserGrade = "E" 
        else: 
            currentUserGrade = "F" 
        userGrade[str(currentUserClass)] = currentUserGrade 
        print(f"Class type {currentUserClass} is now set to grade {currentUserGrade}") 
</pre>
Seventh one, libaries: <button onclick = "javascript:getPythonCode(7)">Copy code</button>

<pre id = "codeCellOpen7" style = "display: none;">
Here’s the HW for Libraries 
 
from imdb import Cinemagoer 
import random 
 
ia = Cinemagoer() 
 
name = "Tarzan" 
 
randMovieID = "0120855" 
 
def callMovies(): 
    try: 
        movies = ia.get_movie(str(randMovieID)) 
        print(movies) 
        print(movies.current_info) 
        for x in movies.current_info: 
            print(x) 
            print(type(x)) 
            print(movies["plot"]) 
            print(movies[x]) 
    except: 
        print("Error, can't find Movie") 
         
def parseMovie(dataSet): 
    dataSet = str(dataSet) 
    dataSet = dataSet[1: -2] 
    dataSet = dataSet.replace("<", "").replace(">", "", -1).replace("_", "",  -1).replace("[http]", "") 
    dataSet = dataSet.split("Movie id:") 
    dataSet = dataSet[1:-1] 
    return dataSet 
     
print("Type 'result' to get the plot")  
 
terms = [] 
userTerms = [] 
     
while 7 == 7: 
    userInput = input("What movies do you want to get the plot of?: ") 
    userTerms += [userInput] 
    if(userInput == "result"): 
        plotSums = [] 
        for x in range(0, len(terms)): 
            finalText = "" 
            plotSums += [[]] 
            try: 
                plotSums[x] += [str(ia.get_movie(terms[x])["plot"])] 
            except: 
                print("Can't get summery") 
                continue 
        # print(plotSums[0]) 
            banList = ["\n", "\'", "\\", "[", "]", "\""] 
            for y in plotSums[x][0]: 
                currentText = y 
                for z in banList: 
                    currentText = str(currentText).replace(z, "") 
                if(currentText != ""): 
                    finalText += str(currentText) 
            print(f"\n \nFinal Text for {userTerms[x]}: \n" + "-"*20 + "\n" + str(finalText)) 
     

    results = ia.search_movie(userInput) 
    results = str(parseMovie(results)[0]) 
    terms.append(results[0:7]) 
    print("\nFinal Result: " + str(results[0:7])) 
  2.) Imdb api, allows for you to get an id from a movie title and get other terms, directors, genres, plot and more. 
 
1.) Pygame API, allows for videogames to be played, favorite variables being get num_displays and pygame.font.quit 
 
Imdb api, used to search for movies, favorite variables being tv kind ([‘kind’]) and filmography ([‘filmography’]) 
 
Turtle API, used to make graphics, favorite variables being speed() and bye() 
</pre> 

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

