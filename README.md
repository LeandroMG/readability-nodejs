# readability-nodejs

Fork of [@mozilla/readability.js](https://github.com/mozilla/readability) to work with Node.

This repository will only be active as long as the official Readability.js does not be published as NPM package.

## Installation
- `npm i readability-nodejs`

## Usage

To parse a document, you must create a new `Readability` object from a DOM document object, and then call `parse()`. Here's an example:

```javascript
const readability = require('readability-nodejs')

let reader = new readability.Readability(dom.window.document);
let article = reader.parse();
```

This `article` object will contain the following properties:

* `title`: article title
* `content`: HTML string of processed article content
* `length`: length of article, in characters
* `excerpt`: article description, or short excerpt from content
* `byline`: author metadata
* `dir`: content direction

If you're using Readability on the web, you will likely be able to use a `document` reference from elsewhere (e.g. fetched via XMLHttpRequest, in a same-origin `<iframe>` you have access to, etc.).

### Optional

Readability's `parse()` works by modifying the DOM. This removes some elements in the web page. You could avoid this by passing the clone of the `document` object while creating a `Readability` object.

```
var documentClone = document.cloneNode(true); 
var article = new Readability(uri, documentClone).parse();
```
