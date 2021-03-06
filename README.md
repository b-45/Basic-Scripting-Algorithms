# Algorithms
Javascript Algorithms 

![badge](https://img.shields.io/badge/lesson--notes-javascript-orange.svg)

> Algorithm is a set of rules to accomplish a computational task.


### 1. Reverse string
***

#### Problem Statement
Return a new string with the reversed order of characters.

#### Strategy
- declare a function and give it a string as parameter 
- use the `split` method to convert the string into an array
- use `reverse` method to reverse the items in the array
- then use the `join` method to convert the array back into a string 
- return the string

#### Code
```
function reverse(str) {
    return str
    .split('')
    .reverse()
    .join('')
    return str
}
```


### 2. Palindrome
***

#### Problem Statement
Palindromes are strings that form the same word when reversed. i.e kayak, civic.  Return true if the string is a palindrome or false if it is not.

#### Strategy
- declare a function and give it a string as parameter 
- use the `split` method to covert the string into an array
- use `reverse` method to reverse the items in the array
- use the `join` method to convert the array back into a string 
- then check to see if the reversed string and original string is truthy or falsy.

#### Code
```
function palindrome(str) {
  let reversed = str.split('').reverse().join('');
    return reversed === str;
}
```


### 3. Fizzbuzz
***

#### Problem Statement
Write a script that prints the number 1 to n, however for multiples of 3 - print "fizz", for multiples of 5 - print "buzz" and finally for multiples of 3 and 5 - print "fizbuzz".

#### Strategy
- declare a function and give it a number as parameter 
- write a for loop to iterate from 1 to n
- write multiple `else if` statements
- condition 1 checks if n modulo 3 and n modulo 5 equals 0 then console log 'fizzbuzz'
- condition 2 checks if n modulo 3 equals 0 then console log 'fizz'
- condition 3 checks if n modulo 5 equals 0 then console log 'buzz'
- else console log any number outside of the aforementioned conditions

#### Code
```
function fizzBuzz(n) {
  for (let i = 1; i <= n; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
      console.log('fizzbuzz');
    } else if (i % 3 === 0) {
      console.log('fizz');
    } else if (i % 5 === 0) {
      console.log('buzz');
    } else {
      console.log(i);
    }
  }
}
```


### 4. Reverse Integer
***

#### Problem Statement
Given an integer, return an integer that is reversed while satisfying the following conditions i.e 15 returns 51, -25 returns -52,  100 returns 1.

#### Strategy
- declare a function and give it a number as parameter 
- use the `toString` method to covert the integer into an string
- use `reverse` method to reverse the string
- use the `join` method to join the string 
- use the `parseInt` method to convert the string back to an integer
- then use the `Math.sign` method to maintain negative numbers

#### Code
```
function reverseInt(n) {
  const reverse = n
    .toString()
    .split('')
    .reverse()
    .join('')
return parseInt(reverse) * Math.sign(n)
}
```

#### Alternative 
```
function reverseInt(n) {
  const reverse = n
  .toString()
  .split('')
  .reverse()
  .join('')
  
// use the ternary operator to check if the integer is negative
  const checkNegativeSign = n < 0 ? parseInt(reverse) * -1 : parseInt(reverse)  
  return checkNegativeSign
  }
```


### 5. Max Character
***

#### Problem Statement
Given a string, return the most repeated character that occurs in the string. i.e "apple" === 'p'

#### Strategy
- declare a function and give it a string as parameter 
- using the `for of` loop, generate an object named 'charMap' that maps each character in the string to the object.
- declare a helper variable named 'max' that stores the maximum **value** of the string most repeated in the object.
- declare another helper variable named 'maxChar' that stores the most repeated **character**. 
- iterate through the object using a `for in` loop while incrementing the "max" variable and assigning the "maxChar" variable with the most repeated character.
- return maxChar

#### Code
```
function maxChar(str) {
  const charMap = {}
  let max = 0
  let maxChar = ''

  for (let char of str) {
    charMap[char] ? charMap[char]++ : charMap[char] = 1
  }

  for (let char in charMap) {
    if (charMap[char] > max) {
      max = charMap[char]
      maxChar = char
    }
  }
  return maxChar
}

```


### 6. Array Chunking
***

#### Problem Statement
Given an array and chunk size, divide the array into many subarrays where each subarray is of length size. i.e [1, 2, 3, 4] --> [[1,2], [3, 4]]

#### Strategy
- declare a function and give it an `array` and `size` as parameter 
- create a helper variable named `chunked` that stores chunks of subarrays where each array is of length size.
- create another helper variable named `index` starting from 0
- in a `while` loop, iterate from `index` up to length of `array` 
- using the slice method, push slices of subarrays that equals of length `size` into `chunked`
- increment `index` with 'size' to kill the  loop
- return `chunked`


#### Code
```
function chunk(array, size) {
  const chunked = []
  let index = 0

  while (index < array.length) {
  chunked.push(array.slice(index, index + size))
  index += size
  }
  return chunked
}  

```


### 7. Anagrams
***

#### Problem Statement
Given two strings, check to see if they anagrams of each other. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as cinema, formed from iceman.  Capital letter should be lowercase, no spaces or punctuations allowed.  i.e "RAIL SAFETY!", "fairy tales" --> True.

#### Strategy
- declare a function `anagrams` and give it two strings as parameter.
- declare another helper function `cleanString`that formats the string by removing undesired characters and transforms letters to lowercase.
- after formatting the string with `cleanString`, use the function `anagrams` to compare both strings to each other
- return `anagrams`.

#### Code
```
function anagrams(stringA, stringB) {
  return cleanString(stringA) === cleanString(stringB)
}

function cleanString(str) {
  return str.replace(/[^\w]/g, '').split('').sort().join('')
}
 
```


### 8. Sentence Capitalization
***

#### Problem Statement
Write a function that capitalizes the first letter of each word. i.e "i love javascript" --> "I Love Javascript"

#### Strategy
- declare a function `capitalize` and give it a string as parameter.
- make an empty array named `words` to store transformed words
- iterate over the array while using `split` to convert each string into an array
- apply `toUpperCase` to transform the first character in each word then concatenate the remaining characters using the `slice` method
- push the transformed words into the empty array named `words`.
- `join` array back into string and return.

#### Code
```
function capitalize(str) {
  const words = []

  for (let word of str.split(' ')) {
    words.push(word[0].toUpperCase() + word.slice(1)) 
  }
  return words.join(' ')
}

```


### 9. Stairsteps
***

#### Problem Statement
Write a function that takes a positive number and prints a step shape N levels using the "#" character.  i.e
stairSteps(3) should return -->


'#  '

'## '

'###'

consider the trailng empty spaces within quotes

#### Strategy
- declare a function `steps` and give it a positive number as parameter.
- create a 3 x 3 matrix by iterating from 0 to n for (i) rows and (j)columns 
- if column is less than or equal to row, increment `stair` with '#'
- else increment `steps` with ' '
- console.log(steps)

#### Code
```
function stairSteps(n) {
  for (row = 0; row < n; row++) {
    let steps = ''

    for(column = 0; column < n; column++) {
      if (column <= row) {
        steps += '#'
      }
      else {
        steps += ' '
      }

    }
    console.log(steps);
  }
}

```


### 10. Pyramid
***

#### Problem Statement
Write a function that accepts a positive number N.  The function should output a pyramid shape with N levels using the # character.  Make sure the pyramid has spaces on both the left and right hand sides.
i.e  pyramid(3) -->
 
 
  '  #  '
 
  ' ### '
 
  '#####'

#### Strategy
- declare a function `pyramid` and give it a positive number as parameter.
- write a `for loop` that iterates through each n rows. 
- create a variable 'level' that assigns empty space to each row.
- write another `for loop` that iterates over columns such that when given n, each column computes logic that doubles n and subtracts 1.
- in order to assign "#" to the matrix created, create a variable `midpoint` that locates index of the row's midpoint.
- use a if block to assign # when midpoint minus row is less than and equal to column and when midpoint plus row greater than and equal to column else add an empty space
- return level

#### Code
```
function pyramid(n){
  const midpoint = Math.floor((2 * n - 1)/2)

  for (let row = 0; row < n; row++) {
    let level = ''

    for (let column = 0; column < 2 * n - 1; column++){
      if (midpoint - row <= column && midpoint + row >= column){
        level += '#'
      } else {
        level += ' '
      }

    }
    console.log(level);
  }
}

```


### 11. Vowels
***

#### Problem Statement
Write a function that returns the number of vowels used in a string.  Vowels are the characters 'a', 'e''i', 'o', and 'u'.
i.e. vowels('Hi There!') --> 3

#### Strategy
- declare a function `vowels` and give it string as parameter.
- assign 0 to a variable labeled `counter` to count occurences of a vowel
- assign characters in vowels to a variable labeled `vowels'
- iterate through lowercased characters in given string and check if it `includes` any vowels
- if so, increment counter
- return counter
 
#### Code
```
function vowels (str) {
  let counter = 0
  const vowels = ['a', 'e', 'i', 'o', 'u']
  
  for (let char of str.toLowerCase()) {
    if (vowels.includes(char)) {
      counter++
    } 
  }
  return counter
}
 
```


### 12. Factorialize
***

#### Problem Statement
Write a function that returns the factorial of the provided integer
for example: 

5! = 1 * 2 * 3 * 4 * 5 = 120 
#### Strategy
- declare a function named `factorialize` and give it integer as parameter.
- assign 1 to a variable named `result` 
- iterate through given integer and multiply each iteration of given argument by `result` 
- return result
 
 
#### Code
```
function factorialize(num) {
  let result = 1
  for (let i = 1;  i <= num;  i++) {
    result = result * i
  }
  return result
}

```











Resources:


[The Coding Interview Bootcamp: Algorithms + Data Structures](https://www.udemy.com/coding-interview-bootcamp-algorithms-and-data-structure/)


[Freecodecamp](https://www.freecodecamp.org/)

[MDN Javascript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
