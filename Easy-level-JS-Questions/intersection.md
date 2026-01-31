let intersection = (arr1, arr2) => {
    let result = [];

    for (let i = 0; i < arr1.length; i++) {
        if (
            arr2.indexOf(arr1[i]) !== -1 &&   // exists in arr2
            result.indexOf(arr1[i]) === -1   // not already in result
        ) {
            result.push(arr1[i]);
        }
    }

    return result;
};

// Example
let a = [1, 2, 2, 3, 4];
let b = [2, 3, 5];

console.log(intersection(a, b)); // [2, 3]
