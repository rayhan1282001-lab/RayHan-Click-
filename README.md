<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RayHan'S Click - ফটো গ্যালারি</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
        }
        
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            opacity: 0.9;
            z-index: -1;
            filter: blur(5px);
        }
        
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.5);
            z-index: -1;
        }
        
        .container {
            max-width: 1200px;
            width: 100%;
            z-index: 1;
        }
        
        .logo-container {
            margin-bottom: 20px;
            position: relative;
        }
        
        .logo {
            font-size: 4.5rem;
            font-weight: 800;
            margin-bottom: 10px;
            text-shadow: 3px 3px 10px rgba(0, 0, 0, 0.7);
            letter-spacing: 3px;
            background: linear-gradient(45deg, #ffffff, #fdbb2d, #ffffff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            position: relative;
            display: inline-block;
        }
        
        .logo::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 10%;
            width: 80%;
            height: 4px;
            background: linear-gradient(90deg, transparent, #fdbb2d, transparent);
            border-radius: 2px;
        }
        
        .logo-subtitle {
            font-size: 1.2rem;
            font-weight: 300;
            letter-spacing: 8px;
            margin-top: 5px;
            opacity: 0.9;
        }
        
        .tagline {
            font-size: 1.5rem;
            margin-bottom: 40px;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
            font-style: italic;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.6;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 30px;
        }
        
        .btn {
            padding: 15px 30px;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid white;
            color: white;
            font-size: 1.1rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            text-decoration: none;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
            z-index: -1;
        }
        
        .btn:hover {
            background: white;
            color: #1a2a6c;
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }
        
        .btn:hover::before {
            left: 100%;
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }
        
        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #1a2a6c, #b21f1f, #fdbb2d);
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
        
        .feature-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #fdbb2d;
        }
        
        .feature-card p {
            font-size: 1rem;
            line-height: 1.6;
        }
        
        .gallery-section {
            margin-top: 80px;
            padding: 40px 0;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            backdrop-filter: blur(10px);
        }
        
        .section-title {
            font-size: 2.5rem;
            margin-bottom: 40px;
            color: #fdbb2d;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
        }
        
        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            padding: 0 20px;
        }
        
        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            height: 250px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }
        
        .gallery-item:hover {
            transform: scale(1.03);
        }
        
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .gallery-item:hover img {
            transform: scale(1.1);
        }
        
        .image-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.7);
            padding: 15px;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }
        
        .gallery-item:hover .image-overlay {
            transform: translateY(0);
        }
        
        .image-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .image-category {
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .upload-section {
            margin-top: 40px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .upload-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: #fdbb2d;
        }
        
        .upload-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
            text-align: left;
        }
        
        .form-group label {
            margin-bottom: 5px;
            font-weight: bold;
        }
        
        .form-group input, .form-group select {
            padding: 12px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }
        
        .form-group input::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }
        
        .upload-btn {
            padding: 15px;
            background: #fdbb2d;
            color: #1a2a6c;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
        }
        
        .upload-btn:hover {
            background: #ffcc44;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .upload-status {
            margin-top: 15px;
            padding: 10px;
            border-radius: 5px;
            display: none;
        }
        
        .status-success {
            background: rgba(40, 167, 69, 0.2);
            border: 1px solid #28a745;
            color: #28a745;
        }
        
        .status-error {
            background: rgba(220, 53, 69, 0.2);
            border: 1px solid #dc3545;
            color: #dc3545;
        }
        
        .footer {
            margin-top: 60px;
            padding: 20px;
            font-size: 0.9rem;
            opacity: 0.8;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            width: 100%;
        }
        
        @media (max-width: 768px) {
            .logo {
                font-size: 3rem;
            }
            
            .logo-subtitle {
                font-size: 1rem;
                letter-spacing: 5px;
            }
            
            .tagline {
                font-size: 1.2rem;
            }
            
            .buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 80%;
            }
            
            .gallery-container {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
        }
        
        @media (max-width: 480px) {
            .logo {
                font-size: 2.2rem;
            }
            
            .logo-subtitle {
                font-size: 0.8rem;
                letter-spacing: 3px;
            }
            
            .tagline {
                font-size: 1rem;
            }
            
            .gallery-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="overlay"></div>
    
    <div class="container">
        <div class="logo-container">
            <h1 class="logo">RayHan'S Click</h1>
            <div class="logo-subtitle">PHOTOGRAPHY</div>
        </div>
        <p class="tagline">মুহূর্তগুলোকে ধরে রাখার এক অনন্য সংগ্রহ, জীবনকে ক্যামেরার চোখে দেখা</p>
        
        <div class="buttons">
            <a href="#gallery" class="btn">গ্যালারি দেখুন</a>
            <a href="#upload" class="btn">ছবি আপলোড</a>
            <a href="#contact" class="btn">যোগাযোগ</a>
        </div>
        
        <div class="features">
            <div class="feature-card">
                <h3>প্রকৃতি</h3>
                <p>প্রকৃতির সৌন্দর্যকে ক্যামেরার মাধ্যমে ধারণ করা অসাধারণ সব মুহূর্ত</p>
            </div>
            <div class="feature-card">
                <h3>পোর্ট্রেট</h3>
                <p>মানুষের আবেগ, অনুভূতি এবং অভিব্যক্তির অনবদ্য চিত্রায়ন</p>
            </div>
            <div class="feature-card">
                <h3>স্থাপত্য</h3>
                <p>মানুষের তৈরি স্থাপত্যের নান্দনিক ও শৈল্পিক দিকের ফটোগ্রাফি</p>
            </div>
        </div>
        
        <!-- গ্যালারি সেকশন -->
        <section id="gallery" class="gallery-section">
            <h2 class="section-title">আমার গ্যালারি</h2>
            <div class="gallery-container" id="galleryContainer">
                <!-- গ্যালারি আইটেমগুলি এখানে যোগ হবে -->
            </div>
        </section>
        
        <!-- ছবি আপলোড সেকশন -->
        <section id="upload" class="upload-section">
            <h2 class="upload-title">নতুন ছবি আপলোড করুন</h2>
            <form class="upload-form" id="uploadForm">
                <div class="form-group">
                    <label for="imageTitle">ছবির শিরোনাম</label>
                    <input type="text" id="imageTitle" placeholder="ছবির একটি শিরোনাম দিন" required>
                </div>
                <div class="form-group">
                    <label for="imageCategory">বিভাগ</label>
                    <select id="imageCategory" required>
                        <option value="">একটি বিভাগ নির্বাচন করুন</option>
                        <option value="প্রকৃতি">প্রকৃতি</option>
                        <option value="পোর্ট্রেট">পোর্ট্রেট</option>
                        <option value="স্থাপত্য">স্থাপত্য</option>
                        <option value="অন্যান্য">অন্যান্য</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="imageFile">ছবি নির্বাচন করুন</label>
                    <input type="file" id="imageFile" accept="image/*" required>
                </div>
                <button type="submit" class="upload-btn">ছবি আপলোড করুন</button>
                
                <!-- আপলোড স্ট্যাটাস -->
                <div id="uploadStatus" class="upload-status"></div>
            </form>
        </section>
        
        <!-- যোগাযোগ সেকশন -->
        <section id="contact" class="upload-section">
            <h2 class="upload-title">যোগাযোগ</h2>
            <p>ইমেইল: rayhan@example.com</p>
            <p>ফোন: +880 1XXX-XXXXXX</p>
        </section>
        
        <div class="footer">
            <p>© 2023 RayHan'S Click - সকল স্বত্ব সংরক্ষিত</p>
            <p id="siteInfo" style="margin-top: 10px; font-size: 0.8rem;"></p>
        </div>
    </div>

    <script>
        // গ্যালারি ডেটা
        const galleryData = [
            {
                id: 1,
                title: "সূর্যাস্ত",
                category: "প্রকৃতি",
                url: "https://images.unsplash.com/photo-1505142468610-359e7d316be0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 2,
                title: "শহরের রাত",
                category: "স্থাপত্য",
                url: "https://images.unsplash.com/photo-1477959858617-67f85cf4f1df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 3,
                title: "প্রতিকৃতি",
                category: "পোর্ট্রেট",
                url: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            }
        ];

        // DOM লোড হওয়ার পর
        document.addEventListener('DOMContentLoaded', function() {
            const galleryContainer = document.getElementById('galleryContainer');
            const uploadForm = document.getElementById('uploadForm');
            const uploadStatus = document.getElementById('uploadStatus');
            const siteInfo = document.getElementById('siteInfo');
            
            // সাইট তথ্য দেখাও
            siteInfo.textContent = `ডোমেন: ${window.location.hostname}`;
            
            // গ্যালারি লোড করা
            loadGallery();
            
            // আপলোড ফর্ম হ্যান্ডলিং
            uploadForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const title = document.getElementById('imageTitle').value;
                const category = document.getElementById('imageCategory').value;
                const fileInput = document.getElementById('imageFile');
                
                if (fileInput.files.length > 0) {
                    const file = fileInput.files[0];
                    
                    // ফাইল সাইজ চেক (max 5MB)
                    if (file.size > 5 * 1024 * 1024) {
                        showUploadStatus('ছবির সাইজ 5MB এর কম হতে হবে!', 'error');
                        return;
                    }
                    
                    const reader = new FileReader();
                    
                    reader.onloadstart = function() {
                        showUploadStatus('ছবি আপলোড হচ্ছে...', 'loading');
                    };
                    
                    reader.onload = function(e) {
                        const newImage = {
                            id: galleryData.length + 1,
                            title: title,
                            category: category,
                            url: e.target.result
                        };
                        
                        galleryData.push(newImage);
                        addImageToGallery(newImage);
                        
                        // ফর্ম রিসেট
                        uploadForm.reset();
                        
                        showUploadStatus('✅ ছবিটি সফলভাবে আপলোড হয়েছে! গ্যালারিতে দেখুন।', 'success');
                        
                        // 3 সেকেন্ড পর স্ট্যাটাস হাইড
                        setTimeout(() => {
                            uploadStatus.style.display = 'none';
                        }, 3000);
                    };
                    
                    reader.onerror = function() {
                        showUploadStatus('❌ আপলোড ব্যর্থ হয়েছে! আবার চেষ্টা করুন।', 'error');
                    };
                    
                    reader.readAsDataURL(file);
                }
            });
            
            // গ্যালারি লোড ফাংশন
            function loadGallery() {
                galleryContainer.innerHTML = '';
                
                galleryData.forEach(image => {
                    addImageToGallery(image);
                });
            }
            
            // গ্যালারিতে ছবি যোগ করার ফাংশন
            function addImageToGallery(image) {
                const galleryItem = document.createElement('div');
                galleryItem.className = 'gallery-item';
                
                galleryItem.innerHTML = `
                    <img src="${image.url}" alt="${image.title}" loading="lazy">
                    <div class="image-overlay">
                        <div class="image-title">${image.title}</div>
                        <div class="image-category">${image.category}</div>
                    </div>
                `;
                
                galleryContainer.appendChild(galleryItem);
            }
            
            // আপলোড স্ট্যাটাস দেখানোর ফাংশন
            function showUploadStatus(message, type) {
                uploadStatus.textContent = message;
                uploadStatus.className = 'upload-status';
                uploadStatus.classList.add(`status-${type}`);
                uploadStatus.style.display = 'block';
            }
        });
    </script>
</body>
</html>        
        .logo::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 10%;
            width: 80%;
            height: 4px;
            background: linear-gradient(90deg, transparent, #fdbb2d, transparent);
            border-radius: 2px;
        }
        
        .logo-subtitle {
            font-size: 1.2rem;
            font-weight: 300;
            letter-spacing: 8px;
            margin-top: 5px;
            opacity: 0.9;
        }
        
        .tagline {
            font-size: 1.5rem;
            margin-bottom: 40px;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
            font-style: italic;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            line-height: 1.6;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 30px;
        }
        
        .btn {
            padding: 15px 30px;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid white;
            color: white;
            font-size: 1.1rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            text-decoration: none;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
            z-index: -1;
        }
        
        .btn:hover {
            background: white;
            color: #1a2a6c;
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }
        
        .btn:hover::before {
            left: 100%;
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }
        
        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #1a2a6c, #b21f1f, #fdbb2d);
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
        
        .feature-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #fdbb2d;
        }
        
        .feature-card p {
            font-size: 1rem;
            line-height: 1.6;
        }
        
        /* গ্যালারি স্টাইল */
        .gallery-section {
            margin-top: 80px;
            padding: 40px 0;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 20px;
            backdrop-filter: blur(10px);
        }
        
        .section-title {
            font-size: 2.5rem;
            margin-bottom: 40px;
            color: #fdbb2d;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
        }
        
        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            padding: 0 20px;
        }
        
        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            height: 250px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }
        
        .gallery-item:hover {
            transform: scale(1.03);
        }
        
        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .gallery-item:hover img {
            transform: scale(1.1);
        }
        
        .image-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.7);
            padding: 15px;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }
        
        .gallery-item:hover .image-overlay {
            transform: translateY(0);
        }
        
        .image-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .image-category {
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .upload-section {
            margin-top: 40px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .upload-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: #fdbb2d;
        }
        
        .upload-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
            text-align: left;
        }
        
        .form-group label {
            margin-bottom: 5px;
            font-weight: bold;
        }
        
        .form-group input, .form-group select {
            padding: 12px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }
        
        .form-group input::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }
        
        .upload-btn {
            padding: 15px;
            background: #fdbb2d;
            color: #1a2a6c;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
        }
        
        .upload-btn:hover {
            background: #ffcc44;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .footer {
            margin-top: 60px;
            padding: 20px;
            font-size: 0.9rem;
            opacity: 0.8;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            width: 100%;
        }
        
        @media (max-width: 768px) {
            .logo {
                font-size: 3rem;
            }
            
            .logo-subtitle {
                font-size: 1rem;
                letter-spacing: 5px;
            }
            
            .tagline {
                font-size: 1.2rem;
            }
            
            .buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 80%;
            }
            
            .gallery-container {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
        }
        
        @media (max-width: 480px) {
            .logo {
                font-size: 2.2rem;
            }
            
            .logo-subtitle {
                font-size: 0.8rem;
                letter-spacing: 3px;
            }
            
            .tagline {
                font-size: 1rem;
            }
            
            .gallery-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="overlay"></div>
    
    <div class="container">
        <div class="logo-container">
            <h1 class="logo">RayHan'S Click</h1>
            <div class="logo-subtitle">PHOTOGRAPHY</div>
        </div>
        <p class="tagline">মুহূর্তগুলোকে ধরে রাখার এক অনন্য সংগ্রহ, জীবনকে ক্যামেরার চোখে দেখা</p>
        
        <div class="buttons">
            <a href="#gallery" class="btn">গ্যালারি দেখুন</a>
            <a href="#upload" class="btn">ছবি আপলোড</a>
            <a href="#" class="btn">যোগাযোগ</a>
        </div>
        
        <div class="features">
            <div class="feature-card">
                <h3>প্রকৃতি</h3>
                <p>প্রকৃতির সৌন্দর্যকে ক্যামেরার মাধ্যমে ধারণ করা অসাধারণ সব মুহূর্ত</p>
            </div>
            <div class="feature-card">
                <h3>পোর্ট্রেট</h3>
                <p>মানুষের আবেগ, অনুভূতি এবং অভিব্যক্তির অনবদ্য চিত্রায়ন</p>
            </div>
            <div class="feature-card">
                <h3>স্থাপত্য</h3>
                <p>মানুষের তৈরি স্থাপত্যের নান্দনিক ও শৈল্পিক দিকের ফটোগ্রাফি</p>
            </div>
        </div>
        
        <!-- গ্যালারি সেকশন -->
        <section id="gallery" class="gallery-section">
            <h2 class="section-title">আমার গ্যালারি</h2>
            <div class="gallery-container" id="galleryContainer">
                <!-- গ্যালারি আইটেমগুলি এখানে যোগ হবে -->
            </div>
        </section>
        
        <!-- ছবি আপলোড সেকশন -->
        <section id="upload" class="upload-section">
            <h2 class="upload-title">নতুন ছবি আপলোড করুন</h2>
            <form class="upload-form" id="uploadForm">
                <div class="form-group">
                    <label for="imageTitle">ছবির শিরোনাম</label>
                    <input type="text" id="imageTitle" placeholder="ছবির একটি শিরোনাম দিন" required>
                </div>
                <div class="form-group">
                    <label for="imageCategory">বিভাগ</label>
                    <select id="imageCategory" required>
                        <option value="">একটি বিভাগ নির্বাচন করুন</option>
                        <option value="প্রকৃতি">প্রকৃতি</option>
                        <option value="পোর্ট্রেট">পোর্ট্রেট</option>
                        <option value="স্থাপত্য">স্থাপত্য</option>
                        <option value="অন্যান্য">অন্যান্য</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="imageFile">ছবি নির্বাচন করুন</label>
                    <input type="file" id="imageFile" accept="image/*" required>
                </div>
                <button type="submit" class="upload-btn">ছবি আপলোড করুন</button>
            </form>
        </section>
        
        <div class="footer">
            <p>© 2023 RayHan'S Click - সকল স্বত্ব সংরক্ষিত</p>
        </div>
    </div>

    <script>
        // গ্যালারি ডেটা - এখানে আপনার ছবি যোগ করুন
        const galleryData = [
            {
                id: 1,
                title: "সূর্যাস্ত",
                category: "প্রকৃতি",
                url: "https://images.unsplash.com/photo-1505142468610-359e7d316be0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 2,
                title: "শহরের রাত",
                category: "স্থাপত্য",
                url: "https://images.unsplash.com/photo-1477959858617-67f85cf4f1df?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 3,
                title: "প্রতিকৃতি",
                category: "পোর্ট্রেট",
                url: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 4,
                title: "পাহাড়",
                category: "প্রকৃতি",
                url: "https://images.unsplash.com/photo-1464822759844-4c9a052c13b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 5,
                title: "পুরনো ভবন",
                category: "স্থাপত্য",
                url: "https://images.unsplash.com/photo-1513584684374-8bab748fbf90?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                id: 6,
                title: "চিন্তাশীল",
                category: "পোর্ট্রেট",
                url: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            }
        ];

        // DOM লোড হওয়ার পর
        document.addEventListener('DOMContentLoaded', function() {
            const buttons = document.querySelectorAll('.btn');
            const featureCards = document.querySelectorAll('.feature-card');
            const galleryContainer = document.getElementById('galleryContainer');
            const uploadForm = document.getElementById('uploadForm');
            
            // বাটন হোভার ইফেক্ট
            buttons.forEach(button => {
                button.addEventListener('mouseenter', function() {
                    this.style.transform = 'translateY(-5px)';
                });
                
                button.addEventListener('mouseleave', function() {
                    this.style.transform = 'translateY(0)';
                });
            });
            
            // কার্ডগুলিতে স্ট্যাগারড এনিমেশন যোগ করা
            featureCards.forEach((card, index) => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                
                setTimeout(() => {
                    card.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, 300 + (index * 200));
            });
            
            // গ্যালারি লোড করা
            loadGallery();
            
            // আপলোড ফর্ম হ্যান্ডলিং
            uploadForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const title = document.getElementById('imageTitle').value;
                const category = document.getElementById('imageCategory').value;
                const fileInput = document.getElementById('imageFile');
                
                if (fileInput.files.length > 0) {
                    const file = fileInput.files[0];
                    const reader = new FileReader();
                    
                    reader.onload = function(e) {
                        const newImage = {
                            id: galleryData.length + 1,
                            title: title,
                            category: category,
                            url: e.target.result
                        };
                        
                        galleryData.push(newImage);
                        addImageToGallery(newImage);
                        
                        // ফর্ম রিসেট
                        uploadForm.reset();
                        
                        alert('ছবিটি সফলভাবে আপলোড হয়েছে!');
                    };
                    
                    reader.readAsDataURL(file);
                }
            });
            
            // গ্যালারি লোড ফাংশন
            function loadGallery() {
                galleryContainer.innerHTML = '';
                
                galleryData.forEach(image => {
                    addImageToGallery(image);
                });
            }
            
            // গ্যালারিতে ছবি যোগ করার ফাংশন
            function addImageToGallery(image) {
                const galleryItem = document.createElement('div');
                galleryItem.className = 'gallery-item';
                
                galleryItem.innerHTML = `
                    <img src="${image.url}" alt="${image.title}">
                    <div class="image-overlay">
                        <div class="image-title">${image.title}</div>
                        <div class="image-category">${image.category}</div>
                    </div>
                `;
                
                galleryContainer.appendChild(galleryItem);
            }
        });
    </script>
</body>
</html>
