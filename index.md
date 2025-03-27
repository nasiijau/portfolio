---
layout: default
---
<div class="gallery">
	{% for video in site.data.videos %}
	{% capture _ %}
	{% increment sumpict %}
	{% endcapture %}
	<div class="example" onclick="openModal();currentSlide({{sumpict}})" cursor>
        <video class="content" src="{{video.video_path}}" autoplay loop muted></video>
      <div class="exampleInfo">
        <div class="info1">
            <h4>{{video.title}}</h4>
          <p>{{video.desc}}</p>
        </div>
      </div>
    </div>
    {% endfor %}
</div>     

<div id="myModal" class="modal">
  <span class="close cursor" onclick="closeModal()">&times;</span>
  <div class="modal-content">
	{% for video in site.data.videos %}
   <div class="mySlides">
      <div class="numbertext">-</div>
      <video class="content" src="{{video.video_path}}" autoplay loop controls muted></video>
         <div class="caption-container">
      <h1>{{video.title}}</h1>
          <p>{{video.desc}}</p>
    </div>
    </div>
      {% endfor %}

   <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
   <a class="next" onclick="plusSlides(1)">&#10095;</a>



   <div class="column">
   	{% for video in site.data.videos %}
   	{% capture _ %}
   	{% increment sumpict2 %}
   	{% endcapture %}
      <video class="democursor" src="{{video.video_path}}" onclick="currentSlide({{sumpict2}})" autoplay loop muted></video>
      {% endfor %}
    </div>
  </div>
</div>

<script>
function openModal() {
  document.getElementById("myModal").style.display = "block";
}

function closeModal() {
  document.getElementById("myModal").style.display = "none";
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
  slides[slideIndex-1].style.display = "block";
  dots[slideIndex-1].className += " active";
  captionText.innerHTML = dots[slideIndex-1].alt;
}
</script>
