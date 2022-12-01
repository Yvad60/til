## 23rd November 2022

### `Element.innerHTML`, `Element.outerHTML`, `Element.textContent`, `Element.innerText`

- **Element.innerHTML** : Property used to get or set a string containing the html inside the current element. the text and html tags included in the element <br>
  `return String` <br>
  Usage

```js
element.innerHTML; // return the html inside the element
element.innerHTML = "Hello world"; // updates the html inside the element to a new value
```

- **Element.outerHTML**: Property used to get or ser a string containing the html element fully as it is including it's start and end tag and it's attributes <br>
  `return String` <br>
  Usage

```js
element.outerHTML; // return the element itself and the html inside
element.outerHTML = "Hello world"; // replaces the whole element with the new html content
```

- **Element.textContent**: Property used to get or set the text (only text) of an element and all it's children <br>
  `return string` note: `textContent` returns everything including spacing and CSS hidden text <br>
  Usage

```js
element.textContent; // return the text contained in the element
element.textContent = "Hello world"; // changes the whole element content to the new text
```

- **Element.innerText**: Property used to get or set the text (only text) of an element and all it's children <br>
  `return string` note: `innerText` will not return spacing and CSS hidden text <br>

```js
element.innerText; // return the text contained in the element
element.innerText = "Hello world"; // changes the whole element content to the new text
```

## 30th November 2022

### `HTML canvas.rect() method`

A method of the canvas element used to dynamically draw rectangles on the canvas. it will require to have a 2D canvas context

`Syntax`: `rect(x, y, width, height)`

`x`: is the point for drawing the rectangle on the x axis
`y`: the point for drawinf the rectangle on the y axis
`width`: the width of the rectangle that will be drawn
`height`: The height of the reactangle that will be drawn
