## Website Performance Optimization portfolio project

To run, you can either navigate to http://lacyjpr.github.io/optimization/, or install the project on your machine.
To do that, either clone the repository using git, or click the download zip button on the right and unzip the file.

To view the optimized page, navigate to dist, then double-click index.html.

I have optimized index.html to achieve at least a 90 PageSpeed score. I've optimized the JavaScript in pizza.html to achieve a frame rate of 60fps when scrolling. I've also reduced the time to resize pizzas in pizza.html to less than 5 ms.

I have included a src directory that includes un-minified code.

The dist directory includes minified code and optimized images.



####Part 1: Optimize PageSpeed Insights score for index.html

##### Optimizations:
* Reduce the size of pizzaria.jpg to 100px width
* Inline css/style.css
* Make google-analytics script async
* Add a media query for print.css
* Use Web Font Loader to load the Google webfont asynchronously
* Use Gulp to:
* Minify CSS
* Uglify JS
* Compress jpg and png files
* Minify HTML

Sources:
https://discussions.udacity.com/t/how-to-optimize-css-and-google-fonts/26997
https://github.com/typekit/webfontloader
https://discussions.udacity.com/t/gulp-and-setting-up-a-gulp-workflow-intermediate/24359


####Part 2: Optimize Frames per Second in pizza.html

##### Optimizations:
* Use requestAnimationFrame for updatePositions
* Move all constants out of the for loop in updatePositions
* Move the Math.sin calculation out for the for loop in updatePositions
* Move var items = document.getElementsByClassName('mover'); to the anonymous function at the bottom of the file to stop updatePositions from re-defining items on every scroll event
* Use window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px'; instead of items...
* Set number of pizzas to 36 in document.addEventListener('DOMContentLoaded', function()
* Replace "querySelector" with getElementById in document.getElementById("movingPizzas1").appendChild(elem);
* Change CSS for .mover: Add transform: translateZ(0); will-change: transform; transform translate3d(0,0,0); and backface-visibility: hidden;


Sources:
https://github.com/Sarika-C/frontend-nanodegree-mobile-portfolio/blob/master/views/js/main.js
https://discussions.udacity.com/t/p4-pizza-scrolling-rasterize-paint/30713/13

####Part 3: Optimize Time to Resize Pizzas in pizza.html

##### Optimizations:
* Made the following changes to changePizzaSizes:
* Move document.document.querySelectorAll(".randomPizzaContainer"); outside the for loop
* Refactor to use a switch to set pizza width in order to avoid Forced Synchronous Layout and avoid use of determineDx to determine new pizza widths
* Change CSS for .randomPizzaContainer: Add transform: translateZ(0); and will-change: transform;

Source:
https://www.udacity.com/course/viewer#!/c-ud860-nd/l-4147498575/e-4154208580/m-4240308553


