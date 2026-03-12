<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Waynique Works | Design. Build. Elevate.</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <style>
        :root {
            --cream: #F5F1E8;
            --sage: #8B9A7D;
            --sage-light: #A8B899;
            --charcoal: #2C2C2C;
            --gold: #D4AF37;
        }
        
        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--cream);
            color: var(--charcoal);
            overflow-x: hidden;
        }
        
        .font-serif {
            font-family: 'Cormorant Garamond', serif;
        }
        
        .text-sage { color: var(--sage); }
        .bg-sage { background-color: var(--sage); }
        .border-sage { border-color: var(--sage); }
        
        /* Botanical Animation */
        .leaf {
            position: absolute;
            opacity: 0.15;
            pointer-events: none;
            animation: float 20s infinite ease-in-out;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
        }
        
        /* Logo Animation */
        .logo-circle {
            stroke-dasharray: 1000;
            stroke-dashoffset: 1000;
            animation: draw 3s ease-out forwards;
        }
        
        @keyframes draw {
            to { stroke-dashoffset: 0; }
        }
        
        /* Hover Effects */
        .service-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .service-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(139, 154, 125, 0.15);
        }
        
        .service-card:hover .card-line {
            width: 100%;
        }
        
        .card-line {
            width: 0;
            height: 2px;
            background: var(--sage);
            transition: width 0.4s ease;
        }
        
        /* Button Styles */
        .btn-primary {
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }
        
        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .btn-primary:hover::before {
            left: 100%;
        }
        
        /* Decorative Elements */
        .star-decoration {
            animation: twinkle 3s infinite ease-in-out;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
        }
        
        /* Scroll Reveal */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
        }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: var(--cream);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--sage);
            border-radius: 4px;
        }

        /* Star Rating Styles */
        .star-rating {
            display: inline-flex;
            flex-direction: row-reverse;
            gap: 4px;
        }
        
        .star-rating input {
            display: none;
        }
        
        .star-rating label {
            cursor: pointer;
            font-size: 2rem;
            color: #ddd;
            transition: all 0.2s ease;
        }
        
        .star-rating label:hover,
        .star-rating label:hover ~ label,
        .star-rating input:checked ~ label {
            color: var(--gold);
            transform: scale(1.1);
        }
        
        .star-rating input:checked ~ label {
            animation: starPulse 0.3s ease;
        }
        
        @keyframes starPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1.1); }
        }

        /* Review Card Styles */
        .review-card {
            transition: all 0.4s ease;
            backdrop-filter: blur(10px);
        }
        
        .review-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(139, 154, 125, 0.2);
        }

        .review-slider {
            scroll-snap-type: x mandatory;
            -webkit-overflow-scrolling: touch;
        }
        
        .review-slide {
            scroll-snap-align: start;
        }

        /* Form Styles */
        .form-input {
            transition: all 0.3s ease;
            border: 1px solid rgba(139, 154, 125, 0.3);
        }
        
        .form-input:focus {
            outline: none;
            border-color: var(--sage);
            box-shadow: 0 0 0 3px rgba(139, 154, 125, 0.1);
        }

        /* Success Animation */
        @keyframes successPop {
            0% { transform: scale(0.8); opacity: 0; }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); opacity: 1; }
        }
        
        .success-message {
            animation: successPop 0.5s ease forwards;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Floating Botanical Background -->
    <div class="fixed inset-0 pointer-events-none overflow-hidden z-0">
        <svg class="leaf top-20 left-10 w-32 h-32 text-[#8B9A7D]" viewBox="0 0 100 100" fill="currentColor">
            <path d="M50 10 Q30 30 20 50 Q30 70 50 90 Q70 70 80 50 Q70 30 50 10" />
        </svg>
        <svg class="leaf top-40 right-20 w-24 h-24 text-[#8B9A7D]" style="animation-delay: 2s;" viewBox="0 0 100 100" fill="currentColor">
            <path d="M50 10 Q20 40 30 70 Q50 60 70 70 Q80 40 50 10" />
        </svg>
        <svg class="leaf bottom-32 left-1/4 w-40 h-40 text-[#8B9A7D]" style="animation-delay: 4s;" viewBox="0 0 100 100" fill="currentColor">
            <path d="M50 5 Q25 25 15 50 Q25 75 50 95 Q75 75 85 50 Q75 25 50 5" />
        </svg>
    </div>

    <!-- Navigation -->
    <nav class="fixed w-full z-50 bg-[#F5F1E8]/90 backdrop-blur-md border-b border-[#8B9A7D]/20 transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
            <div class="font-serif text-2xl font-bold tracking-wider text-[#2C2C2C]">WAYNIQUE</div>
            <div class="hidden md:flex space-x-8 text-sm font-medium tracking-wide">
                <a href="#services" class="hover:text-[#8B9A7D] transition-colors">SERVICES</a>
                <a href="#reviews" class="hover:text-[#8B9A7D] transition-colors">REVIEWS</a>
                <a href="#about" class="hover:text-[#8B9A7D] transition-colors">ABOUT</a>
                <a href="#contact" class="hover:text-[#8B9A7D] transition-colors">CONTACT</a>
            </div>
            <button class="md:hidden text-[#2C2C2C]" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
            </button>
        </div>
        <div id="mobile-menu" class="hidden md:hidden bg-[#F5F1E8] border-t border-[#8B9A7D]/20 px-6 py-4 space-y-3">
            <a href="#services" class="block text-sm font-medium">SERVICES</a>
            <a href="#reviews" class="block text-sm font-medium">REVIEWS</a>
            <a href="#about" class="block text-sm font-medium">ABOUT</a>
            <a href="#contact" class="block text-sm font-medium">CONTACT</a>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center pt-20 overflow-hidden">
        <div class="max-w-5xl mx-auto px-6 text-center relative z-10">
            
            <!-- Animated Logo -->
            <div class="mb-8 relative inline-block">
                <div class="w-64 h-64 md:w-80 md:h-80 mx-auto relative">
                    <svg class="absolute inset-0 w-full h-full animate-spin-slow" style="animation-duration: 20s;" viewBox="0 0 200 200">
                        <circle cx="100" cy="100" r="95" fill="none" stroke="#8B9A7D" stroke-width="1" opacity="0.3"/>
                        <circle cx="100" cy="100" r="85" fill="none" stroke="#8B9A7D" stroke-width="1" opacity="0.5" stroke-dasharray="5,5"/>
                    </svg>
                    
                    <svg class="absolute inset-0 w-full h-full" viewBox="0 0 200 200" fill="none">
                        <path class="logo-circle" d="M100 20 Q120 40 140 30 Q130 60 150 80 Q120 90 110 120 Q100 100 90 120 Q80 90 50 80 Q70 60 60 30 Q80 40 100 20" 
                              stroke="#8B9A7D" stroke-width="2" fill="none" opacity="0.6"/>
                        <g fill="#8B9A7D" opacity="0.8">
                            <ellipse cx="100" cy="25" rx="8" ry="15" transform="rotate(0 100 25)"/>
                            <ellipse cx="140" cy="50" rx="8" ry="15" transform="rotate(60 140 50)"/>
                            <ellipse cx="130" cy="100" rx="8" ry="15" transform="rotate(120 130 100)"/>
                            <ellipse cx="70" cy="100" rx="8" ry="15" transform="rotate(240 70 100)"/>
                            <ellipse cx="60" cy="50" rx="8" ry="15" transform="rotate(300 60 50)"/>
                        </g>
                    </svg>
                    
                    <div class="absolute inset-0 flex items-center justify-center">
                        <span class="font-serif text-7xl md:text-8xl font-bold text-[#2C2C2C]">W</span>
                    </div>
                    
                    <div class="star-decoration absolute top-10 right-12 text-[#D4AF37] text-xl">✦</div>
                    <div class="star-decoration absolute bottom-16 left-10 text-[#D4AF37] text-lg" style="animation-delay: 1s;">✦</div>
                    <div class="star-decoration absolute top-1/2 right-8 text-[#D4AF37] text-sm" style="animation-delay: 2s;">✦</div>
                </div>
            </div>

            <h1 class="font-serif text-5xl md:text-7xl font-bold text-[#2C2C2C] mb-2 tracking-wide reveal">
                WAYNIQUE
            </h1>
            <h2 class="font-serif text-3xl md:text-4xl text-[#8B9A7D] mb-6 reveal" style="animation-delay: 0.1s;">
                WORKS
            </h2>
            
            <div class="flex items-center justify-center gap-4 mb-8 reveal" style="animation-delay: 0.2s;">
                <div class="h-px w-12 bg-[#8B9A7D]"></div>
                <p class="text-sm md:text-base tracking-[0.3em] text-[#2C2C2C] font-medium">DESIGN. BUILD. ELEVATE.</p>
                <div class="h-px w-12 bg-[#8B9A7D]"></div>
            </div>

            <p class="max-w-2xl mx-auto text-lg md:text-xl text-[#2C2C2C]/80 leading-relaxed mb-12 font-light reveal" style="animation-delay: 0.3s;">
                Waynique Works provides professional and reliable creative support for individuals and businesses seeking to enhance their brand and professional image.
            </p>

            <div class="reveal" style="animation-delay: 0.4s;">
                <a href="#services" class="btn-primary inline-block bg-[#2C2C2C] text-[#F5F1E8] px-10 py-4 text-sm tracking-widest font-medium hover:bg-[#8B9A7D] transition-colors duration-300">
                    EXPLORE SERVICES
                </a>
            </div>
        </div>

        <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
            <svg class="w-6 h-6 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
            </svg>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-24 relative">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16 reveal">
                <div class="flex items-center justify-center gap-4 mb-4">
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                </div>
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-4">Our Services</h3>
                <div class="h-px w-24 bg-[#8B9A7D] mx-auto"></div>
            </div>

            <div class="grid md:grid-cols-3 gap-8 md:gap-12">
                <div class="service-card bg-white/50 backdrop-blur-sm p-8 md:p-10 border border-[#8B9A7D]/20 relative group reveal">
                    <div class="card-line absolute top-0 left-0"></div>
                    <div class="mb-6">
                        <svg class="w-12 h-12 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/>
                        </svg>
                    </div>
                    <h4 class="font-serif text-2xl md:text-3xl text-[#2C2C2C] mb-6">Career<br>Support</h4>
                    <ul class="space-y-3 text-[#2C2C2C]/80">
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Professional CV design and formatting</span>
                        </li>
                    </ul>
                </div>

                <div class="service-card bg-white/50 backdrop-blur-sm p-8 md:p-10 border border-[#8B9A7D]/20 relative group reveal" style="animation-delay: 0.1s;">
                    <div class="card-line absolute top-0 left-0"></div>
                    <div class="mb-6">
                        <svg class="w-12 h-12 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11 5.882V19.24a1.76 1.76 0 01-3.417.592l-2.147-6.15M18 13a3 3 0 100-6M5.436 13.683A4.001 4.001 0 017 6h1.832c4.1 0 7.625-1.234 9.168-3v14c-1.543-1.766-5.067-3-9.168-3H7a3.988 3.988 0 01-1.564-.317z"/>
                        </svg>
                    </div>
                    <h4 class="font-serif text-2xl md:text-3xl text-[#2C2C2C] mb-6">Marketing &<br>Social Media</h4>
                    <ul class="space-y-3 text-[#2C2C2C]/80">
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Business advertisements and promotional posts</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Poster and business page setup</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Short-form video editing</span>
                        </li>
                    </ul>
                </div>

                <div class="service-card bg-white/50 backdrop-blur-sm p-8 md:p-10 border border-[#8B9A7D]/20 relative group reveal" style="animation-delay: 0.2s;">
                    <div class="card-line absolute top-0 left-0"></div>
                    <div class="mb-6">
                        <svg class="w-12 h-12 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01"/>
                        </svg>
                    </div>
                    <h4 class="font-serif text-2xl md:text-3xl text-[#2C2C2C] mb-6">Business &<br>Design Services</h4>
                    <ul class="space-y-3 text-[#2C2C2C]/80">
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Logo layout and business cards</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Business profiles</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <span class="text-[#8B9A7D] mt-1.5">•</span>
                            <span>Custom designs for clothing, caps, and promotional items</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Reviews Section -->
    <section id="reviews" class="py-24 bg-[#8B9A7D]/10 relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 relative z-10">
            
            <!-- Section Header -->
            <div class="text-center mb-16 reveal">
                <div class="flex items-center justify-center gap-4 mb-4">
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                </div>
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-4">Client Reviews</h3>
                <div class="h-px w-24 bg-[#8B9A7D] mx-auto mb-6"></div>
                <p class="text-[#2C2C2C]/70 max-w-2xl mx-auto">See what our clients say about working with us. Your feedback helps us grow and serve you better.</p>
            </div>

            <!-- Reviews Display -->
            <div class="mb-16">
                <div class="flex justify-between items-center mb-8 reveal">
                    <h4 class="font-serif text-2xl text-[#2C2C2C]">Recent Testimonials</h4>
                    <div class="flex gap-2">
                        <button onclick="scrollReviews(-1)" class="w-10 h-10 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"/></svg>
                        </button>
                        <button onclick="scrollReviews(1)" class="w-10 h-10 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
                        </button>
                    </div>
                </div>

                <!-- Reviews Container -->
                <div id="reviews-container" class="review-slider flex gap-6 overflow-x-auto pb-4 snap-x snap-mandatory scrollbar-hide" style="scrollbar-width: none; -ms-overflow-style: none;">
                    
                    <!-- Review 1 -->
                    <div class="review-slide min-w-[350px] md:min-w-[400px] bg-white/70 backdrop-blur-sm p-8 rounded-lg border border-[#8B9A7D]/20 review-card">
                        <div class="flex items-center gap-1 mb-4 text-[#D4AF37]">
                            <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                        </div>
                        <p class="text-[#2C2C2C]/80 mb-6 italic leading-relaxed">"Waynique Works transformed my outdated CV into a stunning professional document. I landed three interviews within the first week of using it!"</p>
                        <div class="flex items-center gap-4">
                            <div class="w-12 h-12 rounded-full bg-[#8B9A7D]/20 flex items-center justify-center font-serif text-xl text-[#8B9A7D]">S</div>
                            <div>
                                <div class="font-medium text-[#2C2C2C]">Sarah Mitchell</div>
                                <div class="text-sm text-[#2C2C2C]/60">Marketing Director</div>
                            </div>
                        </div>
                    </div>

                    <!-- Review 2 -->
                    <div class="review-slide min-w-[350px] md:min-w-[400px] bg-white/70 backdrop-blur-sm p-8 rounded-lg border border-[#8B9A7D]/20 review-card">
                        <div class="flex items-center gap-1 mb-4 text-[#D4AF37]">
                            <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                        </div>
                        <p class="text-[#2C2C2C]/80 mb-6 italic leading-relaxed">"The attention to detail in our business cards and logo design was exceptional. They truly understood our brand vision and elevated it beyond expectations."</p>
                        <div class="flex items-center gap-4">
                            <div class="w-12 h-12 rounded-full bg-[#8B9A7D]/20 flex items-center justify-center font-serif text-xl text-[#8B9A7D]">J</div>
                            <div>
                                <div class="font-medium text-[#2C2C2C]">James Chen</div>
                                <div class="text-sm text-[#2C2C2C]/60">Startup Founder</div>
                            </div>
                        </div>
                    </div>

                    <!-- Review 3 -->
                    <div class="review-slide min-w-[350px] md:min-w-[400px] bg-white/70 backdrop-blur-sm p-8 rounded-lg border border-[#8B9A7D]/20 review-card">
                        <div class="flex items-center gap-1 mb-4 text-[#D4AF37]">
                            <span>★</span><span>★</span><span>★</span><span>★</span><span>☆</span>
                        </div>
                        <p class="text-[#2C2C2C]/80 mb-6 italic leading-relaxed">"Professional, timely, and incredibly creative. Our social media presence has grown significantly since implementing their marketing materials."</p>
                        <div class="flex items-center gap-4">
                            <div class="w-12 h-12 rounded-full bg-[#8B9A7D]/20 flex items-center justify-center font-serif text-xl text-[#8B9A7D]">A</div>
                            <div>
                                <div class="font-medium text-[#2C2C2C]">Amanda Rodriguez</div>
                                <div class="text-sm text-[#2C2C2C]/60">Small Business Owner</div>
                            </div>
                        </div>
                    </div>

                    <!-- Review 4 -->
                    <div class="review-slide min-w-[350px] md:min-w-[400px] bg-white/70 backdrop-blur-sm p-8 rounded-lg border border-[#8B9A7D]/20 review-card">
                        <div class="flex items-center gap-1 mb-4 text-[#D4AF37]">
                            <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
                        </div>
                        <p class="text-[#2C2C2C]/80 mb-6 italic leading-relaxed">"The video editing work was phenomenal. They took our raw footage and created something that truly captures our brand story."</p>
                        <div class="flex items-center gap-4">
                            <div class="w-12 h-12 rounded-full bg-[#8B9A7D]/20 flex items-center justify-center font-serif text-xl text-[#8B9A7D]">M</div>
                            <div>
                                <div class="font-medium text-[#2C2C2C]">Michael Thompson</div>
                                <div class="text-sm text-[#2C2C2C]/60">Content Creator</div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>

            <!-- Leave a Review Form -->
            <div class="max-w-2xl mx-auto reveal">
                <div class="bg-white/80 backdrop-blur-md p-8 md:p-12 rounded-lg border border-[#8B9A7D]/30 shadow-lg">
                    <h4 class="font-serif text-3xl text-[#2C2C2C] mb-2 text-center">Share Your Experience</h4>
                    <p class="text-center text-[#2C2C2C]/60 mb-8">We'd love to hear about your experience working with us</p>
                    
                    <form id="reviewForm" class="space-y-6">
                        <!-- Star Rating Input -->
                        <div class="text-center">
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-3 tracking-wider">YOUR RATING</label>
                            <div class="star-rating justify-center">
                                <input type="radio" id="star5" name="rating" value="5" required>
                                <label for="star5" title="5 stars">★</label>
                                
                                <input type="radio" id="star4" name="rating" value="4">
                                <label for="star4" title="4 stars">★</label>
                                
                                <input type="radio" id="star3" name="rating" value="3">
                                <label for="star3" title="3 stars">★</label>
                                
                                <input type="radio" id="star2" name="rating" value="2">
                                <label for="star2" title="2 stars">★</label>
                                
                                <input type="radio" id="star1" name="rating" value="1">
                                <label for="star1" title="1 star">★</label>
                            </div>
                        </div>

                        <!-- Name Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR NAME</label>
                            <input type="text" name="name" required class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="Enter your name">
                        </div>

                        <!-- Role/Company Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">ROLE / COMPANY</label>
                            <input type="text" name="role" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="e.g. Marketing Director at Company">
                        </div>

                        <!-- Review Text -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR REVIEW</label>
                            <textarea name="review" required rows="4" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30 resize-none" placeholder="Tell us about your experience..."></textarea>
                        </div>

                        <!-- Submit Button -->
                        <button type="submit" class="btn-primary w-full bg-[#2C2C2C] text-[#F5F1E8] py-4 text-sm tracking-widest font-medium hover:bg-[#8B9A7D] transition-colors duration-300 rounded-lg">
                            SUBMIT REVIEW
                        </button>
                    </form>

                    <!-- Success Message (Hidden by default) -->
                    <div id="successMessage" class="hidden text-center py-8 success-message">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center text-3xl">✓</div>
                        <h5 class="font-serif text-2xl text-[#2C2C2C] mb-2">Thank You!</h5>
                        <p class="text-[#2C2C2C]/70">Your review has been submitted successfully.</p>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- About/Process Section -->
    <section id="about" class="py-24 relative overflow-hidden">
        <div class="max-w-5xl mx-auto px-6 text-center relative z-10">
            <div class="reveal">
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-8">Why Choose Waynique?</h3>
                <p class="text-lg text-[#2C2C2C]/80 leading-relaxed max-w-3xl mx-auto mb-12">
                    We believe every brand has a unique story waiting to be told. Our approach combines strategic thinking with creative excellence to deliver designs that not only look beautiful but drive real results for your business.
                </p>
                
                <div class="grid md:grid-cols-3 gap-8 mt-16">
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">1</div>
                        <h5 class="font-serif text-xl mb-2">Discover</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Understanding your vision and goals</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">2</div>
                        <h5 class="font-serif text-xl mb-2">Design</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Crafting tailored creative solutions</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">3</div>
                        <h5 class="font-serif text-xl mb-2">Deliver</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Elevating your professional image</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 bg-[#8B9A7D]/10 relative">
        <div class="max-w-4xl mx-auto px-6 text-center">
            <div class="reveal">
                <div class="flex items-center justify-center gap-4 mb-6">
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                </div>
                
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-6">Let's Create Together</h3>
                <p class="text-lg text-[#2C2C2C]/80 mb-12 max-w-2xl mx-auto">
                    Ready to elevate your brand? Get in touch to discuss your project and discover how we can help you stand out.
                </p>

                <div class="bg-white/70 backdrop-blur-sm border border-[#8B9A7D]/30 p-8 md:p-12 inline-block max-w-lg w-full">
                    <div class="flex items-center justify-center gap-3 mb-2">
                        <svg class="w-6 h-6 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                        </svg>
                        <span class="text-sm tracking-widest text-[#8B9A7D] font-medium">CONTACT</span>
                    </div>
                    <a href="mailto:wayniqueworks@gmail.com" class="font-serif text-2xl md:text-3xl text-[#2C2C2C] hover:text-[#8B9A7D] transition-colors duration-300 break-all">
                        wayniqueworks@gmail.com
                    </a>
                </div>

                <div class="mt-12 flex justify-center gap-6">
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.5742C2C2C]">Michael Thompson</div>
                                <div class="text-sm text-[#2C2C2C]/60">Content Creator</div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>

            <!-- Leave a Review Form -->
            <div class="max-w-2xl mx-auto reveal">
                <div class="bg-white/80 backdrop-blur-md p-8 md:p-12 rounded-lg border border-[#8B9A7D]/30 shadow-lg">
                    <h4 class="font-serif text-3xl text-[#2C2C2C] mb-2 text-center">Share Your Experience</h4>
                    <p class="text-center text-[#2C2C2C]/60 mb-8">We'd love to hear about your experience working with us</p>
                    
                    <form id="reviewForm" class="space-y-6">
                        <!-- Star Rating Input -->
                        <div class="text-center">
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-3 tracking-wider">YOUR RATING</label>
                            <div class="star-rating justify-center">
                                <input type="radio" id="star5" name="rating" value="5" required>
                                <label for="star5" title="5 stars">★</label>
                                
                                <input type="radio" id="star4" name="rating" value="4">
                                <label for="star4" title="4 stars">★</label>
                                
                                <input type="radio" id="star3" name="rating" value="3">
                                <label for="star3" title="3 stars">★</label>
                                
                                <input type="radio" id="star2" name="rating" value="2">
                                <label for="star2" title="2 stars">★</label>
                                
                                <input type="radio" id="star1" name="rating" value="1">
                                <label for="star1" title="1 star">★</label>
                            </div>
                        </div>

                        <!-- Name Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR NAME</label>
                            <input type="text" name="name" required class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="Enter your name">
                        </div>

                        <!-- Role/Company Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">ROLE / COMPANY</label>
                            <input type="text" name="role" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="e.g. Marketing Director at Company">
                        </div>

                        <!-- Review Text -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR REVIEW</label>
                            <textarea name="review" required rows="4" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30 resize-none" placeholder="Tell us about your experience..."></textarea>
                        </div>

                        <!-- Submit Button -->
                        <button type="submit" class="btn-primary w-full bg-[#2C2C2C] text-[#F5F1E8] py-4 text-sm tracking-widest font-medium hover:bg-[#8B9A7D] transition-colors duration-300 rounded-lg">
                            SUBMIT REVIEW
                        </button>
                    </form>

                    <!-- Success Message (Hidden by default) -->
                    <div id="successMessage" class="hidden text-center py-8 success-message">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center text-3xl">✓</div>
                        <h5 class="font-serif text-2xl text-[#2C2C2C] mb-2">Thank You!</h5>
                        <p class="text-[#2C2C2C]/70">Your review has been submitted successfully.</p>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- About/Process Section -->
    <section id="about" class="py-24 relative overflow-hidden">
        <div class="max-w-5xl mx-auto px-6 text-center relative z-10">
            <div class="reveal">
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-8">Why Choose Waynique?</h3>
                <p class="text-lg text-[#2C2C2C]/80 leading-relaxed max-w-3xl mx-auto mb-12">
                    We believe every brand has a unique story waiting to be told. Our approach combines strategic thinking with creative excellence to deliver designs that not only look beautiful but drive real results for your business.
                </p>
                
                <div class="grid md:grid-cols-3 gap-8 mt-16">
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">1</div>
                        <h5 class="font-serif text-xl mb-2">Discover</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Understanding your vision and goals</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">2</div>
                        <h5 class="font-serif text-xl mb-2">Design</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Crafting tailored creative solutions</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">3</div>
                        <h5 class="font-serif text-xl mb-2">Deliver</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Elevating your professional image</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 bg-[#8B9A7D]/10 relative">
        <div class="max-w-4xl mx-auto px-6 text-center">
            <div class="reveal">
                <div class="flex items-center justify-center gap-4 mb-6">
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                </div>
                
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-6">Let's Create Together</h3>
                <p class="text-lg text-[#2C2C2C]/80 mb-12 max-w-2xl mx-auto">
                    Ready to elevate your brand? Get in touch to discuss your project and discover how we can help you stand out.
                </p>

                <div class="bg-white/70 backdrop-blur-sm border border-[#8B9A7D]/30 p-8 md:p-12 inline-block max-w-lg w-full">
                    <div class="flex items-center justify-center gap-3 mb-2">
                        <svg class="w-6 h-6 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                        </svg>
                        <span class="text-sm tracking-widest text-[#8B9A7D] font-medium">CONTACT</span>
                    </div>
                    <a href="mailto:wayniqueworks@gmail.com" class="font-serif text-2xl md:text-3xl text-[#2C2C2C] hover:text-[#8B9A7D] transition-colors duration-300 break-all">
                        wayniqueworks@gmail.com
                    </a>
                </div>

                <div class="mt-12 flex justify-center gap-6">
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                    </a>
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    </a>
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 12C2C2C]">Michael Thompson</div>
                                <div class="text-sm text-[#2C2C2C]/60">Content Creator</div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>

            <!-- Leave a Review Form -->
            <div class="max-w-2xl mx-auto reveal">
                <div class="bg-white/80 backdrop-blur-md p-8 md:p-12 rounded-lg border border-[#8B9A7D]/30 shadow-lg">
                    <h4 class="font-serif text-3xl text-[#2C2C2C] mb-2 text-center">Share Your Experience</h4>
                    <p class="text-center text-[#2C2C2C]/60 mb-8">We'd love to hear about your experience working with us</p>
                    
                    <form id="reviewForm" class="space-y-6">
                        <!-- Star Rating Input -->
                        <div class="text-center">
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-3 tracking-wider">YOUR RATING</label>
                            <div class="star-rating justify-center">
                                <input type="radio" id="star5" name="rating" value="5" required>
                                <label for="star5" title="5 stars">★</label>
                                
                                <input type="radio" id="star4" name="rating" value="4">
                                <label for="star4" title="4 stars">★</label>
                                
                                <input type="radio" id="star3" name="rating" value="3">
                                <label for="star3" title="3 stars">★</label>
                                
                                <input type="radio" id="star2" name="rating" value="2">
                                <label for="star2" title="2 stars">★</label>
                                
                                <input type="radio" id="star1" name="rating" value="1">
                                <label for="star1" title="1 star">★</label>
                            </div>
                        </div>

                        <!-- Name Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR NAME</label>
                            <input type="text" name="name" required class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="Enter your name">
                        </div>

                        <!-- Role/Company Input -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">ROLE / COMPANY</label>
                            <input type="text" name="role" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30" placeholder="e.g. Marketing Director at Company">
                        </div>

                        <!-- Review Text -->
                        <div>
                            <label class="block text-sm font-medium text-[#2C2C2C]/70 mb-2 tracking-wider">YOUR REVIEW</label>
                            <textarea name="review" required rows="4" class="form-input w-full px-4 py-3 bg-white/50 rounded-lg text-[#2C2C2C] placeholder-[#2C2C2C]/30 resize-none" placeholder="Tell us about your experience..."></textarea>
                        </div>

                        <!-- Submit Button -->
                        <button type="submit" class="btn-primary w-full bg-[#2C2C2C] text-[#F5F1E8] py-4 text-sm tracking-widest font-medium hover:bg-[#8B9A7D] transition-colors duration-300 rounded-lg">
                            SUBMIT REVIEW
                        </button>
                    </form>

                    <!-- Success Message (Hidden by default) -->
                    <div id="successMessage" class="hidden text-center py-8 success-message">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center text-3xl">✓</div>
                        <h5 class="font-serif text-2xl text-[#2C2C2C] mb-2">Thank You!</h5>
                        <p class="text-[#2C2C2C]/70">Your review has been submitted successfully.</p>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- About/Process Section -->
    <section id="about" class="py-24 relative overflow-hidden">
        <div class="max-w-5xl mx-auto px-6 text-center relative z-10">
            <div class="reveal">
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-8">Why Choose Waynique?</h3>
                <p class="text-lg text-[#2C2C2C]/80 leading-relaxed max-w-3xl mx-auto mb-12">
                    We believe every brand has a unique story waiting to be told. Our approach combines strategic thinking with creative excellence to deliver designs that not only look beautiful but drive real results for your business.
                </p>
                
                <div class="grid md:grid-cols-3 gap-8 mt-16">
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">1</div>
                        <h5 class="font-serif text-xl mb-2">Discover</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Understanding your vision and goals</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">2</div>
                        <h5 class="font-serif text-xl mb-2">Design</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Crafting tailored creative solutions</p>
                    </div>
                    <div class="relative">
                        <div class="w-16 h-16 mx-auto mb-4 rounded-full bg-[#8B9A7D] text-white flex items-center justify-center font-serif text-2xl">3</div>
                        <h5 class="font-serif text-xl mb-2">Deliver</h5>
                        <p class="text-sm text-[#2C2C2C]/70">Elevating your professional image</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 bg-[#8B9A7D]/10 relative">
        <div class="max-w-4xl mx-auto px-6 text-center">
            <div class="reveal">
                <div class="flex items-center justify-center gap-4 mb-6">
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                    <span class="text-[#D4AF37] text-2xl">✦</span>
                    <div class="h-px w-16 bg-[#8B9A7D]"></div>
                </div>
                
                <h3 class="font-serif text-4xl md:text-5xl text-[#2C2C2C] mb-6">Let's Create Together</h3>
                <p class="text-lg text-[#2C2C2C]/80 mb-12 max-w-2xl mx-auto">
                    Ready to elevate your brand? Get in touch to discuss your project and discover how we can help you stand out.
                </p>

                <div class="bg-white/70 backdrop-blur-sm border border-[#8B9A7D]/30 p-8 md:p-12 inline-block max-w-lg w-full">
                    <div class="flex items-center justify-center gap-3 mb-2">
                        <svg class="w-6 h-6 text-[#8B9A7D]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                        </svg>
                        <span class="text-sm tracking-widest text-[#8B9A7D] font-medium">CONTACT</span>
                    </div>
                    <a href="mailto:wayniqueworks@gmail.com" class="font-serif text-2xl md:text-3xl text-[#2C2C2C] hover:text-[#8B9A7D] transition-colors duration-300 break-all">
                        wayniqueworks@gmail.com
                    </a>
                </div>

                <div class="mt-12 flex justify-center gap-6">
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/></svg>
                    </a>
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    </a>
                    <a href="#" class="w-12 h-12 rounded-full border border-[#8B9A7D]/30 flex items-center justify-center hover:bg-[#8B9A7D] hover:text-white transition-all duration-300 text-[#2C2C2C]">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-[#2C2C2C] text-[#F5F1E8] py-12 border-t border-[#8B9A7D]/30">
        <div class="max-w-7xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="font-serif text-2xl font-bold tracking-wider">WAYNIQUE WORKS</div>
            <div class="text-sm opacity-60 tracking-wider">© 2024 Waynique Works. All rights reserved.</div>
            <div class="flex gap-6 text-sm">
                <a href="#" class="hover:text-[#8B9A7D] transition-colors">Privacy</a>
                <a href="#" class="hover:text-[#8B9A7D] transition-colors">Terms</a>
            </div>
        </div>
    </footer>

    <script>
        // GSAP ScrollTrigger Registration
        gsap.registerPlugin(ScrollTrigger);

        // Navbar scroll effect
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('shadow-md');
                navbar.classList.replace('py-4', 'py-2');
            } else {
                navbar.classList.remove('shadow-md');
                navbar.classList.replace('py-2', 'py-4');
            }
        });

        // Reveal animations
        gsap.utils.toArray('.reveal').forEach((element, i) => {
            gsap.fromTo(element, 
                {
                    opacity: 0,
                    y: 30
                },
                {
                    opacity: 1,
                    y: 0,
                    duration: 0.8,
                    ease: "power2.out",
                    scrollTrigger: {
                        trigger: element,
                        start: "top 85%",
                        toggleActions: "play none none reverse"
                    },
                    delay: element.style.animationDelay ? parseFloat(element.style.animationDelay) : 0
                }
            );
        });

        // Service cards stagger animation
        gsap.from(".service-card", {
            opacity: 0,
            y: 50,
            duration: 0.8,
            stagger: 0.2,
            ease: "power2.out",
            scrollTrigger: {
                trigger: "#services",
                start: "top 70%"
            }
        });

        // Review cards animation
        gsap.from(".review-card", {
            opacity: 0,
            x: 50,
            duration: 0.8,
            stagger: 0.15,
            ease: "power2.out",
            scrollTrigger: {
                trigger: "#reviews",
                start: "top 70%"
            }
        });

        // Smooth scroll for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Parallax effect for botanical elements
        document.addEventListener('mousemove', (e) => {
            const leaves = document.querySelectorAll('.leaf');
            const x = e.clientX / window.innerWidth;
            const y = e.clientY / window.innerHeight;
            
            leaves.forEach((leaf, index) => {
                const speed = (index + 1) * 10;
                leaf.style.transform = `translate(${x * speed}px, ${y * speed}px) rotate(${x * 10}deg)`;
            });
        });

        // Reviews Slider Functionality
        function scrollReviews(direction) {
            const container = document.getElementById('reviews-container');
            const scrollAmount = 400;
            container.scrollBy({
                left: direction * scrollAmount,
                behavior: 'smooth'
            });
        }

        // Review Form Submission
        document.getElementById('reviewForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form values
            const formData = new FormData(this);
            const rating = formData.get('rating');
            const name = formData.get('name');
            const role = formData.get('role');
            const reviewText = formData.get('review');
            
            // Create new review card
            const newReview = document.createElement('div');
            newReview.className = 'review-slide min-w-[350px] md:min-w-[400px] bg-white/70 backdrop-blur-sm p-8 rounded-lg border border-[#8B9A7D]/20 review-card success-message';
            
            // Generate stars HTML
            let starsHtml = '';
            for(let i = 1; i <= 5; i++) {
                starsHtml += i <= rating ? '★' : '☆';
            }
            
            // Get initials
            const initials = name.split(' ').map(n => n[0]).join('').toUpperCase();
            
            newReview.innerHTML = `
                <div class="flex items-center gap-1 mb-4 text-[#D4AF37]">
                    ${starsHtml.split('').map(star => `<span>${star}</span>`).join('')}
                </div>
                <p class="text-[#2C2C2C]/80 mb-6 italic leading-relaxed">"${reviewText}"</p>
                <div class="flex items-center gap-4">
                    <div class="w-12 h-12 rounded-full bg-[#8B9A7D]/20 flex items-center justify-center font-serif text-xl text-[#8B9A7D]">${initials}</div>
                    <div>
                        <div class="font-medium text-[#2C2C2C]">${name}</div>
                        <div class="text-sm text-[#2C2C2C]/60">${role || 'Client'}</div>
                    </div>
                </div>
            `;
            
            // Add to beginning of reviews container
            const container = document.getElementById('reviews-container');
            container.insertBefore(newReview, container.firstChild);
            
            // Scroll to new review
            container.scrollTo({ left: 0, behavior: 'smooth' });
            
            // Hide form and show success message
            this.style.display = 'none';
            document.getElementById('successMessage').classList.remove('hidden');
            
            // Reset form after 3 seconds
            setTimeout(() => {
                this.reset();
                this.style.display = 'block';
                document.getElementById('successMessage').classList.add('hidden');
            }, 3000);
        });

        // Auto-scroll reviews periodically
        let autoScrollInterval;
        const reviewsContainer = document.getElementById('reviews-container');
        
        function startAutoScroll() {
            autoScrollInterval = setInterval(() => {
                if (reviewsContainer.scrollLeft + reviewsContainer.clientWidth >= reviewsContainer.scrollWidth) {
                    reviewsContainer.scrollTo({ left: 0, behavior: 'smooth' });
                } else {
                    reviewsContainer.scrollBy({ left: 400, behavior: 'smooth' });
                }
            }, 5000);
        }
        
        function stopAutoScroll() {
            clearInterval(autoScrollInterval);
        }
        
        reviewsContainer.addEventListener('mouseenter', stopAutoScroll);
        reviewsContainer.addEventListener('mouseleave', startAutoScroll);
        
        // Start auto-scroll on load
        startAutoScroll();
    </script>
</body>
</html>
