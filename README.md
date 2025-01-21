# dtools
Slider
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Slider</title>
    <link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.min.css">
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
        }

        .slider-container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            position: relative;
        }

        .swiper {
            width: 100%;
            height: auto;
        }

        .swiper-slide {
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .swiper-slide img {
            width: 420px;
            height: 420px;
            object-fit: cover;
            cursor: pointer;
        }

        .swiper-button-next,
        .swiper-button-prev {
            color: orange;
            background: gray;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
        }

        .swiper-button-next:after,
        .swiper-button-prev:after {
            font-size: 20px;
        }

        .swiper-thumbs {
            margin-top: 10px;
        }

        .swiper-thumbs .swiper-slide img {
            width: 80px;
            height: 80px;
            object-fit: cover;
            cursor: pointer;
            opacity: 0.6;
        }

        .swiper-thumbs .swiper-slide-thumb-active img {
            opacity: 1;
        }

        .fullscreen-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            display: none;
        }

        .fullscreen-overlay img {
            max-width: 90%;
            max-height: 90%;
        }
    </style>
</head>
<body>

<div class="slider-container">
    <div class="swiper main-slider">
        <div class="swiper-wrapper">
            <div class="swiper-slide"><img src="https://i.ibb.co/Yb8CSYz/distarcsx82.jpg" alt="Product 1"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/xdVK26hb/distarcsx.jpg" alt="Product 2"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/JzMkYskb/72distarpack-min.jpg" alt="Product 3"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/RZpZ1hQC/72distarcloseup-min.jpg" alt="Product 4"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/pTTQGp30/72distar-min.jpg" alt="Product 5"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/9QQGF4Qc/225.jpg" alt="Product 6"></div>
        </div>
        <div class="swiper-button-next"></div>
        <div class="swiper-button-prev"></div>
    </div>

    <div class="swiper swiper-thumbs">
        <div class="swiper-wrapper">
            <div class="swiper-slide"><img src="https://i.ibb.co/Yb8CSYz/distarcsx82.jpg" alt="Product 1"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/xdVK26hb/distarcsx.jpg" alt="Product 2"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/JzMkYskb/72distarpack-min.jpg" alt="Product 3"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/RZpZ1hQC/72distarcloseup-min.jpg" alt="Product 4"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/pTTQGp30/72distar-min.jpg" alt="Product 5"></div>
            <div class="swiper-slide"><img src="https://i.postimg.cc/9QQGF4Qc/225.jpg" alt="Product 6"></div>
        </div>
    </div>
</div>

<div class="fullscreen-overlay" id="fullscreenOverlay">
    <img id="fullscreenImage" src="" alt="Fullscreen Image">
</div>

<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>
<script>
    const mainSlider = new Swiper('.main-slider', {
        spaceBetween: 10,
        navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
        },
    });

    const thumbsSlider = new Swiper('.swiper-thumbs', {
        spaceBetween: 10,
        slidesPerView: 4,
        freeMode: true,
        watchSlidesProgress: true,
    });

    mainSlider.controller.control = thumbsSlider;
    thumbsSlider.controller.control = mainSlider;

    const fullscreenOverlay = document.getElementById('fullscreenOverlay');
    const fullscreenImage = document.getElementById('fullscreenImage');

    document.querySelectorAll('.swiper-thumbs .swiper-slide img').forEach((thumb, index) => {
        thumb.addEventListener('click', () => {
            mainSlider.slideTo(index);
        });
    });

    document.querySelectorAll('.main-slider .swiper-slide img').forEach(img => {
        img.addEventListener('click', () => {
            fullscreenImage.src = img.src;
            fullscreenOverlay.style.display = 'flex';
        });
    });

    fullscreenOverlay.addEventListener('click', () => {
        fullscreenOverlay.style.display = 'none';
    });
</script>

</body>
</html>
