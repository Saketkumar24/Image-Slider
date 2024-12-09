<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Image Slider</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <div class="slider-container">
            <div class="slider">
                <div class="slide">
                    <img src="./Mountain Landscape 1.jpeg"
                        alt="Mountain Landscape">
                    <p class="caption">Mountain Landscape</p>
                </div>
                <div class="slide">
                    <img src="./Beach Paradise.jpeg"
                        alt="Beach Paradise">
                    <p class="caption">Beach Paradise</p>
                </div>
                <div class="slide">
                    <img src="./Serene Forest.jpeg"
                        alt="Serene Forest">
                    <p class="caption">Serene Forest</p>
                </div>
                <div class="slide">
                    <img src="./Urban Skyline.jpeg"
                        alt="Urban Skyline">
                    <p class="caption">Urban Skyline</p>
                </div>
            </div>
            <button class="prev" onclick="prevSlide()">&#10094;</button>
            <button class="next" onclick="nextSlide()">&#10095;</button>
        </div>

        <script src="script.js"></script>
    </body>
</html>






/* General Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to bottom, #74ebd5, #acb6e5);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    overflow: hidden;
  }
  
  /* Slider Container */
  .slider-container {
    position: relative;
    width: 80%;
    max-width: 800px;
    height: 400px;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  }
  
  /* Slides */
  .slider {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }
  
  .slide {
    min-width: 100%;
    text-align: center;
    position: relative;
  }
  
  .slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 15px;
  }
  
  .caption {
    position: absolute;
    bottom: 10%;
    left: 50%;
    transform: translateX(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    color: #fff;
    padding: 0.5rem 1rem;
    border-radius: 5px;
    font-size: 1rem;
  }
  
  /* Navigation Buttons */
  button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    color: #fff;
    border: none;
    font-size: 2rem;
    padding: 0.5rem;
    cursor: pointer;
    border-radius: 50%;
    z-index: 10;
  }
  
  button.prev {
    left: 10px;
  }
  
  button.next {
    right: 10px;
  }
  
  button:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }
  
  /* Responsive Design */
  @media (max-width: 768px) {
    .slider-container {
      height: 300px;
    }
  
    .caption {
      font-size: 0.9rem;
    }
  
    button {
      font-size: 1.5rem;
    }
  }




  let currentSlide = 0;

function showSlide(index) {
  const slides = document.querySelectorAll('.slide');
  const totalSlides = slides.length;

  if (index >= totalSlides) currentSlide = 0;
  if (index < 0) currentSlide = totalSlides - 1;

  const offset = -currentSlide * 100;
  document.querySelector('.slider').style.transform = `translateX(${offset}%)`;
}

function nextSlide() {
  currentSlide++;
  showSlide(currentSlide);
}

function prevSlide() {
  currentSlide--;
  showSlide(currentSlide);
}

// Initialize the slider
showSlide(currentSlide);
