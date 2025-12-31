const compressString = (str) => {
    let result = '';
    let count = 1;

    for (let i = 0; i < str.length; i++) {
        if (str[i] === str[i + 1]) {
            count++;
        } else {
            result += str[i] + count;
            count = 1;
        }
    }
    return result;
};

console.log(compressString("aaabbccccdaa"));
//outpur - a3b2c4d1a2
