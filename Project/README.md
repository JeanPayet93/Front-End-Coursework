Manchester Uited Fan Page - Read Me File

In this file I will go through my main design choices and why I chose to use them and how I got them to work.

*Page Design and Navigability*

I chose to make a One Page application as this was a design choice I felt would be a lot easier to manage as all my content will be in seperate <div> tags
and all my content will be on one single page which makes things easier for me to find and manage.

The way I managed to work around hiding and displaying the content I wanted and certain 'click' events was by using javascript code. The first code I came across
while doing research on how to do this was:

<script>
    function show(shown, hidden) {
      document.getElementById(shown).style.display='block';
      document.getElementById(hidden).style.display='none';
      return false;
    }
</script>

I used the above code to switch between two pages which are actually just two sepearte <div> tags with the IDs Page1 and Page2. Page1 was the welcome to the Website
page with an "Enter Website" button that would then display Page2. Page2 was the <div> which contains all the content displayed on the website once "entering".

This was a stable and good function, and I wanted to use it for further hiding and displaying of content, for example showing the extended information of a particular
News item. However, the more variables I added, this script became unstable and stopped functiong properly so I decided to do more research to find a function that was similar
and could be replicated with different variables. After much research I found:

<script>
      function myFunction() {
        var x = document.getElementById('News1');
        var page = document.getElementById('Page2');
        var nav = document.getElementById('nav1');
        if (x.style.display === 'none') {
            x.style.display = 'block'
            page.style.display = 'none'
            nav.style.display = 'none';
        } else {
            x.style.display = 'none'
            page.style.display = 'block'
            nav.style.display = 'block';
        }
    }
</script>

This javascript function allowed me to hide all the contents of Page2 and show seperate content, all contained within their seperate <div>, and it allowed me to return to 
Page2 without causing errors. For example I use this for News items, when a use clicks on the Read More button underneathe a particular News Item, this function hides 
all of Page2 and displays the content of the <div> with the associated ID stated in the function, in the case of the function above that <div> would have and ID of News1.
I replicated this function several times to create the illusion of page navigation on my website.


*Gallery Slideshow*

Initially I wanted a simple flimstrip javascript function to show my images in a Gallery format, but I came across the below code for creating an indepth slideshow which has
multiple styles and functionality I could change:

<script type="text/javascript">
        $(function(){
        $('#myGallery').galleryView({
        transition_speed: 2000, 		//INT - duration of panel/frame transition (in milliseconds)
        transition_interval: 4000, 		//INT - delay between panel/frame transitions (in milliseconds)
        easing: 'swing', 				//STRING - easing method to use for animations (jQuery provides 'swing' or 'linear', more available with jQuery UI or Easing plugin)
        show_panels: true, 				//BOOLEAN - flag to show or hide panel portion of gallery
        show_panel_nav: false, 			//BOOLEAN - flag to show or hide panel navigation buttons
        enable_overlays: true, 			//BOOLEAN - flag to show or hide panel overlays
        
        panel_width: 900, 				//INT - width of gallery panel (in pixels)
        panel_height: 500, 				//INT - height of gallery panel (in pixels)
        panel_animation: 'crossfade', 		//STRING - animation method for panel transitions (crossfade,fade,slide,none)
        panel_scale: 'fit', 			//STRING - cropping option for panel images (crop = scale image and fit to aspect ratio determined by panel_width and panel_height, fit = scale image and preserve original aspect ratio)
        overlay_position: 'bottom', 	//STRING - position of panel overlay (bottom, top)
        pan_images: true,				//BOOLEAN - flag to allow user to grab/drag oversized images within gallery
        pan_style: 'drag',				//STRING - panning method (drag = user clicks and drags image to pan, track = image automatically pans based on mouse position
        pan_smoothness: 15,				//INT - determines smoothness of tracking pan animation (higher number = smoother)
        start_frame: 1, 				//INT - index of panel/frame to show first when gallery loads
        show_filmstrip: true,
        ........
</script>

This extensive slideshow works by using javascript and allowed me to create a functioning slideshow that did not clash with the <styles> of my website or other javascript
functions.
I use this code, with sepearte IDs of course, twice to create two slideshows.
This code also allowed me to add text and display that text in a format that did not disrupt the slideshow and skew the images in anyway.

*PopUps and Modals*

Within my Fixtures and Results table, I wanted to implement a function that would allow users to change the timezone of upcomming match times and I managed to get it working 
within a <modal> but when I wanted to replicate this code to work in other rows and other modals, the javascript just would not work and I could not get it to function on
multiple occasions. I left one <modal> function to show that I did get the TimeZone changer to work and display a new time.
This javascript code can be found in the time.js file found in the scripts section of my project.


*Google Maps*

I managed to implement Google Maps functionality into my website, which would show the location of Manchester United's home stadium. Initially I wanted to be able to display
the different locations the team has been too with arrows drawn across the Map but after much research I could not find out how to do it. Here is the code for the Map:

<div id="map"></div>
                    <script>
                    function initMap() {
                        var uluru = {lat: 53.463066, lng: -2.291422};
                        var map = new google.maps.Map(document.getElementById('map'), {
                        zoom: 15,
                        center: uluru
                        });
                        var marker = new google.maps.Marker({
                        position: uluru,
                        map: map
                        });
                    }
                    </script>
                    <script async defer
                        src="https://maps.googleapis.com/maps/api/js?key=AIzaSyA6DDSPso0LksDhuV3a-mN00BjTXRHx9mU&callback=initMap">
</script> 

The code does work and display a map, but I found that in some browsers it would not render unless the user right-clicks and inspects element (Internet Explore and
FireFox). The Map works as it should in Opera.

*Styles*

I implement a lot of styles within my website, a lot for individual elements. One I would like to point out is the .navbar style. This css style allowed me to maintain my navbar
in a fixed position so that even when users scrolled through the website the navbar would always be fixed. I also changed the opacity value so that when not hovered over
the navbar would appear almost transparent. Here is the code:

.navbar a {
    
    width: 100%;
    display: block;
    background-color: silver;
    text-decoration: none;
    color: #000;
    border-bottom: 4px solid darkred;
    text-decoration: none;
    opacity: 0.3;
    background-color: silver;
}

.navbar a:hover {
    opacity: 1.0;
    background-color: darkred;
    transition: all 0.7s;
    border-top-right-radius: 40%;
    border-top-left-radius: 40%;
    border-bottom-right-radius: 40%;
    border-bottom-left-radius: 40%;
    font: bold;
}
