# Birthday-special-one-

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday, My Love Ivana 💖</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Poppins:wght@300;400;600&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            overflow: hidden;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 1;
        }
        
        .container {
            text-align: center;
            z-index: 10;
            position: relative;
            max-width: 800px;
            padding: 20px;
        }
        
        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 4rem;
            color: #fff;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.8), 0 0 40px #ff6b9d;
            margin-bottom: 20px;
            animation: glow 2s ease-in-out infinite alternate;
        }
        
        @keyframes glow {
            from { text-shadow: 0 0 20px rgba(255, 255, 255, 0.8), 0 0 40px #ff6b9d; }
            to { text-shadow: 0 0 30px rgba(255, 255, 255, 1), 0 0 60px #ff1493; }
        }
        
        .message {
            font-size: 1.5rem;
            color: #fff;
            line-height: 1.6;
            margin-bottom: 30px;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInUp 1s ease forwards;
        }
        
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .heart {
            font-size: 3rem;
            color: #ff1493;
            animation: heartbeat 1.5s ease-in-out infinite;
            margin: 0 10px;
        }
        
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }
        
        .btn {
            background: linear-gradient(45deg, #ff6b9d, #ff1493);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(255, 105, 157, 0.4);
            transition: all 0.3s ease;
            font-weight: 600;
        }
        
        .btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(255, 105, 157, 0.6);
        }
        
        .fireworks {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            opacity: 0;
        }
    </style>
</head>
<body>
    <canvas id="particles"></canvas>
    <div class="container">
        <h1>Happy Birthday, My Dearest Ivana! 🎉💕</h1>
        <p class="message">
            On this magical day, my heart beats only for you. 
            You are the light that brightens my world, the melody in my soul, 
            and the dream I never want to wake from. 
            Here's to countless more adventures, laughter, and love together. 
            I love you more than words—or stars—can say. 🌟❤️
        </p>
        <div class="heart">💖</div>
        <button class="btn" onclick="launchFireworks()">Celebrate with Fireworks! 🎆</button>
    </div>
    <canvas id="fireworks" class="fireworks"></canvas>

    <script>
        // Floating particles
        const canvas = document.getElementById('particles');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const particles = [];
        for (let i = 0; i < 100; i++) {
            particles.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                vx: (Math.random() - 0.5) * 0.5,
                vy: (Math.random() - 0.5) * 0.5,
                radius: Math.random() * 3 + 1,
                alpha: Math.random() * 0.5 + 0.2,
                color: `hsl(${Math.random() * 60 + 300}, 100%, 70%)`
            });
        }

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.x += p.vx;
                p.y += p.vy;
                if (p.x < 0 || p.x > canvas.width) p.vx *= -1;
                if (p.y < 0 || p.y > canvas.height) p.vy *= -1;
                
                ctx.save();
                ctx.globalAlpha = p.alpha;
                ctx.fillStyle = p.color;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                ctx.fill();
                ctx.restore();
            });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        // Fireworks
        function launchFireworks() {
            const fwCanvas = document.getElementById('fireworks');
            const fwCtx = fwCanvas.getContext('2d');
            fwCanvas.width = window.innerWidth;
            fwCanvas.height = window.innerHeight;

            function createFirework() {
                const fw = {
                    x: Math.random() * fwCanvas.width,
                    y: fwCanvas.height,
                    vy: -Math.random() * 15 - 10,
                    exploded: false,
                    particles: []
                };
                
                let timer = 0;
                function update() {
                    fwCtx.clearRect(0, 0, fwCanvas.width, fwCanvas.height);
                    
                    if (!fw.exploded) {
                        fw.y += fw.vy;
                        fw.vy += 0.1;
                        if (fw.vy > 0) {
                            fw.exploded = true;
                            for (let i = 0; i < 50; i++) {
                                fw.particles.push({
                                    x: fw.x,
                                    y: fw.y,
                                    vx: (Math.random() - 0.5) * 10,
                                    vy: (Math.random() - 0.5) * 10,
                                    alpha: 1,
                                    life: 60
                                });
                            }
                        }
                    } else {
                        fw.particles.forEach((p, i) => {
                            p.x += p.vx;
                            p.y += p.vy;
                            p.vy += 0.2;
                            p.alpha -= 1 / p.life;
                            p.life--;
                            
                            if (p.life > 0) {
                                fwCtx.save();
                                fwCtx.globalAlpha = p.alpha;
                                fwCtx.fillStyle = `hsl(${Math.random() * 60 + 0}, 100%, 50%)`;
                                fwCtx.beginPath();
                                fwCtx.arc(p.x, p.y, 3, 0, Math.PI * 2);
                                fwCtx.fill();
                                fwCtx.restore();
                            } else {
                                fw.particles.splice(i, 1);
                            }
                        });
                    }
                    
                    if (fw.exploded && fw.particles.length === 0) {
                        fwCtx.clearRect(0, 0, fwCanvas.width, fwCanvas.height);
                        return;
                    }
                    requestAnimationFrame(update);
                }
                update();
            }

            for (let i = 0; i < 10; i++) {
                setTimeout(createFirework, i * 300);
            }
            
            fwCanvas.style.opacity = '1';
            setTimeout(() => { fwCanvas.style.opacity = '0'; }, 5000);
        }

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
