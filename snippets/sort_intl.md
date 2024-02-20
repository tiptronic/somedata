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
const arrayOfStrings = ['a', 'b', 'ø', ,'ö', 'o','A', 'B','C', 'ç', 'à', 'Ä', 'c', 'Ç', 'ä', 'Ä'];
const intlCollator_de = new Intl. Collator('de');

const arrayOfTexts = [
    {
        text: 'alphabet'
    },
    {
        text: 'busy'
    },
    {
        text: 'øde'
    },
    {
        text: 'öde'
    },
     {
        text: 'ode'
    },
    {
        text: 'Alphabet'
    },
    {
        text: 'Berta'
    },
    {
        text: 'Cäsar'
    },
    {
        text: 'çedilla'
    },
    {
        text: 'àla'
    },
    {
        text: 'Äther'
    },
    {
        text: 'circa'
    },
    {
        text: 'ÇedillaUpper'
    },
    {
        text: 'ästhetisch'
    },
    {
        text: 'Ästhetisch'
    }
];

// Note: the regular sort is not language aware
// `intlCollator` is language aware
// `localeCompare` is language aware
// `localeCompare` with caseFirst is language aware
// we first copy the source-array to avoid changing the original array
// e.g. [...arrayOfTexts].sort(...)

console.log('regular sort');
console.log([...arrayOfStrings].sort());
console.log('sort using intlCollator');
console.log([...arrayOfStrings].sort(intlCollator_de.compare));
console.log('sort text using intlCollator');
console.log([...arrayOfTexts].sort((a, b) => intlCollator_de.compare(a.text, b.text)));
console.log('sort text using localeCompare');
console.log([...arrayOfTexts].sort((a,b) => a.text.localeCompare(b.text, 'de', { sensitivity: "base" })));
console.log('sort text using localeCompare upperCase first');
console.log([...arrayOfTexts].sort((a,b) => a.text.localeCompare(b.text, 'de', { caseFirst: 'upper' })));
console.log('sort first character of text using localeCompare upperCase first');
console.log([...arrayOfTexts].sort((a,b) => a.text[0].localeCompare(b.text[0], 'de', { caseFirst: 'upper' })));


```



