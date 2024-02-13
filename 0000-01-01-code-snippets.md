---
title: Code Snippets
path: /code-snippets
date: 2061-01-01
summary: code-snippets to remember
categories: [Development]
tags: ["development", "javascript"]
image: images/code-snippets.jpg
color: yellow
---

## reduce colors using canvas

Reduce colors or create greyscale images

```javascript
const imageData = ctx.getImageData(0, 0, width, height);
  const data = imageData.data;

  for (let i = 0, len = data.length; i < len; i += 4) {
    const avg = (data[i] + data[i + 1] + data[i + 2]) / 3;

    data[i]     = avg; // red
    data[i + 1] = avg; // green
    data[i + 2] = avg; // blue
  }

  ctx.putImageData(imageData, 0, 0);
}, false);
```

## Blobs

### create blob from json

```javascript
const data = {
  name: "Glad Chinda",
  country: "Nigeria",
  role: "Web Developer"
};

// SOURCE 1:
// Creating a blob object from non-blob data using the Blob constructor
const blob = new Blob([JSON.stringify(data)], { type: "application/json" });
```

## create blob from text

```javascript
const paragraphs = ["First paragraph.\r\n", "Second paragraph.\r\n", "Third paragraph."];
const blob = new Blob(paragraphs, { type: "text/plain" });

// SOURCE 2:
// Creating a new blob by slicing part of an already existing blob object
const slicedBlob = blob.slice(0, 100);
```

### blob from http-query

```javascript
// Generating a blob object from a Web API like the Fetch API
// Notice that Response.blob() returns a promise that is fulfilled with a blob object
fetch("https://picsum.photos/id/6/100")
  .then(response => response.blob())
  .then(blob => {
    // use blob here...
  });
```
