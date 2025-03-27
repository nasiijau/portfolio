---
layout: default
---
<div class="gallery">
	{% for image in site.data.images %}
	{% capture _ %}
	{% increment x %}
	{% endcapture %}
	<div class="example" onclick="openModal();currentSlide({{x}})" cursor>
        <img class="content" src="{{image.image_path}}" cursor>
      <div class="exampleInfo">
        <div class="info1">
            <h4>{{image.title}}</h4>
          <p>Plane arriving at May 15th, 6am</p>
        </div>
      </div>
    </div>
    {% endfor %}
</div>     

<div id="myModal" class="modal">
  <span class="close cursor" onclick="closeModal()">&times;</span>
  <div class="modal-content">
	{% for image in site.data.images %}
   <div class="mySlides">
      <div class="numbertext">1 / 4</div>
      <img src="{{image.image_path}}" style="width:100%">
    </div>
      {% endfor %}

   <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
   <a class="next" onclick="plusSlides(1)">&#10095;</a>

   <div class="caption-container">
      <p id="caption"></p>
    </div>


   <div class="column">
   	{% for image in site.data.images %}
   	{% capture _ %}
   	{% increment y %}
   	{% endcapture %}
      <img class="demo cursor" src="{{image.image_path}}" style="width:20%" onclick="currentSlide({{y}})" alt="{{image.title}}">
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



<!-- <div class="row">
	{% for image in site.data.images %}
	<div class="column">
			<img class ="content" src="{{image.image_path}}" alt="{{image.title}}">
			<div class="ExampleInfo">
				<div class="info1">
					<h2>TESTING</h2>
					<p>te</p>
				</div>
			</div>
			
	</div>
	{% endfor %}
</div> -->

<!-- <div class="row">
	{% for video in site.data.videos %}
	<div class="column">
		<video class="content" style="width:100%;height:400px;" src="{{video.video_path}}" alt="" muted autoplay loop></video>
		<div class="overlay">
		<div class="caption">{{video.title}}</div>
		</div>
	</div>
	{% endfor %}
</div>
 -->