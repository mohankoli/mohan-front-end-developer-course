# Implement Queue using Stack

## Idea

Use two stacks:

-   stack1 → input stack
-   stack2 → output stack

### Steps

1.  Push elements into `stack1`
2.  When dequeue is needed:
    -   Move all elements from `stack1` → `stack2`
3.  Pop from `stack2`

This reverses the order to maintain FIFO.

------------------------------------------------------------------------

# JavaScript Implementation

``` javascript
class MyQueue {

    constructor(){
        this.stack1 = []
        this.stack2 = []
    }

    enqueue(x){
        this.stack1.push(x)
    }

    dequeue(){

        if(this.stack2.length === 0){
            while(this.stack1.length){
                this.stack2.push(this.stack1.pop())
            }
        }

        return this.stack2.pop()
    }

    peek(){

        if(this.stack2.length === 0){
            while(this.stack1.length){
                this.stack2.push(this.stack1.pop())
            }
        }

        return this.stack2[this.stack2.length - 1]
    }

    empty(){
        return this.stack1.length === 0 && this.stack2.length === 0
    }
}

let q = new MyQueue()

q.enqueue(1)
q.enqueue(2)
q.enqueue(3)

console.log(q.dequeue())
console.log(q.peek())
console.log(q.empty())
```
