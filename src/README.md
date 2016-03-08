
## Website Performance Optimization portfolio project

Challenge was to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible.

### How to run the application

1.  Check out the repository or Download the project.

1.  Directly run the index.html file on browser.

1.  To run the project on local server:
    
     a.  Open command line window.

     b.  cd /path/to/your-project-folder > python -m SimpleHTTPServer 8000   

     c.  Open a browser and visit localhost:8000

1.  There are various pages links on the page. Click on the link to visit separate pages.

1.  There is last link "Cam's Pizzeria", which was initially not giving 60 frames per second on scrolling. Changes have been made in views/js/main.js file and now pizza.html page is optimized to give 60fps.

1.   Pizzeria page can also be opened by browsing views/pizza.html 

###  Part 1: Changes done to Optimize PageSpeed Insights score for index.html 

1.  Moved scripts to bottom of the <body>

1.  Added async parameters to scripts.

1.  Added media="print" for print.css and made style.css as inline in index.html to remove CSS rendering blocking.

1.  Compressed images losslessly and lossy methods.

1.  Resized big images.

1. Removed extra comments and whitespaces.  

### Part2: Changes done in views/js/main.js to Optimize Frames per Second in pizza.html.

1.  When DOMContentLoaded event is performed, sliding pizzas are generated, I have reduced the pizza numbers to 50, initially it was 200. This does not affect display on screen but performance is improved.

1.  Replaced the querySelectorAll with more efficient getElementsByClassName for selecting elements by class name.

1.  When Scroll event is performed, updatePositions function is called which moves the sliding pizzas based on scroll position. There are two changes:

    *  Moved the code for phase calculation into separate loop. Earlier it was within the main for loop which was doing layout changes. Recalculation of style and layout were happening more frequently which was causing performance issues. Anyway phase calculation is giving five different values then and now irrespective of how many loops are performed.

    *  Replaced the element.style.left with element.style.transform, because this function only does composite changes whereas .left performs layout, paint and composite, So transform saves time.

1.  changeSliderLabel function is called whenever pizza size is changed on slider and pizza width is changed. Previously there was separate function determinDx  which was returning new width as per pizza size. I have removed this function and included small code in changeSliderLabel function itself. Now it is directly calculating % size and adding it to pizza width. 

