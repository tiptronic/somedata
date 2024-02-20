---
title: Sort array using intlCollator
path: /code-snippets
date: 2024-02-20
summary: sort using language features
categories: [Development]
tags: ["development", "javascript"]
---


```javascript
const sourceArray = Array.from({ length: 67 }, (_, i) => i);

// Create a function that takes an array and chunk size and returns chunked arrays
// using Array.from and Math.ceil
const createChunkedArray = (array = [], size = 10) => {
    // Array.from to create a new array with a length of the number of chunks we need
    // Math.ceil to round up to the nearest whole number
    return Array.from({ length: Math.ceil(array.length / size) }, (_, i) =>
        array.slice((size * i), size * i + size));
}

// Create a function that takes an array and chunk size and returns chunked arrays
// using a while loop
const createChunkedArrayWithLoop = (array = [], size) => {
    const chunkedArray = [];
    let index = 0;
    while(index < array.length) {
        chunkedArray.push(array.slice(index, index + size));
        index += size;
    }
    return chunkedArray;
}

// Test the functions (both should return the same result)

console.log(createChunkedArray(sourceArray, 10));
console.log(createChunkedArrayWithLoop(sourceArray, 10));
```