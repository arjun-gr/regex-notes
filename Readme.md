# Regex freeCodeCamp notes.

## Using the test Method 🔍


Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

for eg. If you want to find the word **the** in the string **The dog chased the cat**, you could use the regular expression: **/the/**.

- The regular expressions dont have " " around the string.

### checking using **test** method

JS has many methods to do the testing weather the regex matches the string or not. The **test** method returns **true** if the regex matches the string, or returns **false** if it cannot find the matching string.<br>

The test method is used on a regex and then followed by the string as an argument.

```js
let testStr = "freeCodeCamp";

let testRegex = /Code/;

testRegex.test(testStr);
```

The **test** method returns **true** as the regex matches the testStr.

<span style="color:#e1b8ff; font-weight:bold"> The test methods does a literal match i.e. For regex **/Code/** the string **code** and **CoDe** the test will return false.</span>

### Searching for multiple literal strings using OR operator "|"  🟥🟡🔷
If you want to find multiple patterns you can do that using | operator.
 <br>
```
    /yes | no/ <br>
    /yes | no | maybe/<br>
    /house | home | bunglow/<br>
```    
### Ignore case sensitivity using "i" flag. 👨‍🎓👨‍⚕️
In the above example we did literal matching of the string, like "dog" should match "dog", if the string had "Dog" it would return false.<br>
Hence by specifying "i" flag, It ignores the Case sensitivity and lets you match dog for Dog or doG.
```js
let str = "my Dog is lost, Please find Timo"
let regex = /dog | timo/i
regex.test(str)
returns true
```
So we can see that it matched the strings Dog and Timo even if the regex was not cased as per the string.

The above method that is test was used to find weather the pattern exists in a string or not.

## Extract Matches. 🥤
In the above lesson we saw that using <span style="color:#0077ff; font-weight:bold">"test"</span> method we can check weather the regex exists in the string or not by the results that we get either true if matched and false if not matched.

### <span style="color:pink">match</span> method
The match method lets you extract the actual matches you found with the .match( ) method.<br>

To use the .match( ) method, apply the method on a string and pass in the regex as an argument.
```js
let string = "Peter is a good guy"
let regex = /good/
let result = string.match(regex)
```
### finding more than the first match using "g" flag. 🚗 🚗 🚗
The above example extracts the first match for the string good. <br>
If you want to extract more than one match for the expression you can use the "g" flag. aka global search flag.
```js
let str = "this is a good movie, the movie had great action"
let regex = /good/g
let result = str.match(regex);
//result: ["movie", "movie"]
```
In the result, as you can see it returns an array with number of matched strings.<br>

The above flag i.e. "g" for global search you can use it with "i" so that the search will return the matched strings regardless for the case sensitivity.
```js
let str = "This World was created Millions of years ago, this worlD is great"
let regex = /world/gi
let result = str.match(regex)
//result: [World, worlD]
```
as it can be seen that the result is an array of world. Hence using "i" it ignored the case sensitivity.

## Match anything with wildcard period " . " 🤵👮‍♂️👨‍⚕️
This wild card can match anything thats before it. Lets say i have string "This is a good car the price is good on this, together we can buy this car". <br>
here if i want to find all the strings/words starting with t or th and i dont want to bother with the rest i can just say <span style="color:red; font-weight:bold"> t . or th . </span> this will return the values that has t or th in it.
```js
let str = "The girl is humming the song, She want to hum a song"
let regex = /h./g
regex.test(str) or
let result = str.match(regex)

// This will return all the occurance of h with anything preciding that like he, hu, he, he, hu
```
![Alt text](image.png)

The same goes for preciding texts les say i want to search for sun,gun,fun,bun,run

```js
let str = "the boy run,gun,fun,bun,sun"
let regex = /.un/g
// so the above will match anything that ends with un but the preciding it dont care.
// result: sun, run, gun, fun, bun
```
![Alt text](image-1.png)

## Match single character with multiple possibilities
You can search for a literal pattern ***/literal/*** with some flexibility with character classes. Character classes allow you to define a group of characters you wish to match by placing them inside square ( [ and ] ) brackets.

for example, you want to match bag, big, bug, but not bog. You can do something like /b.g/ where it will match everyting that has b and a letter in middle and g. It will match something like this also beging.

So inorder to match bag, big, bug, but not bog. You can use [ ]. 
```js
    let string = "big, bog, bag, and not bug"
    let regex = /b[ioa]g/
    // the above will match anything that starts with b and ends with g and in middle contains either i or o or a.
    regex.test(string)
    // results: true
    let result = string.match(regex)
    // results: ["big","bog","bag"]
```

Or you can just use [ ] to make searching individual letters
```js
    let string = "Beware of bugs in the above code; I have only proved it correct, not tried it."
    let regex = /[aeiou]/
    let result = string.match(regex)
```
![Alt text](image-2.png)

## 🆎 Match letters of the Alphabet
We can use the above example with the [ ] to match specific letters but lets say we want to search for 10-12 letters it wont be too intuitive. So you can use the [ ] with the " - " to specify a range. <br>
eg. /[a-y]/g this will match every letter that comes in the range of a to y.<br>
This can be further used with the prefix and suffix regex like /a[b-r]t/g so this will return words starting with a and ending with g in between anything that contains letters from b to r.

```js
let str = "mat,bat, cat, bat, hat, tat, that"
let regex = /[a-z]at/g
let result = str.match(regex);
// result: ["mat","bat","cat","hat","tat","hat"]
```

![Alt text](image-3.png)

## Match Numbers and letters of the alphabet
using the hyphen( - ) to match a range of characters is not limited to letters. It also works to match a range of numbers. <br>

for ex: /[0-5]/ matches any number between 0 and 5, Including 0 and 5. <br>
![Alt text](image-4.png)

Also it is possible to combine a range of letters and numbers in a single character set.<br>
![Alt text](image-5.png)

## Dont match these characters."^"
Lets say you have a specific character set **/[abxd]/** and you dont want to match these characters, you can use the caret character " ^ " like this **/[^abxd]/** this will negate these characters and rest will be matched
```js
let string = "this is working fine"
let regex = /[^ine]/gi
let result = string.match(regex)
//result : ["ths","s","workg","f"]
```
As per the example it will neglect i,n,e and return the rest.<br>
![Alt text](image-6.png)

Lets say i want to neglect a set of characters and numbers
```js
let string = "this is my number 0909"
let regex = /[^aeiou0-9]/ or /[^aeiou^0-9]/
let result = string.match(regex)
// result: ["Ths","s","my","nmbr"]
```
![Alt text](image-7.png)  ![Alt text](image-8.png)

## Match characters that occur one or more times " + "
Sometimes, you need to match a character or groupof characters that appear <span style="color:pink"> **one or more times in a row** </span>. this means it occurs at least once, and may be repeated. for eg "mississippi" <br>
Here you can use the " + " to match the ss and pp or just s or p <br>

```js
let string = "mississippi"
let regex = /s+/gi
let result = string.match(regex)
// result: ["s"]
```

![Alt text](image-12.png) ![Alt text](image-13.png) ![Alt text](image-14.png)


## Match characters that occur zero or more times
You can use the " * " <br>
```js
let string = "goooooal"
let regex = /go*/
let result = string.match(regex)
// result: gooooo
```
This matches the occurance of go* means that g and then o* means oooo's after g 