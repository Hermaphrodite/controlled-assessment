#Controlled Assessment

##Task 1


###Currency Converter

####Design 

#####User Requirements:

For this task I needed to split the code into three different parts. These parts were:

1) The system should be able to have exchange rates changed when necessary by the user.

2) The user must input the amount they want to convert, the currency they are converting from and the currency they are converting to. 

3) The output must be put to two decimal places (eg. £1.09)

I also need to make sure that the input is a number, and an error message must be displayed if the input is invalid. 

The program will ask for what abbreviated currency code for the currency you want to convert from.
They will be: GBP, EUR, USD, JPY
GBP being Pounds Sterling(£), EUR is Euros(€), USD is US Dollars($), JPY is Japanese Yen(¥).
After that it then asks what currency you want to convert to.
It will use the same system before, currency codes.
It will then multiply the input by the currency rate.
It then prints out the result.
The answer is the value of the two numbers you just multiplied.

This is what I believe is necessary for the code to work successfully.




####Psuedocode

```
BEGIN
INPUT currency to be converted, currency converting to (Pound Sterling/Euro/US Dollar/Japanese Yen)
ASSIGN to variables: c_type1, c_type2
INPUT numb1 as c_type1[key]
MATCH c_type1, c_type2 to key in dictionary
IF c_type1 != Pound Sterling and c_type2 != Pound Sterling:
    CONVERT c_type1 into Pound Sterling
    CONVERT Pound Sterling into c_type2
    RETURN int of c_type2
ELSE:
    IDENTIFY Pound Sterling as c_type1 or c_type2
    CHANGE this value to or from Pound Sterling
    RETURN int of c_type2

```

####Attempt 1 (FAILED)

This was the first code for the conversion:
```python
allowables = ["pounds", "dollars", "euro", "yen"]
rates = [1,2,3,4]
pounds = 'pounds'
dollars = 'dollars'
yen = 'yen'
euro = 'euro'
print("Welcome to the currency converter")

var1 = None
while var1 not in range(len(allowables)):
    print('Please type the currency code you wish to convert from')
    for index, currency in enumerate(allowables):
        print ('enter {0} for {1}'.format(index, currency))
    var1 = input("Please type what currency you wish to convert from ")
var1 = int(var1)

var2 = None
while var2 not in range(len(allowables)):
    print('Please type the currency code you wish to convert to')
    for index, currency in enumerate(allowables):
        print ('enter {0} for {1}'.format(index, currency))
    var2 = input("Please type the currency that you wish to convert to ")
var2 = int(var2)

var3 = float(input("Please type the amount of currency you wish to convert "))

ammount = var3/rates[var1] *rates[var2]
print(' your converted ammount is {0} {1}'.format(ammount,allowables[var2]))

#[GBP]


# if var1 == pounds and var2 == dollars:
#     sumusd1 = var3 * 1.64
#     print("You will recieve, ", sumusd)
# elif something != somethingelse: 
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == pounds and var2 == euro:
#     sumeuro = var3 * 1.22
#     print("You will recieve, ", sumeuro)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == pounds and var2 == yen:
#     sumyen = var3 * 171.53
#     print("You will recieve, ", sumyen)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# #[USD]
# if var1 == dollars and var2 == pounds:
#     sumpounds = var3 * 0.61
#     print("You will recieve, ", sumpounds)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == dollars and var2 == euro:
#     sumeuro = var3 * 0.74
#     print("You will recieve, ", sumeuro)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == dollars and var2 == yen:
#     sumyen = var3 * 104.16
#     print("You will recieve, ", sumyen)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# #[EURO]
# if var1 == euro and var2 == dollars:
#     sumusd2 = var3 * 1.64
#     print("You will recieve, ", sumusd)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == euro and var2 == pounds:
#     sumpounds = var3 * 0.82
#     print("You will recieve, ", sumpounds)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == euro and var2 == yen:
#     sumyen = var3 * 141.24
#     print("You will recieve, ", sumyen)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# #[YEN]
#     if var1 == yen and var2 == dollars:
#         sumusd3 = var3 * 0.0096
#     print("You will recieve, ", sumusd3)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == yen and var2 == euro:
#     sumeuro = var3 * 0.0071
#     print("You will recieve, ", sumeuro)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)
# if var1 == yen and var2 == pounds:
#     sumpounds = var3 * 0.0058
#     print("You will recieve, ", sumpounds)
# elif something != somethingelse:
#     print("Sorry, an error has occurred, please input a currency")
#     print(var1)

```

This code worked but only with GBP used as the currency being converted from, I have commented my first attempt at the code however I realised I could make it much shorter by not using different equations for the conversions between each currency and instead, using one master equation, into which the currencies may be substituted.

####Attempt 2 (PASSED)

```python
currencies= {
    "Pound Sterling": 1, 
    "Euro": 1.2, 
    "US Dollar": 1.6, 
    "Japanese Yen": 200
    }

short_hand = {
    "GBP": "Pound Sterling",
    "EUR": "Euro",
    "USD": "US Dollar",
    "JPY": "Japanese Yen"
    }
    
c_type1 = raw_input("What Currency are you converting from? GBP/EUR/USD/JPY: ")

if c_type1 == "GBP" or "EUR" or "USD" or "JPY":
    "You entered %s" %(c_type1)
else:
    print c_type1, "is not a valid input"
    c_type1 = raw_input("Please enter a valid currency to convert from- GBP/EUR/USD/JPY: ")
    
c_type2 = raw_input("What Currency are you converting to? GBP/EUR/USD/JPY: ")

if c_type2 != "GBP" or "EUR" or "USD" or "JPY":
    "You entered %s" %(c_type1)
else:
    print c_type2, "is not a valid input"
    c_type2 = raw_input("Please enter a valid currency to convert to- GBP/EUR/USD/JPY: ")

def rate(c_type1, c_type2):
    if c_type1 == "GBP":
        print "exchange rate is", currencies["Pound Sterling"]
    if c_type1 == "EUR":
        print "exchange rate is", currencies["Euro"]
    if c_type1 == "USD":
        print "exchange rate is", currencies["US Dollar"]
    if c_type1 == "JPY":
        print "exchange rate is", currencies["Japanese Yen"]
    if c_type2 == "GBP":
        print "to", currencies["Pound Sterling"]
    if c_type2 == "EUR":
        print "to", currencies["Euro"]
    if c_type2 == "USD":
        print "to", currencies["US Dollar"]
    if c_type2 == "JPY":
        print "to", currencies["Japanese Yen"]

rate(c_type1, c_type2)

numb1 = float(raw_input("How much %s do you wish to convert? " %c_type1))

def conversion(fromCurr, toCurr, value):
    if fromCurr == "GBP":
        answer = value * float(currencies[short_hand[toCurr]])
        return answer
    elif toCurr == "GBP":
        answer = value / float(currencies[short_hand[fromCurr]])
    else:
        answer = value / float(currencies[short_hand[fromCurr]])
        answer = value * float(currencies[short_hand[toCurr]]) 
        return answer

print "%2.f %s is %2.f %s" %(numb1, short_hand[c_type1], conversion(c_type1, c_type2, numb1), short_hand[c_type2])

```
For this code I set the currenices and their rates, using Pounds Sterling as the base value meaning it held the value of 1. I then set the shorthand or currency codes, for example: Pounds Sterling is GBP, US Dollars are USD and so on. I then had the program ask the user for the currency code for the currencies they are converting from and to, followed by the amount they wish to convert. It then displays the conversion rate and the amount of their chosen currency that they will recieve. 

##Success Critera

My program meets all the requirements, apart from the fact it gives responses to only 1 decimal place.

Task 1 PASSED


####Programming Techniques
List - I used this whilst setting the rates in my first attempt at the code.

Variable - I used 'c_type' then a value, which stood for currency type, this was the currencies being converted from and to.



##Task 2


###Address book

1. lastname
2. firstname
3. phone        
4. email
5. address
6. postcode

####Design

At the start of the program, the user will be displayed an option whether to create a new entry into the address book or to search the address book for an already present entry. If 'Option 1' is selected then the user will be asked to enter the necessary information. If instead, 'Option 2' is selected then the user will be aksed to input the piece of information they want to search, such as entering the name or phone number that is being searched for within the database. Once the bit of information wanted has been searched then the program runs through the different categories until a match is found. It will display an error message for each category that does not have a match within it. 


###Pseudocode
```
BEGIN
CHOOSE either create an entry or search an entry
IF creating:
    INPUT details:
                  -lastname
                  -firstname
                  -phone
                  -email
                  -address
                  -postcode
STORE details in addressbookdata
Print ('Data Entry Successful')

ELSE IF searching:
    INPUT information being searched
    FOR each category containing necessary data 
Print whole data entry

ELSE Print ('No Results Found')
END
```

###Attempt 1 (PASSED)
```Python 
answer = raw_input("Are You Creating An Entry [Press 1] \nOr Are You Searching An Entry [Press 2] ")

# IF we are creating 

if answer == "1" : 
    #print ("This is where we create")
    # collect information

    lastname = input("What is the persons last name? ")
    firstname = input("What is the persons first name? ")
    phone = input("What id the persons phone number? ")
    email = input("What is the persons email address? ")
    address = input("What is the persons address? ")
    postcode = input("What is the persons postcode? ")
    #create or append addressbookdata

    temp1 = open("addressbookdata","a")
    
    #create string to print to file
    #print temp1
    #print (firstname + " " + lastname + ", " + phone + ", " + email + ", " + address) 

    temp1.write(firstname + " " + lastname + ", " + phone + ", " + email + ", " + address)
    temp1.write("\n")

# SEARCHING FOR A RECORD

elif answer == "2" :
    print ("this is where we search")
    searchcriteria = raw_input("Enter your search Criteria, name? phone number etc ")
    print searchcriteria
    temp1 = open("addressbookdata","r")
    for line in temp1:
        if searchcriteria in line:
            print line
        else: 
            print ("No Results Found") 


# USER DID NOT PICK CREATE OR SEARCH 

else :
    print ("Incorrect Answer")
    exit()
```


#####addressbookdata contains:
```
Jackson, Samantha, 2 Heather Row, Basingstoke, RG21 3SD, 01256 135434, 23/04/1973, sam.jackson@hotmail.com
Vickers, Jonathan, 18 Saville Gardens, Reading, RG3 5FH, 01196 678254, 04/02/1965, the_man@btinternet.com
Morris, Sally, The Old Lodge, Hook, RG23 5RD, 01256 728443, 19/02/1975, smorris@fgh.co.uk
Cobbly, Harry, 345 The High Street, Guildford, GU2 4KJ,	01458 288763, 30/03/1960, harry.cobbly@somewhere.org.uk
Khan, Jasmine, 36 Hever Avenue, Edenbridge, TN34 4FG, 01569 276524, 28/02/1980, jas.khan@hotmail.com
Vickers, Harriet, 45 Sage Gardens, Brighton, BN3 2FG, 01675 662554,	04/04/1968,	harriet.vickers@btinternet.com
```
I got this program to work as I wanted it on my first attempt; I struggled with getting the data into the database however, and had to input the data into addressbookdata manually by copy and pasting from the document containing the necessary data. I added the option to manually add a new entry into the address book, although it was not compulsary.

My program meets all the requirements and is easily accessible.

Task 2 PASSED


##Task 3


###ISBN

####Design

#####User Requirements

1) The inputted number should be exactly 10 digits long.

2) It can only contain letters, no other characters.

3) It should take the input which is 10 digits and work out the 11th digit, adding it on to the end, creating an 11-digit number.

This is by far the easiest of the three tasks. All I had to do was create an system with which the necessary equation could work, then add the answer from this equation onto the input.



###Pseudocode

```
BEGIN
INPUT 10-digit number[list]
IF INPUT==10 numbers 
STORE INPUT as BASE
INPUT=LIST:
           Index=0*11
           Index=1*10
           Index=2*9
           Index=3*8
           Index=4*7
           Index=5*6
           Index=6*5
           Index=7*4
           Index=8*3
           Index=9*2
SUMOF LIST = DIGIT11
DIGIT11/11 = DIGIT11+Remainder
DIGIT11-Remainder = DIGIT11
ISBN == [BASE, DIGIT11]

```

###Attempt 1 (FAILED)

```python 
decision = str(input(""" What would you like to do?; 
1) Convert a 10 digit number to an ISBN number 
2) Quit and end the programme""")) 

if decision == "2": 
    quit()

elif decision == "1": 
    ISBN=input("Enter a 10 digit number:") 

while len(ISBN)!= 10: 

    print('YOU DID NOT ENTER A 10 DIGIT NUMBER !!!') 
    ISBN=int(input('Please enter a 10 digit number: ')) 
    continue

else: 

    Di1=int(ISBN[0])*11
    Di2=int(ISBN[1])*10
    Di3=int(ISBN[2])*9
    Di4=int(ISBN[3])*8
    Di5=int(ISBN[4])*7
    Di6=int(ISBN[5])*6
    Di7=int(ISBN[6])*5
    Di8=int(ISBN[7])*4
    Di9=int(ISBN[8])*3
    Di10=int(ISBN[9])*2

sum=(Di1+Di2+Di3+Di4+Di5+Di6+Di7+Di8+Di9+Di10) 

num=sum%11
Di11=11-num 
if Di11==10: 
    Di11='X'
ISBNNumber=str(ISBN)+str(Di11) 
print('The ISBN number is -->    ' + ISBNNumber)

```

This code was a failure due to the fact that I tried to implement a quit feature, this being unnecessary I removed it and made an altered code.


###Attempt 2 (PASSED)

```python
ISBN=''

while len(str(ISBN))!=10:

    print('Please make sure you have entered a number which is exactly 10 characters long.')
    ISBN=raw_input('Please enter the 10 digit number: ')
    

Digit1=int(ISBN[0])*11
Digit2=int(ISBN[1])*10
Digit3=int(ISBN[2])*9
Digit4=int(ISBN[3])*8
Digit5=int(ISBN[4])*7
Digit6=int(ISBN[5])*6
Digit7=int(ISBN[6])*5
Digit8=int(ISBN[7])*4
Digit9=int(ISBN[8])*3
Digit10=int(ISBN[9])*2
Result=(Digit1+Digit2+Digit3+Digit4+Digit5+Digit6+Digit7+Digit8+Digit9+Digit10)
Remainder=Result%11
Digit11=11-Remainder
if Digit11==10:
   Digit11='X'
ISBNNumber=str(ISBN)+str(Digit11)
print('Your 11 digit ISBN Number is ' + ISBNNumber)

```

This code works efficiently and creates the ISBN accurately. Without the addition of the 'quit' feature this program was reasonably simple to create. 

My program meets all the requirements and is easily accessible.

Task 3 PASSED




