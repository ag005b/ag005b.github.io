## Website Performance Optimization portfolio project

I was tasked with optimizing this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques I picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).



To get started, check out the repository and inspect the code.


#### Part 1: Optimize PageSpeed Insights score for index.html

Website Location: https://ag005b.github.io/

PageSpeed Insights Scores:
1- Desktop: 96
2- Mobile: 95

Changes Made to Attain these Scores:
Index.html
  WITHIN THE HEAD TAG:
     Added:
      - meta tag for caching capability
      - media attribute to link tage for print.css      
      - minified and inline critical css to reduce # of requests
     
     Removed:
      - link tag for style.css to reduce # of requests
      - call to google api for font
      - all non manipulating js - to unblock DOM construction

   WITHIN THE BODY TAG:
     Added:
      - Compressed two(2) images [pizzeria.jpg and profilepic.jpg] 

   WITHIN THE HTML TAG:
     Added:
      - moved script tags from head tag; placed them after body tag therefore would not block DOM construction
      - moved call to google api for font from head tag; used javascript to retrieve font; utilized the load function
      - added async attribute to non manipulating js      - 


#### Part 2: Optimize Frames per Second in pizza.html

Website Location: https://ag005b.github.io/views/pizza.html

Changes Made:
pizza.html
 - Compressed two(2) images [pizzeria.jpg and pizza.png]

main.js
 - Update function changeSliderLabel() and determineDx ()
     To use documnet.getElementById instead of document.querySelector because it's more efficient accessing the DOM
 - Update changePizzaSizes() to help avoid forced synchronous layout bottle necking	  
	 To use documnet.getElementsByClassName & is more efficient accessing the DOM instead of document.querySelector
	 Moved reading layout properties outside of the loop and  batch update the styling afterwards
 - Update function updatePositions()
     To use document.getElementsByClassName('mover') is more efficient accessing the DOM instead of instead of querySelectorAll(.'mover')
     Moved all code reading layout property 'scrollTop'  outside of the loop and batch update the styling afterwards
     Reduced the number of pizza images appended to 25

     
#### Resubmission
 Updates to:
 
 images:
  - Update and renamed the compressed pizzeria jpg to be used on index.html and optimized/compressed pizzeria jpg for the pizza.html page
  
 Index.htmml
  - Update src attribute with the pizzeria jpeg with the required compressed dimensions
  
 main.js
  - Update conditional statement in function changePizzaSizes() to make length a localized variable rather than accessing the array 
    property each iteration
  - Declare the elem variable in the initialisation of the for-loop
  - Move DOM call for movingPizzas1 outside the for loop
  - Use the height property to dynamically calculate number of pizzas to fill screen