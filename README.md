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
