// 2. Reverse a String (Using Loop)
const reverseStringLoop = (str) => {
    let reversed = '';
    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }
    console.log(reversed);
}

reverseStringLoop('test'); // Output: 'tset'

// 3. Reverse a String (Using Built-in Functions)
const reverseString = (str) => {
    let reversed = str.split('').reverse().join('');
    return reversed;
}

console.log(reverseString('Mohan')); // Output: 'nahoM'

