# My Website Optimization Project
## Lesson 4 - Udacity FEND

The challenge at hand was to optimize certain portions of an existing website for different metrics.

1. Optimize the index.html page to achive a Page Speed Insights ranking of 90 or better on both mobile and desktop.
2. Optimize the slider widget on views/pizza.html to resize in < 5ms as indicated in the console.
3. Optimize the views/pizza.html to achieve 60FPS or better on the scroll event.

### Part 1: Optimize index.html

First part for me was to optimize the CSS, first i added the media attribute to the print.css stylesheet and set the value to "Print". then i minified and inlined the necessary CSS into the head of the document. 

my next step was to get the images down to a reasonable size. as for the JS file i minimized the code and added async attribute to the script tags to allow the page to load and run when ready.