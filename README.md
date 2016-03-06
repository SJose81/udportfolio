### Website Performance Optimization portfolio project


##Page speed and onload time:
The public url ngrogk provided for the project is: http://e09573c6.ngrok.io/
-> On analyzing the site with page speed insight (https://developers.google.com/speed/pagespeed/insights/), the fix suggestion was to optimze the images. I used the Compressor.io image compression software to compress the pizzaria image. The next run gave better numbers page speed insight. But since the image was on my local machine, the score was still low. Hosted the compressed image on a remote server 'http://s12.postimg.org':
 * 63/100 on Mobile and 74/100 on Desktop.

-> To increase the page speed score, I further compressed the pizzaria image and hostet it on postimg.org.
-> Minified the style.css file (from https://cssminifier.com). Used print media query and deferred inline javascript to eliminate render blocking above the fold content. The page speed score increased to 73/100 on Mobile and 88/100 on Desktop  

-> The google fonts link still seemed to be the bottleneck, so I commented out the link. The html elements now refer to the font style provided in style.min.css. This increased the page speed score to: 
* 88/100 on Mobile and 93/100 on Desktop.

-> As per the comments provided in the review, I got the critical path css using the link: https://jonassebastianohlsson.com/criticalpathcssgenerator/. As per suggestions provided in the link. I have minified and inlined the critical path css in index.html. For the rest of the css which is not critical for page rendering, I have moved it to the end of the html script, just before the closing body tag.
-> The page speed score has now increased: 95/100 on Mobile and 95/100 on Desktop.

-> On loading the page on the browser, the load time was as follows: DCL: 139ms, onload: 1182ms. THis was because the pizzaria image was on my local machine. On hosting image from remote machine, the load time is now as follows: DCL: 156ms, onload: 443ms

-> After code optimization in main.js (modification details given in the next section) and loading the pizza.html page, the chrome console displays: 
 * 'Time to generate pizzas on load: 17ms' 
 * 'Average time to generate last 10 frames: 3.718000000000461ms'
 
-> After code optimizations, time to resize pizza is:
 * Time to resize pizzas: 4.695000000298023ms 


##Code modifications:
-> Modifiactions made in index.html:
* 1) Removed the google fonts css link as it was lowering the page speed score and also giving a console 404 error
* 2) Added print media query for print.css stylesheet link to reduce render blocking
* 3) Used 'Async' attribute to external scripts to optimize javascript
* 4) Used 'defer' in inline google analytics script to optimize and execute the script only once the page has loaded.
* 5) Used compressed pizzaria image

-> Two Code fixes made in main.js to eleminate Jank:
* 1) Updated the changePizzaSizes(size) function to move DeterminDX function out of the for loop. The size is now calculated using one of the pizza elements current width.  Since all the pizza elements size is the same, moving offsetwidth out of for loop eliminates Jank.
* 2) Updated the updatePositions() function, to move document.body.scrollTop value outside the for loop. Used the tips provided in 
'https://www.igvita.com/slides/2012/devtools-tips-and-tricks/jank-demo.html', used the same logic that is provided in non-heavy scroll.
* 3) Used compressed images, JSHint and jsbeautifier

-> Modifiactions made in project-2048.html, project-mobile.html and project-webperf.html:
* 1) Added print media query for print.css stylesheet link to reduce render blocking
* 2) Used 'Async' attribute to external scripts to optimize javascript
* 3) Used 'defer' in inline google analytics script to optimize and execute the script only once the page has loaded.






