<div id="smart-float-container" class="float-wrapper">
    <div id="float-nudge" class="float-nudge">
        <p>Claim your <strong>.wordpress.com</strong> site!</p>
        <button onclick="dismissNudge()" class="nudge-close">×</button>
    </div>

    <div class="float-main-btn" onclick="launchWPSignup()">
        <i class="fab fa-wordpress"></i>
        <span class="btn-label">Create Site</span>
    </div>
</div>

<style>
    .float-wrapper {
        position: fixed;
        bottom: 20px;
        left: 70%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 12px;
        z-index: 10005;
        font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Floating Nudge Bubble */
    .float-nudge {
        background: rgba(10, 10, 12, 0.9);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(0, 242, 255, 0.3);
        padding: 8px 15px;
        border-radius: 12px;
        color: #f0f6fc;
        font-size: 11px;
        white-space: nowrap;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        display: none; /* Controlled by JS */
        animation: slideUpFade 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        align-items: center;
        gap: 10px;
    }

    .nudge-close {
        background: none;
        border: none;
        color: #64748b;
        font-size: 16px;
        cursor: pointer;
        padding: 0 2px;
        line-height: 1;
    }

    .nudge-close:hover { color: #00f2ff; }

    /* Main Button */
    .float-main-btn {
        background: #00f2ff;
        color: #000;
        padding: 10px 20px;
        border-radius: 99px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        font-weight: 800;
        text-transform: uppercase;
        font-size: 10px;
        letter-spacing: 1px;
        box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        transition: all 0.3s ease;
    }

    .float-main-btn:hover {
        transform: translateY(-3px) scale(1.05);
        background: #fff;
        box-shadow: 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .float-main-btn i { font-size: 14px; }

    @keyframes slideUpFade {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 480px) {
        .float-main-btn { padding: 10px 16px; }
        .btn-label { display: none; } /* On mobile, only show icon to save space */
    }
</style>

<script>
    const NUDGE_KEY = 'wp_nudge_dismissed';

    function showNudge() {
        const isDismissed = localStorage.getItem(NUDGE_KEY);
        if (!isDismissed) {
            document.getElementById('float-nudge').style.display = 'flex';
        }
    }

    function dismissNudge() {
        document.getElementById('float-nudge').style.display = 'none';
        // Remember dismissal for 24h
        localStorage.setItem(NUDGE_KEY, 'true');
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Blogger-sign-up-button-/";
        
        // Use existing overlay logic if available
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-popup nudge after 8 seconds
    window.addEventListener('load', () => {
        setTimeout(showNudge, 8000);
    });
</script>






<iframe class="BLOG_video_class" allowfullscreen="" youtube-src-id="rg7rR2MHdkQ" width="320" height="266" src="https://www.youtube.com/embed/rg7rR2MHdkQ"></iframe>
<!-- Floating Flashcards Widget -->
<style>
/* Floating Button */
#flashcards-launcher {
  position: fixed;
  center: 40px;
  right: 20px;
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  font-size: 26px;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  z-index: 9999;
}

/* Modal Overlay */
#flashcards-modal {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.6);
  z-index: 10000;
  justify-content: center;
  align-items: center;
}

/* Modal Content */
#flashcards-box {
  background: white;
  padding: 20px;
  border-radius: 15px;
  width: 320px;
  max-width: 95%;
  box-shadow: 0 6px 16px rgba(0,0,0,0.3);
  text-align: center;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.9);}
  to { opacity: 1; transform: scale(1);}
}

/* Flashcard Style */
#flashcard {
  width: 100%;
  height: 180px;
  margin: auto;
  perspective: 1000px;
  cursor: pointer;
}
#card-inner {
  position: relative;
  width: 100%; height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}
#question, #answer {
  position: absolute;
  width: 100%; height: 100%;
  backface-visibility: hidden;
  display: flex; align-items: center; justify-content: center;
  font-size: 18px; padding: 10px; border-radius: 12px;
}
#question { background: #2563eb; color: white; }
#answer { background: #facc15; color: black; transform: rotateY(180deg); }

/* Buttons */
#flashcards-box button {
  padding: 8px 14px;
  margin: 6px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
}
#close-btn { background: #dc2626; color: white; }
#prev-btn { background: #64748b; color: white; }
#next-btn { background: #16a34a; color: white; }
</style>

<!-- Floating Button -->
<button id="flashcards-launcher">💡</button>

<!-- Modal -->
<div id="flashcards-modal">
  <div id="flashcards-box">
    <h3>💡 Flashcards Learning App</h3>
    <div id="flashcard" onclick="flipCard()">
      <div id="card-inner">
        <div id="question"></div>
        <div id="answer"></div>
      </div>
    </div>
    <div style="margin-top:12px;">
      <button id="prev-btn" onclick="prevCard()">⬅ Prev</button>
      <button id="next-btn" onclick="nextCard()">Next ➡</button>
    </div>
    <button id="close-btn" onclick="closeFlashcards()">✖ Close</button>
  </div>
</div>

<script>
// Flashcards Data
const flashcards = [
  { question: "What does HTTP stand for?", answer: "HyperText Transfer Protocol" },
  { question: "What is the function of a web browser?", answer: "To retrieve, interpret, and display web content" },
  { question: "What is an API?", answer: "Application Programming Interface – allows apps to communicate" },
  { question: "What is DNS?", answer: "Domain Name System" },
  { question: "What does AI stand for?", answer: "Artificial Intelligence" },
  { question: "What is Machine Learning?", answer: "AI systems that learn patterns from data" },
  { question: "What is NLP?", answer: "Natural Language Processing – AI that understands human language" },
  { question: "Give an example of an AI tool", answer: "ChatGPT, Siri, MidJourney" },
  { question: "What is Computer Vision?", answer: "AI that interprets images and videos" },
  { question: "What does HTML stand for?", answer: "HyperText Markup Language" },
  { question: "Difference between Java & JavaScript?", answer: "Java = programming language, JS = web scripting" },
  { question: "What is CSS?", answer: "Cascading Style Sheets" },
  { question: "What is Git?", answer: "Version control system" },
  { question: "What is open-source software?", answer: "Software with public code, free to modify & share" },
  { question: "What is e-commerce?", answer: "Buying and selling products/services online" },
  { question: "What is dropshipping?", answer: "Selling online without holding inventory" },
  { question: "What is affiliate marketing?", answer: "Earning commissions by promoting products" },
  { question: "What is SEO?", answer: "Search Engine Optimization" },
  { question: "What is digital marketing?", answer: "Promoting products/services online" },
  { question: "What is SaaS?", answer: "Software as a Service – cloud-based applications" }
];

// State
let currentIndex = 0;
const cardInner = document.getElementById("card-inner");
const question = document.getElementById("question");
const answer = document.getElementById("answer");
const modal = document.getElementById("flashcards-modal");

// Load Card
function loadCard(index) {
  question.textContent = flashcards[index].question;
  answer.textContent = flashcards[index].answer;
  cardInner.style.transform = "rotateY(0deg)";
}
function flipCard() {
  cardInner.style.transform = 
    cardInner.style.transform === "rotateY(180deg)" ? "rotateY(0deg)" : "rotateY(180deg)";
}
function nextCard() {
  currentIndex = (currentIndex + 1) % flashcards.length;
  loadCard(currentIndex);
}
function prevCard() {
  currentIndex = (currentIndex - 1 + flashcards.length) % flashcards.length;
  loadCard(currentIndex);
}

// Modal Controls
document.getElementById("flashcards-launcher").onclick = () => {
  modal.style.display = "flex";
  loadCard(currentIndex);
};
function closeFlashcards() {
  modal.style.display = "none";
}

// Init
loadCard(currentIndex);
</script>




# 💡 Floating Flashcards Widget

A simple **floating flashcards learning app** for websites and blogs.  
Click the floating 💡 button to launch the flashcards modal, flip through interactive Q&A cards, and learn on the go!

---

## 🚀 Features
- Floating launcher button (bottom-right corner)
- Smooth modal pop-up with fade-in animation
- Interactive flashcards with **flip effect**
- 20 curated questions on **Tech, AI, Software Development & Online Business**
- Next / Previous navigation buttons
- Easy to embed in **Blogger, WordPress, or any website**

---

## 📸 Preview
![Thumbnail](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/min.png)

👉 **[Live Preview](https://beatzde4.blogspot.com/p/open-debeatzgh.html)**

---

## 📦 Installation
1. Copy the full widget code from [`index.html`](index.html).
2. Paste inside your website/blog HTML (before the `</body>` tag).
3. Save & publish 🚀

---

## 🛠️ Usage
- Click 💡 to open flashcards
- Tap a card to flip (Question ↔ Answer)
- Navigate using ⬅ Prev / Next ➡
- Close ❌ button to exit

---

## 📂 File Structure

# 🚀 DeBeatzGH – AI Tools & Side Hustle Hub  

![DeBeatzGH Thumbnail](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticdesignfeaturinganai-themedicon28likeabraincircuitorrobot29overlaidwithdebeatzghoraitoolshustles6089986211026037047.jpg)  

## 🌟 About  
Welcome to **[DeBeatzGH](https://debeatzgh.wordpress.com/)** — your go-to hub for **AI tools, side hustle strategies, blogging resources, and digital growth guides**.  

Our platform is built to help **students, creators, startups, and professionals** unlock the power of AI, monetize their skills, and thrive in today’s digital economy.  

### ✨ What You’ll Find  
- 💡 Explore **AI prompts, tools, and hacks**  
- 📈 Discover **side hustle strategies & online income ideas**  
- ✍️ Access **blogging & digital business guides**  
- 🚀 Stay ahead with **regular updates and fresh insights**  

---

## 👉 Get Started  
🔥 **Start your journey today → [Visit DeBeatzGH](https://debeatzgh.wordpress.com/)**  

---

<!-- README: DebeatzGH Digital Store (HTML-friendly for GitHub) -->
<div align="center">
  <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">
    <img
      src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"
      alt="DebeatzGH Digital Store"
      style="max-width:100%; border-radius:16px;"
    />
  </a>

  <h1 style="margin-top: 14px;">DebeatzGH Digital Store</h1>
  <p style="max-width:780px;">
    Your hub for AI insights, tech tutorials, side-hustle playbooks, and productivity tools.
    Learn, build, and launch digital projects faster.
  </p>

  <!-- CTAs -->
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      🚀 View Live App
    </a>
    <a href="https://github.com/debeatzgh1/Personal-Portfolio-site-" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #111827;">
      ⭐ Star this Repo
    </a>
  </p>
</div>

<hr/>

<h2>Overview</h2>
<p>
  <strong>DebeatzGH</strong> helps beginners and creators build profitable digital assets:
  blogs, affiliate funnels, AI-assisted content, and more. Explore tutorials, tools, and
  ready-to-use components to speed up your workflow.
</p>

<h2>Features</h2>
<ul>
  <li><strong>AI & Tech Learning:</strong> Bite-sized guides for modern tools and workflows.</li>
  <li><strong>Side-Hustle Playbooks:</strong> Practical steps to validate and launch ideas.</li>
  <li><strong>Productivity Toolkit:</strong> Reusable widgets, templates, and scripts.</li>
  <li><strong>Beginner-Friendly:</strong> Clear explanations, curated resources, and examples.</li>
</ul>

<h2>Quick Start</h2>
<ol>
  <li>Clone:
    <pre><code>git clone https://github.com/debeatzgh1/Personal-Portfolio-site-</code></pre>
  </li>
  <li>Enter folder:
    <pre><code>cd debeatzgh</code></pre>
  </li>
  <li>Install deps (adjust to your stack):
    <pre><code># Node
npm install
npm run dev

# or Python
pip install -r requirements.txt
python app.py</code></pre>
  </li>
  <li>Open in browser:
    <pre><code>http://localhost:3000</code></pre>
  </li>
</ol>

<h2>Project Links</h2>
<ul>
  <li>🌐 Live App: <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">socialcreator.com/debeatzgh</a></li>
  <li>🖼️ Thumbnail: <a href="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" target="_blank" rel="noopener">View image</a></li>
</ul>

<h2>Contributing</h2>
<p>
  Contributions are welcome! Open an issue for bugs or ideas. For changes, fork the repo,
  create a feature branch, and submit a pull request.
</p>

<h2>License</h2>
<p>
  Released under the <a href="./LICENSE">MIT License</a>.
</p>

<hr/>

<div align="center">
  <p><em>If this project helps you, consider giving it a star. It really helps! ⭐</em></p>
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin-top:6px; border-radius:10px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      Open DebeatzGH Now →
    </a>
  </p>
</div>
