# Valid Parentheses

Classic stack / counting interview problem.

------------------------------------------------------------------------

# Problem

Given a string containing parentheses:

( ) { } \[ \]

Determine if the string is **valid**.

Rules:

1.  Opening brackets must be closed by the same type.
2.  Brackets must close in the correct order.

------------------------------------------------------------------------

# Solution 1 --- Count Method (Only for `()`)

This works **only when the string contains `(` and `)`**.

## Idea

1.  Increase count when `(` appears
2.  Decrease count when `)` appears
3.  If count becomes negative → invalid
4.  At the end count must be `0`

## JavaScript Implementation

``` javascript
function isValidParenthesesCount(s){

    let count = 0

    for(let char of s){

        if(char === "("){
            count++
        } else {
            count--
        }

        if(count < 0){
            return false
        }
    }

    return count === 0
}

console.log(isValidParenthesesCount("()()"))
console.log(isValidParenthesesCount("(()"))
console.log(isValidParenthesesCount(")("))
```

Time Complexity: O(N)\
Space Complexity: O(1)

Limitation: Works only for `()` and cannot detect incorrect nesting.

------------------------------------------------------------------------

# Solution 2 --- Stack Method (Works for `() {} []`)

## Idea

1.  Push opening brackets into stack
2.  When closing bracket appears
3.  Check if it matches the stack top
4.  If mismatch → invalid

## JavaScript Implementation

``` javascript
function isValid(s){

    let stack = []

    let map = {
        ')':'(',
        '}':'{',
        ']':'['
    }

    for(let char of s){

        if(map[char]){

            if(stack.pop() !== map[char]){
                return false
            }

        } else {
            stack.push(char)
        }
    }

    return stack.length === 0
}

console.log(isValid("()"))
console.log(isValid("()[]{}"))
console.log(isValid("(]"))
```

Time Complexity: O(N)\
Space Complexity: O(N)

------------------------------------------------------------------------

# Comparison

  Method   Works For    Limitation
  -------- ------------ -----------------------------
  Count    `()`         Cannot detect nesting order
  Stack    `() {} []`   Correct solution

------------------------------------------------------------------------

# Interview Explanation

For a single bracket type we can use a counter.\
For multiple bracket types we must use a stack to preserve the order of
brackets.
