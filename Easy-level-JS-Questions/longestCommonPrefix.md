let longestCommonPrefix = (str) => {
    if (!str.length) return '';

    // Sort the strings alphabetically
    str.sort();

    let first = str[0];
    let last = str[str.length - 1];
    let prefix = '';

    // Compare characters of first and last string
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
