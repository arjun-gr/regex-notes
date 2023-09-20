# Regex freeCodeCamp notes.

### Using the Test Method
Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

for eg. If you want to find the word **the** in the string **The dog chased the cat**, you could use the regular expression: **/the/**. 
- The regular expressions dont have " " around the string.

### checking using **test** method
JS has many methods to do the testing weather the regex matches the string or not. The **test** method returns **true** if the regex matches the string, or returns **false** if it cannot find the matching string.

eg: ```js
        let testStr = "freeCodeCamp";
        let testRegex = /Code/;
        testRegex.test(testStr);```

The **test** method returns **true** as the regex matches the testStr.