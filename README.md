<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday, My Love! 🎉❤️</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Animated Vibrant Background */
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(-45deg, #ff9a9e, #fecfef, #ffdde1, #ee9ca7);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .confetti {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1000;
        }

        /* Floating Music Button */
        .music-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 70px;
            height: 70px;
            background: linear-gradient(45deg, #ff6b6b, #ff8a80);
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(255,107,107,0.4);
            z-index: 2000;
            transition: all 0.3s ease;
            animation: pulse 2s infinite;
        }

        .music-btn.playing {
            background: linear-gradient(45deg, #4ecdc4, #a8e6cf);
            animation: none;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        /* Gift Button */
        .gift-btn {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px 40px;
            background: linear-gradient(45deg, #ffd700, #ffed4e);
            color: #333;
            border: none;
            border-radius: 50px;
            font-size: 1.5rem;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 20px 40px rgba(255,215,0,0.4);
            z-index: 1500;
            opacity: 0;
            display: none;
            transition: all 0.5s ease;
            font-family: 'Dancing Script', cursive;
        }

        .gift-btn.show {
            display: block;
            opacity: 1;
            animation: bounceIn 1s ease, floatBtn 3s ease-in-out infinite;
        }

        @keyframes floatBtn {
            0%, 100% { transform: translate(-50%, -50%) translateY(0); }
            50% { transform: translate(-50%, -50%) translateY(-20px); }
        }

        @keyframes bounceIn {
            0% { transform: translate(-50%, -50%) scale(0.3); opacity: 0; }
            50% { transform: translate(-50%, -50%) scale(1.05); }
            70% { transform: translate(-50%, -50%) scale(0.9); }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }

        /* Gift Modal */
        .gift-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.85);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 3000;
            backdrop-filter: blur(8px);
        }

        .gift-modal.show {
            display: flex;
        }

        .gift-content {
            background: linear-gradient(135deg, #fff, #ffe4e1);
            padding: 40px;
            border-radius: 30px;
            text-align: center;
            max-width: 500px;
            margin: 20px;
            box-shadow: 0 40px 80px rgba(0,0,0,0.5);
            animation: modalPop 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes modalPop {
            0% { transform: scale(0.7) rotate(-10deg); opacity: 0; }
            100% { transform: scale(1) rotate(0deg); opacity: 1; }
        }

        /* Hearts Explosion */
        .hearts-explosion {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 4000;
        }

        .heart {
            position: absolute;
            font-size: 2rem;
            pointer-events: none;
            animation: heartFloat 3s ease-out forwards;
        }

        @keyframes heartFloat {
            0% { opacity: 1; transform: translateY(0) scale(1) rotate(0); }
            100% { opacity: 0; transform: translateY(-400px) scale(0) rotate(720deg); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }

        /* Animated Title */
        .birthday-title {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(3.5rem, 8vw, 6rem);
            color: #fff;
            text-shadow: 4px 4px 8px rgba(0,0,0,0.3);
            margin: 40px 0;
            animation: titleEntrance 2s ease-out;
        }

        @keyframes titleEntrance {
            from { opacity: 0; transform: translateY(-50px); letter-spacing: 10px; }
            to { opacity: 1; transform: translateY(0); letter-spacing: normal; }
        }

        /* Memory Row Scroll Animations */
        .memory-row {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 100px 0;
            gap: 40px;
            opacity: 0;
            transform: translateY(50px);
            transition: all 1s ease-out;
        }

        .memory-row.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .memory-row:nth-child(even) {
            flex-direction: row-reverse;
        }

        .photo-side {
            flex: 1;
            max-width: 500px;
        }

        /* Photo Frame Floating Animation */
        .photo-frame {
            width: 100%;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            background: white;
            padding: 10px;
            transition: all 0.5s ease;
            animation: imageFloat 6s ease-in-out infinite;
        }

        @keyframes imageFloat {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(1deg); }
        }

        .photo-frame:hover {
            transform: scale(1.05) rotate(0deg) !important;
            box-shadow: 0 30px 60px rgba(0,0,0,0.3);
            z-index: 10;
        }

        .photo-frame img {
            width: 100%;
            height: auto;
            border-radius: 15px;
            display: block;
        }

        .quote-side {
            flex: 1;
            padding: 40px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 25px;
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease;
        }

        .quote-side:hover {
            transform: scale(1.02);
        }

        .quote-text {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            font-style: italic;
            color: #444;
            line-height: 1.6;
            font-family: 'Dancing Script', cursive;
        }

        .shayari-section {
            margin: 100px 0;
            padding: 60px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 30px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            animation: pulseShayari 3s infinite;
        }

        @keyframes pulseShayari {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .shayari-text {
            font-size: 1.8rem;
            line-height: 2;
            color: #e91e63;
            font-weight: 600;
            white-space: pre-line;
        }

        @media (max-width: 850px) {
            .memory-row, .memory-row:nth-child(even) {
                flex-direction: column;
                margin: 60px 0;
            }
            .photo-side { max-width: 100%; }
        }
    </style>
</head>
<body>

    <button class="music-btn" id="musicBtn">🎵</button>
    <audio id="birthdaySong" loop>
        <source src="https://www.soundjay.com/misc/sounds/bell-ringing-05.wav" type="audio/wav">
    </audio>

    <button class="gift-btn" id="giftBtn">🎁 Click for Birthday Wish!</button>

    <div class="gift-modal" id="giftModal">
        <div class="gift-content">
            <h2 style="font-family: 'Dancing Script', cursive; font-size: 2.5rem; color: #e91e63; margin-bottom: 20px;">
                🎂 Happy Birthday, My Love! 🎂
            </h2>
            <p style="font-size: 1.2rem; line-height: 1.6; color: #333;">
                Today isn't just about another year; it's about celebrating your strength and spirit. 
                I know things have been a whirlwind lately, but seeing you stay focused makes me so proud. 
                Here's to a year of big wins and even bigger smiles! ✨💕
            </p>
            <p style="margin-top: 20px; font-size: 1.5rem; color: #ff6b6b; font-family: 'Dancing Script';">
                I love you more than words can say! ❤️
            </p>
            <button onclick="closeGift()" style="margin-top: 25px; padding: 12px 25px; background: #ff6b6b; color: white; border: none; border-radius: 20px; cursor: pointer;">✨ Close</button>
        </div>
    </div>

    <div class="hearts-explosion" id="hearts"></div>
    <div class="confetti" id="confetti"></div>

    <div class="container">
        <h1 class="birthday-title">Happy Birthday, Januuu! 🎂✨</h1>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/LDXpNjhG/Screenshot-2025-10-08-003336.png"></div></div>
            <div class="quote-side"><p class="quote-text">Every moment with you feels like a dream I never want to wake up from. ✨</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/1tZbbdNp/Screenshot-2025-10-09-004720.png"></div></div>
            <div class="quote-side"><p class="quote-text">Your smile is the only sunshine I'll ever need. ☀️</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/r2QJ18pL/Screenshot-2025-10-21-185826.png"></div></div>
            <div class="quote-side"><p class="quote-text">In your eyes, I found my favorite place to get lost. 💕</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/kg5v75QQ/Screenshot-2025-10-22-193333.png"></div></div>
            <div class="quote-side"><p class="quote-text">Forever isn't long enough to spend with you. ♾️</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/CKccQyF2/Screenshot-2025-11-01-001739.png"></div></div>
            <div class="quote-side"><p class="quote-text">You are the music my heart has been waiting to play. 🎵</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/tMdQHFGX/Screenshot-2025-12-07-223208.png"></div></div>
            <div class="quote-side"><p class="quote-text">My world is beautiful because you are in it. 🌍</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/jPXPwdzk/Screenshot-2025-12-20-153519.png"></div></div>
            <div class="quote-side"><p class="quote-text">You are my today and all of my tomorrows. ❤️</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/60mFxZjP/Screenshot-2025-12-27-010909.png"></div></div>
            <div class="quote-side"><p class="quote-text">Wrapped in your love is the safest I've ever felt. 🫂</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/NzKwgzQ/Screenshot-2025-12-31-145803.png"></div></div>
            <div class="quote-side"><p class="quote-text">To the girl who changed my life—Happy Birthday! 🎂</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/KcMJG549/Screenshot-2025-12-31-150539.png"></div></div>
            <div class="quote-side"><p class="quote-text">With you, even the simplest days feel like a celebration. 🎉</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/W4ZXB1kH/Screenshot-2025-12-31-150550.png"></div></div>
            <div class="quote-side"><p class="quote-text">You're the missing piece I never knew I was looking for. 🧩</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/VYsQty4R/Screenshot-2026-02-08-125036.png"></div></div>
            <div class="quote-side"><p class="quote-text">The best part of my day is seeing your beautiful face. 😍</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/7JQbXzJZ/Screenshot-2026-02-08-125048.png"></div></div>
            <div class="quote-side"><p class="quote-text">Your love is the greatest gift I have ever received. 🎁</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/Z6mW59xn/Screenshot-2026-03-15-161524.png"></div></div>
            <div class="quote-side"><p class="quote-text">I fall in love with you a little more every single day. 💞</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/G3QHMjHy/Screenshot-2026-03-15-161532.png"></div></div>
            <div class="quote-side"><p class="quote-text">You are the queen of my heart, today and forever. 👑</p></div>
        </div>

        <div class="memory-row">
            <div class="photo-side"><div class="photo-frame"><img src="https://i.ibb.co/Jwv7VqF6/Whats-App-Image-2026-01-22-at-1-34-46-AM.jpg"></div></div>
            <div class="quote-side"><p class="quote-text">Thinking of you keeps me awake, dreaming of you keeps me asleep. 💭</p></div>
        </div>

        <div class="shayari-section">
            <div style="font-size: 5rem; margin-bottom: 20px;">🎂🥳🎉</div>
            <p class="shayari-text">
                Khuda kare aapki har khwahish puri ho,
                Zindagi ki har raah khushiyon se bhari ho,
                Meri dua hai us rab se bas itni si,
                Ki meri umar bhi ab aapke naam likhi ho! ❤️
            </p>
        </div>
    </div>

    <script>
        // Simple Scroll Observer to trigger animations
        const observerOptions = { threshold: 0.2 };
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.memory-row').forEach(row => {
            observer.observe(row);
        });

        // Music Logic
        const musicBtn = document.getElementById('musicBtn');
        const audio = document.getElementById('birthdaySong');
        let isPlaying = false;

        musicBtn.addEventListener('click', () => {
            if (isPlaying) {
                audio.pause();
                musicBtn.textContent = '🎵';
                musicBtn.classList.remove('playing');
            } else {
                audio.play();
                musicBtn.textContent = '⏸️';
                musicBtn.classList.add('playing');
            }
            isPlaying = !isPlaying;
        });

        // Confetti Logic
        function createConfetti() {
            const container = document.getElementById('confetti');
            setInterval(() => {
                const piece = document.createElement('div');
                piece.style.position = 'absolute';
                piece.style.width = '10px';
                piece.style.height = '10px';
                piece.style.left = Math.random() * 100 + 'vw';
                piece.style.top = '-10px';
                piece.style.backgroundColor = ['#ff6b6b', '#4ecdc4', '#ffe66d', '#ff8a80'][Math.floor(Math.random()*4)];
                piece.style.borderRadius = '50%';
                piece.style.animation = `fall ${Math.random() * 3 + 2}s linear forwards`;
                container.appendChild(piece);
                setTimeout(() => piece.remove(), 5000);
            }, 300);
        }

        const styleSheet = document.createElement("style");
        styleSheet.innerText = "@keyframes fall { to { transform: translateY(100vh) rotate(360deg); opacity: 0; } }";
        document.head.appendChild(styleSheet);
        createConfetti();

        // Gift & Hearts Logic
        const giftBtn = document.getElementById('giftBtn');
        const giftModal = document.getElementById('giftModal');
        const heartsContainer = document.getElementById('hearts');

        setTimeout(() => { giftBtn.classList.add('show'); }, 3000);

        giftBtn.addEventListener('click', () => {
            createHearts();
            giftModal.classList.add('show');
            giftBtn.style.display = 'none';
        });

        function closeGift() { giftModal.classList.remove('show'); }

        function createHearts() {
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'heart';
                    heart.innerHTML = ['💖', '💕', '💗', '💝', '❤️'][Math.floor(Math.random() * 5)];
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.top = '60vh';
                    heartsContainer.appendChild(heart);
                    setTimeout(() => heart.remove(), 3000);
                }, i * 60);
            }
        }
    </script>
</body>
</html>
