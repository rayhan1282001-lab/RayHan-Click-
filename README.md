DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RayHan - Nature Photography</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
            color: #fff;
            line-height: 1.6;
        }

        header {
            text-align: center;
            padding: 60px 20px;
            background: linear-gradient(135deg, #2c5f2d 0%, #97bc62 100%);
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        h1 {
            font-size: 3em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .subtitle {
            font-size: 1.3em;
            opacity: 0.9;
            margin-bottom: 20px;
        }

        .contact-info {
            margin-top: 20px;
            font-size: 1.1em;
        }

        .contact-info a {
            color: #fff;
            text-decoration: none;
            margin: 0 15px;
            transition: opacity 0.3s;
        }

        .contact-info a:hover {
            opacity: 0.7;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        .about-section {
            text-align: center;
            padding: 40px 20px;
            max-width: 800px;
            margin: 0 auto 60px;
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
            backdrop-filter: blur(10px);
        }

        .about-section h2 {
            margin-bottom: 20px;
            color: #97bc62;
        }

        .upload-section {
            text-align: center;
            margin-bottom: 40px;
            padding: 30px;
            background: rgba(255,255,255,0.05);
            border-radius: 15px;
            backdrop-filter: blur(10px);
        }

        .upload-section h2 {
            margin-bottom: 20px;
            color: #97bc62;
        }

        #fileInput {
            display: none;
        }

        .file-input-button {
            background: linear-gradient(135deg, #2c5f2d 0%, #97bc62 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.1em;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            display: inline-block;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            margin: 20px 10px;
        }

        .file-input-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(151, 188, 98, 0.4);
        }

        .clear-button {
            background: linear-gradient(135deg, #c73e1d 0%, #e74c3c 100%);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.1em;
            cursor: pointer;
            margin: 20px 10px;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .clear-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(231, 76, 60, 0.4);
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.4);
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            background: rgba(255,255,255,0.05);
        }

        .gallery-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 35px rgba(151, 188, 98, 0.3);
        }

        .gallery-item img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            display: block;
            transition: transform 0.3s;
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            position: relative;
            margin: auto;
            padding: 20px;
            width: 90%;
            max-width: 1200px;
            top: 50%;
            transform: translateY(-50%);
            text-align: center;
        }

        .modal-content img {
            max-width: 100%;
            max-height: 85vh;
            border-radius: 10px;
            box-shadow: 0 10px 50px rgba(0,0,0,0.5);
        }

        .close {
            position: absolute;
            top: 20px;
            right: 40px;
            color: #fff;
            font-size: 50px;
            font-weight: bold;
            cursor: pointer;
            z-index: 1001;
            transition: color 0.3s;
        }

        .close:hover {
            color: #97bc62;
        }

        .empty-gallery {
            text-align: center;
            padding: 60px 20px;
            color: rgba(255,255,255,0.6);
            font-size: 1.2em;
        }

        footer {
            text-align: center;
            padding: 30px;
            margin-top: 60px;
            background: rgba(0,0,0,0.3);
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2em;
            }
            
            .gallery {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
                gap: 15px;
            }

            .close {
                font-size: 35px;
                right: 20px;
            }

            .file-input-button, .clear-button {
                display: block;
                margin: 10px auto;
                width: 90%;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>RayHan</h1>
        <p class="subtitle">🌿 Nature Photography 🌿</p>
        <div class="contact-info">
            <a href="mailto:rayhan1282001@gmail.com">📧 rayhan1282001@gmail.com</a>
            <a href="https://facebook.com/rayhan1282001" target="_blank">📘 Facebook</a>
        </div>
    </header>

    <div class="container">
        <div class="about-section">
            <h2>আমার সম্পর্কে</h2>
            <p>প্রকৃতির সৌন্দর্য ক্যামেরায় বন্দী করা আমার প্যাশন। প্রতিটি ছবির মাধ্যমে প্রকৃতির অপরূপ মুহূর্তগুলো আপনাদের সাথে শেয়ার করতে ভালোবাসি।</p>
        </div>

        <div class="upload-section">
            <h2>📸 আপনার ফটোগ্রাফি আপলোড করুন</h2>
            <p>নিচের বাটনে ক্লিক করে আপনার ছবিগুলো যুক্ত করুন</p>
            <input type="file" id="fileInput" accept="image/*" multiple>
            <button class="file-input-button" id="uploadBtn">🖼️ ছবি নির্বাচন করুন</button>
            <button class="clear-button" id="clearBtn">🗑️ সব ছবি মুছে ফেলুন</button>
        </div>

        <div id="gallery" class="gallery"></div>
        <div id="emptyMessage" class="empty-gallery">
            আপনার সুন্দর ছবিগুলো এখানে দেখাবে! উপরের বাটনে ক্লিক করে ছবি আপলোড করুন। 📷
        </div>
    </div>

    <div id="modal" class="modal">
        <span class="close" id="closeModal">&times;</span>
        <div class="modal-content">
            <img id="modalImage" src="" alt="Full size image">
        </div>
    </div>

    <footer>
        <p>&copy; 2024 RayHan Photography. All Rights Reserved.</p>
    </footer>

    <script>
        const fileInput = document.getElementById('fileInput');
        const uploadBtn = document.getElementById('uploadBtn');
        const clearBtn = document.getElementById('clearBtn');
        const gallery = document.getElementById('gallery');
        const emptyMessage = document.getElementById('emptyMessage');
        const modal = document.getElementById('modal');
        const modalImage = document.getElementById('modalImage');
        const closeModal = document.getElementById('closeModal');
        
        let images = [];

        uploadBtn.addEventListener('click', function(e) {
            e.preventDefault();
            console.log('Upload button clicked!');
            fileInput.click();
        });

        fileInput.addEventListener('change', function(e) {
            const files = e.target.files;
            console.log('Files selected:', files.length);
            
            if (files.length === 0) return;
            
            for (let i = 0; i < files.length; i++) {
                const file = files[i];
                const reader = new FileReader();
                
                reader.onload = function(event) {
                    const imageData = event.target.result;
                    images.push(imageData);
                    
                    const item = document.createElement('div');
                    item.className = 'gallery-item';
                    
                    const img = document.createElement('img');
                    img.src = imageData;
                    img.alt = 'Nature Photography by RayHan';
                    
                    img.addEventListener('click', function() {
                        openModal(imageData);
                    });
                    
                    item.appendChild(img);
                    gallery.appendChild(item);
                    
                    emptyMessage.style.display = 'none';
                };
                
                reader.readAsDataURL(file);
            }
            
            fileInput.value = '';
        });

        clearBtn.addEventListener('click', function(e) {
            e.preventDefault();
            
            if (images.length === 0) {
                alert('গ্যালারিতে কোনো ছবি নেই!');
                return;
            }
            
            if (confirm('আপনি কি সব ছবি মুছে ফেলতে চান?')) {
                images = [];
                gallery.innerHTML = '';
                emptyMessage.style.display = 'block';
            }
        });

        function openModal(imageSrc) {
            modal.style.display = 'block';
            modalImage.src = imageSrc;
        }

        closeModal.addEventListener('click', function() {
            modal.style.display = 'none';
        });

        modal.addEventListener('click', function(e) {
            if (e.target === modal) {
                modal.style.display = 'none';
            }
        });

        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                modal.style.display = 'none';
            }
        });

        window.addEventListener('load', function() {
            if (images.length === 0) {
                emptyMessage.style.display = 'block';
            }
        });
    </script>
    /script>
</body>
