<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Undangan Pernikahan Digital</title>
    <style>
        /* Dasar Halaman */
        body, html { 
            margin: 0; padding: 0; height: 100%; 
            background-color: #f8f8f8; 
            font-family: sans-serif;
            overflow: hidden; 
        }

        /* Container untuk Canva */
        .container {
            position: relative;
            width: 100%;
            height: 100vh;
        }

        /* Styling Frame Canva */
        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Tombol Musik Melayang */
        #music-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 999;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            font-size: 24px;
            transition: all 0.3s ease;
        }

        /* Animasi Berputar saat Musik Jalan */
        .rotating {
            animation: spin 4s linear infinite;
        }

        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>

    <div class="container">
        <div id="music-btn" onclick="toggleMusic()">🎵</div>

        <audio id="myAudio" loop>
            <source src="https://drive.google.com/uc?export=download&id=1f-eRVbvfE2-nr3wMQ_nK2sMJVP-ROkpD" type="audio/mpeg">
            
        </audio>

        <iframe src="https://www.canva.com/design/DAHIP_CR-rU/skuuN5_rAlZol2BMTEzd3Q/view?embed" 
                allow="autoplay">
        </iframe>
    </div>

    <script>
        const audio = document.getElementById('myAudio');
        const btn = document.getElementById('music-btn');
        let playing = false;

        // Musik akan aktif saat tamu pertama kali klik di mana saja (untuk memicu autoplay)
        // Ini memenuhi permintaanmu agar aktif saat mereka mulai berinteraksi menuju halaman 2
        document.body.addEventListener('click', function() {
            if (!playing) {
                playAudio();
            }
        }, { once: true });

        function playAudio() {
            audio.play().then(() => {
                playing = true;
                btn.classList.add('rotating');
                btn.innerHTML = "🎵";
            }).catch(error => {
                console.log("Autoplay dicegah oleh browser, perlu klik manual.");
            });
        }

        function toggleMusic() {
            if (playing) {
                audio.pause();
                btn.classList.remove('rotating');
                btn.innerHTML = "🔇";
            } else {
                audio.play();
                btn.classList.add('rotating');
                btn.innerHTML = "🎵";
            }
            playing = !playing;
        }
    </script>

</body>
</html>
