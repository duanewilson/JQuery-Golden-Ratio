# JQuery-Golden-Ratio
================

Calculate a pleasing layout based on the "Golden Mean" using Bootstrap 4 + JQuery

#Demo:

  * https://duanewilson.github.io

##Requires:

  * JQuery (https://jquery.com)
  * //code.jquery.com/jquery-3.2.1.slim.min.js
  
##License:

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">JQuery Golden Ratio</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://helloduane.com/" property="cc:attributionName" rel="cc:attributionURL">HelloDuane</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
  

##Code

###CSS CLASS
```css
/* Golden Ratio Basic Style
-------------------------------------------------- */
#phi { width:100%; }
.phi-right, .phi-left { padding:20px 20px; }
.phi-right { background-color:#99276f; }
.phi-left  { background-color:#eb4f50; }
		
/* 
 * Setup for a horizontal orientation on large screens, 
   remove the media query or change float:left to display:block
   to stack the layout in portrait orientation
   ************************** */
@media (max-width:768px) {
  .phi-right { display: block; }
  .phi-left  { display: block; }
}
@media (min-width:768px) {
  .phi-right { float: left; }
  .phi-left  { float: left; }
}
```

####HTML
```HTML
<div class="container phi-container">
 <div class="row row-eq-height">
  <div id="phi">
   <div class="col phi-right"></div>
   <div class="col phi-left"></div>
  </div>
 </div>
 <p>#phi container element size: <span class="phi-total"></span></p>
</div>
```

####JQuery
```HTML
<script>		
/* Phi - calculate the Golden Ratio for a pleasing visual design w. Jquery */

function goldenRatio() {
	var phi = $('#phi').width();
	var phi_width = Math.round(phi);
  	var phi_total = Math.round(phi_width * 1.61803);
	var phi_right = Math.round(phi_width / 1.61803);
	var phi_left = phi_width - Math.round(phi_width / 1.61803);

	if (phi_width <= 768) { //stack them (col-12) for extra small bootstrap responsive breakpoint
		$('.phi-left').css('height', phi_left + 'px').css('width', '100%').html(phi_left + 'px');
		$('.phi-right').css('height', phi_right + 'px').css('width', '100%').html(phi_right + 'px');
		$('.phi-total').html(phi + 'px');
	} else {
  		$('.phi-left').css('height', '300px').css('width', phi_left + 'px').html(phi_left + 'px');
	    	$('.phi-right').css('height','300px').css('width', phi_right + 'px').html(phi_right + 'px');
	  	$('.phi-total').html(phi + 'px');
	}
}

$(document).ready(function() {
	goldenRatio();
});

$(window).on('resize', function(){
	goldenRatio(); 
});
</script>
```
