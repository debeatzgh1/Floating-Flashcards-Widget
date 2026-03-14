
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G-Dev Portfolio | Hiring Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Google+Sans:wght@400;500;700&display=swap');

        :root {
            --g-blue: #8ab4f8;
            --g-green: #34A853;
            --dark-bg: #1a1c1e;
            --dark-card: #2d2f31;
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        body { font-family: 'Google Sans', sans-serif; background: #121212; margin: 0; }

        /* 1. LAUNCHER WITH ENTRANCE ANIMATION */
        #gdev-launcher {
            position: fixed; bottom: 20px; top: 50%; transform: translateY(-50%);
            display: flex; align-items: center; gap: 12px;
            background: var(--dark-card); padding: 8px 18px 8px 8px;
            border-radius: 40px; cursor: pointer; z-index: 9999;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid var(--glass-border);
            animation: slide-wobble 1.2s ease forwards;
            opacity: 0;
        }

        @keyframes slide-wobble {
            0% { transform: translateY(-50%) translateX(-100px); opacity: 0; }
            60% { transform: translateY(-50%) translateX(10px); opacity: 1; }
            80% { transform: translateY(-50%) translateX(-2px); }
            100% { transform: translateY(-50%) translateX(0); opacity: 1; }
        }

        #gdev-launcher:hover { transform: translateY(-50%) scale(1.08) translateX(5px); border-color: var(--g-blue); }

        .dev-avatar {
            width: 30px; height: 30px; background: #121212; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid var(--g-blue); color: var(--g-blue); position: relative;
        }

        .status-dot {
            position: absolute; bottom: 2px; right: 2px; width: 10px; height: 10px;
            background: var(--g-green); border-radius: 50%; border: 2px solid var(--dark-card);
        }

        .status-glow {
            position: absolute; inset: 0; background: var(--g-green);
            border-radius: 50%; animation: status-pulse 2s infinite;
        }

        @keyframes status-pulse { 0% { transform: scale(1); opacity: 0.8; } 100% { transform: scale(2.5); opacity: 0; } }

        /* 2. OVERLAY MODAL */
        #gdev-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.85);
            backdrop-filter: blur(12px); display: none; z-index: 10000;
            justify-content: center; align-items: center; padding: 20px;
            opacity: 0; transition: opacity 0.4s ease;
        }

        #gdev-overlay.active { display: flex; opacity: 1; }

        .gdev-modal {
            width: 100%; max-width: 950px; height: 92vh;
            background: var(--dark-bg); border-radius: 28px;
            display: flex; flex-direction: column; overflow: hidden;
            border: 1px solid var(--glass-border); position: relative;
            transform: scale(0.9); transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        #gdev-overlay.active .gdev-modal { transform: scale(1); }

        /* 3. IFRAME & FOOTER */
        #gdev-frame { flex-grow: 1; width: 100%; border: none; background: #fff; }

        .close-gdev {
            position: absolute; top: 20px; right: 25px; width: 30px; height: 30px;
            background: var(--dark-card); border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; color: #fff; z-index: 20; transition: 0.3s;
        }
        .close-gdev:hover { background: #ff4d4d; }

        .hire-btn {
            background: var(--g-green); color: white; padding: 8px 18px;
            border-radius: 20px; font-size: 11px; font-weight: 800;
            text-transform: uppercase; letter-spacing: 1px; display: flex;
            align-items: center; gap: 8px; transition: 0.3s;
            box-shadow: 0 4px 15px rgba(52, 168, 83, 0.3);
        }
        .hire-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(52, 168, 83, 0.4); background: #2e964a; }

        @media (max-width: 768px) {
            .gdev-modal { height: 100vh; border-radius: 0; }
            .footer-controls { flex-direction: column; gap: 10px; padding: 15px; }
        }
    </style>
</head>
<body>

    <div id="gdev-launcher" onclick="toggleGDev(true)">
        <div class="dev-avatar">
            <i class="fab fa-google"></i>
            <div class="status-dot"><div class="status-glow"></div></div>
        </div>
        <div class="hidden sm:block">
            <div class="flex items-center gap-2">
                <span class="text-[9px] text-[#34A853] font-bold uppercase tracking-widest">Active</span>
            </div>
            <p class="text-[14px] font-medium text-gray-200">@debeatzgh</p>
        </div>
    </div>

    <div id="gdev-overlay">
        <div class="gdev-modal">
            <div class="close-gdev" onclick="toggleGDev(true)"><i class="fas fa-times"></i></div>
            <iframe id="gdev-frame" src=""></iframe>
            <div class="footer-controls p-4 bg-[#1a1c1e] border-t border-white/5 flex justify-between items-center px-8">
                <span class="text-[9px] text-gray-600 font-bold uppercase tracking-[2px]">G-Dev Protocol v4.0</span>
                <div class="flex items-center gap-3">
                    <button id="copy-btn" class="text-[11px] text-[#8ab4f8] font-bold px-4 py-2 hover:text-white transition" onclick="copyProfileLink()">
                        Copy Profile
                    </button>
                    <a href="https://wa.me/233549757544" target="_blank" class="hire-btn">
                        <i class="fas fa-briefcase"></i> Contact Me
                    </a>
                </div>
            </div>
        </div>
    </div>

    <script>
        const overlay = document.getElementById('gdev-overlay');
        const frame = document.getElementById('gdev-frame');
        const profileUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header";
        
        let autoPopTimer = null;
        let isUserInteracted = false;

        function toggleGDev(isManual = false) {
            // If user clicks, stop all automatic pop-ups/closings
            if (isManual) {
                isUserInteracted = true;
                clearTimeout(autoPopTimer);
            }

            if (overlay.classList.contains('active')) {
                overlay.classList.remove('active');
                setTimeout(() => { 
                    overlay.style.display = 'none'; 
                    frame.src = ""; 
                }, 400);
                document.body.style.overflow = 'auto';
            } else {
                overlay.style.display = 'flex';
                setTimeout(() => overlay.classList.add('active'), 10);
                frame.src = profileUrl;
                document.body.style.overflow = 'hidden';
            }
        }

        // --- AUTOMATIC ENGINE ---
        window.addEventListener('load', () => {
            // 1. Auto Open after 6 seconds
            autoPopTimer = setTimeout(() => {
                if (!isUserInteracted) {
                    toggleGDev();
                    
                    // 2. Auto Close after 3 more seconds
                    autoPopTimer = setTimeout(() => {
                        if (!isUserInteracted) toggleGDev();
                    }, 6000);
                }
            }, 6000);
        });

        async function copyProfileLink() {
            await navigator.clipboard.writeText(profileUrl);
            const btn = document.getElementById('copy-btn');
            btn.innerText = "Copied!";
            setTimeout(() => { btn.innerText = "Copy Profile"; }, 2000);
        }

        overlay.onclick = (e) => { if (e.target === overlay) toggleGDev(true); };
    </script>
</body>
</html>





<nav id="slim-nav" class="slim-nav-container">
    <div class="nav-left">
        <button class="theme-toggle" onclick="toggleTheme()" title="Switch Theme">
            <i id="theme-icon" class="fas fa-moon"></i>
        </button>
        <div class="nav-divider"></div>
        <span class="nav-inscription" onclick="openForm()">
            Browse modern UI layout and pages <i class="fas fa-external-link-alt ml-1 opacity-40"></i>
        </span>
    </div>

    <div class="nav-right">
        <button onclick="scrollToTop()" class="nav-ctrl" title="Scroll to Top">
            <i class="fas fa-chevron-up"></i>
        </button>
        <button onclick="scrollToBottom()" class="nav-ctrl" title="Scroll to Bottom">
            <i class="fas fa-chevron-down"></i>
        </button>
    </div>
</nav>

<style>
    /* 1. THEME & TRANSITION LOGIC */
    :root {
        --nav-bg: rgba(10, 10, 12, 0.85);
        --nav-text: #f0f6fc;
        --nav-accent: #00f2ff;
        --nav-border: rgba(0, 242, 255, 0.15);
        --page-bg: #030712;
    }

    body[data-theme="light"] {
        --nav-bg: rgba(255, 255, 255, 0.9);
        --nav-text: #0f172a;
        --nav-accent: #2563eb;
        --nav-border: rgba(0, 0, 0, 0.08);
        --page-bg: #f8fafc;
    }

    body {
        background-color: var(--page-bg);
        transition: background-color 0.4s ease, color 0.4s ease;
    }

    /* 2. STICKY-HIDE ANIMATION */
    .slim-nav-container {
        position: fixed;
        top: 15px;
        left: 50%;
        transform: translateX(-50%);
        width: 92%;
        max-width: 750px;
        height: 44px;
        background: var(--nav-bg);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border: 1px solid var(--nav-border);
        border-radius: 14px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 12px;
        z-index: 10000;
        box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
        transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1), 
                    top 0.4s ease, 
                    background 0.3s ease;
    }

    /* The 'Hidden' State */
    .nav-up {
        transform: translateX(-50%) translateY(-100px);
    }

    /* 3. COMPONENT STYLING */
    .nav-left, .nav-right { display: flex; align-items: center; gap: 8px; }

    .nav-inscription {
        font-size: 11px;
        font-weight: 800;
        letter-spacing: 0.3px;
        color: var(--nav-text);
        cursor: pointer;
        transition: 0.2s;
        text-transform: uppercase;
    }

    .nav-inscription:hover { color: var(--nav-accent); }

    .nav-divider { width: 1px; height: 16px; background: var(--nav-border); margin: 0 4px; }

    .theme-toggle, .nav-ctrl {
        width: 32px; height: 32px;
        border-radius: 10px;
        display: flex; align-items: center; justify-content: center;
        cursor: pointer; color: var(--nav-text);
        transition: 0.2s; border: none; background: transparent;
    }

    .theme-toggle:hover, .nav-ctrl:hover {
        background: rgba(255, 255, 255, 0.08);
        color: var(--nav-accent);
    }

    body[data-theme="light"] .theme-toggle:hover,
    body[data-theme="light"] .nav-ctrl:hover {
        background: rgba(0, 0, 0, 0.05);
    }

    @media (max-width: 480px) {
        .nav-inscription { font-size: 9px; max-width: 180px; }
        .slim-nav-container { width: 96%; }
    }
</style>

<script>
    // --- 1. STICKY HIDE LOGIC ---
    let lastScrollY = window.scrollY;
    const nav = document.getElementById('slim-nav');

    window.addEventListener('scroll', () => {
        const currentScrollY = window.scrollY;

        if (currentScrollY > lastScrollY && currentScrollY > 100) {
            // Scrolling Down - Hide Nav
            nav.classList.add('nav-up');
        } else {
            // Scrolling Up - Show Nav
            nav.classList.remove('nav-up');
        }
        lastScrollY = currentScrollY;
    });

    // --- 2. EXTERNAL REDIRECT ---
    function openForm() {
        window.open('https://debeatzgh1.github.io/Pages-/', '_blank');
    }

    // --- 3. THEME ENGINE ---
    function toggleTheme() {
        const body = document.body;
        const icon = document.getElementById('theme-icon');
        const isLight = body.getAttribute('data-theme') === 'light';
        
        if (isLight) {
            body.removeAttribute('data-theme');
            icon.className = 'fas fa-moon';
            localStorage.setItem('debeatz_theme', 'dark');
        } else {
            body.setAttribute('data-theme', 'light');
            icon.className = 'fas fa-sun';
            localStorage.setItem('debeatz_theme', 'light');
        }
    }

    // --- 4. NAVIGATION ---
    function scrollToTop() { window.scrollTo({ top: 0, behavior: 'smooth' }); }
    function scrollToBottom() { window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' }); }

    // Init Theme on Load
    if (localStorage.getItem('debeatz_theme') === 'light') toggleTheme();
</script>



# 💎 Digital Ecosystem UI 
**Professional Software Development & AI Content Strategy Hub**

This ui serves as the central command center for brands. It features a high-end, responsive UI built with Tailwind CSS and a custom JavaScript-driven overlay system.

## 🚀 Key Features
- **Master Overlay Engine:** Opens external tools (WordPress Signup, Firebase Distribution, Sales Shop) in a professional, branded iframe without leaving the site.
- **Glassmorphic Bento Grid:** A modern layout showcasing services like Custom Dev, AI Automation, and Passive Income Blueprints.
- **Smart Dock:** A persistent floating navigation bar for mobile-first user engagement.
- **Session Intelligence:** Uses `localStorage` to ensure popups are non-intrusive and respect the user's journey.

## 🛠️ Tech Stack
- **Styling:** [Tailwind CSS](https://tailwindcss.com/)
- **Icons:** [FontAwesome](https://fontawesome.com/)
- **Typography:** Plus Jakarta Sans & JetBrains Mono
- **Deployment:** GitHub Pages

## 📂 Architecture
- `index.html`: Main landing page and UI logic.
- `Blogger-sign-up-button/`: Repository for WordPress subdomain claims.
- `Side-hustle-starter-kit/`: Educational resource distribution.

## ⚖️ Legal & Privacy
This UI uses local storage to optimize performance and track session status for authentication popups. No personal data is stored outside the user's browser.

---




<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Performance Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;700;800&family=JetBrains+Mono&display=swap');
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #030712; color: #f0f6fc; }
        .glass { background: rgba(255, 255, 255, 0.02); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.08); }
        
        /* Lazy Load Placeholder Style */
        .lazy-bg { background: #0f172a; position: relative; overflow: hidden; }
        .lazy-bg::before {
            content: ""; position: absolute; inset: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.05), transparent);
            animation: skeleton 1.5s infinite;
        }
        @keyframes skeleton { 0% { transform: translateX(-100%); } 100% { transform: translateX(100%); } }

        /* Auto-Slide Caption Logic */
        .caption-slider { height: 40px; overflow: hidden; cursor: pointer; }
        .caption-track { animation: slideCaptions 12s infinite; }
        @keyframes slideCaptions {
            0%, 20% { transform: translateY(0); }
            25%, 45% { transform: translateY(-40px); }
            50%, 70% { transform: translateY(-80px); }
            75%, 95% { transform: translateY(-120px); }
            100% { transform: translateY(0); }
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <div class="max-w-7xl mx-auto mb-12">
        <div onclick="redirectBanner()" class="glass rounded-2xl p-4 flex items-center justify-between border-cyan-500/20 hover:border-cyan-500/50 transition-all group">
            <div class="flex items-center gap-4">
                <div class="w-10 h-10 rounded-xl bg-cyan-500/10 flex items-center justify-center text-cyan-400">
                    <i class="fas fa-bolt animate-pulse"></i>
                </div>
                <div class="caption-slider">
                    <div id="caption-track" class="caption-track">
                        <div class="h-10 flex items-center text-xs font-bold uppercase tracking-widest text-white" data-url="https://beatzde4.blogspot.com">New: The AI Prompt Advantage E-book →</div>
                        <div class="h-10 flex items-center text-xs font-bold uppercase tracking-widest text-cyan-400" data-url="https://debeatzgh1.github.io/Blogger-sign-up-button-/">Claim Your Free .wordpress Domain →</div>
                        <div class="h-10 flex items-center text-xs font-bold uppercase tracking-widest text-white" data-url="https://appdistribution.firebase.dev/i/dc2da2d4d3766b8a">v2.4 Mobile Build Available for Test →</div>
                        <div class="h-10 flex items-center text-xs font-bold uppercase tracking-widest text-cyan-400" data-url="https://debeatzgh1.github.io/sales">Exclusive Sales Platform Now Open →</div>
                    </div>
                </div>
            </div>
            <i class="fas fa-external-link-alt text-slate-700 group-hover:text-cyan-400 text-xs transition"></i>
        </div>
    </div>

    <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="glass rounded-[2rem] p-8 min-h-[250px] flex flex-col justify-between overflow-hidden relative">
            <div class="lazy-bg absolute inset-0 -z-10">
                <img data-src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=800&q=60" class="lazy-img w-full h-full object-cover opacity-0 transition-opacity duration-1000" alt="Tech">
            </div>
            <div class="relative">
                <h3 class="text-xl font-black uppercase tracking-tighter">Software_Dev</h3>
                <p class="text-xs text-slate-400 mt-2">Tailwind CSS & Mobile Optimization.</p>
            </div>
            <button onclick="openLink('https://debeatzgh1.github.io/me-/')" class="bg-white text-black text-[10px] font-black px-4 py-2 rounded-lg w-fit uppercase">View Hub</button>
        </div>

        </div>

    <div id="master-overlay" class="fixed inset-0 bg-black/95 z-[9999] hidden flex-col">
        <div class="p-4 flex justify-between items-center border-b border-white/5">
            <span class="text-[10px] font-mono text-cyan-500">DYNAMIC_NODE_LOADING...</span>
            <button onclick="closeOverlay()" class="text-xs font-bold text-red-500 uppercase">Close [X]</button>
        </div>
        <div id="frame-container" class="flex-grow w-full relative">
            </div>
    </div>

    <script>
        // --- LAZY IMAGE LOADING ENGINE ---
        document.addEventListener("DOMContentLoaded", function() {
            const lazyImages = document.querySelectorAll('.lazy-img');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const img = entry.target;
                        img.src = img.dataset.src;
                        img.onload = () => {
                            img.classList.remove('opacity-0');
                            img.parentElement.classList.remove('lazy-bg');
                        };
                        observer.unobserve(img);
                    }
                });
            });

            lazyImages.forEach(img => observer.observe(img));
        });

        // --- BANNER REDIRECT LOGIC ---
        function redirectBanner() {
            const track = document.getElementById('caption-track');
            const style = window.getComputedStyle(track);
            const matrix = new WebKitCSSMatrix(style.transform);
            const y = Math.abs(matrix.m42);
            
            // Logic to find which slide is currently active based on Y translation
            const slideIndex = Math.round(y / 40);
            const activeSlide = track.children[slideIndex] || track.children[0];
            const targetUrl = activeSlide.getAttribute('data-url');
            
            window.open(targetUrl, '_blank');
        }

        // --- LAZY IFRAME LOGIC ---
        function openLink(url) {
            const container = document.getElementById('frame-container');
            const overlay = document.getElementById('master-overlay');
            
            // Only inject the iframe when the user asks for it (Lazy Load)
            container.innerHTML = `<iframe src="${url}" class="w-full h-full border-none"></iframe>`;
            overlay.classList.remove('hidden');
            overlay.classList.add('flex');
            document.body.style.overflow = 'hidden';
        }

        function closeOverlay() {
            const container = document.getElementById('frame-container');
            const overlay = document.getElementById('master-overlay');
            
            overlay.classList.add('hidden');
            container.innerHTML = ''; // Wipe memory
            document.body.style.overflow = 'auto';
        }
    </script>
</body>
</html>
