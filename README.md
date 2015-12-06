# My Website Optimization Project
## Lesson 4 - Website Optimization

The challenge at hand was to optimize certain portions of an existing website for different metrics.

1. Optimize the index.html page to achive a Page Speed Insights ranking of 90 or better on both mobile and desktop.
2. Optimize the views/pizza.html to achieve 60FPS or better on the scroll event.

### Part 1: Optimize PageSpeed insights score for index.html

First part for me was to optimize the CSS, first i added the media attribute to the print.css stylesheet and set the value to "Print". then i minified and inlined the necessary CSS into the head of the document. 

my next step was to get the images down to a reasonable size. as for the JS file i minimized the code and added async attribute to the script tags to allow the page to load and run when ready.

### Part 2: Pizza Optimization

The main optimization to begin with here, which was discussed in class, was to remove the added calculations and intracacy of the determineDx function since it wasn't necessary when the sizeSwitcher function could merely return a value to be used as a percentage. A much more elegant and significantly quicker solution!

Next up was to move the selection of the pizza containers outside of the for loop, so the js engine didn't need to parse the document each time through the loop. An additional small optimization was to use the length method only once on the returned DOM element array and store it in a variable to use within the for loop. Again, the assumption being the js interpreter wouldn't need to look it up each time. 

In the quest for 60FPS on scroll for these sliding pizzas of doom was reduce the number of pizzas being created and packted in the first place. The initial loop created 200 pizzas... Considering there are 8 columns mandated at a height of 256px.

As we learned in class, it is important to query the state of the DOM outside of the loop then batch process as efficiently as possible, so it was time to look at the loop. The next obivous optimization was to move the phase calculation out of the loop since it had a layout triggering scrollTop within it. That could be queried once outside the loop. Two small additional improvements were to select elements using getElementById and to use the length method on it once and store in a var; as explained above.

Next, in what I thought was a very interesting approach was to declare an array and store the phase calculation results in it, so that they could be referenced rather than continually calculated within the loop. When inspected, those numbers repeat, so it isn't necessary to continue to replicate them. Very cool and decent performance gain.

The next optimization, and very large performance gain, was when I added "will-change: transform" to the pizza element's "mover" class declaration in the stylesheet. That gave an enormous boost to performance and pretty much put me mostly under 60FPS. As an additional optimization in concert with the preceeding, backface-visibility: hidden was added to boost performance in browsers which support hardware acceleration.


