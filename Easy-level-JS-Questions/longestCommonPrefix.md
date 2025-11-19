let longestCommonPrefix = (str) => {
   if (!str.length) return '';

   // Step 1: Sort the array
   str.sort();

   // Step 2: Compare only the first and last string
   let first = str[0];
   let last = str[str.length - 1];
   let prefix = '';

   // Step 3: Build prefix character-by-character
   for (let i = 0; i < first.length; i++) {
       if (first[i] === last[i]) {
           prefix += first[i];
       } else {
           break;
       }
   }

   return prefix;
}

console.log(longestCommonPrefix(["flaower", "flow", "flaight"]));
