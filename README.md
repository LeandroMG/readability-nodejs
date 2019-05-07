# readability-nodejs

Port of [@mozilla/readability.js](https://github.com/mozilla/readability) to work with Node.

Added new features to get images from processed article. Work in progress.

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

- `title`: article title
- `byline`: author metadata
- `dir`: content direction
- `content`: HTML string of processed article content
- `textContent`: String of processed article content
- `length`: length of article, in characters
- `excerpt`: article description, or short excerpt from content
- `siteName`: Site name
- `image`: main image of processed article content
- `images`: Array with all images of processed article content. Use it only if image is null.

### Optional

Readability's `parse()` works by modifying the DOM. This removes some elements in the web page. You could avoid this by passing the clone of the `document` object while creating a `Readability` object.

```javascript
var documentClone = document.cloneNode(true);
var article = new Readability(documentClone).parse();
```

## Code porting

Up to date with Readability.js as of [29 Mar 2019](https://github.com/mozilla/readability/commit/26379fe62ebe24a3476a6ce705c3c27c024740dd).

## Warnings

- `page`: Was removed as a class to preserve. You can recover it passing as argument with `classesToPreserve` option as following:

```javascript
var article = new Readability(document, {
  'classesToPreserve': 'page'
}).parse();
```

## License

Copyright (c) 2010 Arc90 Inc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
