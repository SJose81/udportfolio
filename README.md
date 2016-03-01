### Website Performance Optimization portfolio project

##Page speed and onload time:
The public url ngrogk provided for the project is: http://24a4a89b.ngrok.io
-> On analyzing the site, the should fix suggestion was to optimze the images. I used the Compressor.io image compression software to compress the pizzaria image. The next run gave better numbers page speed insight:
 * 55/100 on Mobile and 63/100 on Desktop.
-> On loading the page on the browser, the load time is as follows: DCL: 139ms, onload: 1182ms. THis seems to be due to the pizzaria image which is still taking time to load. If like other images, it is moved to the server then the onload time should decrease.
-> After code optimization in main.js and loading the pizza.html page, the chrome console displays 
 * 'Time to generate pizzas on load: 17ms' 
 * 'Average time to generate last 10 frames: 3.718000000000461ms'

##Code modifications:
-> Modifiactions made in index.html:
* 1) Measured and provided analysis on the impact of web fond on speed. The link provided in the code gives 404, so replaced it with the correct link.
* 2) Added print media query for print.css stylesheet link to reduce render blocking
* 3) Used 'Async' attribute to external scripts to optimize javascript
* 4) Used 'defer' in inline google analytics script to optimize and execute the script only once the page has loaded.
* 5) Used compressed pizzaria image

-> Two Code fixes made in main.js to eleminate Jank:
* 1) Updated the changePizzaSizes(size) function to remove the use of element offsetwidth within the for loop as this causes the browser to recalulate the layout.
* 2) Updated the updatePositions() function, to move document.body.scrollTop value outside the for loop and using the cached value instead.
* 3) Used compressed images

-> Modifiactions made in project-2048.html, project-mobile.html and project-webperf.html:
* 1) Added print media query for print.css stylesheet link to reduce render blocking
* 2) Used 'Async' attribute to external scripts to optimize javascript
* 3) Used 'defer' in inline google analytics script to optimize and execute the script only once the page has loaded.

-> Issues found:
* 1) On reviewing the timeline in Chrome dev tools for index.html, I found that Jank still occurs due to analytics.js script
* 2) Inspite of the code fixes in updatePositions() function, jank still occurs due to the use of document.body.scrollTop value in the method.




