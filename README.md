<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday! 🎉</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 600px;
        }

        .greeting-card {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            text-align: center;
            animation: slideIn 0.8s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .title {
            font-size: 2.5em;
            color: #764ba2;
            margin-bottom: 30px;
            animation: bounce 1s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        .flowers {
            display: flex;
            justify-content: space-around;
            margin: 40px 0;
            flex-wrap: wrap;
            gap: 15px;
        }

        .flower {
            font-size: 3em;
            animation: float 3s ease-in-out infinite;
        }

        .flower1 { animation-delay: 0s; }
        .flower2 { animation-delay: 0.3s; }
        .flower3 { animation-delay: 0.6s; }
        .flower4 { animation-delay: 0.9s; }
        .flower5 { animation-delay: 1.2s; }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
        }

        .message {
            margin: 30px 0;
        }

        .main-text {
            font-size: 1.5em;
            color: #333;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .sub-text {
            font-size: 1.1em;
            color: #666;
            line-height: 1.6;
        }

        .gift-button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2em;
            border-radius: 50px;
            cursor: pointer;
            margin-top: 30px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 10px 25px rgba(118, 75, 162, 0.3);
        }

        .gift-button:hover {
            transform: scale(1.05);
            box-shadow: 0 15px 35px rgba(118, 75, 162, 0.4);
        }

        .gift-button:active {
            transform: scale(0.95);
        }

        .gift-message {
            background: #f0f0f0;
            padding: 20px;
            border-radius: 15px;
            margin-top: 30px;
            animation: revealGift 0.6s ease-out;
        }

        .gift-message p {
            color: #333;
            font-size: 1.1em;
            margin: 10px 0;
            line-height: 1.5;
        }

        .hidden {
            display: none;
        }

        @keyframes revealGift {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @media (max-width: 600px) {
            .greeting-card {
                padding: 25px;
            }
            .title {
                font-size: 2em;
            }
            .flower {
                font-size: 2.5em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="greeting-card">
            <h1 class="title">🎉 Happy Birthday! 🎉</h1>
            
            <div class="flowers">
                <div class="flower flower1">🌹</div>
                <div class="flower flower2">🌺</div>
                <div class="flower flower3">🌸</div>
                <div class="flower flower4">🌻</div>
                <div class="flower flower5">🌷</div>
            </div>
            
            <div class="message">
                <p class="main-text">I hope I'm not too late to give you a gift!</p>
                <p class="sub-text">Wishing you the most wonderful day filled with joy and happiness.</p>
            </div>
            
            <button class="gift-button" onclick="openGift()">Open Your Gift 🎁</button>
            
            <div id="gift-message" class="gift-message hidden">
                <p>You deserve all the happiness in the world!</p>
                <p>Thank you for being amazing. Happy Birthday! 🎊</p>
            </div>
        </div>
    </div>

    <script>
        function openGift() {
            const giftMessage = document.getElementById('gift-message');
            const button = document.querySelector('.gift-button');
            
            if (giftMessage.classList.contains('hidden')) {
                giftMessage.classList.remove('hidden');
                button.textContent = 'Gift Opened! 🎉';
                button.disabled = true;
                createConfetti();
            }
        }

        function createConfetti() {
            const confettiPieces = 30;
            
            for (let i = 0; i < confettiPieces; i++) {
                const confetti = document.createElement('div');
                confetti.style.position = 'fixed';
                confetti.style.width = '10px';
                confetti.style.height = '10px';
                confetti.style.backgroundColor = getRandomColor();
                confetti.style.left = Math.random() * window.innerWidth + 'px';
                confetti.style.top = '-10px';
                confetti.style.borderRadius = '50%';
                confetti.style.pointerEvents = 'none';
                
                document.body.appendChild(confetti);
                animateConfetti(confetti);
            }
        }

        function animateConfetti(confetti) {
            let top = -10;
            let left = parseFloat(confetti.style.left);
            let velocity = Math.random() * 5 + 2;
            let horizontalVelocity = (Math.random() - 0.5) * 4;
            
            const interval = setInterval(() => {
                top += velocity;
                left += horizontalVelocity;
                
                confetti.style.top = top + 'px';
                confetti.style.left = left + 'px';
                confetti.style.opacity = 1 - (top / window.innerHeight);
                
                if (top > window.innerHeight) {
                    clearInterval(interval);
                    confetti.remove();
                }
            }, 20);
        }

        function getRandomColor() {
            const colors = ['#ff6b6b', '#4ecdc4', '#45b7d1', '#f9ca24', '#6c5ce7', '#a29bfe'];
            return colors[Math.floor(Math.random() * colors.length)];
        }
    </script>
</body>
</html>
