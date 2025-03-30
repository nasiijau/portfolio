---
layout: default
title : drawings
---
<div class="gallery">
	{% for image in site.data.images %}
	{% capture _ %}
	{% increment sumpict %} 
	{% endcapture %}
	<div class="example" onclick="openModal();currentSlide({{sumpict}})" cursor>
      <image class="content" src="{{image.image_path}}"></image>
      <div class="exampleInfo">
        <div class="info1">
            <h4>{{image.title}}</h4>
          <p>{{image.desc}}</p>
        </div>
      </div>
    </div>
    {% endfor %}
</div>     

<div id="myModal" class="modal" >
  <span class="close cursor" onclick="closeModal()">&times;</span>
  <div class="modal-content">
	{% for image in site.data.images %}
   <div class="mySlides">
    <div class="image-container">
      <image class="content" src="{{image.image_path}}"></image>
           <div class="menu-control">
        <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
        <a class="next" onclick="plusSlides(1)">&#10095;</a>
       </div>
    </div>
    <div class="caption-container">
      <div>
        <h1>{{image.title}}</h1>
          <p>{{image.desc}}</p>
      </div>
      </div>
    </div>
      {% endfor %}

  </div>
</div>

<script>
function openModal() {
  document.getElementById("myModal").style.display = "flex";
}

function closeModal() {
  document.getElementById("myModal").style.display = "none";
}

var modal = document.getElementById('myModal');

window.onclick = function(event) {
  if (event.target == modal) {
    modal.style.display = "none";
  }
}

var slideIndex = 1;
showSlides(slideIndex);

function plusSlides(n) {
  showSlides(slideIndex += n);
}

function currentSlide(n) {
  showSlides(slideIndex = n);
}

function showSlides(n) {
  var i;
  var slides = document.getElementsByClassName("mySlides");
  var dots = document.getElementsByClassName("demo");
  var captionText = document.getElementById("caption");
  if (n > slides.length) {slideIndex = 1}
  if (n < 1) {slideIndex = slides.length}
  for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";
  }
  for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" active", "");
  }
  slides[slideIndex-1].style.display = "flex";
  dots[slideIndex-1].className += " active";
  captionText.innerHTML = dots[slideIndex-1].alt;
}
</script>
