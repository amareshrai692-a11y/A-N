
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy 15th Birthday Navya ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Cinzel:wght@400;700&family=Poppins:wght@300;400;600&family=Sacramento&display=swap" rel="stylesheet">
    <style>
        /* --- 1. CORE VARIABLES & RESET --- */
        :root {
            --primary: #d90429;
            --accent: #ff4d6d;
            --gold: #ffd700;
            --glass: rgba(255, 255, 255, 0.1);
            --glass-solid: rgba(255, 255, 255, 0.9);
            --border: rgba(255, 255, 255, 0.2);
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            overflow: hidden; /* Hide scrollbars for story mode */
            font-family: 'Poppins', sans-serif;
            background: #050505;
            color: white;
            height: 100vh;
            width: 100vw;
        }

        /* --- 2. CANVAS BACKGROUND --- */
        #canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: 0; pointer-events: none;
            background: radial-gradient(circle at center, #1a0b0e 0%, #000 100%);
        }

        /* --- 3. SLIDE SYSTEM --- */
        .slide {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            opacity: 0; pointer-events: none; transform: scale(0.9);
            transition: all 0.8s cubic-bezier(0.68, -0.55, 0.27, 1.55);
            z-index: 10;
        }
        
        .slide.active {
            opacity: 1; pointer-events: all; transform: scale(1);
        }

        .slide.exit {
            opacity: 0; transform: translateY(-100vh) scale(0.8);
        }

        /* --- COMMON UI ELEMENTS --- */
        h1 { font-family: 'Great Vibes', cursive; font-size: 3.5rem; color: var(--accent); margin-bottom: 20px; text-shadow: 0 0 10px var(--primary); text-align: center;}
        p { font-size: 1.1rem; color: #ddd; margin-bottom: 30px; text-align: center; max-width: 600px; line-height: 1.6; }
        
        .btn {
            padding: 12px 30px; font-size: 1.1rem; border-radius: 50px; border: none;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            color: white; cursor: pointer; box-shadow: 0 5px 20px rgba(217, 4, 41, 0.4);
            transition: transform 0.2s; font-family: 'Poppins', sans-serif;
        }
        .btn:hover { transform: scale(1.05); }

        /* --- SLIDE 1: LOCK SCREEN --- */
        .lock-icon { font-size: 4rem; margin-bottom: 20px; animation: pulse 2s infinite; }

        /* --- SLIDE 2: CARTOON COUPLE --- */
        .avatar-container {
            width: 250px; height: 250px; border-radius: 50%;
            border: 5px solid var(--gold);
            overflow: hidden; margin-bottom: 20px;
            box-shadow: 0 0 30px var(--gold);
            animation: float 3s infinite ease-in-out;
            background: white;
            display: flex; align-items: center; justify-content: center;
        }
        .avatar-img { width: 100%; height: 100%; object-fit: cover; }

        /* --- SLIDE 3: MEMORY LANE (POLAROIDS) --- */
        .gallery {
            display: flex; gap: 20px; flex-wrap: wrap; justify-content: center;
        }
        .polaroid {
            background: white; padding: 10px 10px 30px 10px;
            color: #333; box-shadow: 0 10px 20px rgba(0,0,0,0.5);
            transform: rotate(-5deg); transition: transform 0.3s;
            width: 160px; text-align: center;
        }
        .polaroid:nth-child(even) { transform: rotate(5deg); }
        .polaroid:hover { transform: scale(1.1) rotate(0deg); z-index: 20; }
        .polaroid img { width: 100%; height: 180px; object-fit: cover; border: 1px solid #eee; }
        .caption { font-family: 'Sacramento', cursive; font-size: 1.5rem; margin-top: 10px; color: #555; }

        /* --- SLIDE 4: ENVELOPE (Classic) --- */
        .envelope-wrapper { position: relative; cursor: pointer; animation: float 3s infinite; }
        .envelope { width: 300px; height: 200px; background: var(--primary); position: relative; border-radius: 0 0 10px 10px; }
        .envelope::before { content:''; position:absolute; top:0; border-left:150px solid transparent; border-right:150px solid transparent; border-top:130px solid #ff5c7c; transform-origin:top; transition:0.5s; }
        .envelope.open::before { transform: rotateX(180deg); }
        .letter { position:absolute; top:10px; left:10px; width:280px; height:180px; background:white; color:#333; z-index:0; transition:0.5s; display:flex; align-items:center; justify-content:center; flex-direction:column; font-family:'Great Vibes'; font-size:1.8rem; }
        .envelope.open .letter { transform: translateY(-150px); z-index:2; }

        /* --- SLIDE 5: CAKE --- */
        .cake-container { font-size: 8rem; cursor: pointer; user-select: none; transition: 0.3s; filter: drop-shadow(0 0 20px rgba(255,255,255,0.5)); }
        .cake-container:active { transform: scale(0.9); }
        .candles { font-size: 2rem; position: absolute; top: -20px; width: 100%; text-align: center; opacity: 1; transition: 1s; }
        .candles.blown { opacity: 0; transform: translateY(-20px); }

        /* --- SLIDE 6: DASHBOARD --- */
        .dashboard {
            background: var(--glass-solid); color: #333; padding: 30px;
            border-radius: 20px; width: 90%; max-width: 500px; text-align: center;
        }
        .dashboard h1 { color: var(--primary); font-size: 2.5rem; }
        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 20px; }
        .box { background: #ffe3e8; padding: 15px; border-radius: 15px; cursor: pointer; transition: 0.3s; border: 1px solid var(--primary); }
        .box:hover { transform: translateY(-5px); background: #ffccd5; }

        /* --- UTILS --- */
        .hidden { display: none; }
        @keyframes pulse { 0% { opacity:0.6; } 50% { opacity:1; } 100% { opacity:0.6; } }
        @keyframes float { 0%,100% { transform:translateY(0); } 50% { transform:translateY(-15px); } }

        /* MODALS */
        .modal { position: fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.8); display:none; align-items:center; justify-content:center; z-index:100; }
        .modal-box { background:white; color:#333; padding:30px; border-radius:20px; text-align:center; max-width:80%; position:relative; animation: float 1s ease-out; }
        .close { position:absolute; top:10px; right:15px; font-size:24px; cursor:pointer; }

    </style>
</head>
<body>

    <div id="player"></div>

    <canvas id="canvas"></canvas>

    <div class="slide active" id="slide1">
        <div class="lock-icon">🔒</div>
        <h1>Navya's World</h1>
        <p>A magical story awaits the Birthday Girl...</p>
        <button class="btn" onclick="nextSlide(1)">Enter Surprise ✨</button>
    </div>

    <div class="slide" id="slide2">
        <h1>The Birthday Star</h1>
        <div class="avatar-container">
            <img src="https://img.freepik.com/free-vector/cute-couple-love-illustration_138676-267.jpg?w=740" class="avatar-img" alt="Cartoon Couple">
        </div>
        <p>Welcome to your special day, Navya!<br>Featuring: Amaresh & Navya</p>
        <button class="btn" onclick="nextSlide(2)">Continue ➔</button>
    </div>

    <div class="slide" id="slide3">
        <h1>Beautiful Memories</h1>
        <div class="gallery">
            <div class="polaroid">
                <img src="1000032569.jpg" onerror="this.src='https://via.placeholder.com/150x200?text=Your+Photo+Here'">
                <div class="caption">So Pretty!</div>
            </div>
            <div class="polaroid">
                <img src="1000032568.jpg" onerror="this.src='https://via.placeholder.com/150x200?text=Teddy+Love'">
                <div class="caption">Cuteness</div>
            </div>
        </div>
        <p style="margin-top:20px;">Every moment with you is a treasure.</p>
        <button class="btn" onclick="nextSlide(3)">Next ➔</button>
    </div>

    <div class="slide" id="slide4">
        <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
            <div class="envelope">
                <div class="letter">
                    <p style="margin:0; font-size:1.5rem; color:#d90429;">For You</p>
                    <p style="margin:10px 0; font-size:1rem; font-family:'Poppins'">Tap to read</p>
                    <p style="margin:0; font-size:1.5rem;">❤️</p>
                </div>
            </div>
        </div>
        <p style="margin-top:30px;">There is a message inside...</p>
        <button class="btn" onclick="nextSlide(4)">Next ➔</button>
    </div>

    <div class="slide" id="slide5">
        <h1>Make a Wish!</h1>
        <div style="position:relative; display:inline-block;">
            <div id="candles" class="candles">🕯️ 🕯️ 🕯️</div>
            <div class="cake-container" onclick="blowCandles()">🎂</div>
        </div>
        <p>Tap the cake to blow out the candles!</p>
        <button class="btn hidden" id="cakeBtn" onclick="nextSlide(5)">Celebrate! 🎉</button>
    </div>

    <div class="slide" id="slide6">
        <div class="dashboard">
            <div style="background:var(--primary); color:white; padding:5px 15px; border-radius:20px; display:inline-block; font-size:0.8rem; margin-bottom:10px;">14th January</div>
            <h1>Happy 15th!</h1>
            
            <div style="display:flex; justify-content:center; gap:10px; margin:15px 0;">
                <div style="background:#eee; padding:5px 10px; border-radius:5px;"><b id="d">0</b>d</div>
                <div style="background:#eee; padding:5px 10px; border-radius:5px;"><b id="h">0</b>h</div>
                <div style="background:#eee; padding:5px 10px; border-radius:5px;"><b id="m">0</b>m</div>
                <div style="background:#eee; padding:5px 10px; border-radius:5px;"><b id="s">0</b>s</div>
            </div>

            <div class="grid">
                <div class="box" onclick="showModal('m1')">💌 Wish</div>
                <div class="box" onclick="triggerConfetti()">🦋 Magic</div>
                <div class="box" onclick="showModal('m3')">💐 Gift</div>
                <div class="box" onclick="showModal('m4')">❤️ Love</div>
            </div>
            
            <div style="margin-top:20px; font-family:'Great Vibes'; font-size:2rem; color:var(--primary);">Amaresh Rai</div>
        </div>
    </div>

    <div id="m1" class="modal" onclick="this.style.display='none'"><div class="modal-box"><h2>My Wish</h2><p>"May your year be as beautiful as you are, Navya!"</p></div></div>
    <div id="m3" class="modal" onclick="this.style.display='none'"><div class="modal-box"><div style="font-size:3rem;">💐🍫</div><p>Flowers & Chocolates for my favorite girl!</p></div></div>
    <div id="m4" class="modal" onclick="this.style.display='none'"><div class="modal-box"><h1 style="color:red;">I Love You</h1><p>Always & Forever.</p></div></div>

    <script>
        // --- MUSIC ---
        var player;
        function onYouTubeIframeAPIReady() {
            player = new YT.Player('player', { height: '0', width: '0', videoId: 'nAw2ooeubSQ', playerVars: { 'autoplay': 0, 'loop': 1, 'playlist': 'nAw2ooeubSQ' } });
        }
        var tag = document.createElement('script'); tag.src = "https://www.youtube.com/iframe_api";
        var firstScriptTag = document.getElementsByTagName('script')[0]; firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

        // --- NAVIGATION ---
        function nextSlide(current) {
            // Play music on first click
            if(current === 1 && player && player.playVideo) player.playVideo();

            document.getElementById('slide' + current).classList.add('exit');
            document.getElementById('slide' + current).classList.remove('active');
            
            let next = current + 1;
            let nextSlideEl = document.getElementById('slide' + next);
            if(nextSlideEl) {
                nextSlideEl.classList.add('active');
            }
        }

        // --- CAKE INTERACTION ---
        function blowCandles() {
            document.getElementById('candles').classList.add('blown');
            setTimeout(() => {
                document.getElementById('cakeBtn').classList.remove('hidden');
                triggerConfetti();
            }, 800);
        }

        // --- COUNTDOWN ---
        function updateTimer() {
            const now = new Date();
            const year = now.getFullYear();
            let bday = new Date(`Jan 14, ${year} 00:00:00`);
            if(now > bday) bday.setFullYear(year + 1);
            const diff = bday - now;
            document.getElementById('d').innerText = Math.floor(diff / (1000*60*60*24));
            document.getElementById('h').innerText = Math.floor((diff%(1000*60*60*24))/(1000*60*60));
            document.getElementById('m').innerText = Math.floor((diff%(1000*60*60))/(1000*60));
            document.getElementById('s').innerText = Math.floor((diff%(1000*60))/1000);
        }
        setInterval(updateTimer, 1000);
        updateTimer();

        // --- MODALS ---
        function showModal(id) { document.getElementById(id).style.display = 'flex'; triggerConfetti(); }

        // --- CANVAS PARTICLES ---
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth; canvas.height = window.innerHeight;
        let particles = [];
        
        function initParticles() {
            for(let i=0; i<50; i++) particles.push({
                x: Math.random()*canvas.width, y: Math.random()*canvas.height,
                r: Math.random()*3+1, d: Math.random()*50,
                c: ['#ff4d6d','#d90429','#ffd700'][Math.floor(Math.random()*3)]
            });
        }
        
        function drawParticles() {
            ctx.clearRect(0,0,canvas.width,canvas.height);
            particles.forEach(p => {
                ctx.fillStyle = p.c; ctx.beginPath(); ctx.arc(p.x, p.y, p.r, 0, Math.PI*2); ctx.fill();
                p.y -= 0.5; p.x += Math.sin(p.d)*0.5; p.d += 0.05;
                if(p.y < 0) p.y = canvas.height;
            });
            requestAnimationFrame(drawParticles);
        }
        initParticles(); drawParticles();

        // --- CONFETTI/MAGIC ---
        function triggerConfetti() {
            for(let i=0; i<30; i++) {
                let d = document.createElement('div');
                d.style.position = 'fixed'; d.style.left = Math.random()*100+'vw'; d.style.top = '100vh';
                d.style.fontSize = (Math.random()*20+10)+'px';
                d.innerHTML = ['🦋','✨','❤️','🎉'][Math.floor(Math.random()*4)];
                d.style.transition = '2s'; d.style.zIndex = '1000';
                document.body.appendChild(d);
                setTimeout(() => { d.style.transform = `translateY(-100vh) rotate(${Math.random()*360}deg)`; d.style.opacity = '0'; }, 100);
                setTimeout(() => d.remove(), 2000);
            }
        }
    </script>
</body>
</html>
