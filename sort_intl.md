---
title: Sort array using intlCollator
path: /code-snippets
date: 2024-02-20
summary: sort using language features
categories: [Development]
tags: ["development", "javascript"]
---

## Sort array using intlCollator

Sort array using intlCollator

```javascript
const arrayOfStrings = ['A', 'B','a', 'b', 'ç', 'à', 'Ä', 'c', 'Ç', 'ä'];
const intlCollator_de = new Intl. Collator('de');

console.log('regular sort');
console.log(arrayOfStrings.sort());
console.log('sort using intlCollator');
console.log(arrayOfStrings.sort(intlCollator_de.compare));

```



