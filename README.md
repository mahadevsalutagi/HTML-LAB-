# HTML-LAB-
PROGRAMS
5.  Design an html having a text box and four buttons viz. factorial, Fibonacci, prime, and palindrome. when a button is pressed an appropriate JavaScript function should be called to display
a. factorial of that number 
b. Fibonacci series up to that number
c. Prime numbers up to that number
d. is it palindrome or not. 
 
index.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Number Operations</title>
   <script src="scripts.js"></script>
   <style>
       body {
           font-family: Arial, sans-serif;
           margin: 20px;
       }
       .container {
           max-width: 400px;
           margin: 0 auto;
           text-align: center;
       }
       input, button {
           margin: 10px;
           padding: 10px;
           font-size: 16px;
       }
       .result {
           margin-top: 20px;
           font-size: 18px;
           color: #333;
       }
   </style>
</head>
<body>
   <div class="container">
       <h2>Number Operations</h2>
       <input type="text" id="number" placeholder="Enter a number">
       <br>
       <button onclick="calculateFactorial()">Factorial</button>
       <button onclick="generateFibonacci()">Fibonacci</button>
       <button onclick="listPrimes()">Prime</button>
       <button onclick="checkPalindrome()">Palindrome</button>
       <div class="result" id="result"></div>
   </div>
</body>
</html>
 
scripts.js
function calculateFactorial() {
   let number = parseInt(document.getElementById("number").value);
   if (isNaN(number) || number < 0) {
       alert("Please enter a valid non-negative number");
       return;
   }
 
   let factorial = 1;
   for (let i = 1; i <= number; i++) {
       factorial *= i;
   }
 
   document.getElementById("result").innerText = `Factorial of ${number} is ${factorial}`;
}
 
function generateFibonacci() {
   let number = parseInt(document.getElementById("number").value);
   if (isNaN(number) || number < 1) {
       alert("Please enter a valid positive number");
       return;
   }
 
   let fibonacci = [0, 1];
   for (let i = 2; i < number; i++) {
       fibonacci[i] = fibonacci[i - 1] + fibonacci[i - 2];
   }
 
   document.getElementById("result").innerText = `Fibonacci series up to ${number}: ${fibonacci.slice(0, number).join(", ")}`;
}
 
function listPrimes() {
   let number = parseInt(document.getElementById("number").value);
   if (isNaN(number) || number < 2) {
       alert("Please enter a valid number greater than 1");
       return;
   }
 
   let primes = [];
   for (let i = 2; i <= number; i++) {
       let isPrime = true;
       for (let j = 2; j * j <= i; j++) {
           if (i % j === 0) {
               isPrime = false;
               break;
           }
       }
       if (isPrime) {
           primes.push(i);
       }
   }
 
   document.getElementById("result").innerText = `Prime numbers up to ${number}: ${primes.join(", ")}`;
}
 
function checkPalindrome() {
   let number = document.getElementById("number").value;
   if (number === "") {
       alert("Please enter a valid number");
       return;
   }
 
   let reversed = number.split("").reverse().join("");
   let isPalindrome = (number === reversed);
 
   document.getElementById("result").innerText = `${number} is ${isPalindrome ? "" : "not "}a palindrome`;
}
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
6. Write JavaScript programs on Event Handling
b. Open a Window from the current window
c. Change color of background at each click of button or refresh of a page
d. Display calendar for the month and year selected from combo box
e. On mouse over event
 
 
a. Validation of registration form
scripts.js
function validateForm() {
   var name = document.getElementById("name").value;
   var email = document.getElementById("email").value;
   var password = document.getElementById("password").value;
   var emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
 
   if (name == "") {
       alert("Name must be filled out");
       return false;
   }
   
   if (email == "" || !emailPattern.test(email)) {
       alert("Please enter a valid email address");
       return false;
   }
if (password == "" || password.length < 6) {
       alert("Password must be at least 6 characters long");
       return false;
   }
window.location.href = "success.html";
   return false;
}
 
form.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Simple Validation Form</title>
   <link rel="stylesheet" href="styles.css">
</head>
<body>
   <h2>Simple Validation Form</h2>
   <form id="myForm" onsubmit="return validateForm()">
       <label for="name">Name:</label>
       <input type="text" id="name" name="name"><br><br>
       
       <label for="email">Email:</label>
       <input type="text" id="email" name="email"><br><br>
       
       <label for="password">Password:</label>
       <input type="password" id="password" name="password"><br><br>
       
       <input type="submit" value="Submit">
   </form>
 
   <script src="scripts.js"></script>
</body>
</html>
 
 
styless.css
body {
   font-family: Arial, sans-serif;
}
 
form {
   max-width: 300px;
   margin: auto;
   padding: 1em;
   border: 1px solid #ccc;
   border-radius: 1em;
}
 
label {
   margin-top: 1em;
   margin-bottom: .5em;
   color: #333333;
   display: block;
}
 
input[type="text"],
input[type="password"] {
   width: 100%;
   padding: .5em;
   box-sizing: border-box;
   border: 1px solid #ccc;
   border-radius: 4px;
}
 
input[type="submit"] {
   padding: 0.7em;
   color: #fff;
   background-color: #007BFF;
   border: none;
   border-radius: 4px;
   cursor: pointer;
}
 
input[type="submit"]:hover {
   background-color: #0056b3;
}
 
 
 
b. Open a Window from the current window
index.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Open a New Window</title>
   <script src="openWindow.js"></script>
</head>
<body>
   <button onclick="openNewWindow()">Open New Window</button>
</body>
</html>
openWindow.js
function openNewWindow() {
   window.open("https://www.example.com", "_blank", "width=800,height=600");
}
 
c. Change color of background at each click of button or refresh of a page
index.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Change Background Color</title>
   <script src="changeColor.js"></script>
</head>
<body onload="changeBackgroundColor()">
   <button onclick="changeBackgroundColor()">Change Background Color</button>
</body>
</html>
changeColor.js
function getRandomColor() {
   var letters = '0123456789ABCDEF';
   var color = '#';
   for (var i = 0; i < 6; i++) {
       color += letters[Math.floor(Math.random() * 16)];
   }
   return color;
}
 
function changeBackgroundColor() {
   document.body.style.backgroundColor = getRandomColor();
}
d. Display calendar for the month and year selected from combo box
index.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Display Calendar</title>
   <script src="displayCalendar.js"></script>
</head>
<body>
   <label for="month">Month:</label>
   <select id="month" onchange="displayCalendar()">
       <option value="0">January</option>
       <option value="1">February</option>
       <option value="2">March</option>
       <option value="3">April</option>
       <option value="4">May</option>
       <option value="5">June</option>
       <option value="6">July</option>
       <option value="7">August</option>
       <option value="8">September</option>
       <option value="9">October</option>
       <option value="10">November</option>
       <option value="11">December</option>
   </select>
   
   <label for="year">Year:</label>
   <input type="number" id="year" value="2023" onchange="displayCalendar()">
   
   <div id="calendar"></div>
</body>
</html>
displayCalendar.js
function displayCalendar() {
   var month = document.getElementById("month").value;
   var year = document.getElementById("year").value;
   var firstDay = new Date(year, month, 1).getDay();
   var daysInMonth = new Date(year, parseInt(month) + 1, 0).getDate();
   var calendar = "<table><tr><th>Sun</th><th>Mon</th><th>Tue</th><th>Wed</th><th>Thu</th><th>Fri</th><th>Sat</th></tr><tr>";
 
   for (var i = 0; i < firstDay; i++) {
       calendar += "<td></td>";
   }
   for (var day = 1; day <= daysInMonth; day++) {
       calendar += "<td>" + day + "</td>";
       if ((firstDay + day) % 7 == 0) {
           calendar += "</tr><tr>";
       }
   }
   calendar += "</tr></table>";
 
   document.getElementById("calendar").innerHTML = calendar;
}
 
e. On mouse over event
index.html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Mouse Over Event</title>
   <script src="mouseOverEvent.js"></script>
   <style>
       .hover-box {
           width: 200px;
           height: 100px;
           border: 1px solid black;
           text-align: center;
           line-height: 100px;
           margin-top: 20px;
       }
   </style>
</head>
<body>
   <div class="hover-box" onmouseover="mouseOver()" onmouseout="mouseOut()">Hover over me!</div>
   <div id="message"></div>
</body>
</html>
mouseOverEvent.js
function mouseOver() {
   document.getElementById("message").innerText = "Mouse is over the box!";
}
 
function mouseOut() {
   document.getElementById("message").innerText = "";
}
 