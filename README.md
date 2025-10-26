<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RayHan'S Click - Photo Gallery</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            color: #333;
        }

        header {
            text-align: center;
            padding: 2rem;
            background-color: #2c3e50;
            color: white;
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }

        header p {
            font-size: 1.2rem;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            padding: 2rem;
        }

        .gallery img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
            transition: transform 0.3s ease;
            cursor: pointer;
        }

        .gallery img:hover {
            transform: scale(1.05);
        }

        /* লাইটবক্স স্টাইল */
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
            border-radius: 8px;
        }

        .close {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 2rem;
            cursor: pointer;
        }

        /* রেসপনসিভ */
        @media (max-width: 600px) {
            .gallery {
                grid-template-columns: 1fr;
                padding: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>RayHan'S Click</h1>
        <p>আমার ফটোগ্রাফির গ্যালারি স্বাগতম!</p>
    </header>
    
    <div class="gallery" id="gallery">
        <!-- ছবিগুলো এখানে যোগ হবে -->
    </div>

    <!-- লাইটবক্স -->
    <div class="lightbox" id="lightbox">
        <span class="close">&times;</span>
        <img class="lightbox-content" id="lightbox-img">
    </div>

    <script>
        // ছবিগুলোর তালিকা (প্লেসহোল্ডার URL – আপনার ছবি দিয়ে রিপ্লেস করুন)
        const photos = [
            'https://source.unsplash.com/random/400x300/?nature',
            'https://source.unsplash.com/random/400x300/?city',
            'https://source.unsplash.com/random/400x300/?portrait',
            'https://source.unsplash.com/random/400x300/?food',
            // আরও যোগ করুন, যেমন: 'images/yourphoto.jpg'
        ];

        // গ্যালারিতে ছবি যোগ করা
        const gallery = document.getElementById('gallery');
        photos.forEach((photo, index) => {
            const img = document.createElement('img');
            img.src = photo;
            img.alt = `RayHan'S Click Photo ${index + 1}`;
            img.onerror = function() { // যদি ছবি লোড না হয়
                this.src = 'https://via.placeholder.com/400x300?text=Image+Not+Found';
            };
            gallery.appendChild(img);
        });

        // লাইটবক্স ফাংশনালিটি
        const lightbox = document.getElementById('lightbox');
        const lightboxImg = document.getElementById('lightbox-img');
        const closeBtn = document.querySelector('.close');

        gallery.addEventListener('click', (e) => {
            if (e.target.tagName === 'IMG') {
                lightbox.style.display = 'flex';
                lightboxImg.src = e.target.src;
            }
        });

        closeBtn.addEventListener('click', () => {
            lightbox.style.display = 'none';
        });

        lightbox.addEventListener('click', (e) => {
            if (e.target === lightbox) {
                lightbox.style.display = 'none';
            }
        });
    </script>
</body>
</html>