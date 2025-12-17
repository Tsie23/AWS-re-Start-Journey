# Python Lab: Working with Numeric Data Types

## Objective
- Use the Python shell
- Use the int data type
- Use the float data type
- Use the complex data type
- Use the bool data type

## Steps Taken
1. Interacting with the Python Shell
To get a feel for the environment, I launched the Python shell from the terminal to perform basic arithmetic.
* Ran the command: `python3` to enter Python shell in terminal
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120428.png>)

* Tested *addition (2 + 2)*, 
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120450.png>)

*subtraction (4 - 2)*,
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120513.png>) 

*multiplication (5 * 3)*, 
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120531.png>)

and *division (4 / 2)*
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120622.png>)

* Noted that division returned a float (2.0) rather than an integer.
![alt text](<images/Python Numericals/Screenshot 2025-12-17 120622.png>)

* Exit: Used quit() to return to the main terminal.
![alt text](<images/Python Numericals/Screenshot 2025-12-17 130048.png>)

2. Writing a Python Script
Instead of one-off commands, I moved into a script to make the code reusable.
* Execution: Created a .py file and added a print statement:
`Python`
* print("Python has three numeric types: int, float, and complex")
Run: Executed the script using the IDE Play button and via the terminal with python3 <filename>.py.
![alt text](<images/Python Numericals/Screenshot 2025-12-17 130229.png>)
![alt text](<images/Python Numericals/Screenshot 2025-12-17 130427.png>)

3. Defining and Identifying Integers (int)
I used a variable as a "labeled box" to store a whole number and inspected its metadata.
* Code: ```python myValue=1 print(myValue) print(type(myValue))
![alt text](<images/Python Numericals/Screenshot 2025-12-17 130827.png>)

* Used str() to combine the numeric data with text for a readable output: print(str(myValue) + " is of the data type " + str(type(myValue)))
![alt text](<images/Python Numericals/Screenshot 2025-12-17 131307.png>)

4. Exploring Floats (float) and Complex Numbers (complex)
I updated the same variable to handle decimals and imaginary numbers.
* Assigned 3.14 to myValue to observe how Python handles decimal precision.
* Assigned 5j to myValue. Python uses j to represent the imaginary unit in advanced math.
* For each type, I repeated the print(), type(), and str() pattern to confirm the class change in the console.
![alt text](<images/Python Numericals/Screenshot 2025-12-17 131511.png>)

5. Implementing Booleans (bool)
Finally, I tested the "fake" numeric type: Booleans, which represent binary logic.
* Assigned True and then False to myValue.
* Confirmed that Python categorizes these as <class 'bool'>, though they effectively function as 1 and 0 under the hood.
![alt text](<images/Python Numericals/Screenshot 2025-12-17 131923.png>)

## Challenges
As the script grew, the console output became quite long. I had to get used to scrolling up to verify that the earlier int and float outputs were still printing correctly alongside the new code. Early on, I forgot to wrap myValue in the str() function when printing. This triggered a TypeError because Python cannot natively "add" a number to a string of text.

## Takeaways
- I learned that Python variables are flexible; I can reuse myValue to store an integer, then a complex number, and finally a boolean without the program crashing. 
- The type() function is an essential debugging tool. It’s the easiest way to see exactly how Python is interpreting the data you've assigned.
- Understanding str() is vital for creating user-friendly output is vital. Converting data types (casting) is a frequent necessity when building interactive scripts.