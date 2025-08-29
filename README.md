<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>MAKEM — Groupe Industriel</title>
  <meta name="description" content="MAKEM est un groupe industriel diversifié basé à Kinshasa : alimentation, énergie, construction et mines." />
  <meta name="theme-color" content="#0B1320" />

  <!-- Tailwind CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              red: '#D21E2B',
              redDark: '#A51822',
              navy: '#0B1320',
              navyLight: '#1A2335'
            }
          },
          fontFamily: {
            inter: ['Inter','system-ui','Segoe UI','Roboto','Helvetica','Arial','sans-serif']
          },
          boxShadow: {
            soft: '0 8px 30px rgba(0,0,0,.25)'
          }
        }
      }
    }
  </script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">

  <style>
    body {
      background: linear-gradient(135deg, #0B1320 0%, #1A2335 100%);
      color: #f9f9f9;
    }
    .glass {
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.15);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
    }
  </style>
</head>
<body class="font-inter">

  <!-- NAV -->
  <header class="sticky top-0 z-50 glass">
    <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      <a href="#top" class="text-xl font-extrabold tracking-wide text-white">MAKEM</a>
      <button id="btnMenu" class="lg:hidden p-2 rounded-md border border-gray-400/40 text-white" aria-label="Ouvrir le menu">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
      </button>
      <div id="navLinks" class="hidden lg:flex items-center gap-8">
        <a href="#apropos" class="hover:text-brand-red text-gray-200">À propos</a>
        <a href="#metiers" class="hover:text-brand-red text-gray-200">Nos Pôles</a>
        <a href="#projets" class="hover:text-brand-red text-gray-200">Projets</a>
        <a href="#gouvernance" class="hover:text-brand-red text-gray-200">Gouvernance</a>
        <a href="#contact" class="hover:text-brand-red text-gray-200">Contact</a>
        <a href="#contact" class="ml-2 inline-flex items-center rounded-md bg-brand-red px-4 py-2 font-semibold text-white hover:bg-brand-redDark shadow-soft">Nous écrire</a>
      </div>
    </nav>
  </header>

  <!-- TON CONTENU RESTE LE MÊME ICI -->
  <!-- (toutes les sections : hero, stats, apropos, pôles, projets, gouvernance, direction, contact, footer...) -->

  <!-- Scripts -->
  <script>
    // Année dynamique
    document.getElementById('year').textContent = new Date().getFullYear();

    // Menu mobile
    const btn = document.getElementById('btnMenu');
    const drawer = document.getElementById('drawer');
    const closeBtn = document.getElementById('btnClose');
    btn?.addEventListener('click', () => drawer.classList.remove('hidden'));
    closeBtn?.addEventListener('click', () => drawer.classList.add('hidden'));
    drawer?.addEventListener('click', (e) => {
      if (e.target === drawer) drawer.classList.add('hidden');
    });

    // Apparition on-scroll
    const items = document.querySelectorAll('[data-animate]');
    const io = new IntersectionObserver((entries)=>{
      entries.forEach(e=>{
        if(e.isIntersecting){
          e.target.classList.add('animate-fadeUp');
          e.target.classList.remove('opacity-0','translate-y-4','translate-y-3');
          io.unobserve(e.target);
        }
      })
    },{threshold:0.15});
    items.forEach(el=>io.observe(el));
  </script>
</body>
</html>
