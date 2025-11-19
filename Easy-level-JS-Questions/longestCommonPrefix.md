# Check if a String is a longest common prefix

```javascript
// longest common prefix
let longestCommonPrefix = (str) =>{
   if(!str.length) return '';
   str.sort();
   let first = str[0]
   let last = str[str.length-1];
   let prefix = '';
   for(let i=0;i<=str.length; i++) {
       if(first[i] === last[i]) {
           prefix +=first[i];
       } else {
           break;
       }
   }
   return prefix;
}



console.log(longestCommonPrefix(["flaower", "flow", "flaight"])); 


