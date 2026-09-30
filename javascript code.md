// const a = 10;
// const b = 20;

// function add(x, y) {
//     return x + y;
// }

// console.log(add(a, b));

// function debounce(fn, delay) {
//     let timer;

//     return function (...args) {
//         clearTimeout(timer);

//         timer = setTimeout(() => {
//             fn.apply(this, args);
//         }, delay);
//     };
// }

// function search(value) {
//     console.log("Searching for:", value);
// }

// const debouncedSearch = debounce(search,0);

// debouncedSearch("j");
// debouncedSearch("ja");
// debouncedSearch("jav");
// debouncedSearch("java");

// const n = 10;
// let a = 0, b = 1;

// for (let i = 0; i < n; i++) {
//     console.log(a);
//     [a, b] = [b, a + b]; // This does the simultaneous swap, just like Python
// }

// const limit = 10;
// const output = febNum(limit);

// function febNum(n){
//     if (n<= 0) return[];
//     if (n === 0)return[0];
//     const sequence = [ 0, 1];
//     for (let i = 2; i < n; i++){
//         const result = sequence[i - 1]+sequence[i -2]
//         sequence.push(result)
//     }
//     return sequence;
// }
// console.log(output)

// // 1. We mock the functions to simulate asynchronous tasks using setTimeout
// function getBread(callback) {
//     console.log("Getting the bread...");
//     // The first argument is 'error' (null means no error). 
//     // The second argument is the 'bread' data.
//     setTimeout(() => callback(null, "Whole Wheat Loaf"), 1000); 
// }

// function sliceBread(bread, callback) {
//     console.log(`Slicing the ${bread}...`);
//     setTimeout(() => callback(null, "2 Slices"), 1000);
// }

// function addPeanutButter(slices, callback) {
//     console.log(`Adding PB to ${slices}...`);
//     setTimeout(() => callback(null, "PB Sandwich"), 1000);
// }

// function serve(sandwich, callback) {
//     console.log(`Serving the ${sandwich}...`);
//     setTimeout(() => callback(null), 1000);
// }

// // 2. Now we run your callback hell code
// getBread(function(error, bread) {
//     if (error) return console.error("No bread!");

//     sliceBread(bread, function(error, slices) {
//         if (error) return console.error("Knife broken!");

//         addPeanutButter(slices, function(error, sandwich) {
//             if (error) return console.error("Out of peanut butter!");

//             serve(sandwich, function(error) {
//                 if (error) return console.error("Dropped it!");
                
//                 // 3. This will finally print!
//                 console.log("Finally eating!"); 
//             });
//         });
//     });
// });

// 1. Successful steps
// function getBread(callback) {
//     console.log("Getting the bread...");
//     setTimeout(() => callback(null, "Whole Wheat Loaf"), 1000); 
// }

// function sliceBread(bread, callback) {
//     console.log(`Slicing the ${bread}...`);
//     setTimeout(() => callback(null, "2 Slices"), 1000);
// }

// // 2. THIS STEP WILL FAIL
// function addPeanutButter(slices, callback) {
//     console.log(`Adding PB to ${slices}...`);
//     // Instead of passing null for the error, we pass an actual error message
//     setTimeout(() => callback("Jar is empty!", null), 1000);
// }

// function serve(sandwich, callback) {
//     console.log(`Serving the ${sandwich}...`);
//     setTimeout(() => callback(null), 1000);
// }

// // 3. Running the same callback hell code
// getBread(function(error, bread) {
//     if (error) return console.error("No bread!");

//     sliceBread(bread, function(error, slices) {
//         if (error) return console.error("Knife broken!");

//         addPeanutButter(slices, function(error, sandwich) {
//             // Because our mock function passed an error, this 'if' statement is triggered
//             if (error) return console.error("Out of peanut butter!");

//             // Everything below this is skipped because the line above used 'return'
//             serve(sandwich, function(error) {
//                 if (error) return console.error("Dropped it!");
                
//                 console.log("Finally eating!");
//             });
//         });
//     });
// });

// const users ={
//     name:"naveen",
//     address:{
//         city: "chennai"
//     },
//     name:"jeni",
//     address:{
//         city:"coimbatior"
//     }
// }
// const copy = {...users};
// copy.address.city = "banglore";
// console.log(copy.address.city);

// let newRname = "naveen";
// const str = newRname;
// const out = revString(str)

// function revString(text){
//     return text.split("").reverse().join("");
// }

// console.log(JSON.stringify(out))
// var example
// var name = "Jane"; // Allowed (re-declared)
// var name = "John";
// name = "Bob";     // Allowed (updated)
// console.log(name)
// let example
// let age = 25;
// // let age = 30;  // Error! Cannot re-declare 'age' in the same scope
// age = 26;         // Allowed (updated)
// console.log(age)
// const example
// const name= "naveen";
// const name = "jeni"; //error
// name = "anas"; //error
// console.log(name)

//garbage
// let user = {
//     name: "Naveen"
// };
// user = null
// console.log(user)

// palindrom
// let name1 = "naveen"
// let name2 = "arora"
// const output1 = isPalindrome(name1)
// const output2 = isPalindrome(name2) 
// function isPalindrome(str) {
//     let reversed = "";
//     for (let i = str.length - 1; i >= 0; i--) {
//         // reversed += str[i];
//         reversed = reversed+str[i];
//     }
//     return str === reversed;
// }

// console.log(output1, output2)

// largest
// const numbers = [10, 50, 20, 80, 30,100,110]
// const largest = findLargest(numbers)
// function findLargest(arr) {
//     let max = arr[0];
//     for (let i = 1; i < arr.length; i++) {
//         if (arr[i] > max) {
//             max = arr[i];
//         }
//     }
//     return max;
// }
// console.log(largest);
//second
// const out_1= secondLargest(numbers)
// function secondLargest(arr) {
//     let largest = -Infinity;
//     let second = -Infinity;
//     for (const num of arr) {
//         if (num > largest) {
//             second = largest;
//             largest = num;
//         } else if (num > second && num !== largest) {
//             second = num;
//         }
//     }
//     return second;
// }
// console.log(out_1)
// Find duplicate values
// const num=[1, 2, 3, 2, 4, 3, 5]
// const out_1 = duplicates(num)
// function duplicates(arr) {
//     const seen = new Set();
//     const duplicate = new Set();
//     for (const num of arr) {
//         if (seen.has(num)) {
//             duplicate.add(num);
//         }
//         seen.add(num);
//     }
//     return [duplicate];
// }
// console.log(out_1);

// // character frequency
// const letter = "naveen"
// const output = frequency(letter)
// function frequency(str) {
//     const result = {}
//     for (const char of str) {
//         result[char] = (result[char] || 0) + 1;
//     }
//     return result;
// }
// console.log(output);

// // twoSum
// const nums = [2, 6, 3, 11, 15]
// const target = 9
// const out = twoSum(nums, target)
// function twoSum(nums, target) {
//     const map = new Map();
//     for (let i = 0; i < nums.length; i++) {
//         const complement = target - nums[i];
//         if (map.has(complement)) {
//             return [map.get(complement), i];
//         }
//         map.set(nums[i], i);
//     }
//     return [];
// }
// console.log(out);

// const a = "listen"
// const b = "silent"
// const out = isAnagram(a,b)
// function isAnagram() {
//     if (a.length !== b.length) {
//         return false;
//     }
//     const count = {};
//     for (const char of a) {
//         count[char] = (count[char] || 0) + 1;
//     }
//     for (const char of b) {
//         if (!count[char]) {
//             return false;
//         }
//         count[char]--;
//     }
//     return true;
// }
// console.log(out);
// prime
// const number1 = 7;
// const number2 = 2;
// const out1 = isPrime(number1);
// const out2 = isPrime(number2);
// function isPrime(n) {
//     if (n < 2) {
//         return false;
//     }
//     for (let i = 2; i * i <= n; i++) {
//         if (n % i === 0) {
//             return false;
//         }
//     }
//     return true;
// }
// console.log(out1); // true (17 is prime)
// console.log(out2); // false (20 is not prime)

// factroial
// const num = 5
// const out  = factorial(num)
// function factorial(n) {
//     let result = 1;

//     for (let i = 2; i <= n; i++) {
//         result *= i;
//     }

//     return result;
// }

// console.log(out);

// let a;
// var a;
// const a = 3;
// console.log(a)
//if (true) {
  //let blockScoped = "Hidden";
  //var functionScoped = "Exposed";
//}

// console.log(functionScoped); // Logs: "Exposed"
// console.log(blockScoped);    // ReferenceError: blockScoped is not defined

// const limit = 10
// const result = febonaccinum(limit)

// function febonaccinum(n) {
//     if (n<=0) return[];
//     if (n === 0) return[0];
//     const sequence = [0,1];
//     for (let i =2; i < n; i++){
//         const next = sequence[i-1] + sequence[i-2];
//         sequence.push(next)
//     }
//     return sequence;
// }
// console.log(result)

// const timer = setTimeout(()=>{
//     console.log("olunga padi da")
// })

// const limit = 10
// const output = febNum(limit)

// function febNum(n){
//     if (n<=0) return[];
//     if (n === 0) return[1];
//     const febSeq = [0,1];
//     for(let i = 2; i < n; i++){
//         const seq = febSeq[i-1]+febSeq[i-2]
//         febSeq.push(seq)
//         console.log(febSeq)
//     }
//     return febSeq

// }
// console.log(JSON.stringify(output));
// console.log(output)

// const lim = 10
// const set = febSeq(lim)

// function febSeq(n){
//     if (n<=0)return[];
//     if(n === 0)return[1];
//     const seqq = [0,1];
//     for(let i = 2; i<n; i++){
//         const setSeq = seqq[i-1]+seqq[i-2]
//         seqq.push(setSeq)
//     }
//     return seqq;
// }
// console.log(JSON.stringify(set))
// const input = "0,1,1,2,3,5,8,13,21,34";

// const revrseNum = number(input);

// function number(n) {
//     let result = "";
//     let currentNUm = "";

//     for (let i = 0; i < n.length; i++) {
//         if (n[i] === ",") {
//             if (result === "") {
//                 result = currentNUm;
//             } else {
//                 result = currentNUm + "," + result;
//             }
//             currentNUm = "";
//         } else {
//             currentNUm += n[i];
//         }
//     }
//     if (result === "") {
//         result = currentNUm;
//     } else {
//         result = currentNUm + "," + result;
//     }
//     return result;
// }
// console.log(revrseNum);

// const input = "0,1,1,2,3,5,8,13,21,34";
// const revrseNum = number(input);
// console.log(String(input.split(",").reverse().join(",")))

// function number(n) {
//     let result = "";
//     let currentNUm = "";

//     for (let i = 0; i < n.length; i++) {
//         if (n[i] === ",") {
//             if (result === "") {
//                 result = currentNUm;
//             } else {
//                 result = currentNUm + "," + result;
//             }
//             currentNUm = "";
//         } else {
//             currentNUm += n[i];
//         }
//     }
    
//     if (result === "") {
//         result = currentNUm;
//     } else {
//         result = currentNUm + "," + result;
//     }
//     return result; 
// }
// console.log(revrseNum);

// const n = input
// let out=[]
// number(n);
// function number(n){
    
//     out.push(n.split(",").reverse().join(","))
// }
// console.log(out)

// const rev = [16, 13, 1, 10, 3, 9, 2];
// // Use the spread operator [...] to create a copy, then reverse it
// const out = [...rev].reverse();
// console.log(JSON.stringify(out));

// const rev = [16, 13, 1, 10, 3, 9, 2];
// let out = [];
// reverseArray(rev);
// function reverseArray(arr) {
//     // 2. Arrays don't need split(). Just reverse it and push it.
//     out.push([...arr].reverse());
// }
// console.log(out);

// function number(n){
//     return n.split(',')
//     .reverse()
//     .map(Number);
// }
// console.log(JSON.stringify(revrseNum))

// What is hoisting?
// console.log(user); // Output: undefined
// let user = "123";

// var a;
// console.log(a);

// a = 10;

// What are primitive and non-primitive data types?
// let name = "Naveen";
// let age = 25;
// let isActive = true;

// let user = {
//     name: "Naveen",
//     age: 25
// };

// console.log(typeof name);
// console.log(typeof age);
// console.log(typeof user);
// console.log(typeof isActive)

// What is scope?
// let globalVariable = "global";

// function test() {
//     let functionVariable = "function";

//     if (true) {
//         let blockVariable = "block";

//         console.log(globalVariable);
//         console.log(functionVariable);
//         console.log(blockVariable);
//     }
//     console.log("222",functionVariable);

// }
// console.log("111",globalVariable);

// test();

// Find duplicate number
// const arr = [1, 3, 4, 2, 2,1,5,6,5,9,0,3,9,4,2,1,0];
// const output = []

// for (const[index, value] of arr.entries()){
//     if (arr.indexOf(value) !== index){
//         output.push(value);
//     }
// }
// console.log(output)

// Distruction
// const user = { name: "Alice", age: 28, role: "Admin" };
// const { name, age } = user;
// const rolae = user.role;

// console.log(name, age);
// console.log(rolae);

// What is this in JavaScript?
// const user = {
//     name: "Naveen",

//     greet: function () {
//         console.log(this.name);
//     }
// };

// user.greet();

// Normal function vs arrow function this
// const user = {
//     name: "Naveen",

//     normal: function () {
//         console.log(this.name);
//     },
//     arrow: () => {
//         console.log(this.name);
//     }
// };

// user.normal();
// user.arrow();

// const user = {
//     name: "Naveen",
//     normal: function () {
//         console.log(this.name);
//     },
//     shorthand() {
//         console.log(this.name);
//     },

//     // 3. If you MUST use an arrow function, you cannot use 'this'. 
//     // You have to reference the object name directly:
//     arrow: () => {
//         console.log(user.name); 
//     }
// };

// user.normal();    
// user.shorthand(); 
// user.arrow();     

// What is the spread operator?
// const a = [1, 2, 3];
// const b = [...a, 4, 5];

// console.log(b);
// const user = {
//     name: "Naveen",
//     age: 25
// };

// const updatedUser = {
//     ...user,
//     age: 26
// };

// console.log(updatedUser);

// map
// const num = [1,2,3,4,9]
// let output=[]
// for (const n of num){
//     const double = n*2
//     console.log(double)
//     output.push(double)
// }
// const result = num.map(n => n*2  )
// console.log(output)

// filter

// const filterNum = [1,2,3,4,5,6,7,8,9,10]

// const output = filterNum.filter(n => n<5)
// function reverse(output){
//     return output.s}
// console.log(output)
// const numbers = [1,2,3,4,5,6,7,8,9,10]

// const result = numbers.reduce((sum, n) => sum + n, 0);

// console.log(result);

// 1. Creating a Promise
// const orderCoffee = new Promise((resolve, reject) => {
//     let coffeeMachineWorking = true;

//     if (coffeeMachineWorking) {
//         resolve("Here is your Latte!"); // Success
//     } else {
//         reject("Sorry, machine is broken."); // Failure
//     }
// });

// // 2. Consuming the Promise
// orderCoffee
//     .then(message => {
//         // This runs if the Promise is resolved
//         console.log("Success:", message); 
//     })
//     .catch(error => {
//         // This runs if the Promise is rejected
//         console.log("Error:", error); 
//     })
//     .finally(() => {
//         // This runs no matter what happens (optional)
//         console.log("Finished waiting for coffee.");
//     });

// What is async/await?
// .then()
// function getUserData() {
//     fetch('https://api.example.com/user')
//         .then(response => response.json())
//         .then(data => {
//             console.log("User data:", data);
//         })
//         .catch(error => {
//             console.log("Error fetching data:", error);
//         });
// }
// async await
// async function getUserData() {
//     try {
//         // Code pauses here until the fetch is complete
//         const response = await fetch('https://api.example.com/user');
        
//         // Code pauses here until the data is parsed
//         const data = await response.json(); 
        
//         console.log("User data:", data);
//     } catch (error) {
//         // This catches any rejection from the Promises above
//         console.log("Error fetching data:", error);
//     }
// }

// event loop
// console.log("1");
// setTimeout(() => {
//     console.log("2");
// }, 0);
// Promise.resolve().then(() => {
//     console.log("3");
// });
// console.log("4");

// const animal = {
//    eat() {
//        console.log("Eating");
//   }
// };

// const dog = Object.create(animal);

// dog.bark = function () {
//    console.log("Barking");
// };

// dog.bark();
// dog.eat();