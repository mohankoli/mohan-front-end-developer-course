# Count Nested Comments (Recursive)

## Problem

Given a nested comment structure where each comment can have `replies`, count the total number of replies including nested ones.

---

## Input Structure

```js
const comment = {
  text: "some comment",
  replies: [
    { text: "some comment 1", replies: [] },
    { text: "some comment 2", replies: [] },
    { text: "some comment 3", replies: [
        { text: "some comment 5", replies: [] }
      ]
    }
  ]
};
```

This forms a tree-like structure (depth may vary).

---

## Solution (DFS Recursion)

```js
let countComments = (comment) => {
    let count = 0;
    for (let reply of comment.replies) {
        count++; // count this reply
        let replyCount = countComments(reply); // count nested replies
        count = count + replyCount;
    }
    return count;
}

console.log(countComments(comment)); // 4
```

---

## Explanation

- Uses recursion to traverse nested replies (DFS style).
- Each reply increments the `count`.
- For each reply, we add nested reply counts recursively.
- Root comment is not counted (only its replies).

---

## Output

```
4
```

---

## Time Complexity

```
O(N) — visits each comment once
```

## Space Complexity

```
O(H) — recursion depth (height of tree)
```

---

## Notes

- If you want to include the root in the count:
  `return 1 + count`
- Recursive tree processing is common in:
  - Comments UI (Reddit, YouTube)
  - File explorers
  - JSON data processing
  - AST parsing
  - Menu components
