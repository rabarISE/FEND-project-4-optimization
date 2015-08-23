## Website Performance Optimization portfolio project

Fourth project from the Front-End Web Developer Nanodegree in <a href="http://www.udacity.com" target="_blank">Udacity</a>:<br>
optimized index.html to achieve a score of 90 in PageSpeed, and optimized main.js to achieve 60 fps in pizza.html.

####Part 1: Optimize PageSpeed Insights 

- Minified CSS and JS files with Grunt, in a folder called /dist/
- Optimized images (size and compression) with Grunt, in a folder called /dist/
- Eliminated render-blocking JavaScript and CSS in above-the-fold content:
  - style.css inlined in index.html.
  - print.css with the media=print tag.
  - Put the Google Analytics script to the footer of the page.
  - Loaded asyncronoulsy the Google Fonts with a script in the footer.
- Created web.config file to put an expiry date to static resources (css, images and js).

####Part 2: Optimize Frames per Second 

- Apply optimizations for PageSpeed: minified css and js, optimized images, inlined css, configured the viewport.
- Optimizations made in views/js/main.js:
  - Put 'use strict' in each function to make the code more secure.
  - Lines 416: changed the querySelector for the getElementById, to make it faster.
  - Lines 440-461: deleted the function determineDx, since we change the pizza size inside the changePizzaSizes. Also optimized the for loop to put the new width in each .randomPizzaContainer and used getElementsByClassName instead of querySelectorAll.
  - Line 474: created variable outside of loop, using getElementById.
  - Line 510: used getElementsByClassName for .mover instead of document.querySelectorAll.
  - Line 513: the document.body.scrollTop is a constant number, so we don't want to create the varible each time inside the for loop, moved it outside in a new variable.
  - Lines 517-519: phase only have 5 different values, because it changes for each (i % 5). So we create an array where we put the 5 values. We also put the phase variable outside the for loop, to separate the manipulation of the DOM from the methods that query the state.
  - Lines 522-524: optimized the for loop function with the new outside variables created, and the items.length outside the loop in a variable.
  - Line 544: move the variable elem outside the loop.
  - Line 545: changed the querySelector for the getElementById to make it faster, and put outside the loop
  - Lines 549-551: calculated the total number of pizzas we need for the screen we are using.
  - Line 554: create the exact number of pizzas onscreen.
  - Lines 557-559: put the optimized image of the pizza with its real size.
- Optimizations in CSS: put will-change:transform;transform:translateZ(0);backface-visibility:hidden; in the .mover class. This way we will create diferent layouts for each pizza and the main layout will not be repainted every time we create a pizza.

-----------------------------------------------

### Folders

In the /original/ folder, there is the original code provided by Udacity.

In the /test/ folder, there is the working code.

In the /dist/ folder, there is the final production code with the minified css/js and optimized images. 

-----------------------------------------------

### To run the application

1. Download the /dist/ folder in your computer.
1. To inspect the site on your phone, you can run a local server:

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080.
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely:

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights and Chrome DevTools!

Or you can use the project uploaded in this link: <a href="http://irene.marin.cat/udacity/project4/dist/index.html" target="_blank">Project 4</a>

-----------------------------------------------

### Udacity's instructions

You will optimize a provided website with a number of optimization- and performance-related issues so that it achieves a target PageSpeed score and runs at 60 frames per second.

1. Review our course on Website Performance Optimization using Google PageSpeed.
2. Download the required project assets.
3. Use Chrome Developer Tools to review the current state of various pages within the application and identify areas for improvement.
4. Review the code powering the website and identify areas where you believe modifications are warranted.
5. Iteratively make changes and test those changes using the tools available to you to determine if they are a performance gain or loss.
