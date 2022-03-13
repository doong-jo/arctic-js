# arctic-js

Does the side project or SEO to create a small website that is not important? If so, you do not need to use React, Vue, Angular. **You can make it sufficiently with JavaScript, HTML, and CSS.**

> Use a Sledgehammer to Crack a Nut

## Concept & Meaning of Arctic Words

- The current browser is fast enough in most environments without having a specific framework. In addition, the future will be faster.
- Rendering is not involved and only the component abstraction is written.
- As you can find the purity of calmness and glaciers in the Arctic, I wanted to make it possible to develop web close to a pure browser without a special skill in Arctic-JS.

## Getting Started

### Installation

```bash
npm i arctic-js
```

### Example

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="./src/styles.css" />
  </head>
  <body>
    <div id="root"></div>
    <script src="App.js" type="module"></script>
  </body>
</html>
```

```javascript
// components/Button.js
import { Component } from "arctic-js";

export class Button extends Component {
  constructor(props) {
    super(props);
  }

  addEvent() {
    this.addEventListener("click", this.props.onClick);
    // Attach inner element
    // this.addEventListener('button > *', 'click', () => {
    //   console.log('I'm button's child');
    // });
  }

  render() {
    this.createElement(
      /* html */`
      <button type="button">
        ${this.props.children}
      </button>
      `
    );
  }
}
```

```javascript
// components/MainPage.js
import Arctic, { Component, render } from "arctic-js";
import { Button } from "Button";

export class MainPage extends Component {
  constructor() {
    super();

    this.count = 0;
  }

  increaseCount() {
    this.count++;
  }

  render() {
    this.createElement(
      /* html */`
      <div>
        <p>
          I'm Main page.
        </p>
        <p>
          count: ${count}
        </p>
        ${render(
          new Button({ children: "Click Me", onClick: this.increaseCount })
        )}
      </div>
      `
    );
  }
}
```

```javascript
// App.js
import Arctic from "arctic-js";
import { MainPage } from "MainPage";

Arctic.route({
  "/": render(new MainPage()),
  // ...
});
```

## RoadMap

- [ ] Component
- [ ] Routing (with Hash)
- [ ] Create Arctic App

## Helpful VSC extension

- [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html)
