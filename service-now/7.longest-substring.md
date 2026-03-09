# Longest Substring Without Repeating Characters

Classic engineering interview problem.

------------------------------------------------------------------------

# Problem

Given a string `s`, find the **length of the longest substring without
repeating characters**.

Example

Input

s = "abcabcefbb"

Output

6

Longest substring

"cabcef"

------------------------------------------------------------------------

# Approach 1 --- Brute Force

## Idea

1.  Start from every index `i`
2.  Build substring until duplicate appears
3.  Track maximum length

------------------------------------------------------------------------

## JavaScript Implementation

``` javascript
function longestSubstring(s){

   let max = 0;
   
   for(let i=0;i<s.length;i++){
      let temp = [];
      
      for(let j=i;j<s.length;j++){

        if(temp.includes(s[j])) break;

        temp.push(s[j]);

        max = Math.max(max, temp.length);
      }
   }

   return max;
}

console.log(longestSubstring("abcabcefbb"));
```

------------------------------------------------------------------------

## Time Complexity

O(N²)

Reason: We check substrings starting from every index.

------------------------------------------------------------------------

## Space Complexity

O(N)

Temporary array for substring.

------------------------------------------------------------------------

# Approach 2 --- Sliding Window (Optimized)

## Idea

Use **two pointers** to maintain a window of unique characters.

Steps

1.  Use `left` and `right` pointers
2.  Maintain a **Set** to track characters
3.  Expand window using `right`
4.  If duplicate appears → move `left`
5.  Track maximum length

------------------------------------------------------------------------

## JavaScript Implementation

``` javascript
function longestSubstringOptimized(s){

    let set = new Set();
    let left = 0;
    let maxLength = 0;

    for(let right = 0; right < s.length; right++){

        while(set.has(s[right])){
            set.delete(s[left]);
            left++;
        }

        set.add(s[right]);

        maxLength = Math.max(maxLength, right - left + 1);
    }

    return maxLength;
}

console.log(longestSubstringOptimized("abcabcefbb"));
```

------------------------------------------------------------------------

## Time Complexity

O(N)

Each character is visited at most twice.

------------------------------------------------------------------------

## Space Complexity

O(N)

Set stores characters in the current window.

------------------------------------------------------------------------

# Comparison

  Approach         Time Complexity   Space   Notes
  ---------------- ----------------- ------- -------------------
  Brute Force      O(N²)             O(N)    Simple but slower
  Sliding Window   O(N)              O(N)    Optimal solution

------------------------------------------------------------------------

# Interview Explanation

"I first implement a brute-force solution that checks substrings
starting from every index.\
Then I optimize it using the sliding window technique with two pointers
to achieve O(N) time complexity."

------------------------------------------------------------------------

# Related Interview Problems

-   Longest Substring with K Distinct Characters\
-   Minimum Window Substring\
-   Longest Repeating Character Replacement
