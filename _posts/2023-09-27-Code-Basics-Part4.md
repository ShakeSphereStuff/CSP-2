alphabet = "abcdefghijklmnopqrstuvwxyz"

alphabetList = []

for i in alphabet:
    alphabetList.append(i)

print(alphabetList)

letter = input("What letter would you like to check?")

i = 0

while i < 26:
    if alphabetList[i] == letter:
        print("The letter " + letter + " is the " + str(i + 1) + " letter in the alphabet")
    i += 1

menu =  {"burger": 3.99,
         "fries": 1.99,
         "drink": 0.99}
total = 0

#shows the user the menu and prompts them to select an item
print("Menu")
for k,v in menu.items():
    print(k + "  $" + str(v)) #why does v have "str" in front of it?

#ideally the code should prompt the user multiple times
item = input("Please select an item from the menu")

for k,v in menu.items():
    if(str(k) == str(item)):
        total = v
if total == 0:
    print("Invalid Item")
print("Your total is " + str(total))
#code should add the price of the menu items selected by the user 