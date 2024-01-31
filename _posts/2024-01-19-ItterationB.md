---
toc: true
comments: true
layout: post
type: hacks
title: Itteration B Review
description: What I have learned for itteration B review.
courses: { csse: {week: 1}, csp: {week: 9, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---

<style>
  td{
    border: solid black;
    padding: 0px;
    padding-left: 5px;
    padding-right: 0px;
  }
  p{
    padding: 0px;
  }
  .selected{
    padding-left: 5px;
    border: solid green;
    border-radius: 5px;
    margin: 0px;
    padding-top: 0px;
    margin-bottom: 5px
  }
  .selectedHead{
    border-bottom: solid green;
    margin-bottom: 4px;
    position: relative;
    padding-left: 5px;
    left: -5px;
    width: calc(100% + 3px)
  }
  .answered{
    padding-left: 5px;
    border: solid red;
    border-radius: 5px;
    margin: 0px;
    padding-top: 0px
    margin-bottom: 5px
  }
  .answeredHead{
    border-bottom: solid red;
    margin-bottom: 4px;
    position: relative;
    padding-left: 5px;
    left: -5px;
    width: calc(100% + 3px)
  }
</style>

Questions for the MCQ

Key assets and projects: https://github.com/saiseahawks/FrontEndBinaryTri2
New Repository for CPT Project: https://github.com/ShakeSphereStuff/GUIFor2DGameEngines

6.) Robot a grid to move
<br>
<table>
  <tr>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>Goal</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
  <tr>
    <td>Robot Facing Right</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
</table>

<table>
  <tr>
    <td>Program 1:</td>
    <td>Program 2:</td>
  </tr>
  <tr>
     <td>
      for(var repeat = 0; repeat < 2; repeat++){<br>
        Move_Forward()<br>
        Rotate_Left()<br>
        Move_Forward()<br>
        Move_Forward()<br>
        Rotate_Left()
      }
    </td>
    <td>
      while(GoalReached){<br>
        if (forward){<br>
          Move_Forward()<br>
        } else{<br>
          Rotate_Left()<br>
        }<br>
      }
    </td>
    </tr>
  </table>

<div class = "selected">
Program II correctly moves the robot to the gray square, but program I does not.
</div>
<div class = "answered">
Both program I and program II correctly move the robot to the gray square.
</div>
7.)  Flight simulation software, which imitates the experience of flying, is often used to train airline pilots. Which of the following is LEAST likely to be an advantage of using flight simulation software for this purpose?
<div class = "selected">
Flight simulation software allows pilots to practice landing in a variety of different terrains and weather conditions without having to physically travel.
</div>
<div class = "answered">
Answer: Flight simulation software allows pilots to practice landing in a variety of different terrains and weather conditions without having to physically travel.
</div>

15.) Which of the following best compares the values of A and B
<table>
<tr><td>Program 1</td>
<td>Program 2</td></tr>
<tr>
<td>i = 1<br>
while (i <= 10){<br>
console.log(i)<br>
i += 1<br>
}
</td>
<td>
i = 0<br>
while (i < 10){<br>
i = 1<br>
console.log(i)<br>
}
</td>
</tr>
</table>
<div class = "selected">
Selected: Program B displays one more value than program A.
</div>
<div class = "answered">
Answer: Program A and program B display identical values in the same order.
</div>

18.) 
<table>
<tr>
<td>Robot Facing Right</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>Block</td>
<td>Block</td>
<td>Block</td>
<td>Block</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>Goal</td>
<td>Block</td>
<td>&nbsp;</td>
<td>Block</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>Block</td>
<td>&nbsp;</td>
<td>Block</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
</table>

Fill in the code<br/>

<code>
while(!GoalReached){<br/>
// Missing Code<br/>
}<br/>
</code>
<div class = "selected">
while(Can_Move (forward) == false){<br>
    Rotate_Right()<br>
}<br>
Move_Forward()
</div>

<div class = "answered">
while(Can_Move (forward) == false){<br>
    Move_Forward()<br>
}<br>
Rotate_Right()
</div>

20.) Graph below is for the users of an application

<table>
<tr>
<td>Years</td>
<td>0</td>
<td>1</td>
<td>2</td>
<td>3</td>
<td>4</td>
<td>5</td>
<td>6</td>
<td>7</td>
</tr>
<tr>
<td>Number of users</td>
<td>262</td>
<td>505</td>
<td>1014</td>
<td>2028</td>
<td>3885</td>
<td>5110</td>
<td>5890</td>
<td>6986</td>
</tr>
<tr>
<td>Number of GB</td>
<td>26</td>
<td>53</td>
<td>105</td>
<td>202</td>
<td>403</td>
<td>504</td>
<td>601</td>
<td>701</td>
</tr>
</table>

<div class = "selected">
Selected: Across all eight years, the average amount of data stored per user was about 100 GB.
</div>
<div class = "answered">
Answer: Across all eight years, the average amount of data stored per user was about 10 GB.
</div>

29.) A person wants to transmit an audio file from a device to a second device. Which of the following scenarios best demonstrates the use of lossless compression of the original file?

<div class = "selected">
A device compresses the audio file by removing details that are not easily perceived by the human ear. The compressed file is transmitted to a second device, which plays it.
</div>

<div class = "answered">
Answer: 
A device compresses the audio file before transmitting it to a second device. The second device restores the compressed file to its original version before playing it.
</div>

32.) Calculate the Average( All Grades / # of classes) minus the lowest class

<div class = "selected">
var finalGrade = Sum (scores) - Min (scores)
finalGrade = finalGrade / LENGTH (scores)
</div>

Forgot to minus the length for the removed item

<div class = "answered">
var finalGrade = Sum (scores) - Min (scores)
finalGrade = finalGrade / (LENGTH (scores) - 1)
</div>

39.) 

Assume that the list of numbers nums has more than 10 elements. The program below is intended to compute and display the sum of the first 10 elements of nums.

<code>
i = 1<br>
sum = 0<br>
while(i <= 10){<br>
    i = i + 1 <br>
    sum += nums[i]<br>
}<br>
console.log(sum)<br>
</code>


Which change, if any, is needed for the program to work as intended?

<div class = "selected">
Line 3 should be changed to REPEAT UNTIL (i >= 10).
</div>
<div class = "answered">
Answer: 
Lines 5 and 6 should be interchanged.
</div>

40.) Which of the following best explains how a certificate authority is used in protecting data?
<div class = "selected">
A certificate authority certifies the safety of a particular Web site so that users know that it does not contain any viruses.
</div>
<div class = "answered">
A certificate authority verifies the authenticity of encryption keys used in secured communications.
</div>
44.) 



In configuration I, what is the minimum number of connections that must be broken or removed before device T can no longer communicate with device U?

<div class = "selected">
Selected: 4 
</div>
<div class = "answered">
Answer: 2
</div>

47.) The procedure BinarySearch (numList, target) correctly implements a binary search algorithm on the list of numbers numList. The procedure returns an index where target occurs in numList, or -1 if target does not occur in numList. Which of the following conditions must be met in order for the procedure to work as intended?

Selected: The list numList must not contain any duplicate values.

Answer: The values in numList must be in sorted order.

50.) Consider the following algorithms. Each algorithm operates on a list containing n elements, where n is a very large integer.

I. An algorithm that accesses each element in the list twice
II. An algorithm that accesses each element in the list n times
III. An algorithm that accesses only the first 10 elements in the list, regardless of the size of the list
Which of the algorithms run in reasonable time?

<div class = "selected">
Selected: I only
</div>
<div class = "answered">
Answer : I, II, III
</div>

51.) Which of the following best describes the impact of Creative Commons?

Selected: Creative Commons gives Internet users the right to legally use and distribute any previously copyrighted work, enabling broad access to digital information.

Answer: Creative Commons gives creators of digital content the ability to indicate how their works can be legally used and distributed, enabling broad access to digital information.
55.) The following algorithm is intended to determine the average height, in centimeters, of a group of people in a room. Each person has a card, a pencil, and an eraser. Step 2 of the algorithm is missing.

Step 1: All people stand up.

Step 2: (missing step)

Step 3: Each standing person finds another standing person and they form a pair. If a person cannot find an unpaired standing person, that person remains standing and waits until the next opportunity to form pairs.

Step 4: In each pair, one person hands their card to the other person and sits down.

Step 5: At this point, the standing person in each pair is holding two cards. The standing person in each pair replaces the top number on their card with the sum of the top numbers on the two cards and replaces the bottom number on their card with the sum of the bottom numbers on the two cards. The sitting partner’s card is discarded.

Step 6: Repeat steps 3–5 until there is only one person standing.

Step 7: The last person standing divides the top number by the bottom number to determine the average height.

Which of the following can be used as step 2 so that the algorithm works as intended?

<div class = "selected">
Selected: Step 2: Each person writes their height, in centimeters, at the top of the card and writes the number 2 at the bottom of the card.
</div>
<div class = "answered">
Answer: Step 2: Each person writes their height, in centimeters, at the top of the card and writes the number 1 at the bottom of the card.
</div>

56.) An online video game collects stats about each players performance, and another program makes predictions about how players will perform in the new game

GetPrediction(idNum) predicts a score takes 1 minute, rest of code is immediately executed

Version 1:

var topScore = 0

var idList = [1298702, 1356846, 8848491, 8675309]

for(var id IN idList){

var score = GetPrediction (id)
if (score > topScore){
topScore = score
}

}
console.log(topScore)

var idList = [1298702, 1356846, 8848491, 8675309]

var topID = idList[1]

for(id IN idList){<br>
if(GetPrediction (id) > GetPrediction (topID)){<br>
topID = id<br>
}<br>
}<br>

console.log(GetPrediction (topID))
<div class = "selected">
Version II requires approximately 1 more minute to execute than version I.
</div>
<div class = "answered">
Answer: Version II requires approximately 5 more minutes to execute than version I.
</div>

57) The transmission control protocol (TCP) and Internet protocol (IP) are used in Internet communication. Which of the following best describes the purpose of these protocols?

<div class = "selected">
Selected: To ensure that private data is inaccessible to unauthorized devices on the Internet
</div>
<div class = "answered">
Answer: To establish a common standard for sending messages between devices on the Internet
</div>

60) Consider two lists of numbers called list1 and list2. A programmer wants to determine how many different values appear in both lists. For example, if list1 contains [10, 10, 20, 30, 40, 50, 60] and list2 contains [20, 20, 40, 60, 80], then there are three different values that appear in both lists (20, 40, and 60).

Find the intended value to the variable count

Built in programs:
Combine(), merges lists together
RemoveAllDups(), removes duplicates of elements

<div class = "selected">
var bothList = Combine (list1, list2)

var uniqueList = RemoveAllDups (bothList)

var count = LENGTH (bothList) - LENGTH (uniqueList)
</div>

<div class = "answered">
var newList1 = RemoveAllDups (list1)

var newList2 = RemoveAllDups (list2)

var bothList = Combine (newList1, newList2)

var uniqueList = RemoveAllDups (bothList)

var count = LENGTH (bothList) - LENGTH (uniqueList)

</div>

67) The procedure NumOccurrences is intended to count and return the number of times targetWord appears in the list wordList. The procedure does not work as intended.

The figure presents a block of code that consists of 7 lines. Throughout the block of code are nested blocks of code. <br>

function NumOccurences(wordList, targetWord){<br>
var count = 0<br>
for (var word of wordlist) {<br>
count = 0<br>
if(word = targetWord){<br>
count = count + 1<br>
}<br>
	return count<br>
}<br>
}

For which of the following code segments will the call to NumOccurrences NOT return the intended value?

Select two answers.

<div class = "selected">

var treeList = [“birch”, “maple”, “birch”]
numOccurrences(treeList, “birch”)

var treeList = [“birch”, “maple”, “oak”]
numOccurrences(treeList, “spruce”)

</div>

<div class = "answered">

Answer:
var treeList = [“birch”, “maple”, “birch”]
numOccurrences(treeList, “birch”)

var treeList = [“birch”, “maple”, “oak”]
numOccurrences(treeList, “maple”)

</div>

<script>
  var selectedInsts = document.getElementsByClassName("selected")
  console.log(selectedInsts)
  for(var selectedCt = 0; selectedCt < (selectedInsts.length); selectedCt++){
    var selectedHeader = document.createElement("p")

    selectedHeader.className = "selectedHead"
    selectedHeader.innerText = "Selected"
    console.log(selectedInsts[selectedCt])
    selectedInsts[selectedCt].insertBefore(selectedHeader, selectedInsts[selectedCt].firstChild)
  }
  var answeredInsts = document.getElementsByClassName("answered")
  console.log(answeredInsts)
  for(var answeredCt = 0; answeredCt < (answeredInsts.length); answeredCt++){
    var answeredHeader = document.createElement("p")

    answeredHeader.className = "answeredHead"
    answeredHeader.innerText = "Answer is"
    console.log(answeredInsts[answeredCt])
    answeredInsts[answeredCt].insertBefore(answeredHeader, answeredInsts[answeredCt].firstChild)
  }
</script>
 

