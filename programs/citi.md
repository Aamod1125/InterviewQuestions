const a = [1, [2, 3], [4, 5, [6, 7]]];


function flatArray(arr) {
    return arr.reduce((acc, val) => {
        Array.isArray((val) ? acc.concat(flatArray(val)) : acc.concat(val),[]);
    })
}

const output = flatArray(a);