---
toc: true
comments: true
layout: post
type: hacks
title: Safe Computing HW
description: My response for the HW in the team teach
courses: { csse: {week: 1}, csp: {week: 9, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---


1. Describe PII you have seen on a project in CompSci Principles.

First Name and Last name on Utterences for projects

2. Describe good and bad passwords? What is another step that is used to assist in authentication?
Bad Password: MePassword123

Good Password: $1WO%W*r@?

Another step that could be used for verifying the user is 2 factor Authentication 

3. Try to describe Symmetric and Asymmetric encryption.

Symetric encription, where 1 Key controls both the encryption and the decryption of data
Asymmetric encryption, where 1 keys controls the encryption and one controls the decryption

4. Provide an example of encryption we used in AWS deployment.

I do not have access to AWS because I put in the wrong info to get access to it.

5. Create a python script that lets the user input a password that is checked by the program

Python Script:

<pre>
import time, math
def commonPassword(password):
    passwords = ["guest",
"123456",
"password",
"12345",
"a1b2c3",
"123456789",
"Password1",
"1234",
"abc123",
"12345678",
"qwerty",
"baseball",
"football",
"unknown",
"soccer",
"jordan23",
"iloveyou",
"monkey",
"shadow",
"g_czechout",
"1234567",
"1q2w3e4r",
"111111",
"f**kyou",
"princess",
"basketball",
"sunshine",
"jordan",
"michael",
"1234567890",
"reset",
"zinch",
"maiden",
"123123",
"81729373759",
"superman",
"hunter",
"anthony",
"maggie",
"super123",
"purple",
"love",
"ashley",
"andrew",
"justin",
"killer",
"pepper",
"tigger",
"buster",
"nicole",
"taylor",
"123",
"matthew",
"babygirl",
"michelle",
"cookie",
"jessica",
"datpiff",
"charlie",
"jasmine",
"peanut",
"abcd1234",
"cheese",
"brandon",
"hannah",
"pokemon",
"family",
"ginger",
"1qaz2wsx",
"hello",
"computer",
"joshua",
"money",
"letmein",
"yankees",
"bailey",
"hockey",
"batman",
"diamond",
"madison",
"michael1",
"amanda",
"thomas",
"passw0rd",
"harley",
"jennifer",
"music",
"daniel",
"samantha",
"mustang",
"freedom",
"robert",
"whatever",
"summer",
"asdfghjkl",
"football1",
"brooklyn",
"654321",
"william",
"trustno1"]
    for x in passwords:
        if(x == password):
            print("Common password")

userspassword = "password"

def checkPassword(attempts):
    global userspassword
    password = input("Enter your Password: ")
    commonPassword(str(password))
    if(password == "password"):
        print("Valid password")
    elif(attempts < 3):
        print("Password is incorrect")
        checkPassword(attempts + 1)
    else:
        print(f"User ran out of attempts, now waiting {(attempts - 2)**2 *5} seconds")
        time.sleep((attempts - 2)**2 *5)
        checkPassword(attempts + 1)
        

checkPassword(0)
</pre>


BONUS: Use online wordlists to compare the password, preventing dictionary attacks
