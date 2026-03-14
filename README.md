# OmarPortfolio
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <!-- === SWAP: Replace with your SEO Title === -->
  <title>Omar Ghaffar — Senior Digital Designer</title>

  <!-- ─── Fonts (Cormorant Garamond & DM Sans) ────────────────────── -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />

  <!-- ─── Tailwind CSS CDN ───────────────────────────────────────── -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- ─── Font Awesome (Social Icons) ───────────────────────────── -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

  <!-- ─── Tailwind Config ───────────────────────────────────────── -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            display: ['"Cormorant Garamond"', 'serif'],
            body:    ['"DM Sans"', 'sans-serif'],
          },
          colors: {
            accent:  '#4ade80', /* Elegant Green */
            accentd: '#22c55e', /* Darker Green */
            bg:      '#0a0d0b', /* Deep Dark Green-Black */
            surface: '#111611', /* Dark Grey-Green Surface */
            border:  '#1e2a1f', /* Subtle Border */
          },
        },
      },
    };
  </script>

  <style>
    /* ─── Base & Scrollbar ────────────────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { background: #0a0d0b; scroll-behavior: smooth; }
    body { overflow-x: hidden; }

    ::-webkit-scrollbar              { width: 4px; }
    ::-webkit-scrollbar-track        { background: #0a0d0b; }
    ::-webkit-scrollbar-thumb        { background: #4ade80; border-radius: 2px; }

    /* ─── Noise Overlay ───────────────────────────────────────────── */
    body::before {
      content: '';
      position: fixed; inset: 0; z-index: 0; pointer-events: none;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
      opacity: 0.4;
    }
    body > * { position: relative; z-index: 1; }

    /* ─── Custom Cursor ───────────────────────────────────────────── */
    html, body { cursor: none; }
    #cursor {
      width: 10px; height: 10px;
      background: #4ade80; border-radius: 50%;
      position: fixed; top: 0; left: 0; z-index: 9999;
      pointer-events: none; mix-blend-mode: screen;
      transition: transform 0.1s ease;
    }
    #cursor-ring {
      width: 40px; height: 40px;
      border: 1px solid rgba(74, 222, 128, 0.4);
      border-radius: 50%;
      position: fixed; top: 0; left: 0; z-index: 9998;
      pointer-events: none;
      transition: transform 0.25s cubic-bezier(.16,1,.3,1), opacity 0.2s;
    }

    /* ─── Navbar ──────────────────────────────────────────────────── */
    #navbar {
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      transition: border-bottom 0.3s;
    }
    #navbar.scrolled { border-bottom: 1px solid #1e2a1f; background: rgba(10, 13, 11, 0.8); }

    .nav-link {
      position: relative; letter-spacing: 0.1em; font-size: 0.75rem; text-transform: uppercase;
      color: #9ab89c; transition: color 0.3s;
    }
    .nav-link:hover { color: #4ade80; }
    .nav-link::after {
      content: ''; position: absolute; bottom: -4px; left: 0; width: 0; height: 1px;
      background: #4ade80; transition: width 0.3s;
    }
    .nav-link:hover::after { width: 100%; }

    /* ─── Hero Stagger Reveal ─────────────────────────────────────── */
    .hero-line { display: block; overflow: hidden; }
    .hero-line span {
      display: block; transform: translateY(110%);
      animation: lineReveal 1.2s cubic-bezier(.16,1,.3,1) forwards;
    }
    @keyframes lineReveal { to { transform: translateY(0); } }

    .hero-line:nth-child(1) span { animation-delay: 0.1s; }
    .hero-line:nth-child(2) span { animation-delay: 0.2s; }
    .hero-line:nth-child(3) span { animation-delay: 0.3s; }

    /* ─── Animations ──────────────────────────────────────────────── */
    .reveal {
      opacity: 0; transform: translateY(30px);
      transition: opacity 1s cubic-bezier(.16,1,.3,1), transform 1s cubic-bezier(.16,1,.3,1);
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    .reveal-stagger > * {
      opacity: 0; transform: translateY(20px);
      transition: opacity 0.8s cubic-bezier(.16,1,.3,1), transform 0.8s cubic-bezier(.16,1,.3,1);
    }
    .reveal-stagger.visible > *:nth-child(1) { opacity: 1; transform: translateY(0); transition-delay: 0.1s; }
    .reveal-stagger.visible > *:nth-child(2) { opacity: 1; transform: translateY(0); transition-delay: 0.2s; }
    .reveal-stagger.visible > *:nth-child(3) { opacity: 1; transform: translateY(0); transition-delay: 0.3s; }
    .reveal-stagger.visible > *:nth-child(4) { opacity: 1; transform: translateY(0); transition-delay: 0.4s; }

    @keyframes scrollPing {
      0% { opacity: 1; transform: translateY(0); }
      100% { opacity: 0; transform: translateY(12px); }
    }
    .scroll-dot { animation: scrollPing 2s infinite; }

    /* ─── Project Card Styles ─────────────────────────────────────── */
    .project-card {
      transition: border-color 0.4s, transform 0.4s cubic-bezier(.16,1,.3,1);
    }
    .project-card:hover {
      border-color: #4ade80;
      transform: translateY(-8px);
    }
    .project-card .img-wrap img {
      filter: grayscale(40%) brightness(0.8);
      transition: transform 0.8s cubic-bezier(.16,1,.3,1), filter 0.4s;
    }
    .project-card:hover .img-wrap img {
      transform: scale(1.05);
      filter: grayscale(0%) brightness(1);
    }

    /* ─── Utility ─────────────────────────────────────────────────── */
    .section-label {
      font-size: 0.65rem; letter-spacing: 0.25em; text-transform: uppercase;
      color: #4ade80; font-weight: 500; display: flex; align-items: center; gap: 1rem;
    }
    .section-label::before { content: ''; width: 24px; height: 1px; background: #4ade80; }
  </style>
</head>

<body class="bg-bg font-body text-[#e8ede9] antialiased">

  <!-- ─── Custom Cursor ─────────────────────────────────────────── -->
  <div id="cursor"></div>
  <div id="cursor-ring"></div>

  <!-- ─── Navbar ────────────────────────────────────────────────── -->
  <header id="navbar" class="fixed top-0 w-full z-50 px-6 md:px-12 py-5 flex justify-between items-center transition-all duration-300">
    <a href="#hero" class="font-display text-2xl font-light tracking-widest text-[#e8ede9] hover:text-accent transition-colors">
      Omar<span class="text-accent">.</span>
    </a>

    <!-- Desktop Nav -->
    <nav class="hidden md:flex gap-10">
      <a href="#about" class="nav-link">About</a>
      <a href="#work" class="nav-link">Work</a>
      <a href="#contact" class="nav-link">Contact</a>
    </nav>

    <!-- Mobile Toggle -->
    <button id="menu-toggle" class="md:hidden flex flex-col gap-1.5 p-2 focus:outline-none" aria-label="Toggle Menu">
      <span class="w-6 h-px bg-white transition-all duration-300"></span>
      <span class="w-6 h-px bg-white transition-all duration-300"></span>
      <span class="w-6 h-px bg-white transition-all duration-300"></span>
    </button>
  </header>

  <!-- Mobile Menu Overlay -->
  <div id="mobile-menu" class="fixed inset-0 z-40 bg-bg translate-x-full transition-transform duration-500 flex flex-col justify-center items-center gap-8 text-2xl font-display">
    <a href="#about" class="mobile-nav-link">About</a>
    <a href="#work" class="mobile-nav-link">Work</a>
    <a href="#contact" class="mobile-nav-link">Contact</a>
  </div>


  <!-- ─── Hero Section ──────────────────────────────────────────── -->
  <section id="hero" class="relative h-screen flex flex-col justify-center px-6 md:px-12 overflow-hidden">
    <!-- Background Glow -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-accent/5 rounded-full blur-[120px] pointer-events-none"></div>

    <div class="max-w-6xl mx-auto w-full pt-20">
      <p class="section-label mb-8 opacity-0 animate-[fadeUp_1s_0.8s_forwards]">
        omarghaffardesign.co.uk
      </p>

      <h1 class="font-display text-[clamp(2.5rem,8vw,6.5rem)] leading-[1.05] font-light mb-10">
        <span class="hero-line"><span>Crafting Visual</span></span>
        <span class="hero-line"><span>Stories that</span></span>
        <span class="hero-line italic text-accent"><span>Move People.</span></span>
      </h1>

      <div class="flex flex-col sm:flex-row sm:items-center gap-8 opacity-0 animate-[fadeUp_1s_1s_forwards]">
        <div class="flex items-center gap-3 border border-border px-4 py-2 rounded-full w-fit bg-surface/50">
          <span class="relative flex h-2 w-2">
            <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-accent opacity-75"></span>
            <span class="relative inline-flex rounded-full h-2 w-2 bg-accent"></span>
          </span>
          <span class="text-xs uppercase tracking-widest font-medium">Senior Digital Designer</span>
        </div>

        <a href="#work" class="group flex items-center gap-4 text-xs uppercase tracking-[0.2em] font-medium bg-accent text-bg px-8 py-4 hover:bg-white transition-all duration-300">
          View My Work
          <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 transition-transform group-hover:translate-x-2" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg>
        </a>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-12 left-1/2 -translate-x-1/2 flex flex-col items-center gap-3">
      <span class="text-[0.6rem] uppercase tracking-widest opacity-40">Scroll</span>
      <div class="w-px h-10 bg-border relative overflow-hidden">
        <div class="scroll-dot absolute top-0 left-0 w-full h-3 bg-accent"></div>
      </div>
    </div>

    <!-- Diagonal Cut -->
    <div class="absolute bottom-0 left-0 w-full h-24 pointer-events-none">
      <svg class="w-full h-full" viewBox="0 0 1440 100" preserveAspectRatio="none">
        <path d="M0 100 L1440 0 V100 Z" fill="#111611"></path>
      </svg>
    </div>
  </section>


  <!-- ─── About Section ─────────────────────────────────────────── -->
  <section id="about" class="bg-surface py-32 px-6 md:px-12">
    <div class="max-w-6xl mx-auto grid md:grid-cols-2 gap-20 items-start">
      
      <div class="reveal">
        <h2 class="font-display text-5xl md:text-6xl font-light leading-tight mb-8">
          Design is both <br/>
          <span class="italic text-accent">craft & strategy.</span>
        </h2>
        <div class="space-y-6 text-[#9ab89c] leading-relaxed max-w-lg">
          <p>Creative and versatile Senior Digital Designer with 4+ years of experience producing high-impact visual content across digital, social, and print platforms.</p>
          <p>Expert in Adobe Creative Suite, motion graphics, and video editing, with a specialized focus on AI Design and AI Motion Design — including hands-on workflows with Google AI Studio and Gemini 2.0 Pro. Proven track record in campaign design and live event production, blending technical precision with a passion for storytelling and audience engagement.</p>
        </div>
        <a href="#contact" class="inline-flex items-center gap-4 text-xs uppercase tracking-widest text-accent mt-10 hover:gap-6 transition-all duration-300">
          Get in touch
          <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg>
        </a>
      </div>

      <div class="reveal-stagger grid gap-4">
        <!-- Stat Grid -->
        <div class="grid grid-cols-2 gap-4 mb-4">
          <div class="p-8 border border-border bg-bg/50">
            <span class="block font-display text-4xl text-accent mb-1">4+</span>
            <span class="text-[0.6rem] uppercase tracking-widest opacity-60">Years Experience</span>
          </div>
          <div class="p-8 border border-border bg-bg/50">
            <span class="block font-display text-4xl text-accent mb-1">GEN</span>
            <span class="text-[0.6rem] uppercase tracking-widest opacity-60">Gemini AI Workflows</span>
          </div>
        </div>
        <!-- Skills Chips -->
        <div class="p-8 border border-border bg-bg/20 flex flex-wrap gap-2">
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">Adobe Suite</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">Motion Graphics</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest text-[#9ab89c]">Video Editing</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">UI/UX Design</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest text-[#9ab89c]">Figma</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">Live Event Visuals</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">Print Design</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest text-[#9ab89c]">Campaign Design</span>
          <!-- Special AI Borders -->
          <span class="px-3 py-1.5 border border-accent/40 text-[0.65rem] uppercase tracking-widest text-accent">Google AI Studio</span>
          <span class="px-3 py-1.5 border border-accent/40 text-[0.65rem] uppercase tracking-widest text-accent">Gemini 2.0 Pro</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">AI Motion Design</span>
          <span class="px-3 py-1.5 border border-border text-[0.65rem] uppercase tracking-widest">Generative AI</span>
        </div>
      </div>
    </div>
  </section>


  <!-- ─── Portfolio Section ──────────────────────────────────────── -->
  <section id="work" class="py-32 px-6 md:px-12 bg-bg">
    <div class="max-w-6xl mx-auto">
      <div class="reveal flex flex-col md:flex-row md:items-end justify-between gap-6 mb-16">
        <div>
          <p class="section-label mb-4">Selected Portfolio</p>
          <h2 class="font-display text-5xl font-light">Work & Experiments</h2>
        </div>
        <!-- === SWAP: Update Behance Link === -->
        <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="text-xs uppercase tracking-widest border border-border px-6 py-3 hover:border-accent hover:text-accent transition-all duration-300">
          View All Projects
        </a>
      </div>

      <div class="reveal-stagger grid md:grid-cols-2 gap-8">
        
        <!-- Project Card 1 -->
        <article class="project-card border border-border bg-surface overflow-hidden group">
          <div class="img-wrap aspect-[16/10] overflow-hidden">
            <!-- === SWAP: Update Card Image === -->
            <img src="https://images.unsplash.com/photo-1620641788421-7a1c342ea42e?auto=format&fit=crop&q=80&w=800" alt="Neural Brand Campaign" class="w-full h-full object-cover">
          </div>
          <div class="p-8">
            <span class="text-[0.6rem] uppercase tracking-[0.2em] text-accent font-medium">AI Motion Design · Campaign</span>
            <h3 class="font-display text-2xl mt-3 mb-4">Neural Brand Campaign</h3>
            <p class="text-sm text-[#9ab89c] leading-relaxed mb-8">A full AI-augmented motion campaign blending generative visuals with precision-timed typography to launch a tech product.</p>
            <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="flex items-center gap-3 text-[0.65rem] uppercase tracking-widest text-white group-hover:text-accent transition-colors">
              View Project <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path d="M14 5l7 7m0 0l-7 7m7-7H3" stroke-width="2"/></svg>
            </a>
          </div>
        </article>

        <!-- Project Card 2 -->
        <article class="project-card border border-border bg-surface overflow-hidden group">
          <div class="img-wrap aspect-[16/10] overflow-hidden">
            <!-- === SWAP: Update Card Image === -->
            <img src="https://images.unsplash.com/photo-1550684848-fac1c5b4e853?auto=format&fit=crop&q=80&w=800" alt="Live Event Stage Visuals" class="w-full h-full object-cover">
          </div>
          <div class="p-8">
            <span class="text-[0.6rem] uppercase tracking-[0.2em] text-accent font-medium">Live Event · Motion</span>
            <h3 class="font-display text-2xl mt-3 mb-4">Live Event Stage Visuals</h3>
            <p class="text-sm text-[#9ab89c] leading-relaxed mb-8">Full-scale real-time motion graphics package designed for a sold-out arena event, covering LED walls and broadcast overlays.</p>
            <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="flex items-center gap-3 text-[0.65rem] uppercase tracking-widest text-white group-hover:text-accent transition-colors">
              View Project <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path d="M14 5l7 7m0 0l-7 7m7-7H3" stroke-width="2"/></svg>
            </a>
          </div>
        </article>

        <!-- Project Card 3 -->
        <article class="project-card border border-border bg-surface overflow-hidden group">
          <div class="img-wrap aspect-[16/10] overflow-hidden">
            <!-- === SWAP: Update Card Image === -->
            <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&q=80&w=800" alt="360 Social Campaign" class="w-full h-full object-cover">
          </div>
          <div class="p-8">
            <span class="text-[0.6rem] uppercase tracking-[0.2em] text-accent font-medium">Social Media · Digital</span>
            <h3 class="font-display text-2xl mt-3 mb-4">360° Social Campaign</h3>
            <p class="text-sm text-[#9ab89c] leading-relaxed mb-8">A cohesive cross-platform visual identity and content system spanning Instagram, TikTok and YouTube for a global brand.</p>
            <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="flex items-center gap-3 text-[0.65rem] uppercase tracking-widest text-white group-hover:text-accent transition-colors">
              View Project <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path d="M14 5l7 7m0 0l-7 7m7-7H3" stroke-width="2"/></svg>
            </a>
          </div>
        </article>

        <!-- Project Card 4 -->
        <article class="project-card border border-border bg-surface overflow-hidden group">
          <div class="img-wrap aspect-[16/10] overflow-hidden">
            <!-- === SWAP: Update Card Image === -->
            <img src="https://images.unsplash.com/photo-1558655146-d09347e92766?auto=format&fit=crop&q=80&w=800" alt="Editorial Brand Identity" class="w-full h-full object-cover">
          </div>
          <div class="p-8">
            <span class="text-[0.6rem] uppercase tracking-[0.2em] text-accent font-medium">Print · Brand Identity</span>
            <h3 class="font-display text-2xl mt-3 mb-4">Editorial Brand Identity</h3>
            <p class="text-sm text-[#9ab89c] leading-relaxed mb-8">End-to-end brand identity and print collateral suite — from logo system to packaging — for a luxury lifestyle brand launch.</p>
            <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="flex items-center gap-3 text-[0.65rem] uppercase tracking-widest text-white group-hover:text-accent transition-colors">
              View Project <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path d="M14 5l7 7m0 0l-7 7m7-7H3" stroke-width="2"/></svg>
            </a>
          </div>
        </article>

      </div>
    </div>
  </section>


  <!-- ─── Contact Section ───────────────────────────────────────── -->
  <section id="contact" class="relative bg-surface py-32 px-6 overflow-hidden">
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[500px] h-[500px] bg-accent/10 rounded-full blur-[100px] pointer-events-none"></div>

    <div class="max-w-3xl mx-auto text-center relative z-10">
      <p class="section-label inline-flex mb-8 reveal">Get In Touch</p>
      <h2 class="reveal font-display text-5xl md:text-7xl font-light mb-8 leading-tight">
        Let's build something <br/>
        <span class="italic text-accent">extraordinary.</span>
      </h2>
      <p class="reveal text-[#9ab89c] text-lg leading-relaxed mb-12">
        Available for freelance projects, creative collaborations, and full-time opportunities. Drop a line — I'd love to hear about your vision.
      </p>

      <!-- === SWAP: Replace Email === -->
      <a href="mailto:hello@omarghaffardesign.co.uk" class="reveal inline-block font-display text-2xl md:text-4xl text-accent border-b border-accent pb-2 hover:text-white hover:border-white transition-all duration-300">
        hello@omarghaffardesign.co.uk
      </a>

      <div class="reveal mt-16 flex justify-center gap-6">
        <!-- === SWAP: Update Social Links === -->
        <a href="https://www.behance.net/Omarghaffar21" target="_blank" class="w-12 h-12 flex items-center justify-center border border-border rounded-full hover:border-accent hover:text-accent transition-all duration-300" aria-label="Behance">
          <i class="fa-brands fa-behance"></i>
        </a>
        <a href="#" target="_blank" class="w-12 h-12 flex items-center justify-center border border-border rounded-full hover:border-accent hover:text-accent transition-all duration-300" aria-label="LinkedIn">
          <i class="fa-brands fa-linkedin-in"></i>
        </a>
        <a href="#" target="_blank" class="w-12 h-12 flex items-center justify-center border border-border rounded-full hover:border-accent hover:text-accent transition-all duration-300" aria-label="Instagram">
          <i class="fa-brands fa-instagram"></i>
        </a>
        <a href="mailto:hello@omarghaffardesign.co.uk" class="w-12 h-12 flex items-center justify-center border border-border rounded-full hover:border-accent hover:text-accent transition-all duration-300" aria-label="Email">
          <i class="fa-regular fa-envelope"></i>
        </a>
      </div>
    </div>
  </section>


  <!-- ─── Footer ────────────────────────────────────────────────── -->
  <footer class="bg-bg py-10 px-6 md:px-12 border-t border-border">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4 text-[0.65rem] uppercase tracking-widest opacity-50 font-medium">
      <p>© <span id="year"></span> Omar Ghaffar Design</p>
      <p>omarghaffardesign.co.uk</p>
    </div>
  </footer>


  <!-- ─── Scripts ───────────────────────────────────────────────── -->
  <script>
    /* ─── Year Updater ─── */
    document.getElementById('year').innerText = new Date().getFullYear();

    /* ─── Custom Cursor ─── */
    const cursor = document.getElementById('cursor');
    const ring   = document.getElementById('cursor-ring');
    let mouseX = 0, mouseY = 0;
    let ringX = 0, ringY = 0;

    window.addEventListener('mousemove', e => {
      mouseX = e.clientX; mouseY = e.clientY;
      cursor.style.transform = `translate3d(${mouseX - 5}px, ${mouseY - 5}px, 0)`;
    });

    function animate() {
      ringX += (mouseX - ringX) * 0.15;
      ringY += (mouseY - ringY) * 0.15;
      ring.style.transform = `translate3d(${ringX - 20}px, ${ringY - 20}px, 0)`;
      requestAnimationFrame(animate);
    }
    animate();

    // Scale ring on interactive elements
    document.querySelectorAll('a, button, .project-card').forEach(el => {
      el.addEventListener('mouseenter', () => ring.style.transform += ' scale(1.5)');
      el.addEventListener('mouseleave', () => ring.style.transform = ring.style.transform.replace(' scale(1.5)', ''));
    });

    // Hide for touch
    if ('ontouchstart' in window) {
      cursor.style.display = 'none';
      ring.style.display = 'none';
    }

    /* ─── Scroll Navbar State ─── */
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 50) navbar.classList.add('scrolled');
      else navbar.classList.remove('scrolled');
    });

    /* ─── Mobile Menu Logic ─── */
    const menuBtn = document.getElementById('menu-toggle');
    const mobileMenu = document.getElementById('mobile-menu');
    const spans = menuBtn.querySelectorAll('span');
    let isOpen = false;

    menuBtn.addEventListener('click', () => {
      isOpen = !isOpen;
      mobileMenu.classList.toggle('translate-x-full', !isOpen);
      spans[0].classList.toggle('rotate-45', isOpen);
      spans[0].classList.toggle('translate-y-[7px]', isOpen);
      spans[1].classList.toggle('opacity-0', isOpen);
      spans[2].classList.toggle('-rotate-45', isOpen);
      spans[2].classList.toggle('-translate-y-[7px]', isOpen);
    });

    document.querySelectorAll('.mobile-nav-link').forEach(link => {
      link.addEventListener('click', () => menuBtn.click());
    });

    /* ─── Intersection Observer for Revelations ─── */
    const observerOptions = { threshold: 0.1 };
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, observerOptions);

    document.querySelectorAll('.reveal, .reveal-stagger').forEach(el => observer.observe(el));

  </script>

  <!-- CSS Animation Polyfills for Hero -->
  <style>
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</body>
</html>
