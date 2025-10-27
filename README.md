<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RayHan'S Click - Photography Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            text-align: center;
        }
        header {
            background-color: #333;
            color: white;
            padding: 1rem;
        }
        h1 {
            margin: 0;
            font-size: 2.5rem;
        }
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 10px;
            padding: 20px;
        }
        .gallery img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            cursor: pointer;
            border-radius: 5px;
            transition: transform 0.3s;
        }
        .gallery img:hover {
            transform: scale(1.05);
        }
        .lightbox {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .lightbox img {
            max-width: 90%;
            max-height: 90%;
            border-radius: 5px;
        }
        .close {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 2rem;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>RayHan'S Click</h1>
        <p>Your Photography Journey</p>
    </header>
    <div class="gallery">
        <!-- ছবির URL যোগ করো -->
        <img src="https://source.unsplash.com/random/300x200?landscape" alt="Photo 1">
        <img src="https://source.unsplash.com/random/300x200?portrait" alt="Photo 2">
        <img src="https://source.unsplash.com/random/300x200?nature" alt="Photo 3">
        <!-- আরও ছবি যোগ করতে পারো -->
    </div>
    <div class="lightbox" id="lightbox">
        <span class="close" onclick="closeLightbox()">&times;</span>
        <img id="lightbox-img" src="">
    </div>

    <script>
        const images = document.querySelectorAll('.gallery img');
        const lightbox = document.getElementById('lightbox');
        const lightboxImg = document.getElementById('lightbox-img');

        images.forEach(img => {
            img.addEventListener('click', () => {
                lightboxImg.src = img.src;
                lightbox.style.display = 'flex';
            });
        });

        function closeLightbox() {
            lightbox.style.display = 'none';
        }
    </script>
</body>
</html>