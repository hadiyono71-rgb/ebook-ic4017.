<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IR Sensor dengan IC 4017 dan Relay - E-Book Interaktif</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #333;
            overflow: hidden;
        }
        .slideshow-container {
            position: relative;
            width: 100%;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .slide {
            display: none;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 1000px;
            height: 85vh;
            padding: 40px;
            overflow-y: auto;
            animation: slideIn 0.5s ease-in-out;
        }
        .slide.active {
            display: block;
        }
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(30px); }
            to { opacity: 1; transform: translateX(0); }
        }
        h1 {
            color: #4a5568;
            font-size: 2.5em;
            margin-bottom: 20px;
            text-align: center;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        h2 {
            color: #2d3748;
            font-size: 2em;
            margin-bottom: 15px;
            border-bottom: 3px solid #667eea;
            padding-bottom: 10px;
        }
        h3 {
            color: #4a5568;
            font-size: 1.5em;
            margin-bottom: 10px;
            margin-top: 20px;
        }
        p, li {
            line-height: 1.6;
            margin-bottom: 10px;
            font-size: 1.1em;
        }
        .circuit-diagram {
            background: #f7fafc;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            text-align: center;
            font-family: monospace;
            font-size: 14px;
            line-height: 1.4;
        }
        .component-box {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        .code-block {
            background: #2d3748;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            border-left: 4px solid #667eea;
        }
        .navigation {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 1000;
        }
        .nav-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        .nav-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
        }
        .nav-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        .slide-counter {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.9);
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            color: #4a5568;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .feature-card {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        .feature-card:hover {
            transform: translateY(-5px);
        }
        .pin-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        .pin-table th, .pin-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }
        .pin-table th {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            font-weight: bold;
        }
        .pin-table tr:nth-child(even) {
            background: #f7fafc;
        }
        .warning-box {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-left: 4px solid #ff6b6b;
            padding: 15px;
            margin: 15px 0;
            border-radius: 10px;
        }
        ul {
            padding-left: 20px;
        }
        li {
            margin-bottom: 8px;
        }
        .video-container {
            position: relative;
            width: 100%;
            height: 0;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            margin: 20px 0;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        .video-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }
        .image-container {
            text-align: center;
            margin: 20px 0;
        }
        .image-container img {
            max-width: 100%;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        .image-caption {
            margin-top: 10px;
            font-style: italic;
            color: #666;
        }
        .quiz-container {
            background: #f7fafc;
            border-radius: 15px;
            padding: 20px;
            margin: 20px 0;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        .quiz-question {
            font-weight: bold;
            margin-bottom: 15px;
            font-size: 1.2em;
        }
        .quiz-options {
            display: grid;
            gap: 10px;
        }
        .quiz-option {
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            padding: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .quiz-option:hover {
            border-color: #667eea;
            background: #f0f4ff;
        }
        .quiz-option.selected {
            background: #667eea;
            color: white;
            border-color: #667eea;
        }
        .quiz-result {
            margin-top: 15px;
            padding: 10px;
            border-radius: 8px;
            font-weight: bold;
            display: none;
        }
        .quiz-result.correct {
            background: #c6f6d5;
            color: #2f855a;
            border: 1px solid #9ae6b4;
        }
        .quiz-result.incorrect {
            background: #fed7d7;
            color: #c53030;
            border: 1px solid #fc8181;
        }
        .resources-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .resource-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        .resource-card:hover {
            transform: translateY(-5px);
        }
        .resource-image {
            height: 180px;
            background-size: cover;
            background-position: center;
        }
        .resource-content {
            padding: 20px;
        }
        .resource-title {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 10px;
            color: #2d3748;
        }
        .resource-description {
            color: #4a5568;
            margin-bottom: 15px;
        }
        .resource-link {
            display: inline-block;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        .resource-link:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        .bookmark-btn {
            position: fixed;
            top: 20px;
            left: 20px;
            background: rgba(255, 255, 255, 0.9);
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            z-index: 1000;
        }
        .bookmark-btn:hover {
            background: white;
            transform: scale(1.1);
        }
        .bookmark-btn.bookmarked {
            background: #f56565;
            color: white;
        }
        .notes-section {
            background: #f7fafc;
            border-radius: 10px;
            padding: 15px;
            margin: 20px 0;
        }
        .notes-textarea {
            width: 100%;
            min-height: 100px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            padding: 10px;
            font-family: inherit;
            font-size: 1em;
            resize: vertical;
        }
        .notes-textarea:focus {
            outline: none;
            border-color: #667eea;
        }
        .save-notes-btn {
            background: #667eea;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        .save-notes-btn:hover {
            background: #5a67d8;
        }
        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: rgba(255, 255, 255, 0.3);
            z-index: 1000;
        }
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            width: 0%;
            transition: width 0.5s ease;
        }
        .evaluation-container {
            background: #f7fafc;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border: 2px solid #e2e8f0;
        }
        .answer-key-container {
            background: #f0fff4;
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border: 2px solid #9ae6b4;
        }
        .print-btn {
            background: #667eea;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        .print-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
        }
        @media (max-width: 768px) {
            .slide {
                width: 95%;
                height: 90vh;
                padding: 20px;
            }
            
            h1 {
                font-size: 2em;
            }
            
            h2 {
                font-size: 1.5em;
            }
            
            .navigation {
                bottom: 20px;
            }
            
            .nav-btn {
                padding: 10px 20px;
                font-size: 14px;
            }
            
            .resources-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Print Styles */
        @media print {
            body {
                background: white;
                overflow: visible;
            }
            
            .slideshow-container {
                position: static;
                height: auto;
            }
            
            .slide {
                display: block !important;
                width: 100%;
                height: auto;
                margin: 0;
                padding: 20px;
                box-shadow: none;
                border-radius: 0;
            }
            
            .navigation,
            .slide-counter,
            .bookmark-btn,
            .progress-bar {
                display: none !important;
            }
            
            .component-box,
            .warning-box {
                background: white !important;
                border: 1px solid #ddd !important;
                color: black !important;
            }
            
            .feature-card,
            .resource-card {
                background: white !important;
                border: 1px solid #ddd !important;
            }
            
            .evaluation-container,
            .answer-key-container {
                border: 1px solid #ddd !important;
                background: white !important;
            }
        }
    </style>
</head>
<body>
    <div class="progress-bar">
        <div class="progress-fill" id="progressFill"></div>
    </div>
    
    <button class="bookmark-btn" id="bookmarkBtn" title="Bookmark Slide">
        <i class="far fa-bookmark"></i>
    </button>
    
    <div class="slide-counter">
        <span id="currentSlide">1</span> / <span id="totalSlides">19</span>
    </div>
    
    <div class="slideshow-container">
        <!-- Slide 1: Cover -->
        <div class="slide active">
            <h1>🔬 IR SENSOR dengan IC 4017</h1>
            <div style="text-align: center; margin: 40px 0;">
                <div class="image-container">
                    <img src="https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Electronic Circuit">
                    <div class="image-caption">Sistem Elektronik Kontrol Otomatis</div>
                    <div class="image-caption">Oleh : Hadi Waluyo budi yono </div>
                </div>
                <div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 30px; border-radius: 20px; box-shadow: 0 15px 30px rgba(0,0,0,0.2); margin-top: 30px;">
                    <h2 style="color: white; border: none; margin-bottom: 20px;">📡 Sistem Otomatis dengan Output Relay</h2>
                    <p style="font-size: 1.3em; margin-bottom: 30px;">Panduan Lengkap Rangkaian Elektronik untuk Kontrol Otomatis</p>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-top: 30px;">
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px;">
                            <strong>📚 Teori</strong><br>
                            Konsep dasar IR Sensor
                        </div>
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px;">
                            <strong>🔧 Praktik</strong><br>
                            Rangkaian & Programming
                        </div>
                        <div style="background: rgba(255,255,255,0.2); padding: 15px; border-radius: 10px;">
                            <strong>⚡ Aplikasi</strong><br>
                            Implementasi Nyata
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Slide 2: Pendahuluan -->
        <div class="slide">
            <h2>📖 Pendahuluan</h2>
            <p>Selamat datang di panduan lengkap tentang <strong>IR Sensor dengan IC 4017 dan output relay</strong>! Materi ini dirancang untuk memberikan pemahaman komprehensif tentang sistem deteksi otomatis menggunakan infrared.</p>
            
            <h3>🎯 Tujuan Pembelajaran</h3>
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🔍 Memahami</h4>
                    <p>Prinsip kerja IR sensor dan karakteristiknya</p>
                </div>
                <div class="feature-card">
                    <h4>⚙️ Menguasai</h4>
                    <p>Fungsi IC 4017 sebagai decade counter</p>
                </div>
                <div class="feature-card">
                    <h4>🔧 Merakit</h4>
                    <p>Rangkaian lengkap dengan output relay</p>
                </div>
                <div class="feature-card">
                    <h4>💡 Mengaplikasikan</h4>
                    <p>Sistem kontrol otomatis dalam kehidupan sehari-hari</p>
                </div>
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Introduction to IR Sensors"></iframe>
            </div>
            
            <div class="component-box">
                <strong>💡 Mengapa Kombinasi Ini Powerful?</strong><br>
                IR Sensor memberikan deteksi tanpa kontak, IC 4017 menyediakan kontrol sekuensial yang presisi, dan relay memungkinkan kontrol beban besar dengan aman!
            </div>
        </div>
        
        <!-- Slide 3: IR Sensor Basics -->
        <div class="slide">
            <h2>🔴 Dasar-Dasar IR Sensor</h2>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="IR Sensor Module">
                <div class="image-caption">Modul IR Sensor Tipe FC-51</div>
            </div>
            
            <h3>📡 Apa itu IR Sensor?</h3>
            <p>IR (Infrared) Sensor adalah perangkat elektronik yang dapat mendeteksi radiasi inframerah. Sensor ini bekerja dengan memancarkan sinar inframerah dan mendeteksi pantulannya dari objek di sekitar.</p>
            
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🌡️ Spektrum Inframerah</h4>
                    <p>Bekerja pada panjang gelombang 700nm - 1mm</p>
                </div>
                <div class="feature-card">
                    <h4>👁️ Deteksi Objek</h4>
                    <p>Dapat mendeteksi keberadaan objek tanpa kontak fisik</p>
                </div>
                <div class="feature-card">
                    <h4>🔄 Output Digital</h4>
                    <p>Menghasilkan sinyal HIGH/LOW untuk kontrol</p>
                </div>
            </div>
            
            <h3>⚙️ Komponen IR Sensor Module</h3>
            <ul>
                <li><strong>IR LED Transmitter:</strong> Memancarkan sinar inframerah</li>
                <li><strong>IR Photodiode Receiver:</strong> Mendeteksi pantulan sinar IR</li>
                <li><strong>Komparator:</strong> Mengubah sinyal analog menjadi digital</li>
                <li><strong>Potensiometer:</strong> Mengatur sensitivitas deteksi</li>
                <li><strong>LED Indikator:</strong> Menunjukkan status deteksi</li>
            </ul>
            
            <div class="video-container">
                <iframe src="https://youtu.be/wOhrx3fAgkQ?si=BD6djHZxR9Vtr4yE" title="Prinsip Kerja IC 4017"></iframe>
            </div>
            
            <div class="warning-box">
                <strong>⚠️ Catatan Penting:</strong> Jarak deteksi IR sensor umumnya 2-30cm tergantung pada warna dan material objek. Objek berwarna gelap lebih mudah dideteksi daripada objek terang.
            </div>
        </div>
        
        <!-- Slide 4: IC 4017 -->
        <div class="slide">
            <h2>🔢 IC 4017 - Decade Counter</h2>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1596495578061-599f179cd90c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="IC 4017">
                <div class="image-caption">IC 4017 Decade Counter</div>
            </div>
            
            <h3>🧠 Fungsi IC 4017</h3>
            <p>IC 4017 adalah <strong>decade counter</strong> yang dapat menghitung dari 0 hingga 9 dan kembali ke 0. Setiap kali menerima pulsa clock, output akan berpindah ke pin berikutnya secara berurutan.</p>
            
            <table class="pin-table">
                <thead>
                    <tr>
                        <th>Pin</th>
                        <th>Nama</th>
                        <th>Fungsi</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>1</td><td>Q5</td><td>Output 5</td></tr>
                    <tr><td>2</td><td>Q1</td><td>Output 1</td></tr>
                    <tr><td>3</td><td>Q0</td><td>Output 0 (START)</td></tr>
                    <tr><td>4</td><td>Q2</td><td>Output 2</td></tr>
                    <tr><td>5</td><td>Q6</td><td>Output 6</td></tr>
                    <tr><td>6</td><td>Q7</td><td>Output 7</td></tr>
                    <tr><td>7</td><td>Q3</td><td>Output 3</td></tr>
                    <tr><td>8</td><td>GND</td><td>Ground</td></tr>
                    <tr><td>9</td><td>Q8</td><td>Output 8</td></tr>
                    <tr><td>10</td><td>Q4</td><td>Output 4</td></tr>
                    <tr><td>11</td><td>Q9</td><td>Output 9</td></tr>
                    <tr><td>12</td><td>CO</td><td>Carry Out</td></tr>
                    <tr><td>13</td><td>INHIBIT</td><td>Enable/Disable (Active HIGH)</td></tr>
                    <tr><td>14</td><td>CLOCK</td><td>Input Clock</td></tr>
                    <tr><td>15</td><td>RESET</td><td>Reset ke Q0 (Active HIGH)</td></tr>
                    <tr><td>16</td><td>VDD</td><td>Supply Voltage (+5V)</td></tr>
                </tbody>
            </table>
            
            <div class="video-container">
                <iframe src="https://youtu.be/WIIcYPLMbgM?si=rKQO_vUsV8FsbF-N" title="Apa itu IC CD4017 | Cara menggunakan IC CD4017"></iframe>
            </div>
            
            <div class="component-box">
                <strong>🎯 Keunggulan IC 4017:</strong><br>
                • Counting otomatis tanpa programming kompleks<br>
                • Output dapat langsung mengontrol relay melalui transistor<br>
                • Dapat direset kapan saja untuk memulai urutan baru<br>
                • Konsumsi daya rendah dan stabil
            </div>
        </div>
        
        <!-- Slide 5: Relay Basics -->
        <div class="slide">
            <h2>🔌 Relay sebagai Output Actuator</h2>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581094271901-8022df4466f9?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Relay Module">
                <div class="image-caption">5V Relay Module</div>
            </div>
            
            <h3>⚡ Apa itu Relay?</h3>
            <p>Relay adalah saklar elektromaknetik yang dapat mengontrol rangkaian dengan daya besar menggunakan sinyal kontrol berdaya kecil. Ini memungkinkan mikrokontroler mengontrol lampu, motor, atau perangkat AC dengan aman.</p>
            
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🔐 Isolasi Elektrik</h4>
                    <p>Memisahkan rangkaian kontrol dari rangkaian beban</p>
                </div>
                <div class="feature-card">
                    <h4>⚡ Switching Tinggi</h4>
                    <p>Dapat mengontrol beban hingga 220V AC / 10A</p>
                </div>
                <div class="feature-card">
                    <h4>🔄 Kontrol Digital</h4>
                    <p>Diaktifkan dengan sinyal TTL 5V</p>
                </div>
            </div>
            
            <h3>🔧 Jenis-Jenis Relay</h3>
            <ul>
                <li><strong>SPDT (Single Pole Double Throw):</strong> 1 input, 2 output (NO & NC)</li>
                <li><strong>DPDT (Double Pole Double Throw):</strong> 2 input, 4 output</li>
                <li><strong>Relay Module:</strong> Sudah dilengkapi dengan driver transistor dan LED indikator</li>
            </ul>
            
            <div class="circuit-diagram">
                <strong>📐 Struktur Relay Module:</strong><br><br>
                [VCC] ── (+5V Power)<br>
                [GND] ── (Ground)<br>
                [IN]  ── (Control Signal dari IC 4017)<br>
                [COM] ── (Common Terminal)<br>
                [NO]  ── (Normally Open)<br>
                [NC]  ── (Normally Close)
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="How Relays Work"></iframe>
            </div>
        </div>
        
        <!-- Slide 6: Circuit Design -->
        <div class="slide">
            <h2>🎛️ Desain Rangkaian Lengkap</h2>
            
            <h3>📋 Komponen yang Dibutuhkan</h3>
            <ul>
                <li>1x IR Sensor Module (FC-51 atau sejenisnya)</li>
                <li>1x IC 4017 (CD4017BE)</li>
                <li>1x Relay Module 5V</li>
                <li>1x Resistor 1kΩ</li>
                <li>1x Kapasitor 100nF (untuk debouncing)</li>
                <li>1x LED + Resistor 330Ω (indikator)</li>
                <li>Breadboard dan jumper wires</li>
                <li>Power Supply 5V</li>
            </ul>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1596495577886-9a6a4a9e7a7f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Circuit Components">
                <div class="image-caption">Komponen-komponen Rangkaian</div>
            </div>
            
            <div class="circuit-diagram">
                <strong>🔗 DIAGRAM RANGKAIAN:</strong><br><br>
                <div style="text-align: center; margin: 20px 0;">
                    <img src="https://via.placeholder.com/600x400?text=Circuit+Diagram+IR+Sensor+%2B+IC+4017+%2B+Relay" alt="Circuit Diagram" style="max-width: 100%; border-radius: 10px;">
                </div>
                <br>
                <strong>Koneksi Utama:</strong><br>
                • IR OUT → IC 4017 Pin 14 (CLOCK)<br>
                • IC 4017 Pin 15 (RESET) → GND<br>
                • IC 4017 Pin 13 (INHIBIT) → GND<br>
                • IC 4017 Q0-Q9 → Relay Module Inputs<br>
                • Relay VCC → +5V<br>
                • Relay GND → GND
            </div>
            
            <div class="component-box">
                <strong>🎯 Prinsip Kerja:</strong><br>
                Setiap kali IR sensor mendeteksi objek → Clock pulse ke IC 4017 → Output berpindah ke pin berikutnya → Relay ON/OFF sesuai urutan
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Complete Circuit Assembly"></iframe>
            </div>
        </div>
        
        <!-- Slide 7: Assembly Steps -->
        <div class="slide">
            <h2>🔨 Langkah-Langkah Perakitan</h2>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581093450021-4a7360e9a6b5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Assembly Process">
                <div class="image-caption">Proses Perakitan Rangkaian</div>
            </div>
            
            <h3>📝 Persiapan</h3>
            <ol>
                <li>Siapkan semua komponen dan periksa kondisinya</li>
                <li>Pastikan breadboard dan jumper wires dalam kondisi baik</li>
                <li>Tes power supply 5V dengan multimeter</li>
            </ol>
            
            <h3>🔧 Perakitan Step-by-Step</h3>
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div>
                    <h4>Step 1-3: Foundation</h4>
                    <ul>
                        <li><strong>Step 1:</strong> Pasang IC 4017 di breadboard</li>
                        <li><strong>Step 2:</strong> Hubungkan power rail (+5V & GND)</li>
                        <li><strong>Step 3:</strong> Koneksi power ke IC 4017</li>
                    </ul>
                </div>
                <div>
                    <h4>Step 4-6: Sensors & Output</h4>
                    <ul>
                        <li><strong>Step 4:</strong> Pasang IR sensor dan hubungkan power</li>
                        <li><strong>Step 5:</strong> Koneksi IR sensor OUT ke IC Clock</li>
                        <li><strong>Step 6:</strong> Hubungkan relay module</li>
                    </ul>
                </div>
            </div>
            
            <div class="warning-box">
                <strong>⚠️ Tips Perakitan:</strong><br>
                • Selalu matikan power saat memasang komponen<br>
                • Periksa polaritas power supply<br>
                • Gunakan jumper wires yang berbeda warna untuk memudahkan troubleshooting<br>
                • Test setiap koneksi dengan multimeter
            </div>
            
            <h3>✅ Checklist Akhir</h3>
            <ul>
                <li>Semua koneksi power sudah benar</li>
                <li>IR sensor dapat mendeteksi objek (LED indikator menyala)</li>
                <li>IC 4017 mendapat supply voltage stabil</li>
                <li>Relay module merespon sinyal kontrol</li>
            </ul>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Step by Step Assembly Guide"></iframe>
            </div>
        </div>
        
        <!-- Slide 8: Working Principle -->
        <div class="slide">
            <h2>⚙️ Prinsip Kerja Sistem</h2>
            
            <h3>🔄 Alur Kerja Sistem</h3>
            <div style="background: #f7fafc; padding: 20px; border-radius: 15px; margin: 20px 0;">
                <div style="display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 10px;">
                    <div style="background: #667eea; color: white; padding: 15px; border-radius: 10px; text-align: center; flex: 1; min-width: 150px;">
                        <strong>1️⃣ DETEKSI</strong><br>
                        IR Sensor mendeteksi objek
                    </div>
                    <div style="font-size: 2em; color: #667eea;">→</div>
                    <div style="background: #764ba2; color: white; padding: 15px; border-radius: 10px; text-align: center; flex: 1; min-width: 150px;">
                        <strong>2️⃣ COUNTING</strong><br>
                        IC 4017 menerima clock pulse
                    </div>
                    <div style="font-size: 2em; color: #764ba2;">→</div>
                    <div style="background: #f093fb; color: white; padding: 15px; border-radius: 10px; text-align: center; flex: 1; min-width: 150px;">
                        <strong>3️⃣ OUTPUT</strong><br>
                        Relay mengaktifkan beban
                    </div>
                </div>
            </div>
            
            <h3>📊 Sequence Output IC 4017</h3>
            <div class="circuit-diagram">
                <strong>Urutan Output saat Clock Pulse:</strong><br><br>
                Clock 1: Q0 (Pin 3) = HIGH → Relay 1 ON<br>
                Clock 2: Q1 (Pin 2) = HIGH → Relay 2 ON<br>
                Clock 3: Q2 (Pin 4) = HIGH → Relay 3 ON<br>
                Clock 4: Q3 (Pin 7) = HIGH → Relay 4 ON<br>
                Clock 5: Q4 (Pin 10) = HIGH → Relay 5 ON<br>
                ...<br>
                Clock 10: Q9 (Pin 11) = HIGH → Reset ke Q0
            </div>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581094271901-8022df4466f9?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Working Principle">
                <div class="image-caption">Animasi Prinsip Kerja Sistem</div>
            </div>
            
            <div class="component-box">
                <strong>🎯 Kelebihan Sistem Ini:</strong><br>
                • Kontrol sekuensial otomatis tanpa microcontroller<br>
                • Deteksi objek yang akurat dan responsif<br>
                • Dapat mengontrol multiple relay secara berurutan<br>
                • Rangkaian sederhana namun powerful untuk automasi
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="System Working Principle"></iframe>
            </div>
        </div>
        
        <!-- Slide 9: Programming & Logic -->
        <div class="slide">
            <h2>💻 Logic dan Programming Konsep</h2>
            
            <h3>🧮 State Machine Logic</h3>
            <p>Meskipun menggunakan IC analog, sistem ini bekerja layaknya state machine digital:</p>
            <div class="code-block">
                PSEUDOCODE LOGIC:
                
                STATE = 0  // Initial state
                
                WHILE (system_running) {
                    IF (IR_sensor_triggered) {
                        STATE = (STATE + 1) % 10  // Increment with rollover
                        ACTIVATE_RELAY(STATE)
                        WAIT_FOR_SENSOR_RESET()
                    }
                }
                
                FUNCTION ACTIVATE_RELAY(state) {
                    TURN_OFF_ALL_RELAYS()
                    TURN_ON_RELAY(state)
                }
            </div>
            
            <h3>⏱️ Timing Considerations</h3>
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🔄 Debouncing</h4>
                    <p>Kapasitor 100nF mencegah multiple triggering</p>
                </div>
                <div class="feature-card">
                    <h4>⏳ Response Time</h4>
                    <p>Sistem merespon dalam 1-5 milliseconds</p>
                </div>
                <div class="feature-card">
                    <h4>🔁 Reset Logic</h4>
                    <p>Auto-reset setelah Q9 atau manual reset</p>
                </div>
            </div>
            
            <div class="warning-box">
                <strong>💡 Pro Tips:</strong><br>
                • Gunakan pull-up resistor pada clock input untuk stabilitas<br>
                • Tambahkan debouncing circuit untuk menghindari false triggering<br>
                • Pertimbangkan menggunakan Schmitt trigger untuk sinyal clock yang lebih clean
            </div>
            
            <div class="quiz-container">
                <div class="quiz-question">Berapa jumlah maksimum output yang dapat dihasilkan oleh IC 4017 dalam satu siklus?</div>
                <div class="quiz-options">
                    <div class="quiz-option" onclick="selectOption(this, false)">8 output</div>
                    <div class="quiz-option" onclick="selectOption(this, true)">10 output</div>
                    <div class="quiz-option" onclick="selectOption(this, false)">12 output</div>
                    <div class="quiz-option" onclick="selectOption(this, false)">16 output</div>
                </div>
                <div class="quiz-result" id="quizResult1"></div>
            </div>
        </div>
        
        <!-- Slide 10: Applications -->
        <div class="slide">
            <h2>🚀 Aplikasi Praktis</h2>
            
            <h3>🏠 Aplikasi Smart Home</h3>
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>💡 Sequential Lighting</h4>
                    <p>Lampu menyala berurutan saat ada orang lewat</p>
                </div>
                <div class="feature-card">
                    <h4>🚪 Automatic Door</h4>
                    <p>Membuka pintu otomatis dengan sequence control</p>
                </div>
                <div class="feature-card">
                    <h4>🔔 Security Alert</h4>
                    <p>Sistem alarm bertingkat untuk keamanan</p>
                </div>
                <div class="feature-card">
                    <h4>💧 Water Dispenser</h4>
                    <p>Kontrol volume air berdasarkan jumlah deteksi</p>
                </div>
            </div>
            
            <h3>🏭 Aplikasi Industri</h3>
            <ul>
                <li><strong>Conveyor Counter:</strong> Menghitung produk yang lewat di conveyor belt</li>
                <li><strong>Quality Control:</strong> Sistem sortir otomatis berdasarkan sequence</li>
                <li><strong>Production Line:</strong> Kontrol tahapan produksi secara berurutan</li>
                <li><strong>Warehouse Automation:</strong> Sistem tracking barang masuk/keluar</li>
            </ul>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Industrial Application">
                <div class="image-caption">Aplikasi Industri Sistem Kontrol Otomatis</div>
            </div>
            
            <div class="component-box">
                <strong>🎯 Contoh Implementasi: Smart Parking Counter</strong><br>
                • IR sensor di pintu masuk mendeteksi mobil<br>
                • IC 4017 menghitung jumlah mobil yang masuk<br>
                • Relay mengontrol lampu indikator kapasitas parkir<br>
                • Setelah 10 mobil, sistem reset otomatis
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Real World Applications"></iframe>
            </div>
        </div>
        
        <!-- Slide 11: Troubleshooting -->
        <div class="slide">
            <h2>🔧 Troubleshooting & Tips</h2>
            
            <h3>❌ Masalah Umum dan Solusi</h3>
            
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div>
                    <h4>🚫 IR Sensor Tidak Responsif</h4>
                    <ul>
                        <li>Periksa koneksi power (+5V & GND)</li>
                        <li>Adjust potensiometer sensitivitas</li>
                        <li>Pastikan tidak ada interferensi cahaya</li>
                        <li>Cek jarak deteksi (2-30cm optimal)</li>
                    </ul>
                </div>
                <div>
                    <h4>🔄 IC 4017 Tidak Counting</h4>
                    <ul>
                        <li>Pastikan clock signal dari IR sensor stabil</li>
                        <li>Periksa pin RESET tidak terhubung ke HIGH</li>
                        <li>Cek pin INHIBIT terhubung ke GND</li>
                        <li>Verify power supply 5V stabil</li>
                    </ul>
                </div>
            </div>
            
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 20px;">
                <div>
                    <h4>⚡ Relay Tidak Aktif</h4>
                    <ul>
                        <li>Test relay dengan input manual 5V</li>
                        <li>Periksa LED indikator pada relay module</li>
                        <li>Cek koneksi output IC 4017 ke relay</li>
                        <li>Pastikan relay cocok dengan voltage supply</li>
                    </ul>
                </div>
                <div>
                    <h4>🔀 Output Tidak Berurutan</h4>
                    <ul>
                        <li>Periksa debouncing circuit</li>
                        <li>Tambahkan delay pada clock signal</li>
                        <li>Cek interferensi electromagnetic</li>
                        <li>Gunakan shielded cable jika perlu</li>
                    </ul>
                </div>
            </div>
            
            <div class="warning-box">
                <strong>🛡️ Safety Tips:</strong><br>
                • Selalu gunakan relay untuk beban AC high voltage<br>
                • Jangan hubungkan beban langsung ke output IC<br>
                • Pastikan proper grounding untuk semua komponen<br>
                • Gunakan fuse protection untuk beban tinggi
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Troubleshooting Guide"></iframe>
            </div>
        </div>
        
        <!-- Slide 12: Advanced Features -->
        <div class="slide">
            <h2>⚡ Fitur Lanjutan dan Modifikasi</h2>
            
            <h3>🔄 Reset Control</h3>
            <p>Untuk kontrol yang lebih fleksibel, Anda dapat menambahkan fitur reset manual atau otomatis:</p>
            
            <div class="code-block">
                RESET MODIFICATIONS:
                
                1. Manual Reset Button:
                   - Hubungkan push button ke pin 15 IC 4017
                   - Gunakan pull-down resistor 10kΩ
                   
                2. Automatic Reset setelah n-count:
                   - Hubungkan Qn ke pin 15 melalui diode
                   - Contoh: Q5 → Reset (count hanya 0-4)
                   
                3. Time-based Reset:
                   - Gunakan 555 timer untuk auto-reset periodik
                   - Interval reset dapat diatur dengan R-C values
            </div>
            
            <h3>🔀 Multiple Output Control</h3>
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🎪 Sequential Control</h4>
                    <p>Kontrol lampu hias berurutan untuk dekorasi</p>
                </div>
                <div class="feature-card">
                    <h4>🏭 Process Control</h4>
                    <p>Kontrol tahapan proses industri otomatis</p>
                </div>
                <div class="feature-card">
                    <h4>🎵 Audio Sequence</h4>
                    <p>Trigger sound effects berurutan</p>
                </div>
            </div>
            
            <h3>📈 Upgrade Possibilities</h3>
            <ul>
                <li><strong>Add Display:</strong> 7-segment display untuk menampilkan counter</li>
                <li><strong>Remote Control:</strong> Tambahkan IR receiver untuk kontrol jarak jauh</li>
                <li><strong>Data Logging:</strong> Simpan count data dengan RTC module</li>
                <li><strong>Wireless:</strong> Integrasikan dengan WiFi module untuk IoT</li>
            </ul>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1596495577886-9a6a4a9e7a7f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Advanced Features">
                <div class="image-caption">Implementasi Fitur Lanjutan</div>
            </div>
        </div>
        
        <!-- Slide 13: Project Examples -->
        <div class="slide">
            <h2>🛠️ Contoh Proyek Lengkap</h2>
            
            <h3>🚗 Proyek 1: Smart Parking Counter</h3>
            <div class="component-box">
                <strong>📋 Spesifikasi:</strong><br>
                • Menghitung mobil yang masuk parkiran<br>
                • Display LED menunjukkan jumlah slot terisi<br>
                • Relay mengontrol lampu indikator "PENUH"<br>
                • Auto-reset setiap 24 jam
            </div>
            
            <div class="circuit-diagram">
                <strong>🔌 Komponen Tambahan untuk Parking Counter:</strong><br><br>
                + 7-Segment Display (untuk menampilkan count)<br>
                + RTC Module DS3231 (untuk auto-reset harian)<br>
                + Buzzer (alarm saat penuh)<br>
                + LCD 16x2 (display info detail)<br>
                + Multiple relay untuk different indicators
            </div>
            
            <h3>💡 Proyek 2: Sequential Garden Sprinkler</h3>
            <div style="background: #e6fffa; padding: 20px; border-radius: 15px; border-left: 4px solid #38b2ac;">
                <strong>🌱 Konsep:</strong> Sistem penyiraman taman otomatis yang mengaktifkan sprinkler secara berurutan berdasarkan deteksi movement atau schedule.
                
                <h4 style="margin-top: 15px;">⚙️ Cara Kerja:</h4>
                <ul>
                    <li>IR sensor mendeteksi pergerakan di taman</li>
                    <li>IC 4017 mengaktifkan zona penyiraman berurutan</li>
                    <li>Setiap relay mengontrol solenoid valve untuk area berbeda</li>
                    <li>Timer circuit menentukan durasi penyiraman per zone</li>
                </ul>
            </div>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1596495577886-9a6a4a9e7a7f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Project Examples">
                <div class="image-caption">Implementasi Proyek Smart Garden</div>
            </div>
            
            <div class="video-container">
                <iframe src="https://www.youtube.com/embed/your_video_id_here" title="Complete Project Examples"></iframe>
            </div>
        </div>
        
        <!-- Slide 14: Testing & Calibration -->
        <div class="slide">
            <h2>🧪 Testing dan Kalibrasi</h2>
            
            <h3>🔍 Prosedur Testing</h3>
            
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div>
                    <h4>📊 Test IR Sensor</h4>
                    <ol>
                        <li>Ukur voltage output tanpa objek (LOW)</li>
                        <li>Dekatkan objek, cek output berubah ke HIGH</li>
                        <li>Test jarak deteksi minimum dan maksimum</li>
                        <li>Kalibrasi sensitivitas dengan potensiometer</li>
                    </ol>
                </div>
                <div>
                    <h4>⚡ Test IC 4017</h4>
                    <ol>
                        <li>Input manual clock pulse</li>
                        <li>Monitor output dengan LED atau multimeter</li>
                        <li>Verify sequence 0→1→2→...→9→0</li>
                        <li>Test reset functionality</li>
                    </ol>
                </div>
            </div>
            
            <h3>📏 Kalibrasi Parameter</h3>
            <table class="pin-table">
                <thead>
                    <tr>
                        <th>Parameter</th>
                        <th>Rentang</th>
                        <th>Optimal</th>
                        <th>Cara Setting</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>IR Detection Range</td>
                        <td>2-30 cm</td>
                        <td>5-15 cm</td>
                        <td>Putar potensiometer pada IR module</td>
                    </tr>
                    <tr>
                        <td>Clock Pulse Width</td>
                        <td>1-100 ms</td>
                        <td>10-50 ms</td>
                        <td>Tambah kapasitor debouncing</td>
                    </tr>
                    <tr>
                        <td>Relay Response Time</td>
                        <td>5-20 ms</td>
                        <td>10 ms</td>
                        <td>Pilih relay dengan spek yang sesuai</td>
                    </tr>
                </tbody>
            </table>
            
            <div class="component-box">
                <strong>🎯 Optimization Tips:</strong><br>
                • Gunakan oscilloscope untuk monitor clock signal<br>
                • Test dengan berbagai jenis objek (warna, material)<br>
                • Ukur konsumsi arus untuk efisiensi power<br>
                • Dokumentasikan setting optimal untuk reproduksi
            </div>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581094271901-8022df4466f9?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Testing Equipment">
                <div class="image-caption">Peralatan Testing dan Kalibrasi</div>
            </div>
        </div>
        
        <!-- Slide 15: Conclusion -->
        <div class="slide">
            <h2>🎓 Kesimpulan dan Pengembangan</h2>
            
            <h3>📚 Rangkuman Pembelajaran</h3>
            <p>Anda telah mempelajari sistem lengkap yang menggabungkan:</p>
            
            <div class="feature-grid">
                <div class="feature-card">
                    <h4>🔴 IR Sensor</h4>
                    <p>Deteksi objek tanpa kontak dengan sensitivitas adjustable</p>
                </div>
                <div class="feature-card">
                    <h4>🔢 IC 4017</h4>
                    <p>Decade counter untuk kontrol sekuensial otomatis</p>
                </div>
                <div class="feature-card">
                    <h4>🔌 Relay Output</h4>
                    <p>Interface ke beban AC/DC dengan isolasi aman</p>
                </div>
            </div>
            
            <h3>🚀 Langkah Pengembangan Selanjutnya</h3>
            <ol>
                <li><strong>Integrasi Microcontroller:</strong> Tambahkan Arduino/ESP32 untuk kontrol yang lebih kompleks</li>
                <li><strong>Wireless Communication:</strong> Implementasi WiFi/Bluetooth untuk remote monitoring</li>
                <li><strong>Machine Learning:</strong> Pattern recognition untuk deteksi objek yang lebih sophisticated</li>
                <li><strong>IoT Integration:</strong> Hubungkan ke cloud platform untuk data analytics</li>
            </ol>
            
            <div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white; padding: 30px; border-radius: 20px; text-align: center; margin: 30px 0;">
                <h3 style="color: white; margin-bottom: 15px;">🌟 Selamat!</h3>
                <p style="font-size: 1.2em;">Anda telah menguasai dasar-dasar sistem IR sensor dengan IC 4017 dan relay output. Sistem ini dapat menjadi foundation untuk berbagai proyek automation yang lebih advanced!</p>
                <div style="margin-top: 20px; font-size: 1.1em;">
                    <strong>📞 Support & Resources:</strong><br>
                    • Datasheet IC 4017 untuk referensi detail<br>
                    • Community forum untuk diskusi dan troubleshooting<br>
                    • Video tutorial untuk visualisasi yang lebih baik
                </div>
            </div>
            
            <div class="warning-box">
                <strong>💡 Remember:</strong> Praktik terbaik adalah selalu test circuit step-by-step, dokumentasikan setting yang bekerja, dan prioritaskan safety dalam implementasi dengan beban real!
            </div>
            
            <div class="image-container">
                <img src="https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Success">
                <div class="image-caption">Selamat Menyelesaikan Pembelajaran!</div>
            </div>
        </div>
        
        <!-- Slide 16: Evaluation Questions -->
        <div class="slide">
            <h2>📝 Evaluasi Pembelajaran</h2>
            
            <div class="component-box">
                <strong>📋 Petunjuk:</strong><br>
                • Jawablah 5 soal berikut di kertas Anda<br>
                • Soal dapat disalin langsung dari layar<br>
                • Waktu pengerjaan: 15 menit<br>
                • Kunci jawaban tersedia di slide berikutnya
            </div>
            
            <h3>📝 Soal-Soal Evaluasi</h3>
            
            <div class="evaluation-container">
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 1 (Pilihan Ganda)</strong><br>
                    IR Sensor bekerja dengan mendeteksi jenis radiasi apa?<br>
                    A. Ultraviolet<br>
                    B. Inframerah<br>
                    C. Radio waves<br>
                    D. Visible light<br><br>
                    Jawaban: __________
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 2 (Pilihan Ganda)</strong><br>
                    Berapa jumlah output yang dimiliki oleh IC 4017 dalam satu siklus lengkap?<br>
                    A. 8 output<br>
                    B. 10 output<br>
                    C. 12 output<br>
                    D. 16 output<br><br>
                    Jawaban: __________
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 3 (Isian Singkat)</strong><br>
                    Sebutkan 3 komponen utama yang terdapat pada modul IR sensor!<br>
                    1. _________________________<br>
                    2. _________________________<br>
                    3. _________________________
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 4 (Uraian Singkat)</strong><br>
                    Jelaskan secara singkat fungsi utama dari relay dalam rangkaian elektronik!<br>
                    Jawaban: ___________________________________________________________<br>
                    ___________________________________________________________<br>
                    ___________________________________________________________
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 5 (Aplikasi)</strong><br>
                    Buatlah contoh satu aplikasi praktis dari sistem IR Sensor + IC 4017 + Relay dalam kehidupan sehari-hari, dan jelaskan cara kerjanya!<br><br>
                    Nama Aplikasi: _________________________<br>
                    Cara Kerja: ___________________________________________________<br>
                    ___________________________________________________________<br>
                    ___________________________________________________________
                </div>
                
            </div>
            
            <div class="warning-box">
                <strong>⏰ Tips Pengerjaan:</strong><br>
                • Baca setiap soal dengan teliti sebelum menjawab<br>
                • Gunakan pengetahuan dari slide-slide sebelumnya<br>
                • Untuk soal uraian, jawab dengan jelas dan singkat<br>
                • Kerjakan secara mandiri tanpa melihat kunci jawaban
            </div>
            
            <div style="text-align: center; margin-top: 30px;">
                <button onclick="printEvaluation()" class="print-btn">
                    <i class="fas fa-print"></i> Cetak Soal
                </button>
            </div>
        </div>
        
        <!-- Slide 17: Answer Key -->
        <div class="slide">
            <h2>🔑 Kunci Jawaban Evaluasi</h2>
            
            <div class="component-box">
                <strong>⚠️ Peringatan:</strong><br>
                Periksa jawaban Anda setelah selesai mengerjakan semua soal!
            </div>
            
            <h3>📝 Kunci Jawaban Lengkap</h3>
            
            <div class="answer-key-container">
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 1:</strong><br>
                    Jawaban: <span style="color: #38a169; font-weight: bold;">B. Inframerah</span><br>
                    <em>Penjelasan: IR Sensor (Infrared Sensor) bekerja dengan mendeteksi radiasi inframerah yang tidak terlihat oleh mata manusia.</em>
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 2:</strong><br>
                    Jawaban: <span style="color: #38a169; font-weight: bold;">B. 10 output</span><br>
                    <em>Penjelasan: IC 4017 adalah decade counter yang memiliki 10 output (Q0 sampai Q9) yang aktif secara berurutan.</em>
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 3:</strong><br>
                    Jawaban:<br>
                    1. <span style="color: #38a169; font-weight: bold;">IR LED Transmitter</span> (memancarkan sinar IR)<br>
                    2. <span style="color: #38a169; font-weight: bold;">IR Photodiode Receiver</span> (mendeteksi pantulan sinar IR)<br>
                    3. <span style="color: #38a169; font-weight: bold;">Komparator</span> (mengubah sinyal analog menjadi digital)<br>
                    <em>Jawaban alternatif yang dapat diterima: Potensiometer, LED Indikator</em>
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 4:</strong><br>
                    Jawaban:<br>
                    <span style="color: #38a169; font-weight: bold;">Relay berfungsi sebagai saklar elektromekanis yang dapat mengontrol rangkaian dengan daya besar menggunakan sinyal kontrol berdaya kecil. Relay menyediakan isolasi elektrik antara rangkaian kontrol (low voltage) dengan rangkaian beban (high voltage), sehingga aman untuk mengontrol perangkat AC seperti lampu, motor, atau peralatan listrik lainnya.</span>
                </div>
                
                <div style="margin-bottom: 25px;">
                    <strong>Soal 5:</strong><br>
                    <strong>Contoh Jawaban:</strong><br>
                    Nama Aplikasi: <span style="color: #38a169; font-weight: bold;">Smart Parking Counter</span><br>
                    Cara Kerja: <span style="color: #38a169; font-weight: bold;">IR sensor dipasang di pintu masuk parkiran untuk mendeteksi mobil yang masuk. Setiap kali mobil terdeteksi, sensor mengirimkan sinyal ke IC 4017 sebagai clock pulse. IC 4017 menghitung jumlah mobil dan mengaktifkan relay untuk menyalakan lampu indikator. Setelah mencapai kapasitas maksimal (misal 10 mobil), sistem akan menyalakan lampu "PENUH" dan bisa direset secara otomatis atau manual.</span><br><br>
                    <em>Jawaban lain yang dapat diterima: Automatic Door, Sequential Lighting, Security System, Water Dispenser Control, dll.</em>
                </div>
                
            </div>
            
            <div style="background: #fef5e7; border-radius: 15px; padding: 20px; margin: 20px 0; border-left: 4px solid #f39c12;">
                <strong>📊 Kriteria Penilaian:</strong><br>
                • Soal 1 & 2: 20 poin (benar = 20, salah = 0)<br>
                • Soal 3: 20 poin (setiap jawaban benar = 6.67 poin)<br>
                • Soal 4: 20 poin (berdasarkan kelengkapan dan kebenaran konsep)<br>
                • Soal 5: 20 poin (berdasarkan kreativitas dan pemahaman aplikasi)<br>
                <br>
                <strong>Total Nilai Maksimal: 100 poin</strong>
            </div>
            
            <div class="warning-box">
                <strong>💡 Saran untuk Pengajar:</strong><br>
                • Diskusikan jawaban bersama peserta didik<br>
                • Berikan kesempatan untuk bertanya jika ada jawaban yang kurang jelas<br>
                • Berikan contoh aplikasi tambahan untuk memperkaya pemahaman
            </div>
        </div>
        
        <!-- Slide 18: Resources & References -->
        <div class="slide">
            <h2>📚 Sumber Belajar & Referensi</h2>
            
            <h3>📖 Buku dan Dokumentasi</h3>
            <div class="resources-grid">
                <div class="resource-card">
                    <div class="resource-image" style="background-image: url('https://images.unsplash.com/photo-1531482615713-2afd69097998?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="resource-content">
                        <div class="resource-title">Datasheet IC 4017</div>
                        <div class="resource-description">Dokumentasi teknis lengkap IC 4017 dari Texas Instruments</div>
                        <a href="https://www.ti.com/lit/ds/symlink/cd4017b.pdf" target="_blank" class="resource-link">Download PDF</a>
                    </div>
                </div>
                <div class="resource-card">
                    <div class="resource-image" style="background-image: url('https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="resource-content">
                        <div class="resource-title">Practical Electronics</div>
                        <div class="resource-description">Buku panduan praktis elektronika untuk pemula</div>
                        <a href="#" target="_blank" class="resource-link">Learn More</a>
                    </div>
                </div>
            </div>
            
            <h3>🎥 Video Tutorial Rekomendasi</h3>
            <div class="resources-grid">
                <div class="resource-card">
                    <div class="resource-image" style="background-image: url('https://images.unsplash.com/photo-1596495577886-9a6a4a9e7a7f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="resource-content">
                        <div class="resource-title">IR Sensor Tutorial</div>
                        <div class="resource-description">Panduan lengkap cara kerja IR sensor</div>
                        <a href="https://www.youtube.com/watch?v=your_video_id" target="_blank" class="resource-link">Watch Video</a>
                    </div>
                </div>
                <div class="resource-card">
                    <div class="resource-image" style="background-image: url('https://images.unsplash.com/photo-1596495577886-9a6a4a9e7a7f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="resource-content">
                        <div class="resource-title">IC 4017 Projects</div>
                        <div class="resource-description">10 proyek menarik dengan IC 4017</div>
                        <a href="https://www.youtube.com/watch?v=your_video_id" target="_blank" class="resource-link">Watch Video</a>
                    </div>
                </div>
                <div class="resource-card">
                    <div class="resource-image" style="background-image: url('https://images.unsplash.com/photo-1581094794329-c8112a89af12?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');"></div>
                    <div class="resource-content">
                        <div class="resource-title">Relay Control Systems</div>
                        <div class="resource-description">Mengontrol beban besar dengan relay</div>
                        <a href="https://www.youtube.com/watch?v=your_video_id" target="_blank" class="resource-link">Watch Video</a>
                    </div>
                </div>
            </div>
            
            <h3>🌐 Forum & Komunitas</h3>
            <ul>
                <li><strong>Electronics Stack Exchange:</strong> Forum Q&A untuk pertanyaan teknis</li>
                <li><strong>Arduino Forum:</strong> Komunitas penggemar mikrokontroler</li>
                <li><strong>Reddit r/electronics:</strong> Diskusi umum elektronika</li>
                <li><strong>Facebook Groups:</strong> Grup lokal elektronika Indonesia</li>
            </ul>
            
            <div class="component-box">
                <strong>💡 Tips Belajar Efektif:</strong><br>
                • Mulai dengan proyek sederhana sebelum yang kompleks<br>
                • Bergabung dengan komunitas untuk bertanya dan berbagi<br>
                • Dokumentasikan setiap proyek yang Anda buat<br>
                • Jangan takut untuk mencoba dan gagal
            </div>
        </div>
        
        <!-- Slide 19: Notes & Bookmarks -->
        <div class="slide">
            <h2>📝 Catatan Pribadi & Bookmark</h2>
            
            <div class="notes-section">
                <h3>📝 Catatan Pembelajaran</h3>
                <textarea class="notes-textarea" id="notesTextarea" placeholder="Tulis catatan pribadi Anda di sini..."></textarea>
                <button class="save-notes-btn" onclick="saveNotes()">Simpan Catatan</button>
                <div id="notesStatus" style="margin-top: 10px; color: #38a169; font-weight: bold;"></div>
            </div>
            
            <h3>🔖 Slide yang Dibookmark</h3>
            <div id="bookmarkedSlides" style="background: #f7fafc; border-radius: 10px; padding: 15px; margin: 20px 0;">
                <p style="color: #718096;">Belum ada slide yang dibookmark. Klik ikon bookmark di sudut kiri atas untuk menandai slide penting.</p>
            </div>
            
            <h3>📊 Progress Pembelajaran</h3>
            <div style="background: #f7fafc; border-radius: 10px; padding: 20px; margin: 20px 0;">
                <p>Anda telah menyelesaikan <span id="progressPercent">0</span>% dari materi pembelajaran.</p>
                <div style="background: #e2e8f0; height: 20px; border-radius: 10px; margin-top: 10px; overflow: hidden;">
                    <div id="progressBar" style="background: linear-gradient(90deg, #667eea, #764ba2); height: 100%; width: 0%; transition: width 0.5s ease;"></div>
                </div>
            </div>
            
            <div class="component-box">
                <strong>🎯 Tips Menggunakan Catatan:</strong><br>
                • Gunakan catatan untuk mencatat ide proyek baru<br>
                • Dokumentasikan troubleshooting yang Anda temui<br>
                • Catatan tersimpan di browser Anda<br>
                • Bookmark slide penting untuk akses cepat
            </div>
        </div>
    </div>
    
    <div class="navigation">
        <button class="nav-btn" onclick="previousSlide()" id="prevBtn">◀ Previous</button>
        <button class="nav-btn" onclick="nextSlide()" id="nextBtn">Next ▶</button>
    </div>
    
    <script>
        let currentSlideIndex = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;
        
        document.getElementById('totalSlides').textContent = totalSlides;
        
        // Initialize bookmarks and notes
        let bookmarks = JSON.parse(localStorage.getItem('bookmarks')) || [];
        let notes = JSON.parse(localStorage.getItem('notes')) || {};
        
        function showSlide(index) {
            slides.forEach(slide => slide.classList.remove('active'));
            slides[index].classList.add('active');
            
            document.getElementById('currentSlide').textContent = index + 1;
            
            // Update navigation buttons
            document.getElementById('prevBtn').disabled = index === 0;
            document.getElementById('nextBtn').disabled = index === totalSlides - 1;
            
            // Update bookmark button
            updateBookmarkButton(index);
            
            // Update progress
            updateProgress();
            
            // Load notes for this slide
            loadNotes(index);
            
            // Update bookmarks display if on bookmarks slide
            if (index === totalSlides - 1) {
                updateBookmarksDisplay();
            }
        }
        
        function nextSlide() {
            if (currentSlideIndex < totalSlides - 1) {
                currentSlideIndex++;
                showSlide(currentSlideIndex);
            }
        }
        
        function previousSlide() {
            if (currentSlideIndex > 0) {
                currentSlideIndex--;
                showSlide(currentSlideIndex);
            }
        }
        
        // Keyboard navigation
        document.addEventListener('keydown', function(event) {
            if (event.key === 'ArrowRight') {
                nextSlide();
            } else if (event.key === 'ArrowLeft') {
                previousSlide();
            }
        });
        
        // Touch/swipe support for mobile
        let startX = null;
        
        document.addEventListener('touchstart', function(event) {
            startX = event.touches[0].clientX;
        });
        
        document.addEventListener('touchend', function(event) {
            if (startX === null) return;
            
            const endX = event.changedTouches[0].clientX;
            const diffX = startX - endX;
            
            if (Math.abs(diffX) > 50) { // Minimum swipe distance
                if (diffX > 0) {
                    nextSlide(); // Swipe left = next
                } else {
                    previousSlide(); // Swipe right = previous
                }
            }
            
            startX = null;
        });
        
        // Bookmark functionality
        document.getElementById('bookmarkBtn').addEventListener('click', function() {
            toggleBookmark(currentSlideIndex);
        });
        
        function toggleBookmark(index) {
            const bookmarkIndex = bookmarks.indexOf(index);
            
            if (bookmarkIndex === -1) {
                bookmarks.push(index);
            } else {
                bookmarks.splice(bookmarkIndex, 1);
            }
            
            localStorage.setItem('bookmarks', JSON.stringify(bookmarks));
            updateBookmarkButton(index);
        }
        
        function updateBookmarkButton(index) {
            const btn = document.getElementById('bookmarkBtn');
            const icon = btn.querySelector('i');
            
            if (bookmarks.includes(index)) {
                btn.classList.add('bookmarked');
                icon.classList.remove('far');
                icon.classList.add('fas');
            } else {
                btn.classList.remove('bookmarked');
                icon.classList.remove('fas');
                icon.classList.add('far');
            }
        }
        
        function updateBookmarksDisplay() {
            const container = document.getElementById('bookmarkedSlides');
            
            if (bookmarks.length === 0) {
                container.innerHTML = '<p style="color: #718096;">Belum ada slide yang dibookmark. Klik ikon bookmark di sudut kiri atas untuk menandai slide penting.</p>';
                return;
            }
            
            let html = '<div style="display: grid; gap: 10px;">';
            
            bookmarks.forEach(index => {
                const slideTitle = slides[index].querySelector('h1, h2').textContent;
                html += `
                    <div style="background: white; border: 1px solid #e2e8f0; border-radius: 8px; padding: 10px; display: flex; justify-content: space-between; align-items: center;">
                        <div>
                            <strong>Slide ${index + 1}:</strong> ${slideTitle}
                        </div>
                        <button onclick="goToSlide(${index})" style="background: #667eea; color: white; border: none; padding: 5px 10px; border-radius: 5px; cursor: pointer;">Buka</button>
                    </div>
                `;
            });
            
            html += '</div>';
            container.innerHTML = html;
        }
        
        function goToSlide(index) {
            currentSlideIndex = index;
            showSlide(index);
        }
        
        // Notes functionality
        function loadNotes(index) {
            const textarea = document.getElementById('notesTextarea');
            textarea.value = notes[index] || '';
        }
        
        function saveNotes() {
            const textarea = document.getElementById('notesTextarea');
            const status = document.getElementById('notesStatus');
            
            notes[currentSlideIndex] = textarea.value;
            localStorage.setItem('notes', JSON.stringify(notes));
            
            status.textContent = 'Catatan berhasil disimpan!';
            setTimeout(() => {
                status.textContent = '';
            }, 3000);
        }
        
        // Progress tracking
        function updateProgress() {
            const progress = ((currentSlideIndex + 1) / totalSlides) * 100;
            document.getElementById('progressPercent').textContent = Math.round(progress);
            document.getElementById('progressBar').style.width = progress + '%';
            document.getElementById('progressFill').style.width = progress + '%';
        }
        
        // Quiz functionality
        function selectOption(element, isCorrect) {
            // Remove previous selections
            const options = element.parentElement.querySelectorAll('.quiz-option');
            options.forEach(opt => opt.classList.remove('selected'));
            
            // Mark selected option
            element.classList.add('selected');
            
            // Show result
            const result = document.getElementById('quizResult1');
            result.style.display = 'block';
            
            if (isCorrect) {
                result.textContent = '✓ Jawaban benar! IC 4017 memiliki 10 output (Q0-Q9).';
                result.className = 'quiz-result correct';
            } else {
                result.textContent = '✗ Jawaban salah. IC 4017 memiliki 10 output (Q0-Q9).';
                result.className = 'quiz-result incorrect';
            }
        }
        
        // Print evaluation functionality
        function printEvaluation() {
            window.print();
        }
        
        // Initialize
        showSlide(0);
    </script>
</body>
</html>
