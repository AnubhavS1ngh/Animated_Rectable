Moving Rectangle Project
This project showcases a moving rectangle that follows the horizontal movement of the mouse cursor. The animation is implemented using GSAP (GreenSock Animation Platform).

Files
index.html: HTML file containing the structure of the webpage.
style.css: CSS file for styling the HTML elements.
script.js: JavaScript file for adding functionality to the webpage.
GSAP Library: External library for animation.
Usage
Clone the repository to your local machine:

bash
Copy code
git clone <repository-url>
Open index.html in your web browser to view the moving rectangle animation.

Structure
The HTML file (index.html) includes the basic structure of the webpage, with a container div (#rect) representing the moving rectangle.

The CSS file (style.css) contains styling rules for the rectangle, setting its position, size, border, and background color.

The JavaScript file (script.js) utilizes the GSAP library to animate the rectangle's left position based on the horizontal movement of the mouse cursor.

The GSAP library is included via a CDN link in the HTML file.

html
Copy code
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js" integrity="sha512-7eHRwcbYkK4d9g/6tD/mhkf++eoTHwpNM9woBxtPUBWm67zeAfFC+HrdoE2GanKeocly/VxeLvIqwvCdk7qScg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
Mouse Move Event and Animation
The JavaScript file (script.js) listens for the mousemove event on the window, capturing the details of the event. It then calculates the new left position for the rectangle using the GSAP utility function gsap.utils.mapRange.

javascript
Copy code
window.addEventListener("mousemove", function(details){
  var rect = document.querySelector("#rect");

  var xval = gsap.utils.mapRange(
    0, 
    window.innerWidth, 
    100 + (rect.getBoundingClientRect().width / 2), 
    window.innerWidth - (100 + rect.getBoundingClientRect().width / 2), 
    details.clientX
  );

  gsap.to("#rect", {
    left: xval,
    ease: Power4.easein,
  });
});
