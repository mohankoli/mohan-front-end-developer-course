let sampleData = [1, 2, [3, 4, [5]], 6, 7, [8]];

// Step 1: Flatten the array
let flattenArray = (arr) => {
    let res = [];
    arr.forEach((item) => {
        if (Array.isArray(item)) {
            res.push(...flattenArray(item)); // recursive flatten
        } else {
            res.push(item);
        }
    });
    return res; // return flattened array
};

// Step 2: Sum the flattened array
let FlatArray = (arr) => {
    let flat = flattenArray(arr);
    let count = flat.reduce((total, item) => total + item, 0);
    return count;
};

console.log(FlatArray(sampleData)); // 36
