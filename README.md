# Website-Performance-Optimization
The objective of this project was to optimize the performance of a mobile web app by diagnosing render blocking issues and make it load faster. Another issue that the project had, was the slow screen scroll speed for *'Cam's Pizzeria'* and larger times for pizza resize function.

## Installation
### Dependencies
- [Fenix web server] (http://fenixwebserver.com/)
### To run the application follow the following steps:
1. Download the GitHub zip file or clone the repository onto your local machine.
2. Use Fenix web server to create an ad-hoc static web server.
3. Select the directory in Fenix where index.html is placed.
4. Hit run!

## Tools and Concepts
- Website optimization
  - Critical Rendering Path (CRP)
  - Optimizing CRP
   1. diagnosing issues causing render blocking
   2. measuring page performance
   3. improve CRP to improve user experience
  - App Life Cycle: RAIL (Response, Animate, Idle, Load)/ LIAR (Load, Idle, Animate, Response)
  - Using Chrome Dev tools to identify jank and removing it
  - Optimize JS animations and use web workers to improve performance
  - Forced Synchronous Layouts (FSL)
  
# Task 1: Critical Rendering Path optimization (CRP) for index.html
  Improve PageSpeed score for index.html to at least 90 for Mobile and Desktop.
## Optimizations Performed
  - Images were compressed using gulp.
  - The image sizes were explicitly written to speed up page rendering.
  - Used Web Font Loader to load the Google web fonts asynchronously.
  - Added async to the Google analytics script so it doesn't block rendering.
  - Scripts were moved to the bottom and placed before closing </body> tag.
  - Used a media query on the *print.css*, to request the CSS file only if screen = print.
  - Minified HTML, CSS and JS.
## Result
  - PageSpeed score for index.html was increased to 99 for Desktop.
  
# Task 2: Frame Rate optimizations made for views/js/main.js
  Make views/pizza.html render with a consistent frame-rate at 60fps when scrolling.
## Optimizations Performed
  - Changed querySelector to getElementById.
  - Changed querySelectorAll to getElementsByClassName.
  - Since there are only 5 unique phases of the moving pizzas, phase calculation (Math.sin) was moved into its own for loop that appends each phase to an array called phases, rather than declaring and setting the phase variable each time.
  - *'items'* was declared on the top in global scope, and then assigned a value only once on page load.
  - Changed the number of pizzas generated on page load, to be based on the browser window resolution.
## Result
  - No jank present during scrolling, meaning frame rate is above 60fps.

# Task 3: Computational Efficiency
  Time to resize pizzas is less than 5 ms using the pizza size slider on the views/pizza.html page.
## Optimizations Performed
  - Deleted determineDx function, and moved sizeSwitcher function and, windWdth variable outside the for loop as it not necessary to recalculate them on each loop.
  - Changed querySelector to getElementById.
  - Changed querySelectorAll to getElementsByClassName.
## Result
  - After the optimization, time to resize pizza is under 3ms.
