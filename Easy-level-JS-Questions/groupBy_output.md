# groupBy Output

``` js
const employees = [
  { name: "Mohan", department: "IT" },
  { name: "Kiran", department: "HR" },
  { name: "Rahul", department: "IT" },
  { name: "Sara", department: "Finance" }
];

function groupBy(arr, key){
     let res = {};
    for(item of arr) {
        const grpName = item[key];
        if(!res.grpName) {
            res[grpName] = [];
        }
        res[grpName].push(item);
    }
    return res;
}

console.log(groupBy(employees,'department'))
```

## ✅ Corrected Output

    {
      IT: [
        { name: "Mohan", department: "IT" },
        { name: "Rahul", department: "IT" }
      ],
      HR: [
        { name: "Kiran", department: "HR" }
      ],
      Finance: [
        { name: "Sara", department: "Finance" }
      ]
    }
