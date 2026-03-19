# The Vermillion Imperium 
<!DOCTYPE html>
<html lang="en" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Vermilion Imperium</title>
    <script src="https://cdn.tailwindcss.com/3.4.17"></script>
    <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700;900&family=Raleway:wght@300;400;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            /* Dynamic Theme Variables */
            --primary: #b91c1c;
            --secondary: #7f1d1d;
            --bg: #0a0708;
            --surface: #16110f;
            --text: #e8ddd0;
            --font-main: 'Raleway', sans-serif;
            --font-title: 'Cinzel', serif;
        }

        body, html { 
            height: 100%; 
            margin: 0; 
            background-color: var(--bg);
            color: var(--text);
            font-family: var(--font-main);
            overflow-x: hidden;
        }

        .app-root {
            position: relative;
            background: radial-gradient(circle at 50% 50%, transparent 0%, rgba(0,0,0,0.5) 100%);
            min-height: 100vh;
        }

        /* Cinematic Ember Particles */
        #embers {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 0;
        }

        .ember {
            position: absolute;
            width: 4px;
            height: 4px;
            border-radius: 50%;
            opacity: 0;
            animation: float-up linear infinite;
        }

        @keyframes float-up {
            0% { transform: translateY(0) scale(1); opacity: 0; }
            20% { opacity: 0.8; }
            80% { opacity: 0.4; }
            100% { transform: translateY(-100vh) scale(0.2); opacity: 0; }
        }

        /* Reveal on Scroll */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s cubic-bezier(0.2, 0.8, 0.2, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Feature Cards */
        .feature-card {
            background: var(--surface);
            border: 1px solid rgba(185, 28, 28, 0.1);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .feature-card:hover {
            transform: translateY(-8px);
            border-color: var(--primary);
            box-shadow: 0 10px 30px rgba(185, 28, 28, 0.2);
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 2px;
            background: linear-gradient(90deg, transparent, var(--primary), transparent);
            opacity: 0.3;
        }

        /* Sigil Spin */
        .sigil-ring {
            animation: spin 20s linear infinite;
            stroke: var(--primary);
        }

        @keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }

        /* Primary Button Style */
        .btn-imperium {
            background: var(--primary);
            color: var(--text);
            font-family: var(--font-title);
            letter-spacing: 0.15em;
            transition: all 0.3s ease;
            box-shadow: 0 0 15px rgba(185, 28, 28, 0.4);
        }

        .btn-imperium:hover {
            transform: scale(1.05);
            box-shadow: 0 0 25px var(--primary);
        }

        /* Modal Blur */
        #roleModal {
            backdrop-filter: blur(8px);
            transition: opacity 0.3s ease;
        }
    </style>
</head>
<body>

    <div class="app-root" id="appRoot">
        <div id="embers"></div>

        <header class="relative z-10 flex flex-col items-center justify-center text-center px-6 pt-24 pb-16">
            <div class="reveal mb-8 relative inline-block">
                <svg class="sigil-ring" width="140" height="140" viewBox="0 0 120 120" style="position: absolute; top: -10px; left: -10px;">
                    <circle cx="60" cy="60" r="55" fill="none" stroke-width="1" stroke-dasharray="4 8" opacity="0.4" />
                </svg>
                <div id="sigilCenter" class="w-24 h-24 rounded-full border-2 border-[var(--primary)] flex items-center justify-center text-4xl font-black font-serif bg-black/40">
                    VI
                </div>
            </div>

            <h1 class="reveal font-serif text-5xl md:text-6xl font-black uppercase tracking-widest mb-4">
                The Vermilion Imperium
            </h1>
            <p class="reveal font-serif text-lg tracking-[0.3em] opacity-60 mb-8 uppercase">
                Forged in Fire. Bound by Legacy.
            </p>
            
            <div class="reveal w-24 h-px bg-gradient-to-r from-transparent via-[var(--text)] to-transparent opacity-20 mb-8"></div>
            
            <p class="reveal max-w-2xl text-lg leading-relaxed font-light opacity-80 mb-10">
                Step into a thriving community of gamers, creators, and strategists. 
                Experience a brotherhood forged through shared victories and unforgettable moments.
            </p>

            <button onclick="openModal()" class="reveal btn-imperium px-10 py-4 rounded flex items-center gap-3">
                <i data-lucide="shield-check"></i>
                JOIN THE IMPERIUM
            </button>
        </header>

        <section class="relative z-10 max-w-6xl mx-auto px-6 py-20">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <div class="feature-card reveal p-8 rounded-lg">
                    <div class="text-[var(--primary)] mb-4"><i data-lucide="users"></i></div>
                    <h3 class="font-serif font-bold text-xl mb-2">Active Legion</h3>
                    <p class="text-sm opacity-60 font-light">Hundreds of members online daily. Jump into tactical discussions and find your squad.</p>
                </div>
                <div class="feature-card reveal p-8 rounded-lg" style="transition-delay: 0.1s;">
                    <div class="text-[var(--primary)] mb-4"><i data-lucide="swords"></i></div>
                    <h3 class="font-serif font-bold text-xl mb-2">Epic Events</h3>
                    <p class="text-sm opacity-60 font-light">Weekly tournaments, movie nights, and community challenges with real rewards.</p>
                </div>
                <div class="feature-card reveal p-8 rounded-lg" style="transition-delay: 0.2s;">
                    <div class="text-[var(--primary)] mb-4"><i data-lucide="crown"></i></div>
                    <h3 class="font-serif font-bold text-xl mb-2">Exclusive Ranks</h3>
                    <p class="text-sm opacity-60 font-light">Prove your loyalty and rise through the hierarchy to unlock secret channels.</p>
                </div>
                <div class="feature-card reveal p-8 rounded-lg" style="transition-delay: 0.3s;">
                    <div class="text-[var(--primary)] mb-4"><i data-lucide="terminal"></i></div>
                    <h3 class="font-serif font-bold text-xl mb-2">Dev Sanctum</h3>
                    <p class="text-sm opacity-60 font-light">A dedicated space for builders and creators to collaborate on Imperium projects.</p>
                </div>
            </div>
        </section>

        <div id="roleModal" class="fixed inset-0 z-50 hidden items-center justify-center bg-black/90 p-4">
            <div class="bg-[var(--surface)] border-2 border-[var(--primary)] rounded-xl p-8 max-w-md w-full text-center">
                <h2 class="font-serif text-2xl font-black mb-2 uppercase tracking-wide">Choose Your Path</h2>
                <p class="text-sm opacity-50 mb-8">Select your primary specialization within the Imperium.</p>
                
                <div class="grid grid-cols-1 gap-4">
                    <button class="flex items-center gap-4 p-4 rounded bg-red-900/20 border border-red-900/40 hover:bg-red-900/40 transition-all">
                        <i data-lucide="sword"></i>
                        <span class="font-serif font-bold">SOLDIER</span>
                    </button>
                    <button class="flex items-center gap-4 p-4 rounded bg-red-900/20 border border-red-900/40 hover:bg-red-900/40 transition-all">
                        <i data-lucide="code-2"></i>
                        <span class="font-serif font-bold">DEVELOPER</span>
                    </button>
                </div>

                <button onclick="closeModal()" class="mt-8 text-xs opacity-40 hover:opacity-100 uppercase tracking-widest font-serif">
                    Return to Void
                </button>
            </div>
        </div>
    </div>

    <script>
        // 1. Initialize Icons
        lucide.createIcons();

        // 2. Scroll Reveal Logic
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) entry.target.classList.add('active');
            });
        }, { threshold: 0.1 });

        document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

        // 3. Cinematic Particles
        function initEmbers() {
            const container = document.getElementById('embers');
            const count = 30;
            const colors = ['#b91c1c', '#7f1d1d', '#f87171'];

            for (let i = 0; i < count; i++) {
                const ember = document.createElement('div');
                ember.className = 'ember';
                const size = Math.random() * 4 + 2;
                const color = colors[Math.floor(Math.random() * colors.length)];
                
                ember.style.width = `${size}px`;
                ember.style.height = `${size}px`;
                ember.style.backgroundColor = color;
                ember.style.boxShadow = `0 0 10px ${color}`;
                ember.style.left = `${Math.random() * 100}vw`;
                ember.style.bottom = `-20px`;
                ember.style.animationDuration = `${Math.random() * 10 + 5}s`;
                ember.style.animationDelay = `${Math.random() * 5}s`;
                
                container.appendChild(ember);
            }
        }

        // 4. Modal Handlers
        function openModal() {
            const modal = document.getElementById('roleModal');
            modal.style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('roleModal').style.display = 'none';
        }

        initEmbers();
    </script>
</body>
</html>