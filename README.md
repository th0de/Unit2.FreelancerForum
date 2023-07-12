# Guided Practice - Shapes

This website is an example of how JavaScript can be used to manipulate the DOM. Every second, a new shape is randomly generated and added to the page.

For this guided practice, you will be implementing new features by modifying `index.html` and `index.js`. You will not need to make any changes to `index.css`, but you should take a look at it to see the class names that will be applied.

## Prompts

The answers can be viewed directly below the respective prompt. The `solution` branch contains the final code.

1. Currently the shapes can only be red, green, or blue. Update the code so that the shapes can also be orange, yellow, or purple.
   <details>
   <summary>Show Answer</summary>

   ```js
   const colors = ["red", "green", "blue", "orange", "yellow", "purple"];
   ```

   </details>

1. The website will continue to generate shapes forever. Update `addShape` to stop the interval after the max number of shapes has been reached.
   <details>
   <summary>Show Answer</summary>

   ```js
   function addShape() {
     // ...
     if (shapes.length >= maxShapes) {
       clearInterval(addShapeIntervalId);
     }
   }
   ```

   </details>

1. Only small shapes are being generated right now, but we have support for other sizes as well! Update `addShape` so that the new shape will be a random size.
   <details>
   <summary>Show Answer</summary>

   ```js
   function addShape() {
     // ...
     const size = sizes[Math.floor(Math.random() * sizes.length)];
     shapes.push({ color, size });
   }
   ```

   </details>

1. Add a new list in the HTML for circles, and update the JS so that circles are _also_ generated. The website should now generate both a square and a circle every second. The circles do not count toward the max number of shapes.

     <details>
     <summary>Show Answer</summary>

   ```html
   <ul id="circles"></ul>
   ```

   ```js
   function render() {
     // ...
     const circles = document.querySelector("#circles");
     const circleElements = shapes.map((shape) => {
       const element = document.createElement("li");
       element.classList.add("circle", shape.color, shape.size);
       return element;
     });
     circles.replaceChildren(...circleElements);
   }
   ```

     </details>

## Extensions

If you're done early, try to implement one or more of the following features:

- Circles now count toward the max number of shapes.
- Add support for an extra large size of shapes.
- Add an announcement to the page when the max number of shapes has been reached.
- Create a counter on the page that shows how many shapes have been generated so far.
  - The [textContent property](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent) will be useful here!
