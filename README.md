<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Noko Simple Fast Food</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Noko Simple – burgers, fries, pizza, chicken and more. Hot, fresh and delivered fast." />

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
          },
          colors: {
            primary: '#ff783a',
            primaryDark: '#e77111',
            secondary: '#ffc857',
            dark: '#020617',
          },
          boxShadow: {
            card: '0 18px 40px rgba(15, 23, 42, 0.25)',
          },
          borderRadius: {
            '3xl': '1.75rem',
          },
        },
      },
    };
  </script>

  <style>
    html {
      scroll-behavior: smooth;
    }

    body {
      background-image:
        radial-gradient(circle at 0 0, rgba(255, 200, 87, 0.16) 0, transparent 40%),
        radial-gradient(circle at 100% 100%, rgba(255, 120, 58, 0.14) 0, transparent 45%);
      background-attachment: fixed;
    }

    /* Scroll reveal */
    .reveal-on-scroll {
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .reveal-on-scroll.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Popup Notification */
    #order-popup {
      position: fixed;
      bottom: 100px;
      right: 22px;
      background: #0f172a;
      color: #fff;
      padding: 12px 18px;
      border-radius: 12px;
      font-size: 0.85rem;
      box-shadow: 0 12px 30px rgba(0,0,0,0.35);
      opacity: 0;
      transform: translateY(20px);
      transition: 0.25s ease;
      z-index: 99999;
      pointer-events: none;
    }
    #order-popup.show {
      opacity: 1;
      transform: translateY(0);
    }

    /* Floating WhatsApp Button with Logo */
    #whatsapp-float {
      position: fixed;
      bottom: 22px;
      right: 22px;
      width: 60px;
      height: 60px;
      background: #25D366;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 34px;
      cursor: pointer;
      z-index: 9999;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      transition: 0.3s ease;
      animation: pulse 1.8s infinite;
    }
    #whatsapp-float img {
      width: 34px;
      height: 34px;
    }
    #whatsapp-float:hover {
      transform: scale(1.15);
      background: #1ebe5d;
    }
    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.12); }
      100% { transform: scale(1); }
    }

    /* Floating Call Button */
    #call-float {
      position: fixed;
      bottom: 22px;
      right: 96px;
      width: 54px;
      height: 54px;
      background: #0f172a;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 26px;
      cursor: pointer;
      z-index: 9998;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      transition: 0.3s ease;
    }
    #call-float:hover {
      transform: scale(1.12);
      background: #020617;
    }

    /* Back to top */
    #back-to-top {
      position: fixed;
      bottom: 90px;
      left: 22px;
      width: 42px;
      height: 42px;
      border-radius: 999px;
      background: #0f172a;
      color: #e5e7eb;
      border: 1px solid rgba(148,163,184,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      cursor: pointer;
      z-index: 9998;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.25s ease, transform 0.25s ease;
      transform: translateY(10px);
    }
    #back-to-top.show {
      opacity: 1;
      pointer-events: auto;
      transform: translateY(0);
    }

    /* Cart badge & panel */
    #cart-badge {
      position: fixed;
      top: 90px;
      right: 22px;
      z-index: 9990;
      background: #0f172a;
      color: #e5e7eb;
      padding: 6px 10px;
      border-radius: 999px;
      font-size: 0.8rem;
      display: flex;
      align-items: center;
      gap: 6px;
      box-shadow: 0 12px 30px rgba(15,23,42,0.4);
      cursor: pointer;
    }
    #cart-panel {
      position: fixed;
      top: 0;
      right: 0;
      width: 290px;
      max-width: 80%;
      height: 100vh;
      background: #020617;
      color: #e5e7eb;
      box-shadow: -8px 0 30px rgba(15,23,42,0.6);
      z-index: 9991;
      transform: translateX(100%);
      transition: transform 0.3s ease;
      display: flex;
      flex-direction: column;
    }
    #cart-panel.open {
      transform: translateX(0);
    }
    #cart-items {
      flex: 1;
      overflow-y: auto;
      padding-right: 6px;
    }
    #cart-items::-webkit-scrollbar {
      width: 4px;
    }
    #cart-items::-webkit-scrollbar-thumb {
      background: rgba(148,163,184,0.7);
      border-radius: 999px;
    }

    /* Dark mode basic override */
    .dark-mode {
      background-color: #020617;
      color: #e5e7eb;
    }
    .dark-mode .bg-white {
      background-color: #020617 !important;
    }
    .dark-mode .bg-slate-100 {
      background-color: #020617 !important;
    }
    .dark-mode .text-slate-900 {
      color: #e5e7eb !important;
    }
    .dark-mode .text-slate-600 {
      color: #cbd5f5 !important;
    }

    /* Admin Modal */
    #admin-modal {
      position: fixed;
      inset: 0;
      background: rgba(15,23,42,0.8);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 99999;
    }
    #admin-modal.open {
      display: flex;
    }
  </style>
</head>
<body class="bg-slate-100 text-slate-900 font-sans antialiased">
<div class="min-h-screen flex flex-col">

  <!-- NAVBAR -->
  <header class="sticky top-0 z-30 bg-slate-900/95 backdrop-blur border-b border-slate-800">
    <nav class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-3 flex items-center justify-between">
      <!-- Left: Brand -->
      <div class="flex items-center gap-3">
        <div class="w-11 h-11 rounded-full bg-gradient-to-br from-amber-200 via-orange-400 to-red-500 shadow-lg flex items-center justify-center text-base font-extrabold text-slate-900">
          NS
        </div>
        <div class="leading-tight">
          <div class="text-sm font-semibold tracking-wide text-slate-50">
            Noko Simple
          </div>
          <div class="text-[0.72rem] text-slate-400">
            Fast Food Joint
          </div>
        </div>
      </div>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-3 text-[0.9rem]">
        <a href="#hero" class="px-3 py-1 rounded-full text-slate-100 hover:bg-slate-800 transition">
          Home
        </a>
        <a href="#menu" class="px-3 py-1 rounded-full text-slate-100 hover:bg-slate-800 transition">
          Menu
        </a>
        <a href="#about" class="px-3 py-1 rounded-full text-slate-100 hover:bg-slate-800 transition">
          Why Us
        </a>
        <a href="#testimonials" class="px-3 py-1 rounded-full text-slate-100 hover:bg-slate-800 transition">
          Reviews
        </a>
        <a href="#contact" class="px-3 py-1 rounded-full text-slate-100 hover:bg-slate-800 transition">
          Contact
        </a>
        <a href="#contact" class="ml-1 inline-flex items-center px-4 py-1.5 rounded-full bg-secondary text-slate-900 font-semibold shadow-md hover:bg-amber-300 transition">
          Order Now
        </a>
        <!-- Dark Mode Toggle -->
        <button
          id="theme-toggle"
          class="ml-2 inline-flex items-center justify-center w-9 h-9 rounded-full border border-slate-600 text-slate-100 text-xs hover:bg-slate-800 transition"
          type="button"
        >
          ☀️
        </button>
      </div>

      <!-- Mobile Toggle -->
      <button
        class="md:hidden text-slate-100 text-2xl"
        aria-label="Toggle navigation"
        onclick="document.getElementById('mobile-nav').classList.toggle('hidden')"
      >
        ☰
      </button>
    </nav>

    <!-- Mobile Nav -->
    <div id="mobile-nav" class="md:hidden hidden border-t border-slate-800 bg-slate-950/95">
      <div class="max-w-6xl mx-auto px-4 py-3 flex flex-col gap-2 text-sm">
        <a href="#hero" class="py-1 text-slate-100 hover:text-secondary" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Home
        </a>
        <a href="#menu" class="py-1 text-slate-100 hover:text-secondary" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Menu
        </a>
        <a href="#about" class="py-1 text-slate-100 hover:text-secondary" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Why Us
        </a>
        <a href="#testimonials" class="py-1 text-slate-100 hover:text-secondary" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Reviews
        </a>
        <a href="#contact" class="py-1 text-slate-100 hover:text-secondary" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Contact
        </a>
        <a href="#contact" class="mt-1 inline-flex items-center justify-center px-4 py-2 rounded-full bg-secondary text-slate-900 font-semibold shadow-md hover:bg-amber-300 transition" onclick="document.getElementById('mobile-nav').classList.add('hidden')">
          Order Now
        </a>
        <button
          id="theme-toggle-mobile"
          class="mt-2 inline-flex items-center justify-center w-9 h-9 rounded-full border border-slate-600 text-slate-100 text-xs hover:bg-slate-800 transition"
          type="button"
        >
          ☀️
        </button>
      </div>
    </div>
  </header>

  <!-- MAIN -->
  <main class="flex-1">

    <!-- HERO -->
    <section id="hero" class="bg-gradient-to-br from-amber-50 via-rose-50 to-orange-100 reveal-on-scroll">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-10 md:py-16 grid md:grid-cols-2 gap-10 items-center">
        <!-- Hero Text -->
        <div class="space-y-6">
          <div class="inline-flex items-center gap-2 px-2.5 py-1 rounded-full bg-slate-900/90 text-[0.75rem] text-slate-100 shadow-lg">
            <span class="px-2 py-0.5 rounded-full bg-secondary text-slate-900 font-semibold">
              Hot
            </span>
            <span class="text-slate-200">24/7 Fast Delivery in Your City</span>
          </div>

          <div class="space-y-3">
            <h1 class="text-3xl sm:text-4xl lg:text-5xl font-semibold text-slate-900 leading-tight">
              Your new favourite
              <span class="text-primaryDark">fast food spot</span>.
            </h1>
            <p class="text-sm sm:text-base text-slate-600 max-w-xl">
              Fried rice, spaghetti, egg fried rice, jollof rice, pizza, potato chips, assorted and more – always hot, fresh and ready.
              Order in, take out or grab a late-night bite with friends.
            </p>
          </div>

          <!-- Hero Actions -->
          <div class="flex flex-wrap items-center gap-3">
            <button
              class="inline-flex items-center justify-center px-5 py-2.5 rounded-full bg-primary text-white font-semibold text-sm shadow-lg hover:bg-primaryDark transition"
              onclick="document.getElementById('menu').scrollIntoView({behavior:'smooth'})"
            >
              View Full Menu →
            </button>
            <button
              class="inline-flex items-center justify-center px-5 py-2.5 rounded-full border border-slate-300 text-slate-800 text-sm font-medium bg-white/70 hover:bg-primary/10 transition"
              onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})"
            >
              Order on WhatsApp
            </button>
          </div>

          <!-- Meta -->
          <div class="flex flex-wrap gap-5 text-xs sm:text-sm text-slate-600">
            <div class="max-w-[220px]">
              <div class="font-semibold text-slate-900 text-sm">
                25+ signature meals
              </div>
              <p>Assorted fried rice, spaghetti, jollof rice & more.</p>
            </div>
            <div class="max-w-[220px]">
              <div class="font-semibold text-slate-900 text-sm">
                Under 30 mins
              </div>
              <p>Average delivery time within town.</p>
            </div>
          </div>
        </div>

        <!-- Hero Visual -->
        <div class="relative">
          <div class="bg-white rounded-3xl shadow-card p-4 sm:p-5 relative overflow-hidden">
            <!-- Top -->
            <div class="flex items-start justify-between gap-3 mb-4">
              <div>
                <p class="text-base font-semibold text-slate-900">
                  Assorted Fried Rice
                </p>
                <p class="inline-flex items-center mt-1 px-2 py-0.5 rounded-full border border-orange-200 bg-orange-50 text-[0.7rem] text-primaryDark font-medium">
                  Best Seller
                </p>
              </div>
              <div class="absolute right-4 -top-3 bg-slate-900 text-slate-50 px-3 py-2 rounded-full shadow-xl text-[0.7rem] leading-tight flex flex-col items-end">
                <span class="opacity-70">Starting from</span>
                <span class="font-semibold text-sm">₵60.00</span>
              </div>
            </div>

            <!-- Food Image -->
            <div class="rounded-2xl overflow-hidden mb-4 bg-slate-900">
              <div class="relative">
                <img
                  src="https://images.bolt.eu/store/2024/2024-10-17/c623efa3-fde8-4cc3-a78c-9006ff8e880c.png"
                  alt="Assorted fried rice combo"
                  class="w-full h-56 object-cover saturate-110 scale-[1.02]"
                />
                <div class="absolute bottom-3 left-3 inline-flex items-center gap-2 px-3 py-1 rounded-full bg-slate-900/85 text-[0.75rem] text-slate-50">
                  <span class="w-2 h-2 rounded-full bg-emerald-400"></span>
                  Ready in 10 minutes
                </div>
              </div>
            </div>

            <!-- Bottom -->
            <div class="flex items-center justify-between gap-3 text-xs sm:text-sm">
              <div class="flex flex-wrap gap-2 max-w-xs">
                <span class="px-2.5 py-1 rounded-full bg-slate-100 text-slate-700">
                  Spicy or classic
                </span>
                <span class="px-2.5 py-1 rounded-full bg-slate-100 text-slate-700">
                  Fries or drink
                </span>
                <span class="px-2.5 py-1 rounded-full bg-slate-100 text-slate-700">
                  Extra add-ups
                </span>
              </div>
              <div class="text-right">
                <div class="text-sm font-semibold text-slate-900">
                  ₵100.00
                </div>
                <div class="text-[0.7rem] text-slate-500">
                  combo price
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- MENU -->
    <section id="menu" class="py-12 md:py-16 reveal-on-scroll">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-4 mb-6">
          <div class="space-y-2">
            <h2 class="text-2xl md:text-3xl font-semibold text-slate-900">
              Our Favourites
            </h2>
            <p class="text-sm sm:text-[0.95rem] text-slate-600 max-w-xl">
              These are the meals customers keep coming back for. Perfect for lunch, late-night cravings or weekend hangouts.
            </p>
          </div>
          <a href="#contact" class="text-sm font-medium text-primaryDark border-b border-orange-300 w-fit">
            Want to pre-order for a party?
          </a>
        </div>

        <!-- Search + Filter -->
        <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-3 mb-5">
          <div class="flex items-center gap-2 flex-wrap">
            <button class="px-3 py-1.5 rounded-full text-xs sm:text-[0.78rem] bg-slate-900 text-slate-50 hover:bg-black transition menu-filter-btn" data-filter="all">
              All
            </button>
            <button class="px-3 py-1.5 rounded-full text-xs sm:text-[0.78rem] bg-slate-100 text-slate-700 hover:bg-slate-200 transition menu-filter-btn" data-filter="rice">
              Rice
            </button>
            <button class="px-3 py-1.5 rounded-full text-xs sm:text-[0.78rem] bg-slate-100 text-slate-700 hover:bg-slate-200 transition menu-filter-btn" data-filter="pasta">
              Pasta
            </button>
            <button class="px-3 py-1.5 rounded-full text-xs sm:text-[0.78rem] bg-slate-100 text-slate-700 hover:bg-slate-200 transition menu-filter-btn" data-filter="sides">
              Sides
            </button>
            <button class="px-3 py-1.5 rounded-full text-xs sm:text-[0.78rem] bg-slate-100 text-slate-700 hover:bg-slate-200 transition menu-filter-btn" data-filter="pizza">
              Pizza
            </button>
          </div>

          <div class="relative w-full sm:w-64">
            <input
              type="text"
              id="menu-search"
              class="w-full rounded-full border border-slate-300 bg-white/80 px-3 py-1.5 text-xs sm:text-sm text-slate-700 placeholder:text-slate-400 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
              placeholder="Search meals (eg: fried, jollof, chips)"
            />
            <span class="absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 text-sm">🔍</span>
          </div>
        </div>

        <!-- Grid -->
        <div id="menu-grid" class="grid gap-5 sm:grid-cols-2 lg:grid-cols-3">
          <!-- Card 1 -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card" data-category="rice" data-name="assorted jollof rice">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-slate-900/90 text-[0.7rem] text-slate-50">
                New
              </span>
              <img
                src="https://images.bolt.eu/store/2025/2025-04-21/ee56f974-13ae-4d72-b1a5-a7a282232180.png"
                alt="Assorted Jollof Rice"
                class="w-full h-40 object-cover"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Assorted Jollof Rice
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 4.8 <span class="text-slate-400">(230+ orders)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="jollof">
                  ₵70 / 100.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                Ghana jollof served with grilled chicken, sausage, fresh salad, spicy shito and extra toppings for a full experience.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Comes with water + drink add-on</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition"
                  onclick="quickOrder('Assorted Jollof Rice', '₵70 / 100.00')"
                >
                  Add
                </button>
              </div>
            </div>
          </article>

          <!-- Card 2 - Fully Loaded Fries (Coming Soon) -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card opacity-90" data-category="sides" data-name="fully loaded fries" data-coming-soon="true">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-rose-600 text-[0.7rem] text-slate-50">
                Hot
              </span>
              <span class="absolute top-3 right-3 inline-flex items-center px-2.5 py-1 rounded-full bg-slate-900/90 text-[0.7rem] text-slate-50">
                Coming Soon
              </span>
              <img
                src="https://static.vecteezy.com/system/resources/thumbnails/050/393/583/small_2x/crispy-loaded-french-fries-with-cheese-sauce-and-bacon-photo.jpg"
                alt="Fully Loaded Fries"
                class="w-full h-40 object-cover grayscale"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Fully Loaded Fries
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 4.9 <span class="text-slate-400">(180+ orders)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="fries">
                  ₵80.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                Crispy seasoned fries topped with chicken, sausages, cheese and our signature creamy sauce — the ultimate comfort snack.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Perfect for sharing (coming soon)</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-400 text-slate-700 text-[0.75rem] font-medium cursor-not-allowed opacity-70"
                  disabled
                >
                  Coming Soon
                </button>
              </div>
            </div>
          </article>

          <!-- Card 3 -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card" data-category="pasta" data-name="spaghetti">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-emerald-600 text-[0.7rem] text-slate-50">
                Combo
              </span>
              <img
                src="https://images.bolt.eu/store/2023/2023-09-01/0d0b8856-b5dc-49b5-9596-5a750ef1b653.jpeg"
                alt="Spaghetti"
                class="w-full h-40 object-cover"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Spaghetti
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 4.7 <span class="text-slate-400">(150+ orders)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="spag">
                  ₵45 / 60.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                Rich, flavourful spaghetti tossed with seasoned chicken, sausages, crunchy vegetables and a hint of shito, served hot and fresh.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Serves 1–2 people</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition"
                  onclick="quickOrder('Spaghetti', '₵45 / 60.00')"
                >
                  Add
                </button>
              </div>
            </div>
          </article>

          <!-- Card 4 -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card" data-category="rice" data-name="fried rice">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-amber-600 text-[0.7rem] text-slate-50">
                Fried Rice
              </span>
              <img
                src="https://www.australianeggs.org.au/assets/Uploads/Egg-fried-rice-2.jpg"
                alt="Fried Rice"
                class="w-full h-40 object-cover"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Fried Rice
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 4.6 <span class="text-slate-400">(190+ orders)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="friedrice">
                  ₵45 / 60.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                Aromatic golden fried rice stir-fried with colourful veggies and eggs, paired with grilled chicken, sausages and spicy shito.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Serves 1–2 people</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition"
                  onclick="quickOrder('Fried Rice', '₵45 / 60.00')"
                >
                  Add
                </button>
              </div>
            </div>
          </article>

          <!-- Card 5 -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card" data-category="rice" data-name="vegetable fried rice">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-lime-600 text-[0.7rem] text-slate-50">
                Veggie
              </span>
              <img
                src="https://feelgoodfoodie.net/wp-content/uploads/2020/01/One-Pot-Chicken-and-Rice-13.jpg"
                alt="Vegetable Fried Rice"
                class="w-full h-40 object-cover"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Vegetable Fried Rice
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 4.5 <span class="text-slate-400">(120+ orders)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="vegrice">
                  ₵45.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                A vibrant mix of fluffy fried rice tossed with crisp vegetables, seasoned to perfection for a light yet satisfying meal.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Serves 1–2 people</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition"
                  onclick="quickOrder('Vegetable Fried Rice', '₵45.00')"
                >
                  Add
                </button>
              </div>
            </div>
          </article>

          <!-- Card 6 - Pizza Coming Soon -->
          <article class="bg-white rounded-3xl shadow-card overflow-hidden flex flex-col reveal-on-scroll menu-card opacity-90" data-category="pizza" data-name="pizza" data-coming-soon="true">
            <div class="relative">
              <span class="absolute top-3 left-3 inline-flex items-center px-2.5 py-1 rounded-full bg-red-700 text-[0.7rem] text-slate-50">
                Pizza
              </span>
              <span class="absolute top-3 right-3 inline-flex items-center px-2.5 py-1 rounded-full bg-slate-900/90 text-[0.7rem] text-slate-50">
                Coming Soon
              </span>
              <img
                src="https://images.bolt.eu/store/2024/2024-12-30/de08005b-25a3-4467-add2-7ba9829476e7.jpeg"
                alt="Pizza"
                class="w-full h-40 object-cover grayscale"
              />
            </div>
            <div class="p-4 flex flex-col flex-1">
              <div class="flex items-baseline justify-between gap-2 mb-1">
                <div>
                  <h3 class="text-sm font-semibold text-slate-900">
                    Pizza
                  </h3>
                  <div class="text-[0.75rem] text-amber-500 flex items-center gap-1">
                    ⭐ 5.0 <span class="text-slate-400">(Launching soon)</span>
                  </div>
                </div>
                <span class="text-sm font-bold text-slate-900 price-span" data-price-key="pizza">
                  ₵120.00
                </span>
              </div>
              <p class="text-[0.8rem] text-slate-600 flex-1">
                Soft crust, rich tomato sauce, melted mozzarella and toppings of your choice — chicken, beef, pepperoni, veggies or mixed.
              </p>
              <div class="mt-3 flex items-center justify-between gap-2 text-[0.72rem] text-slate-500">
                <span>Perfect for sharing (coming soon)</span>
                <button
                  class="px-3 py-1.5 rounded-full bg-slate-400 text-slate-700 text-[0.75rem] font-medium cursor-not-allowed opacity-70"
                  disabled
                >
                  Coming Soon
                </button>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- WHY US -->
    <section id="about" class="bg-slate-950 text-slate-50 py-12 md:py-16 reveal-on-scroll">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="mb-8">
          <h2 class="text-2xl md:text-3xl font-semibold">
            Why everyone loves Noko Simple Fast Food
          </h2>
          <p class="mt-2 text-sm sm:text-[0.95rem] text-slate-300 max-w-2xl">
            We don’t just serve fast meals, we serve unforgettable flavour, true consistency, and the warm vibes that make you feel at home every time you walk through our doors.
          </p>
        </div>

        <div class="grid md:grid-cols-2 gap-10 items-center">
          <!-- Text side -->
          <div class="space-y-5">
            <p class="text-[0.95rem] text-slate-200 leading-relaxed">
              What began as a humble late-night fried rice joint in Teshie has grown into a powerhouse serving hundreds of orders a day. Yet one thing remains unchanged:
              our food stays hot,
              <span class="font-semibold text-secondary">our flavours stay bold, and your experience stays stress-free.</span>
            </p>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="bg-slate-900/80 border border-slate-700 rounded-2xl p-3.5 text-[0.82rem]">
                <strong class="block text-[0.9rem] mb-1 text-slate-50">Freshly made, always</strong>
                No standing food here — your fried rice is prepared hot and fresh the moment you order.
              </div>
              <div class="bg-slate-900/80 border border-slate-700 rounded-2xl p-3.5 text-[0.82rem]">
                <strong class="block text-[0.9rem] mb-1 text-slate-50">Late-night friendly</strong>
                Open till 1:00am on Fridays and Saturdays, so your cravings never have to wait till morning.
              </div>
              <div class="bg-slate-900/80 border border-slate-700 rounded-2xl p-3.5 text-[0.82rem]">
                <strong class="block text-[0.9rem] mb-1 text-slate-50">Easy ordering</strong>
                Call, WhatsApp or walk-in. We keep it simple, quick and friendly – just how fast food should be.
              </div>
              <div class="bg-slate-900/80 border border-slate-700 rounded-2xl p-3.5 text-[0.82rem]">
                <strong class="block text-[0.9rem] mb-1 text-slate-50">Perfect for groups</strong>
                Combos and platters that make sharing easier (and cheaper) for families & squads.
              </div>
            </div>

            <div class="flex flex-wrap gap-6 text-[0.82rem] text-slate-300 pt-2">
              <div>
                <span class="block text-secondary text-lg font-semibold">4.7★</span>
                <span>Average rating from regulars</span>
              </div>
              <div>
                <span class="block text-secondary text-lg font-semibold">20 min</span>
                <span>Typical prep time</span>
              </div>
            </div>
          </div>

          <!-- Visual side -->
          <div class="bg-gradient-to-b from-slate-900 to-slate-950 border border-slate-700 rounded-3xl p-3.5 sm:p-4">
            <div class="rounded-2xl overflow-hidden mb-3 h-52 sm:h-56">
              <img
                src="https://images.pexels.com/photos/941861/pexels-photo-941861.jpeg?auto=compress&cs=tinysrgb&w=1200"
                alt="Fast food interior"
                class="w-full h-full object-cover"
              />
            </div>
            <div class="flex items-center justify-between gap-3 text-[0.8rem]">
              <span class="text-slate-200">
                “Feels like our fast food joint now.”
              </span>
              <span class="px-3 py-1 rounded-full border border-slate-600 text-slate-200">
                Open daily • 10am – 1am (Everyday)
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- TESTIMONIALS -->
    <section id="testimonials" class="bg-slate-900 text-slate-50 py-12 md:py-14 reveal-on-scroll">
      <div class="max-w-4xl mx-auto px-4 sm:px-6">
        <div class="flex items-center justify-between mb-6">
          <h2 class="text-2xl md:text-3xl font-semibold">What people are saying</h2>
          <div class="text-sm text-amber-400 flex items-center gap-1">
            ⭐ 4.7 <span class="text-slate-300">· 100+ happy foodies</span>
          </div>
        </div>
        <div class="relative">
          <div id="testimonial-slider" class="bg-slate-800/70 border border-slate-700 rounded-3xl p-5 sm:p-6 min-h-[160px]">
            <!-- Populated by JS -->
          </div>
          <div class="flex justify-center gap-2 mt-4 text-xs">
            <button id="testimonial-prev" class="w-7 h-7 rounded-full border border-slate-600 flex items-center justify-center hover:bg-slate-700">‹</button>
            <button id="testimonial-next" class="w-7 h-7 rounded-full border border-slate-600 flex items-center justify-center hover:bg-slate-700">›</button>
          </div>
        </div>
      </div>
    </section>

    <!-- INSTAGRAM FEED (placeholder for real embed) -->
    <section id="instagram" class="bg-slate-950 text-slate-50 py-10 md:py-12 reveal-on-scroll">
      <div class="max-w-6xl mx-auto px-4 sm:px-6">
        <div class="flex items-center justify-between mb-5">
          <h2 class="text-xl md:text-2xl font-semibold">Catch us on Instagram</h2>
          <a
            href="#"
            class="text-xs sm:text-sm text-secondary border-b border-secondary/50"
            target="_blank"
            rel="noopener"
          >
            @nokosimple_fastfood
          </a>
        </div>
        <!-- You can replace this grid with an official embed plugin later -->
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-2 sm:gap-3">
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700"></div>
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700"></div>
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700"></div>
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700"></div>
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700 hidden md:block"></div>
          <div class="aspect-square rounded-2xl bg-slate-800/80 border border-slate-700 hidden md:block"></div>
        </div>
        <p class="mt-3 text-[0.8rem] text-slate-400">
          *Connect your real Instagram feed later using an embed widget or plugin.
        </p>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-slate-900 text-slate-50 py-10 md:py-14 text-center reveal-on-scroll">
      <div class="max-w-2xl mx-auto px-4 sm:px-6">
        <h2 class="text-2xl md:text-3xl font-semibold mb-3">
          Ready to eat?
        </h2>
        <p class="text-sm sm:text-[0.95rem] text-slate-200 mb-6">
          Send us your order on WhatsApp, give us a quick call, or just walk in.
          We’ll have your favourites ready in no time.
        </p>

        <div class="flex flex-wrap justify-center gap-3 mb-4">
          <button
            class="inline-flex items-center justify-center px-5 py-2.5 rounded-full bg-primary text-white font-semibold text-sm shadow-lg hover:bg-primaryDark transition"
            onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})"
          >
            Order on WhatsApp
          </button>
          <button
            class="inline-flex items-center justify-center px-5 py-2.5 rounded-full border border-slate-500 text-slate-100 text-sm font-medium hover:bg-slate-800 transition"
            onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})"
          >
            Call the restaurant
          </button>
        </div>

        <p class="text-[0.8rem] text-slate-400">
          Free delivery within 3km for orders above ₵15.
        </p>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="bg-slate-950 text-slate-50 py-12 md:py-16 reveal-on-scroll">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 gap-10 md:gap-12 items-start">
          <!-- Contact Info -->
          <div>
            <h3 class="text-xl md:text-2xl font-semibold mb-2">
              Find us & place your order
            </h3>
            <p class="text-sm sm:text-[0.95rem] text-slate-300 mb-6">
              Visit our joint, send us a WhatsApp message or call us directly.
              We’ll confirm your order and give you an estimated time on the spot.
            </p>

            <div class="space-y-4 text-sm">
              <div>
                <span class="block text-[0.72rem] uppercase tracking-[0.16em] text-slate-500 mb-1">
                  Location
                </span>
                <p class="text-slate-200">
                  Teshie Point 5, Off Tsui Bleoo Rd, Accra<br />
                  (near the clinic)
                </p>
              </div>

              <div>
                <span class="block text-[0.72rem] uppercase tracking-[0.16em] text-slate-500 mb-1">
                  Phone
                </span>
                <a href="tel:+233506484767" class="text-slate-100 hover:text-secondary">
                  +233 50 648 4767
                </a>
              </div>

              <div>
                <span class="block text-[0.72rem] uppercase tracking-[0.16em] text-slate-500 mb-1">
                  WhatsApp
                </span>
                <a
                  href="https://wa.me/233552520440"
                  target="_blank"
                  rel="noopener"
                  class="text-slate-100 hover:text-secondary"
                >
                  Chat with us on WhatsApp
                </a>
              </div>

              <div>
                <span class="block text-[0.72rem] uppercase tracking-[0.16em] text-slate-500 mb-1">
                  Opening Hours
                </span>
                <p class="text-slate-200">
                  Mon–Thu: 10:00 am – 12:00 pm<br />
                  Fri–Sat: 10:00 am – 1:00 am<br />
                  Sun: 12:00 pm – 12:00 pm
                </p>
              </div>
            </div>

            <!-- Google Maps Embed -->
            <div class="mt-5 rounded-2xl overflow-hidden border border-slate-700 h-52">
              <!-- Replace src with your exact Google Maps embed link -->
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3971.0026808535416!2d-0.082!3d5.583!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2sTeshie!5e0!3m2!1sen!2sgh!4v1700000000000"
                width="100%"
                height="100%"
                style="border:0;"
                allowfullscreen=""
                loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"
              ></iframe>
            </div>

            <!-- Delivery Radius Check -->
            <div class="mt-4 bg-slate-900/80 border border-slate-700 rounded-2xl p-3 text-xs sm:text-[0.82rem]">
              <div class="font-semibold mb-1 text-slate-100">
                Check if you get free delivery
              </div>
              <p class="text-slate-400 mb-2">Type your area (eg: Teshie, Teshie-Nungua, Lekma area).</p>
              <div class="flex flex-col sm:flex-row gap-2">
                <input
                  type="text"
                  id="delivery-area"
                  class="flex-1 rounded-xl border border-slate-700 bg-slate-950 px-3 py-1.5 text-xs text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                  placeholder="Eg: Teshie-Nungua"
                />
                <button
                  type="button"
                  onclick="checkDeliveryRadius()"
                  class="px-3 py-1.5 rounded-xl bg-secondary text-slate-900 text-xs font-semibold hover:bg-amber-300 transition"
                >
                  Check
                </button>
              </div>
              <div id="delivery-result" class="mt-2 text-[0.8rem] text-slate-200"></div>
            </div>

            <div class="mt-5 inline-flex items-center px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700 text-[0.8rem] text-slate-200">
              🚗 Free delivery within 3km for large orders
            </div>
          </div>

          <!-- Form -->
          <div>
            <form class="bg-slate-900/90 border border-slate-700 rounded-3xl p-4 sm:p-5 shadow-card" onsubmit="return false;">
              <div class="flex items-center justify-between mb-2">
                <div class="text-sm font-semibold text-slate-100">Place your order</div>
                <button
                  type="button"
                  class="text-[0.75rem] text-secondary border border-secondary/40 rounded-full px-3 py-0.5 hover:bg-secondary hover:text-slate-900 transition"
                  onclick="reorderLastOrder()"
                >
                  Reorder last order
                </button>
              </div>
              <div class="grid sm:grid-cols-2 gap-3 mb-3">
                <div>
                  <label for="name" class="block text-[0.75rem] text-slate-200 mb-1">
                    Your Name
                  </label>
                  <input
                    type="text"
                    id="name"
                    name="name"
                    placeholder="Dodgeboy Flair"
                    class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                  />
                </div>
                <div>
                  <label for="phone" class="block text-[0.75rem] text-slate-200 mb-1">
                    Phone / WhatsApp
                  </label>
                  <input
                    type="tel"
                    id="phone"
                    name="phone"
                    placeholder="+233 20 000 0000"
                    class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                  />
                </div>
              </div>

              <div class="mb-3">
                <label for="address" class="block text-[0.75rem] text-slate-200 mb-1">
                  Delivery Address / Area
                </label>
                <input
                  type="text"
                  id="address"
                  name="address"
                  placeholder="Eg: Teshie-Nungua Estate, house near XYZ"
                  class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                />
                <p class="mt-1 text-[0.72rem] text-slate-500">
                  We’ll remember this on your next visit on this device.
                </p>
              </div>

              <div class="mb-3">
                <label for="order" class="block text-[0.75rem] text-slate-200 mb-1">
                  Your Order / Message
                </label>
                <textarea
                  id="order"
                  name="order"
                  rows="4"
                  placeholder="Eg: 2 assorted jollof, 1 loaded fries, 1 Coke 1L. Delivery to East Legon."
                  class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary resize-y"
                ></textarea>
              </div>

              <div class="grid sm:grid-cols-2 gap-3 mb-4">
                <div>
                  <label for="schedule" class="block text-[0.75rem] text-slate-200 mb-1">
                    Preferred Time
                  </label>
                  <select
                    id="schedule"
                    class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                  >
                    <option value="ASAP">ASAP</option>
                    <option value="In 20 minutes">In 20 minutes</option>
                    <option value="In 30 minutes">In 30 minutes</option>
                    <option value="In 1 hour">In 1 hour</option>
                    <option value="Tonight">Tonight</option>
                    <option value="Custom">I wrote my own time above</option>
                  </select>
                </div>
                <div>
                  <label for="time" class="block text-[0.75rem] text-slate-200 mb-1">
                    Custom Time (Optional)
                  </label>
                  <input
                    type="text"
                    id="time"
                    name="time"
                    placeholder="Eg: 7:30 pm today"
                    class="w-full rounded-xl border border-slate-700 bg-slate-900/70 px-3 py-2 text-sm text-slate-50 placeholder:text-slate-500 focus:outline-none focus:ring-1 focus:ring-secondary focus:border-secondary"
                  />
                </div>
              </div>

              <div id="recommend-bar" class="hidden mb-4 text-[0.78rem] bg-slate-800/80 border border-slate-700 rounded-2xl px-3 py-2 text-slate-200">
                <!-- Smart recommendations appear here -->
              </div>

              <div class="flex justify-end gap-2">
                <button
                  type="button"
                  class="inline-flex items-center px-4 py-2 rounded-full border border-slate-600 text-slate-100 text-xs font-medium hover:bg-slate-800 transition"
                  onclick="copyCartToOrder()"
                >
                  Load cart into message
                </button>
                <button
                  type="button"
                  class="inline-flex items-center px-5 py-2 rounded-full bg-secondary text-slate-900 text-sm font-semibold hover:bg-amber-300 transition"
                  onclick="sendToWhatsApp()"
                >
                  Send on WhatsApp
                </button>
              </div>
            </form>
          </div>
        </div>

        <!-- FOOTER -->
        <footer class="mt-10 pt-5 border-t border-slate-800 text-[0.8rem] text-slate-500 flex flex-wrap items-center justify-between gap-3">
          <div>
            © <span id="year"></span> Noko Simple Fast Food. All rights reserved.
          </div>
          <div>
            Designed by — Koviostudios.
          </div>
        </footer>
      </div>
    </section>
  </main>
</div>

<!-- Sticky Mobile Order Button -->
<div class="fixed bottom-0 inset-x-0 md:hidden z-40 bg-slate-900/95 border-t border-slate-800">
  <div class="max-w-6xl mx-auto px-4 py-2 flex items-center justify-between gap-3 text-xs text-slate-200">
    <span>Hungry? Place your order now.</span>
    <button
      class="px-4 py-1.5 rounded-full bg-primary text-white font-semibold text-xs shadow hover:bg-primaryDark transition"
      onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})"
    >
      Order Now
    </button>
  </div>
</div>

<!-- Floating WhatsApp Button -->
<div id="whatsapp-float" onclick="openMainWhatsApp()" aria-label="Chat on WhatsApp">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp" />
</div>

<!-- Floating Call Button -->
<div id="call-float" onclick="window.location.href='tel:+233506484767'" aria-label="Call restaurant">
  📞
</div>

<!-- Back to Top Button -->
<button id="back-to-top" type="button" onclick="window.scrollTo({top:0, behavior:'smooth'})">
  ↑
</button>

<!-- Order Popup -->
<div id="order-popup"></div>

<!-- Cart Badge -->
<div id="cart-badge" onclick="toggleCartPanel()">
  🛒 <span id="cart-count">0</span> <span class="hidden sm:inline">items</span>
</div>

<!-- Cart Panel -->
<div id="cart-panel">
  <div class="p-3 border-b border-slate-800 flex items-center justify-between text-xs">
    <span class="font-semibold text-slate-100">Your Cart</span>
    <button class="text-slate-400 hover:text-slate-100" type="button" onclick="toggleCartPanel()">
      ✕
    </button>
  </div>
  <div id="cart-items" class="p-3 space-y-2 text-xs">
    <!-- Items via JS -->
  </div>
  <div class="border-t border-slate-800 p-3 text-xs space-y-2">
    <div class="flex items-center justify-between text-slate-300">
      <span>Total items</span>
      <span id="cart-total-items">0</span>
    </div>
    <div class="flex items-center justify-between text-slate-300">
      <span>Estimated total</span>
      <span id="cart-estimate">₵0.00</span>
    </div>
    <button
      type="button"
      class="mt-2 w-full inline-flex items-center justify-center px-4 py-1.5 rounded-full bg-secondary text-slate-900 font-semibold hover:bg-amber-300 transition text-xs"
      onclick="copyCartToOrder(); toggleCartPanel(); document.getElementById('contact').scrollIntoView({behavior:'smooth'})"
    >
      Add cart to order message
    </button>
  </div>
</div>

<!-- Admin Modal (ALT + A to open) -->
<div id="admin-modal">
  <div class="bg-slate-900 border border-slate-700 rounded-3xl p-4 sm:p-5 max-w-md w-full text-xs text-slate-100">
    <div class="flex items-center justify-between mb-3">
      <div class="font-semibold text-sm">Noko Simple Admin</div>
      <button type="button" class="text-slate-400 hover:text-slate-100" onclick="toggleAdminModal(false)">✕</button>
    </div>
    <p class="mb-2 text-[0.75rem] text-slate-400">
      Quick tweaks saved in this browser only (no backend). Use this for price changes & toggling “Coming Soon”.
    </p>
    <div class="space-y-2 mb-3">
      <div class="flex items-center gap-2">
        <label class="w-28">Jollof price</label>
        <input id="admin-price-jollof" class="flex-1 rounded-lg bg-slate-800 border border-slate-700 px-2 py-1" />
      </div>
      <div class="flex items-center gap-2">
        <label class="w-28">Spag price</label>
        <input id="admin-price-spag" class="flex-1 rounded-lg bg-slate-800 border border-slate-700 px-2 py-1" />
      </div>
      <div class="flex items-center gap-2">
        <label class="w-28">Fried rice price</label>
        <input id="admin-price-friedrice" class="flex-1 rounded-lg bg-slate-800 border border-slate-700 px-2 py-1" />
      </div>
      <div class="flex items-center gap-2">
        <label class="w-28">Veg rice price</label>
        <input id="admin-price-vegrice" class="flex-1 rounded-lg bg-slate-800 border border-slate-700 px-2 py-1" />
      </div>
      <div class="flex items-center gap-2">
        <label class="w-28">Pizza price</label>
        <input id="admin-price-pizza" class="flex-1 rounded-lg bg-slate-800 border border-slate-700 px-2 py-1" />
      </div>
    </div>
    <div class="space-y-1 mb-3">
      <label class="flex items-center gap-2">
        <input type="checkbox" id="admin-coming-fries" class="accent-secondary" />
        <span>Fully Loaded Fries - Coming Soon</span>
      </label>
      <label class="flex items-center gap-2">
        <input type="checkbox" id="admin-coming-pizza" class="accent-secondary" />
        <span>Pizza - Coming Soon</span>
      </label>
    </div>
    <div class="flex justify-end gap-2 mt-3">
      <button
        type="button"
        class="px-3 py-1 rounded-full border border-slate-600 text-slate-200 hover:bg-slate-800"
        onclick="resetAdminSettings()"
      >
        Reset
      </button>
      <button
        type="button"
        class="px-4 py-1 rounded-full bg-secondary text-slate-900 font-semibold hover:bg-amber-300"
        onclick="saveAdminSettings()"
      >
        Save
      </button>
    </div>
  </div>
</div>

<script>
  // Set current year in footer
  document.getElementById("year").textContent = new Date().getFullYear();

  // --- Global Config ---
  const whatsAppNumber = "233552520440"; // main WhatsApp number
  const callNumber = "+233506484767";

  // --- Theme Toggle ---
  function applyThemeFromStorage() {
    const saved = localStorage.getItem("nsTheme");
    const isDark = saved === "dark";
    document.body.classList.toggle("dark-mode", isDark);
    const label = isDark ? "🌙" : "☀️";
    const btn1 = document.getElementById("theme-toggle");
    const btn2 = document.getElementById("theme-toggle-mobile");
    if (btn1) btn1.textContent = label;
    if (btn2) btn2.textContent = label;
  }
  function toggleTheme() {
    const isDark = !document.body.classList.contains("dark-mode");
    document.body.classList.toggle("dark-mode", isDark);
    localStorage.setItem("nsTheme", isDark ? "dark" : "light");
    applyThemeFromStorage();
  }

  document.addEventListener("DOMContentLoaded", () => {
    applyThemeFromStorage();
    const t1 = document.getElementById("theme-toggle");
    const t2 = document.getElementById("theme-toggle-mobile");
    if (t1) t1.addEventListener("click", toggleTheme);
    if (t2) t2.addEventListener("click", toggleTheme);
  });

  // Main WhatsApp open
  function openMainWhatsApp() {
    window.open("https://wa.me/" + whatsAppNumber, "_blank");
  }

  // Order popup
  function showOrderPopup(message) {
    const popup = document.getElementById("order-popup");
    if (!popup) return;
    popup.textContent = message;
    popup.classList.add("show");
    clearTimeout(window._orderPopupTimeout);
    window._orderPopupTimeout = setTimeout(() => {
      popup.classList.remove("show");
    }, 2600);
  }

  // Back to top visibility
  window.addEventListener("scroll", () => {
    const btn = document.getElementById("back-to-top");
    if (!btn) return;
    if (window.scrollY > 260) {
      btn.classList.add("show");
    } else {
      btn.classList.remove("show");
    }
  });

  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll(".reveal-on-scroll").forEach(el => observer.observe(el));

  // Testimonials
  const testimonials = [
    {
      name: "Ama, Teshie",
      text: "The assorted jollof is elite. I’ve ordered more than five times and it’s been consistent every single time.",
      tag: "Assorted Jollof Lover"
    },
    {
      name: "Kwesi, East Legon",
      text: "Late-night cravings sorted. Their fried rice and spaghetti combo never disappoints.",
      tag: "Late-night Customer"
    },
    {
      name: "Nana, Spintex",
      text: "Customer service is top tier and the food portions are actually worth the money.",
      tag: "Regular"
    }
  ];
  let testimonialIndex = 0;
  function renderTestimonial() {
    const container = document.getElementById("testimonial-slider");
    if (!container) return;
    const t = testimonials[testimonialIndex];
    container.innerHTML = `
      <div class="flex flex-col gap-3">
        <p class="text-sm text-slate-100 leading-relaxed">“${t.text}”</p>
        <div class="flex items-center justify-between text-[0.78rem] text-slate-300">
          <div>
            <div class="font-semibold text-slate-50">${t.name}</div>
            <div class="text-slate-400">${t.tag}</div>
          </div>
          <div class="text-amber-400">⭐️⭐️⭐️⭐️⭐️</div>
        </div>
      </div>
    `;
  }
  function nextTestimonial(step = 1) {
    testimonialIndex = (testimonialIndex + step + testimonials.length) % testimonials.length;
    renderTestimonial();
  }
  document.addEventListener("DOMContentLoaded", () => {
    renderTestimonial();
    const prevBtn = document.getElementById("testimonial-prev");
    const nextBtn = document.getElementById("testimonial-next");
    if (prevBtn) prevBtn.addEventListener("click", () => nextTestimonial(-1));
    if (nextBtn) nextBtn.addEventListener("click", () => nextTestimonial(1));
    setInterval(() => nextTestimonial(1), 9000);
  });

  // Menu filter & search
  function applyMenuFilters() {
    const searchTerm = (document.getElementById("menu-search")?.value || "").toLowerCase();
    const activeFilterBtn = document.querySelector(".menu-filter-btn.bg-slate-900");
    const filter = activeFilterBtn ? activeFilterBtn.dataset.filter : "all";
    document.querySelectorAll(".menu-card").forEach(card => {
      const category = card.dataset.category || "all";
      const name = (card.dataset.name || "").toLowerCase();
      const text = (card.textContent || "").toLowerCase();
      const matchesCategory = filter === "all" || category === filter;
      const matchesSearch = !searchTerm || name.includes(searchTerm) || text.includes(searchTerm);
      card.style.display = (matchesCategory && matchesSearch) ? "" : "none";
    });
  }
  document.addEventListener("DOMContentLoaded", () => {
    document.querySelectorAll(".menu-filter-btn").forEach(btn => {
      btn.addEventListener("click", () => {
        document.querySelectorAll(".menu-filter-btn").forEach(b => {
          b.classList.remove("bg-slate-900", "text-slate-50");
          b.classList.add("bg-slate-100", "text-slate-700");
        });
        btn.classList.add("bg-slate-900", "text-slate-50");
        btn.classList.remove("bg-slate-100", "text-slate-700");
        applyMenuFilters();
      });
    });
    const search = document.getElementById("menu-search");
    if (search) search.addEventListener("input", applyMenuFilters);
  });

  // Cart system
  let cart = [];

  function parseUnitPrice(priceString) {
    const match = (priceString || "").toString().match(/[\d.]+/);
    return match ? parseFloat(match[0]) : 0;
  }

  function addToCart(itemName, priceString) {
    if (!itemName) return;
    // do not add coming soon items (safety check)
    const card = Array.from(document.querySelectorAll(".menu-card")).find(c => (c.dataset.name || "").toLowerCase() === itemName.toLowerCase());
    if (card && card.dataset.comingSoon === "true") {
      showOrderPopup("This item is coming soon and cannot be added yet.");
      return;
    }

    const unit = parseUnitPrice(priceString);
    const existing = cart.find(item => item.name === itemName);
    if (existing) {
      existing.qty += 1;
    } else {
      cart.push({ name: itemName, priceString, unitPrice: unit, qty: 1 });
    }
    renderCart();
    showOrderPopup("Added: " + itemName + " to cart.");
  }

  function updateCartItem(name, delta) {
    const item = cart.find(i => i.name === name);
    if (!item) return;
    item.qty += delta;
    if (item.qty <= 0) {
      cart = cart.filter(i => i.name !== name);
    }
    renderCart();
  }

  function removeCartItem(name) {
    cart = cart.filter(i => i.name !== name);
    renderCart();
  }

  function renderCart() {
    const countEl = document.getElementById("cart-count");
    const itemsEl = document.getElementById("cart-items");
    const totalItemsEl = document.getElementById("cart-total-items");
    const estimateEl = document.getElementById("cart-estimate");
    let totalItems = 0;
    let estimate = 0;

    if (itemsEl) itemsEl.innerHTML = "";

    cart.forEach(item => {
      totalItems += item.qty;
      estimate += item.unitPrice * item.qty;
      if (itemsEl) {
        const lineTotal = item.unitPrice > 0 ? `₵${(item.unitPrice * item.qty).toFixed(2)}` : "";
        const row = document.createElement("div");
        row.className = "flex items-start justify-between gap-2 border border-slate-800 rounded-xl px-2 py-1.5";
        row.innerHTML = `
          <div class="flex-1">
            <div class="font-semibold text-slate-100">${item.name}</div>
            <div class="text-slate-400 text-[0.72rem]">${item.priceString}</div>
            ${lineTotal ? `<div class="text-slate-300 text-[0.72rem] mt-0.5">≈ ${lineTotal}</div>` : ""}
          </div>
          <div class="flex flex-col items-end gap-1">
            <div class="inline-flex items-center gap-1 bg-slate-900 rounded-full px-1 py-0.5 border border-slate-700">
              <button type="button" class="w-5 h-5 rounded-full flex items-center justify-center text-slate-200 hover:bg-slate-700" onclick="updateCartItem('${item.name.replace(/'/g, "\\'")}', -1)">−</button>
              <span class="min-w-[1.5rem] text-center text-slate-100">${item.qty}</span>
              <button type="button" class="w-5 h-5 rounded-full flex items-center justify-center text-slate-200 hover:bg-slate-700" onclick="updateCartItem('${item.name.replace(/'/g, "\\'")}', 1)">+</button>
            </div>
            <button type="button" class="text-[0.7rem] text-rose-300 hover:text-rose-200" onclick="removeCartItem('${item.name.replace(/'/g, "\\'")}')">Remove</button>
          </div>
        `;
        itemsEl.appendChild(row);
      }
    });

    if (countEl) countEl.textContent = totalItems;
    if (totalItemsEl) totalItemsEl.textContent = totalItems;
    if (estimateEl) estimateEl.textContent = "₵" + estimate.toFixed(2);
  }

  function toggleCartPanel() {
    const panel = document.getElementById("cart-panel");
    if (!panel) return;
    panel.classList.toggle("open");
  }

  function copyCartToOrder() {
    const orderField = document.getElementById("order");
    if (!orderField) return;
    if (!cart.length) {
      showOrderPopup("Your cart is empty.");
      return;
    }
    const lines = cart.map(item => `• ${item.qty} x ${item.name} (${item.priceString})`);
    const existing = orderField.value.trim();
    const cartText = "Cart items:\n" + lines.join("\n");
    orderField.value = existing ? (existing + "\n\n" + cartText) : cartText;
    showOrderPopup("Cart items added to message.");
  }

  // Delivery radius (very simple area name check)
  function checkDeliveryRadius() {
    const input = document.getElementById("delivery-area");
    const result = document.getElementById("delivery-result");
    if (!input || !result) return;
    const area = input.value.trim().toLowerCase();
    if (!area) {
      result.textContent = "Please enter an area.";
      result.className = "mt-2 text-[0.8rem] text-rose-300";
      return;
    }
    const freeAreas = ["teshie", "teshie point 5", "teshie-nungua", "tsui bleoo", "lekma", "lekma hospital"];
    const isFree = freeAreas.some(a => area.includes(a));
    if (isFree) {
      result.textContent = "✅ You’re within our core zone. Free or cheaper delivery available. We’ll confirm exact charges when you order.";
      result.className = "mt-2 text-[0.8rem] text-emerald-300";
    } else {
      result.textContent = "ℹ️ You’re a bit further out. Delivery is still possible, but a small delivery fee may apply.";
      result.className = "mt-2 text-[0.8rem] text-amber-300";
    }
  }

  // Address saver
  function loadSavedAddress() {
    const addressField = document.getElementById("address");
    if (!addressField) return;
    const saved = localStorage.getItem("nsAddress");
    if (saved) addressField.value = saved;
  }
  function attachAddressSaver() {
    const addressField = document.getElementById("address");
    if (!addressField) return;
    addressField.addEventListener("blur", () => {
      const value = addressField.value.trim();
      if (value) localStorage.setItem("nsAddress", value);
    });
  }

  // Last order saver
  function reorderLastOrder() {
    const last = localStorage.getItem("nsLastOrder");
    if (!last) {
      showOrderPopup("No previous order found on this device.");
      return;
    }
    const parsed = JSON.parse(last);
    const name = document.getElementById("name");
    const phone = document.getElementById("phone");
    const order = document.getElementById("order");
    const address = document.getElementById("address");
    const time = document.getElementById("time");
    const schedule = document.getElementById("schedule");

    if (name) name.value = parsed.name || "";
    if (phone) phone.value = parsed.phone || "";
    if (order) order.value = parsed.order || "";
    if (address) address.value = parsed.address || "";
    if (time) time.value = parsed.time || "";
    if (schedule && parsed.schedule) schedule.value = parsed.schedule;

    showOrderPopup("Last order loaded. You can edit and resend.");
  }

  // Smart recommender
  function showRecommendations(itemName) {
    const bar = document.getElementById("recommend-bar");
    if (!bar) return;
    let suggestion = "";
    const lower = (itemName || "").toLowerCase();
    if (lower.includes("jollof") || lower.includes("fried rice")) {
      suggestion = "🔥 Customers who order rice often add Coke, Fanta or extra grilled chicken. Want to add a drink or chicken to your order?";
    } else if (lower.includes("spaghetti")) {
      suggestion = "🍝 Spaghetti pairs well with extra sausage or a side of fries. You can mention it in the message before sending.";
    } else if (lower.includes("pizza")) {
      suggestion = "🍕 When pizza launches, we recommend adding wings or extra cheese. Stay tuned!";
    } else {
      suggestion = "💡 You can add a drink, extra chicken or sausage to almost any meal. Just include it in your WhatsApp message.";
    }
    bar.textContent = suggestion;
    bar.classList.remove("hidden");
  }

  // Quick Order (fills form + adds to cart)
  function quickOrder(itemName, itemPrice = "") {
    const orderField = document.getElementById("order");
    const contactSection = document.getElementById("contact");
    if (orderField) {
      const existing = orderField.value.trim();
      const line = itemName + (itemPrice ? " — " + itemPrice : "");
      orderField.value = existing ? (existing + "\n" + line) : line;
    }
    if (contactSection) {
      contactSection.scrollIntoView({ behavior: "smooth" });
    }
    setTimeout(() => {
      if (orderField) orderField.focus();
    }, 600);

    addToCart(itemName, itemPrice);
    showRecommendations(itemName);
  }

  // WhatsApp form send
  function sendToWhatsApp() {
    let name = document.getElementById("name").value.trim();
    let phone = document.getElementById("phone").value.trim();
    let order = document.getElementById("order").value.trim();
    let time = document.getElementById("time").value.trim();
    let schedule = document.getElementById("schedule").value;
    let address = document.getElementById("address").value.trim();

    if (name === "") {
      alert("Please enter your name.");
      document.getElementById("name").focus();
      return;
    }
    if (phone === "") {
      alert("Please enter your phone or WhatsApp number.");
      document.getElementById("phone").focus();
      return;
    }
    if (!order && !cart.length) {
      alert("Please enter your order or add items to cart.");
      document.getElementById("order").focus();
      return;
    }

    // Build cart text
    let cartText = "";
    if (cart.length) {
      const lines = cart.map(item => `• ${item.qty} x ${item.name} (${item.priceString})`);
      cartText = lines.join("%0A");
    }

    let scheduleText = schedule === "Custom" ? time : schedule;
    let timePart = scheduleText ? scheduleText : (time || "ASAP");

    let message =
      "🍽️ *NEW ORDER REQUEST*%0A%0A" +
      "*Name:* " + name + "%0A" +
      "*Phone:* " + phone + "%0A%0A";

    if (address) {
      message += "*Address:* " + address + "%0A%0A";
    }

    if (order) {
      message += "*Order message:*%0A" + encodeURIComponent(order).replace(/%20/g, "+") + "%0A%0A";
    }

    if (cartText) {
      message += "*Cart Items:*%0A" + cartText + "%0A%0A";
    }

    message += "*Preferred Time:* " + timePart + "%0A%0A" +
      "— Sent from Noko Simple Fast Food Website";

    let url = "https://wa.me/" + whatsAppNumber + "?text=" + message;
    window.open(url, "_blank");

    // Save last order
    const last = {
      name,
      phone,
      order,
      address,
      time,
      schedule
    };
    localStorage.setItem("nsLastOrder", JSON.stringify(last));
  }

  // Admin panel
  function toggleAdminModal(open) {
    const modal = document.getElementById("admin-modal");
    if (!modal) return;
    modal.classList.toggle("open", open);
  }

  function loadAdminSettingsIntoUI() {
    const map = JSON.parse(localStorage.getItem("nsPrices") || "{}");
    const coming = JSON.parse(localStorage.getItem("nsComingSoon") || "{}");

    const keys = ["jollof", "spag", "friedrice", "vegrice", "pizza"];
    keys.forEach(k => {
      const input = document.getElementById("admin-price-" + k);
      if (input && map[k]) input.value = map[k];
    });

    const friesCb = document.getElementById("admin-coming-fries");
    const pizzaCb = document.getElementById("admin-coming-pizza");
    if (friesCb) friesCb.checked = coming.fries !== false; // default on
    if (pizzaCb) pizzaCb.checked = coming.pizza !== false; // default on
  }

  function applyAdminPricesToPage() {
    const map = JSON.parse(localStorage.getItem("nsPrices") || "{}");
    document.querySelectorAll(".price-span").forEach(span => {
      const key = span.dataset.priceKey;
      if (key && map[key]) {
        span.textContent = map[key];
      }
    });
  }

  function applyComingSoonFlagsToPage() {
    const coming = JSON.parse(localStorage.getItem("nsComingSoon") || "{}");
    // fries card
    const friesCard = Array.from(document.querySelectorAll(".menu-card")).find(c => (c.dataset.name || "").toLowerCase().includes("fully loaded fries"));
    if (friesCard) {
      const btn = friesCard.querySelector("button");
      const comingSoon = coming.fries !== false; // default true
      friesCard.dataset.comingSoon = comingSoon ? "true" : "false";
      if (btn) {
        if (comingSoon) {
          btn.textContent = "Coming Soon";
          btn.disabled = true;
          btn.className = "px-3 py-1.5 rounded-full bg-slate-400 text-slate-700 text-[0.75rem] font-medium cursor-not-allowed opacity-70";
        } else {
          btn.textContent = "Add";
          btn.disabled = false;
          btn.className = "px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition";
          btn.setAttribute("onclick", "quickOrder('Fully Loaded Fries', document.querySelector('[data-price-key=\\'fries\\']').textContent)");
        }
      }
    }
    // pizza card
    const pizzaCard = Array.from(document.querySelectorAll(".menu-card")).find(c => (c.dataset.name || "").toLowerCase() === "pizza");
    if (pizzaCard) {
      const btn = pizzaCard.querySelector("button");
      const comingSoon = coming.pizza !== false; // default true
      pizzaCard.dataset.comingSoon = comingSoon ? "true" : "false";
      if (btn) {
        if (comingSoon) {
          btn.textContent = "Coming Soon";
          btn.disabled = true;
          btn.className = "px-3 py-1.5 rounded-full bg-slate-400 text-slate-700 text-[0.75rem] font-medium cursor-not-allowed opacity-70";
        } else {
          btn.textContent = "Add";
          btn.disabled = false;
          btn.className = "px-3 py-1.5 rounded-full bg-slate-900 text-slate-50 text-[0.75rem] font-medium hover:bg-black transition";
          btn.setAttribute("onclick", "quickOrder('Pizza', document.querySelector('[data-price-key=\\'pizza\\']').textContent)");
        }
      }
    }
  }

  function saveAdminSettings() {
    const keys = ["jollof", "spag", "friedrice", "vegrice", "pizza"];
    const prices = {};
    keys.forEach(k => {
      const input = document.getElementById("admin-price-" + k);
      if (input && input.value.trim()) {
        prices[k] = input.value.trim();
      }
    });
    localStorage.setItem("nsPrices", JSON.stringify(prices));

    const coming = {
      fries: document.getElementById("admin-coming-fries").checked,
      pizza: document.getElementById("admin-coming-pizza").checked
    };
    localStorage.setItem("nsComingSoon", JSON.stringify(coming));

    applyAdminPricesToPage();
    applyComingSoonFlagsToPage();
    toggleAdminModal(false);
    showOrderPopup("Admin settings saved on this browser.");
  }

  function resetAdminSettings() {
    localStorage.removeItem("nsPrices");
    localStorage.removeItem("nsComingSoon");
    applyAdminPricesToPage();
    applyComingSoonFlagsToPage();
    loadAdminSettingsIntoUI();
    showOrderPopup("Admin settings reset to default.");
  }

  document.addEventListener("keydown", (e) => {
    if (e.altKey && (e.key === "a" || e.key === "A")) {
      e.preventDefault();
      const modal = document.getElementById("admin-modal");
      const open = !(modal && modal.classList.contains("open"));
      toggleAdminModal(open);
      if (open) loadAdminSettingsIntoUI();
    }
    if (e.key === "Escape") {
      toggleAdminModal(false);
    }
  });

  // Init on DOMContentLoaded
  document.addEventListener("DOMContentLoaded", () => {
    loadSavedAddress();
    attachAddressSaver();
    applyAdminPricesToPage();
    applyComingSoonFlagsToPage();
  });
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Noko Simple Fast Food</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

  <!-- Tailwind -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- CSS -->
  <link rel="stylesheet" href="css/styles.css">
</head>

<body>

  <!-- Your full website content -->
  <!-- I moved ALL styling + scripting out -->
  <div id="app">
    <!-- PLACE **ALL YOUR ORIGINAL HTML BODY CONTENT** HERE -->
    <!-- nothing is removed -->
    <!-- everything else works the same -->
  </div>

  <!-- JS -->
  <script src="js/app.js"></script>
</body>
</html>


