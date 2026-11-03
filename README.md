<!DOCTYPE html>
<html lang="pt-BR" class="dark scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AURA VELOCE | Showroom Premium & Superesportivos</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Plus Jakarta Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        gold: {
                            400: '#FACC15',
                            500: '#EAB308',
                            600: '#CA8A04',
                            700: '#A16207',
                        },
                        dark: {
                            950: '#07090E',
                            900: '#0D1117',
                            850: '#121824',
                            800: '#1C2536',
                            700: '#2A364F'
                        }
                    },
                    boxShadow: {
                        'glow-gold': '0 0 25px -5px rgba(234, 179, 8, 0.3)',
                        'glow-cyan': '0 0 25px -5px rgba(6, 182, 212, 0.3)',
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #07090E;
        }
        ::-webkit-scrollbar-thumb {
            background: #1C2536;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #CA8A04;
        }
        
        .glass-card {
            background: rgba(13, 17, 23, 0.75);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.07);
        }
        
        .glass-nav {
            background: rgba(7, 9, 14, 0.85);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }

        .gold-gradient-text {
            background: linear-gradient(135deg, #FFE885 0%, #EAB308 50%, #9A6A00 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gold-gradient-bg {
            background: linear-gradient(135deg, #FACC15 0%, #CA8A04 100%);
        }
    </style>
</head>
<body class="bg-dark-950 text-slate-100 font-sans antialiased selection:bg-gold-500 selection:text-black min-h-screen flex flex-col justify-between">

    <!-- Toast Notification Overlay -->
    <div id="toast-container" class="fixed top-24 right-5 z-50 flex flex-col gap-3 pointer-events-none"></div>

    <!-- HEADER / NAVIGATION -->
    <header class="fixed top-0 left-0 w-full z-40 glass-nav transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Brand Logo -->
            <a href="#" class="flex items-center gap-3 group">
                <div class="w-10 h-10 rounded-xl gold-gradient-bg flex items-center justify-center text-black font-extrabold text-xl shadow-glow-gold group-hover:scale-105 transition-transform">
                    A
                </div>
                <div>
                    <span class="text-xl font-black tracking-wider text-white block leading-none">AURA <span class="gold-gradient-text">VELOCE</span></span>
                    <span class="text-[10px] tracking-[0.25em] text-slate-400 font-semibold uppercase">Exotic & Luxury</span>
                </div>
            </a>

            <!-- Nav Links Desktop -->
            <nav class="hidden md:flex items-center space-x-8 text-sm font-medium text-slate-300">
                <a href="#hero" class="hover:text-gold-400 transition-colors">Início</a>
                <a href="#showroom" class="hover:text-gold-400 transition-colors">Showroom</a>
                <a href="#simulador" class="hover:text-gold-400 transition-colors">Simulador</a>
                <a href="#diferenciais" class="hover:text-gold-400 transition-colors">Diferenciais</a>
                <a href="#agendamento" class="hover:text-gold-400 transition-colors">Test Drive</a>
            </nav>

            <!-- Header Actions -->
            <div class="hidden lg:flex items-center space-x-4">
                <!-- Search Input in Header -->
                <div class="relative">
                    <input type="text" id="header-search" placeholder="Buscar modelo..." 
                        class="bg-dark-900 border border-slate-800 rounded-full py-2 pl-9 pr-4 text-xs text-slate-200 placeholder-slate-500 focus:outline-none focus:border-gold-500 w-44 focus:w-60 transition-all">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-2.5 text-slate-500 text-xs"></i>
                </div>

                <!-- Favorites Badge Button -->
                <button onclick="scrollToShowroomWithFavorites()" class="relative p-2.5 rounded-full bg-dark-900 border border-slate-800 text-slate-300 hover:text-gold-400 transition-colors" title="Ver Favoritos">
                    <i class="fa-solid fa-heart"></i>
                    <span id="fav-count" class="absolute -top-1 -right-1 bg-gold-500 text-black font-bold text-[10px] w-5 h-5 rounded-full flex items-center justify-center">0</span>
                </button>

                <!-- CTA Button -->
                <a href="#agendamento" class="gold-gradient-bg text-black font-bold text-xs uppercase px-5 py-2.5 rounded-full hover:opacity-90 transition-opacity shadow-glow-gold">
                    Agendar Visita
                </a>
            </div>

            <!-- Mobile Menu Toggle Button -->
            <div class="md:hidden flex items-center gap-3">
                <button id="mobile-menu-btn" class="text-slate-300 text-2xl p-2 focus:outline-none">
                    <i class="fa-solid fa-bars"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Drawer -->
        <div id="mobile-menu" class="hidden md:hidden bg-dark-900/95 backdrop-blur-xl border-b border-slate-800 px-6 py-6 space-y-4">
            <input type="text" id="header-search-mobile" placeholder="Buscar modelo exótico..." 
                class="w-full bg-dark-850 border border-slate-800 rounded-lg py-2.5 px-4 text-sm text-slate-200 placeholder-slate-500 focus:outline-none focus:border-gold-500 mb-2">
            <a href="#hero" class="block text-slate-300 hover:text-gold-400 text-base font-medium py-1">Início</a>
            <a href="#showroom" class="block text-slate-300 hover:text-gold-400 text-base font-medium py-1">Showroom</a>
            <a href="#simulador" class="block text-slate-300 hover:text-gold-400 text-base font-medium py-1">Simulador Financeiro</a>
            <a href="#diferenciais" class="block text-slate-300 hover:text-gold-400 text-base font-medium py-1">Diferenciais VIP</a>
            <a href="#agendamento" class="block text-slate-300 hover:text-gold-400 text-base font-medium py-1">Agendar Test Drive</a>
        </div>
    </header>

    <!-- HERO SECTION -->
    <section id="hero" class="relative min-h-screen flex items-center pt-24 pb-16 overflow-hidden bg-gradient-to-b from-dark-950 via-dark-900 to-dark-950">
        <!-- Background Ambient Glow & Radial Overlays -->
        <div class="absolute top-1/4 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-gold-500/10 rounded-full blur-[140px] pointer-events-none"></div>
        <div class="absolute bottom-10 right-10 w-[400px] h-[400px] bg-cyan-500/10 rounded-full blur-[120px] pointer-events-none"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                <!-- Hero Left Content -->
                <div class="lg:col-span-7 space-y-6">
                    <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-slate-900/80 border border-gold-500/30 text-gold-400 text-xs font-semibold uppercase tracking-wider">
                        <span class="w-2 h-2 rounded-full bg-gold-400 animate-ping"></span>
                        Coleção Exclusiva 2026
                    </div>
                    
                    <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight text-white leading-[1.1]">
                        A Engenharia do Desejo em <span class="gold-gradient-text">Sua Forma Pura.</span>
                    </h1>
                    
                    <p class="text-slate-400 text-base sm:text-lg max-w-2xl font-light leading-relaxed">
                        Curadoria rigorosa dos mais cobiçados superesportivos e elétricos de alta performance do planeta. Entrega nacional com procedência 100% verificada.
                    </p>

                    <!-- Hero Call-to-Actions -->
                    <div class="flex flex-wrap gap-4 pt-2">
                        <a href="#showroom" class="gold-gradient-bg text-black font-extrabold text-sm uppercase px-8 py-4 rounded-full hover:shadow-glow-gold hover:scale-105 transition-all duration-300 flex items-center gap-3">
                            <span>Explorar Acervo</span>
                            <i class="fa-solid fa-arrow-right"></i>
                        </a>
                        <a href="#simulador" class="glass-card text-slate-200 hover:text-white font-bold text-sm uppercase px-8 py-4 rounded-full border border-slate-700 hover:border-gold-500/50 transition-all flex items-center gap-3">
                            <i class="fa-solid fa-calculator text-gold-400"></i>
                            <span>Simular Financiamento</span>
                        </a>
                    </div>

                    <!-- Key Stats Metrics -->
                    <div class="grid grid-cols-3 gap-4 pt-8 border-t border-slate-800/80">
                        <div>
                            <div class="text-2xl sm:text-3xl font-extrabold text-white">100%</div>
                            <div class="text-xs text-slate-400 mt-1">Procedência Certificada</div>
                        </div>
                        <div>
                            <div class="text-2xl sm:text-3xl font-extrabold gold-gradient-text">+1.000cv</div>
                            <div class="text-xs text-slate-400 mt-1">Projetos Customizados</div>
                        </div>
                        <div>
                            <div class="text-2xl sm:text-3xl font-extrabold text-white">VIP 24h</div>
                            <div class="text-xs text-slate-400 mt-1">Concierge & Entrega</div>
                        </div>
                    </div>
                </div>

                <!-- Hero Right Card Showcase -->
                <div class="lg:col-span-5 relative">
                    <div class="relative rounded-3xl overflow-hidden glass-card p-2 border border-slate-800 shadow-2xl group">
                        <!-- Hero Highlight Car Image -->
                        <div class="relative h-80 sm:h-96 rounded-2xl overflow-hidden bg-slate-900">
                            <img src="https://images.unsplash.com/photo-1614162692292-7ac56d7f7f1e?auto=format&fit=crop&w=1200&q=80" 
                                 alt="Porsche 911 GT3 RS" 
                                 class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
                            <div class="absolute inset-0 bg-gradient-to-t from-dark-950 via-transparent to-transparent"></div>
                            
                            <!-- Floating Specs Badge -->
                            <div class="absolute top-4 left-4 bg-black/60 backdrop-blur-md border border-white/10 px-3 py-1.5 rounded-xl text-xs font-semibold text-white flex items-center gap-2">
                                <i class="fa-solid fa-bolt text-gold-400"></i> Destaque da Semana
                            </div>

                            <div class="absolute bottom-4 left-4 right-4 text-white">
                                <span class="text-xs text-gold-400 font-bold uppercase tracking-widest">Porsche</span>
                                <h3 class="text-2xl font-bold leading-tight">911 GT3 RS (2024)</h3>
                                <div class="flex items-center justify-between mt-2 pt-2 border-t border-white/10 text-xs text-slate-300">
                                    <span><i class="fa-solid fa-gauge-high text-gold-400 mr-1"></i> 525 cv</span>
                                    <span><i class="fa-solid fa-stopwatch text-gold-400 mr-1"></i> 0-100: 3.2s</span>
                                    <span class="font-bold text-white text-sm">R$ 2.450.000</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- HIGHLIGHT TICKER -->
    <div class="bg-dark-900 border-y border-slate-800 py-4 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 flex justify-between items-center text-xs font-semibold uppercase tracking-widest text-slate-400 gap-8 flex-wrap">
            <div class="flex items-center gap-2"><i class="fa-solid fa-shield-halved text-gold-500"></i> Laudo Cautelar 100% Aprovado</div>
            <div class="flex items-center gap-2"><i class="fa-solid fa-truck-fast text-gold-500"></i> Entrega Segura em Todo o Brasil</div>
            <div class="flex items-center gap-2"><i class="fa-solid fa-handshake-simple text-gold-500"></i> Garantia de Fábrica Extendida</div>
            <div class="flex items-center gap-2"><i class="fa-solid fa-gem text-gold-500"></i> Atendimento Privativo sob Agendamento</div>
        </div>
    </div>

    <!-- SHOWROOM / CATALOG SECTION -->
    <section id="showroom" class="py-20 bg-dark-950 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            
            <!-- Section Header -->
            <div class="flex flex-col md:flex-row md:items-end justify-between mb-10 gap-6">
                <div>
                    <span class="text-xs font-bold text-gold-400 uppercase tracking-widest block mb-2">Nosso Acervo Privado</span>
                    <h2 class="text-3xl sm:text-4xl font-extrabold text-white">Explore a Frota Premium</h2>
                </div>
                
                <!-- Search & Filters Toolbar -->
                <div class="flex flex-wrap items-center gap-3">
                    <!-- Search Input -->
                    <div class="relative flex-grow sm:flex-grow-0">
                        <input type="text" id="catalog-search" placeholder="Filtrar marca ou modelo..." 
                            class="bg-dark-900 border border-slate-800 rounded-xl py-2.5 pl-10 pr-4 text-sm text-slate-200 placeholder-slate-500 focus:outline-none focus:border-gold-500 w-full sm:w-64">
                        <i class="fa-solid fa-search absolute left-3.5 top-3.5 text-slate-500 text-sm"></i>
                    </div>

                    <!-- Sort Select -->
                    <select id="sort-select" class="bg-dark-900 border border-slate-800 rounded-xl py-2.5 px-4 text-sm text-slate-300 focus:outline-none focus:border-gold-500 cursor-pointer">
                        <option value="default">Ordenar por: Relevância</option>
                        <option value="price-asc">Menor Preço</option>
                        <option value="price-desc">Maior Preço</option>
                        <option value="power-desc">Maior Potência (cv)</option>
                    </select>
                </div>
            </div>

            <!-- Category Pills -->
            <div class="flex items-center gap-2 overflow-x-auto pb-4 mb-8 scrollbar-none" id="category-pills">
                <button data-category="all" class="category-btn active px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-gold-500 text-black shadow-glow-gold">
                    Todos os Veículos
                </button>
                <button data-category="Esportivos" class="category-btn px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-dark-900 text-slate-400 hover:text-white border border-slate-800 hover:border-slate-700">
                    Superesportivos
                </button>
                <button data-category="Elétricos" class="category-btn px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-dark-900 text-slate-400 hover:text-white border border-slate-800 hover:border-slate-700">
                    Elétricos & Híbridos
                </button>
                <button data-category="SUVs" class="category-btn px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-dark-900 text-slate-400 hover:text-white border border-slate-800 hover:border-slate-700">
                    SUVs Premium
                </button>
                <button data-category="Sedans" class="category-btn px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-dark-900 text-slate-400 hover:text-white border border-slate-800 hover:border-slate-700">
                    Sedans de Luxo
                </button>
                <button data-category="favs" class="category-btn px-5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider transition-all bg-dark-900 text-slate-400 hover:text-gold-400 border border-slate-800 hover:border-gold-500/40 flex items-center gap-1.5">
                    <i class="fa-solid fa-heart text-xs"></i> Meus Favoritos
                </button>
            </div>

            <!-- Car Cards Grid -->
            <div id="car-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Dynamic Content Injected via JS -->
            </div>

            <!-- Empty State Message -->
            <div id="empty-state" class="hidden text-center py-16 glass-card rounded-3xl my-8">
                <i class="fa-solid fa-car-rear text-5xl text-slate-700 mb-4"></i>
                <h3 class="text-xl font-bold text-white mb-2">Nenhum veículo encontrado</h3>
                <p class="text-slate-400 text-sm max-w-md mx-auto">Tente ajustar seus termos de busca ou filtros selecionados para encontrar o modelo ideal.</p>
                <button onclick="resetFilters()" class="mt-6 px-6 py-2.5 bg-dark-800 text-gold-400 border border-gold-500/30 rounded-full text-xs font-bold uppercase hover:bg-gold-500 hover:text-black transition-all">Limpar Filtros</button>
            </div>
        </div>
    </section>

    <!-- VEHICLE TECHNICAL SPECS MODAL -->
    <div id="car-modal" class="fixed inset-0 z-50 hidden flex items-center justify-center p-4 bg-black/80 backdrop-blur-md">
        <div class="glass-card bg-dark-900 rounded-3xl max-w-4xl w-full max-h-[90vh] overflow-y-auto border border-slate-800 shadow-2xl relative">
            <!-- Close Button -->
            <button onclick="closeModal()" class="absolute top-4 right-4 z-20 w-10 h-10 rounded-full bg-black/60 text-slate-300 hover:text-white flex items-center justify-center border border-white/10 hover:border-gold-500 transition-colors">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <div id="modal-content" class="p-6 sm:p-8">
                <!-- Injected dynamically -->
            </div>
        </div>
    </div>

    <!-- FINANCING SIMULATOR SECTION -->
    <section id="simulador" class="py-20 bg-dark-900 border-y border-slate-800/80 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <span class="text-xs font-bold text-gold-400 uppercase tracking-widest block mb-2">Planejamento Exclusivo</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white">Simulador de Financiamento VIP</h2>
                <p class="text-slate-400 text-sm mt-3">Calcule as parcelas do seu próximo superesportiva com taxas personalizadas de private banking.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-center">
                <!-- Controls Form -->
                <div class="lg:col-span-7 glass-card p-6 sm:p-8 rounded-3xl space-y-6">
                    <!-- Vehicle Selection -->
                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Selecione o Modelo</label>
                        <select id="sim-car-select" class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3 text-slate-200 text-sm focus:outline-none focus:border-gold-500">
                            <!-- Injected dynamically -->
                        </select>
                    </div>

                    <!-- Custom Vehicle Price Input -->
                    <div>
                        <div class="flex justify-between text-xs font-bold mb-2">
                            <span class="text-slate-300 uppercase tracking-wider">Valor do Veículo</span>
                            <span id="sim-price-display" class="text-gold-400">R$ 1.000.000</span>
                        </div>
                        <input type="range" id="sim-price-range" min="300000" max="5000000" step="50000" value="1200000" 
                            class="w-full accent-gold-500 bg-slate-800 h-2 rounded-lg cursor-pointer">
                    </div>

                    <!-- Down Payment Slider -->
                    <div>
                        <div class="flex justify-between text-xs font-bold mb-2">
                            <span class="text-slate-300 uppercase tracking-wider">Entrada (<span id="sim-entry-percent">30</span>%)</span>
                            <span id="sim-entry-val" class="text-gold-400">R$ 360.000</span>
                        </div>
                        <input type="range" id="sim-entry-range" min="10" max="80" step="5" value="30" 
                            class="w-full accent-gold-500 bg-slate-800 h-2 rounded-lg cursor-pointer">
                    </div>

                    <!-- Installments Select -->
                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Prazo de Financiamento</label>
                        <div class="grid grid-cols-4 gap-3" id="sim-terms-container">
                            <button data-months="12" class="term-btn py-2.5 rounded-xl border border-slate-800 bg-dark-850 text-xs font-bold text-slate-300 hover:border-gold-500">12x</button>
                            <button data-months="24" class="term-btn py-2.5 rounded-xl border border-slate-800 bg-dark-850 text-xs font-bold text-slate-300 hover:border-gold-500">24x</button>
                            <button data-months="36" class="term-btn active py-2.5 rounded-xl border border-gold-500 bg-gold-500 text-black font-extrabold text-xs">36x</button>
                            <button data-months="48" class="term-btn py-2.5 rounded-xl border border-slate-800 bg-dark-850 text-xs font-bold text-slate-300 hover:border-gold-500">48x</button>
                        </div>
                    </div>
                </div>

                <!-- Simulation Result Summary -->
                <div class="lg:col-span-5 bg-gradient-to-br from-dark-850 to-dark-950 p-8 rounded-3xl border border-gold-500/20 shadow-glow-gold space-y-6">
                    <h3 class="text-lg font-bold text-white border-b border-slate-800 pb-4">Resumo da Simulação</h3>

                    <div class="space-y-3 text-sm">
                        <div class="flex justify-between text-slate-400">
                            <span>Valor Total do Veículo:</span>
                            <span id="summary-total" class="text-white font-medium">R$ 1.200.000</span>
                        </div>
                        <div class="flex justify-between text-slate-400">
                            <span>Valor da Entrada:</span>
                            <span id="summary-entry" class="text-white font-medium">R$ 360.000</span>
                        </div>
                        <div class="flex justify-between text-slate-400">
                            <span>Saldo a Financiar:</span>
                            <span id="summary-financed" class="text-white font-medium">R$ 840.000</span>
                        </div>
                        <div class="flex justify-between text-slate-400">
                            <span>Taxa Est. A.M.:</span>
                            <span class="text-gold-400 font-medium">0,99% a.m. (Private)</span>
                        </div>
                    </div>

                    <div class="pt-4 border-t border-slate-800 text-center">
                        <span class="text-xs uppercase text-slate-400 font-bold tracking-wider">Parcela Mensal Estimada</span>
                        <div id="summary-monthly" class="text-3xl sm:text-4xl font-black gold-gradient-text mt-1">R$ 27.850,00</div>
                        <span class="text-[10px] text-slate-500 block mt-1">*Sujeito a aprovação de crédito pelas instituições parceiras.</span>
                    </div>

                    <button onclick="applyFinancingProposal()" class="w-full py-4 gold-gradient-bg text-black font-extrabold text-xs uppercase tracking-wider rounded-xl hover:opacity-90 transition-opacity">
                        Solicitar Análise de Crédito
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- DIFFERENTIALS / VIP EXPERIENCE -->
    <section id="diferenciais" class="py-20 bg-dark-950">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16">
                <span class="text-xs font-bold text-gold-400 uppercase tracking-widest block mb-2">Por Que A AURA VELOCE</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white">Atendimento em Nível Global</h2>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="glass-card p-8 rounded-3xl border border-slate-800 hover:border-gold-500/40 transition-all group">
                    <div class="w-14 h-14 rounded-2xl bg-gold-500/10 border border-gold-500/20 text-gold-400 flex items-center justify-center text-2xl mb-6 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-shield-virus"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white mb-3">Inspeção em 150 Pontos</h3>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Cada veículo do acervo passa por rigoroso processo de auditoria mecânica, eletrônica e laudo cautelar de estrutura.
                    </p>
                </div>

                <div class="glass-card p-8 rounded-3xl border border-slate-800 hover:border-gold-500/40 transition-all group">
                    <div class="w-14 h-14 rounded-2xl bg-gold-500/10 border border-gold-500/20 text-gold-400 flex items-center justify-center text-2xl mb-6 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-truck-ramp-box"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white mb-3">Transporte Fechado VIP</h3>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Entregamos seu superesportivo em caminhão sider/plataforma totalmente fechado diretamente na sua residência.
                    </p>
                </div>

                <div class="glass-card p-8 rounded-3xl border border-slate-800 hover:border-gold-500/40 transition-all group">
                    <div class="w-14 h-14 rounded-2xl bg-gold-500/10 border border-gold-500/20 text-gold-400 flex items-center justify-center text-2xl mb-6 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-user-gear"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white mb-3">Concierge Dedicado</h3>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Atendimento exclusivo para customizações de PPF, blindagem com certificação alemã e emplacamento imediato.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- TEST DRIVE & BOOKING FORM -->
    <section id="agendamento" class="py-20 bg-dark-900 border-t border-slate-800 relative">
        <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="glass-card rounded-3xl p-8 sm:p-12 border border-slate-800 shadow-2xl relative overflow-hidden">
                <div class="absolute -right-20 -bottom-20 w-80 h-80 bg-gold-500/10 rounded-full blur-3xl pointer-events-none"></div>

                <div class="max-w-2xl">
                    <span class="text-xs font-bold text-gold-400 uppercase tracking-widest block mb-2">Experiência Sensorial</span>
                    <h2 class="text-3xl sm:text-4xl font-extrabold text-white mb-4">Agende Seu Test Drive Privativo</h2>
                    <p class="text-slate-400 text-sm mb-8">Vivencie a emoção de pilotar um dos veículos mais potentes do planeta. Agendamento com atendimento individual em nossas suítes VIP.</p>
                </div>

                <form id="test-drive-form" onsubmit="handleTestDriveSubmit(event)" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Nome Completo *</label>
                        <input type="text" required placeholder="Ex: Roberto Silva" 
                            class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 placeholder-slate-600 focus:outline-none focus:border-gold-500">
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">E-mail Corporativo *</label>
                        <input type="email" required placeholder="roberto@empresa.com.br" 
                            class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 placeholder-slate-600 focus:outline-none focus:border-gold-500">
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Telefone / WhatsApp *</label>
                        <input type="tel" required placeholder="(11) 99999-8888" 
                            class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 placeholder-slate-600 focus:outline-none focus:border-gold-500">
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Modelo Desejado *</label>
                        <select id="td-car-select" required class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 focus:outline-none focus:border-gold-500">
                            <!-- Injected dynamically -->
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Data Preferencial *</label>
                        <input type="date" required 
                            class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 focus:outline-none focus:border-gold-500">
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-slate-300 uppercase tracking-wider mb-2">Unidade de Atendimento *</label>
                        <select required class="w-full bg-dark-850 border border-slate-800 rounded-xl p-3.5 text-sm text-slate-200 focus:outline-none focus:border-gold-500">
                            <option value="sp-europa">São Paulo - Av. Europa</option>
                            <option value="rj-barra">Rio de Janeiro - Barra da Tijuca</option>
                            <option value="curitiba">Curitiba - Batel</option>
                            <option value="bh">Belo Horizonte - Lourdes</option>
                        </select>
                    </div>

                    <div class="md:col-span-2 pt-2">
                        <button type="submit" class="w-full py-4 gold-gradient-bg text-black font-extrabold text-xs uppercase tracking-wider rounded-xl hover:shadow-glow-gold hover:opacity-95 transition-all">
                            Confirmar Solicitação de Test Drive
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-dark-950 border-t border-slate-800/80 pt-16 pb-8 text-slate-400 text-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-10 mb-12">
                <!-- Col 1: Brand Info -->
                <div class="space-y-4">
                    <div class="flex items-center gap-3">
                        <div class="w-8 h-8 rounded-lg gold-gradient-bg flex items-center justify-center text-black font-black text-base">A</div>
                        <span class="text-lg font-black tracking-wider text-white">AURA <span class="gold-gradient-text">VELOCE</span></span>
                    </div>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Líder nacional na comercialização e importação direta de superesportivos, hypercars e veículos de luxo.
                    </p>
                    <div class="flex space-x-3 text-slate-300">
                        <a href="#" class="w-9 h-9 rounded-full bg-dark-900 border border-slate-800 flex items-center justify-center hover:text-gold-400 hover:border-gold-500 transition-colors"><i class="fa-brands fa-instagram"></i></a>
                        <a href="#" class="w-9 h-9 rounded-full bg-dark-900 border border-slate-800 flex items-center justify-center hover:text-gold-400 hover:border-gold-500 transition-colors"><i class="fa-brands fa-youtube"></i></a>
                        <a href="#" class="w-9 h-9 rounded-full bg-dark-900 border border-slate-800 flex items-center justify-center hover:text-gold-400 hover:border-gold-500 transition-colors"><i class="fa-brands fa-whatsapp"></i></a>
                    </div>
                </div>

                <!-- Col 2: Navigation -->
                <div>
                    <h4 class="text-white font-bold text-xs uppercase tracking-wider mb-4">Navegação</h4>
                    <ul class="space-y-2.5 text-xs">
                        <li><a href="#hero" class="hover:text-gold-400 transition-colors">Início</a></li>
                        <li><a href="#showroom" class="hover:text-gold-400 transition-colors">Showroom Completo</a></li>
                        <li><a href="#simulador" class="hover:text-gold-400 transition-colors">Simulador de Crédito</a></li>
                        <li><a href="#agendamento" class="hover:text-gold-400 transition-colors">Agendar Test Drive</a></li>
                    </ul>
                </div>

                <!-- Col 3: Categories -->
                <div>
                    <h4 class="text-white font-bold text-xs uppercase tracking-wider mb-4">Categorias</h4>
                    <ul class="space-y-2.5 text-xs">
                        <li><a href="#showroom" onclick="filterByCategory('Esportivos')" class="hover:text-gold-400 transition-colors">Superesportivos</a></li>
                        <li><a href="#showroom" onclick="filterByCategory('Elétricos')" class="hover:text-gold-400 transition-colors">Veículos Elétricos</a></li>
                        <li><a href="#showroom" onclick="filterByCategory('SUVs')" class="hover:text-gold-400 transition-colors">SUVs de Luxo</a></li>
                        <li><a href="#showroom" onclick="filterByCategory('Sedans')" class="hover:text-gold-400 transition-colors">Sedans Executivos</a></li>
                    </ul>
                </div>

                <!-- Col 4: Contact -->
                <div>
                    <h4 class="text-white font-bold text-xs uppercase tracking-wider mb-4">Showroom Flagship</h4>
                    <ul class="space-y-2.5 text-xs text-slate-400">
                        <li><i class="fa-solid fa-location-dot text-gold-400 mr-2"></i> Av. Europa, 850 - Jardins, SP</li>
                        <li><i class="fa-solid fa-phone text-gold-400 mr-2"></i> +55 (11) 3090-0000</li>
                        <li><i class="fa-solid fa-envelope text-gold-400 mr-2"></i> contato@auraveloce.com.br</li>
                        <li><i class="fa-solid fa-clock text-gold-400 mr-2"></i> Seg a Sáb: 09h às 19h</li>
                    </ul>
                </div>
            </div>

            <div class="border-t border-slate-800/80 pt-6 flex flex-col md:flex-row justify-between items-center text-xs text-slate-500 gap-4">
                <p>&copy; 2026 AURA VELOCE Motors. Todos os direitos reservados.</p>
                <div class="flex space-x-6">
                    <a href="#" class="hover:text-slate-300">Termos de Privacidade</a>
                    <a href="#" class="hover:text-slate-300">Políticas de Compliance</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- JAVASCRIPT LOGIC & VEHICLE DATABASE -->
    <script>
        // CAR VEHICLE DATABASE
        const carsData = [
            {
                id: 1,
                brand: "Porsche",
                model: "911 GT3 RS",
                year: "2024",
                category: "Esportivos",
                price: 2450000,
                hp: 525,
                acceleration: "3.2s",
                topSpeed: "296 km/h",
                engine: "4.0 V6 Boxer Aspirado",
                transmission: "PDK 7 marchas",
                drive: "Traseira (RWD)",
                fuel: "Gasolina",
                image: "https://images.unsplash.com/photo-1614162692292-7ac56d7f7f1e?auto=format&fit=crop&w=1000&q=80",
                badge: "Superesportivos",
                gallery: [
                    "https://images.unsplash.com/photo-1614162692292-7ac56d7f7f1e?auto=format&fit=crop&w=1000&q=80",
                    "https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "O auge da aerodinâmica da Porsche. Sistema DRS ativo, pacote Weissach e suspensão adaptável ajustável diretamente no volante."
            },
            {
                id: 2,
                brand: "Audi",
                model: "RS e-tron GT",
                year: "2024",
                category: "Elétricos",
                price: 1099000,
                hp: 646,
                acceleration: "3.3s",
                topSpeed: "250 km/h",
                engine: "100% Elétrico (Dual Motor)",
                transmission: "Automática 2 marchas",
                drive: "Integral quattro",
                fuel: "Elétrico (472 km Autonomia)",
                image: "https://images.unsplash.com/photo-1617814076367-b759c7d7e738?auto=format&fit=crop&w=1000&q=80",
                badge: "Elétrico",
                gallery: [
                    "https://images.unsplash.com/photo-1617814076367-b759c7d7e738?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "O Gran Turismo elétrico definitivo. Recarga ultrarrápida de 800V de 5 a 80% em apenas 22.5 minutos."
            },
            {
                id: 3,
                brand: "Lamborghini",
                model: "Huracán Sterrato",
                year: "2023",
                category: "Esportivos",
                price: 4200000,
                hp: 610,
                acceleration: "3.4s",
                topSpeed: "260 km/h",
                engine: "5.2 V10 Aspirado",
                transmission: "LDF 7 marchas",
                drive: "Integral AWD",
                fuel: "Gasolina",
                image: "https://images.unsplash.com/photo-1544829099-b9a0c07fad1a?auto=format&fit=crop&w=1000&q=80",
                badge: "Edição Limitada",
                gallery: [
                    "https://images.unsplash.com/photo-1544829099-b9a0c07fad1a?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "A empolgação de um V10 superesportiva projetado para dominar o asfalto e superfícies de baixa aderência com suspensão elevada."
            },
            {
                id: 4,
                brand: "BMW",
                model: "i7 xDrive60 M Sport",
                year: "2024",
                category: "Sedans",
                price: 1320000,
                hp: 544,
                acceleration: "4.7s",
                topSpeed: "240 km/h",
                engine: "100% Elétrico eDrive",
                transmission: "Automática",
                drive: "Integral xDrive",
                fuel: "Elétrico (625 km Autonomia)",
                image: "https://images.unsplash.com/photo-1555215695-3004980ad54e?auto=format&fit=crop&w=1000&q=80",
                badge: "Luxo Executivo",
                gallery: [
                    "https://images.unsplash.com/photo-1555215695-3004980ad54e?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "Sedan de representação máximo. Equipado com BMW Theatre Screen de 31.3 polegadas em 8K e portas de abertura automática."
            },
            {
                id: 5,
                brand: "Land Rover",
                model: "Range Rover SV Edition",
                year: "2024",
                category: "SUVs",
                price: 1650000,
                hp: 635,
                acceleration: "3.8s",
                topSpeed: "290 km/h",
                engine: "4.4 V8 Twin-Turbo Mild-Hybrid",
                transmission: "ZF 8 marchas",
                drive: "Integral Terrain Response 2",
                fuel: "Gasolina / Híbrido Leve",
                image: "https://images.unsplash.com/photo-1563720223185-11003d516935?auto=format&fit=crop&w=1000&q=80",
                badge: "SUV Premium",
                gallery: [
                    "https://images.unsplash.com/photo-1563720223185-11003d516935?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "A máxima expressão de requinte e performance off-road. Acabamento interno com detalhes em cerâmica artesanal e couro semi-anilina."
            },
            {
                id: 6,
                brand: "Mercedes-AMG",
                model: "GT 63 S E Performance",
                year: "2024",
                category: "Sedans",
                price: 1850000,
                hp: 843,
                acceleration: "2.9s",
                topSpeed: "316 km/h",
                engine: "4.0 V8 BiTurbo Híbrido Plug-in",
                transmission: "AMG SPEEDSHIFT 9G",
                drive: "AMG Performance 4MATIC+",
                fuel: "Híbrido Plug-in",
                image: "https://images.unsplash.com/photo-1618843479313-40f8afb4b4d8?auto=format&fit=crop&w=1000&q=80",
                badge: "843cv V8",
                gallery: [
                    "https://images.unsplash.com/photo-1618843479313-40f8afb4b4d8?auto=format&fit=crop&w=1000&q=80"
                ],
                description: "Tecnologia derivada diretamente da Fórmula 1. Motor V8 combinado a um motor elétrico de altíssimo rendimento no eixo traseiro."
            }
        ];

        // STATE MANAGEMENT
        let activeCategory = 'all';
        let searchQuery = '';
        let sortBy = 'default';
        let favorites = new Set();
        let selectedTermMonths = 36;

        // INITIALIZATION
        document.addEventListener('DOMContentLoaded', () => {
            renderCars();
            populateSelectOptions();
            setupEventListeners();
            updateSimulation();
        });

        // RENDER CAR CARDS
        function renderCars() {
            const grid = document.getElementById('car-grid');
            const emptyState = document.getElementById('empty-state');
            grid.innerHTML = '';

            let filtered = carsData.filter(car => {
                const matchesCategory = activeCategory === 'all' 
                    || (activeCategory === 'favs' ? favorites.has(car.id) : car.category === activeCategory);
                
                const matchesSearch = (car.brand + " " + car.model + " " + car.category)
                    .toLowerCase()
                    .includes(searchQuery.toLowerCase());

                return matchesCategory && matchesSearch;
            });

            // Sorting
            if (sortBy === 'price-asc') {
                filtered.sort((a, b) => a.price - b.price);
            } else if (sortBy === 'price-desc') {
                filtered.sort((a, b) => b.price - a.price);
            } else if (sortBy === 'power-desc') {
                filtered.sort((a, b) => b.hp - a.hp);
            }

            if (filtered.length === 0) {
                emptyState.classList.remove('hidden');
            } else {
                emptyState.classList.add('hidden');
                filtered.forEach(car => {
                    const isFav = favorites.has(car.id);
                    const formattedPrice = car.price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });
                    
                    const cardHTML = `
                        <div class="glass-card rounded-3xl overflow-hidden border border-slate-800 hover:border-gold-500/40 transition-all duration-300 hover:-translate-y-1.5 group flex flex-col justify-between">
                            <div>
                                <!-- Image Container -->
                                <div class="relative h-60 overflow-hidden bg-slate-900">
                                    <img src="${car.image}" alt="${car.brand} ${car.model}" 
                                         class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                                         onerror="this.src='https://placehold.co/800x600/0D1117/EAB308?text=${encodeURIComponent(car.model)}'">
                                    
                                    <div class="absolute inset-0 bg-gradient-to-t from-dark-900 via-transparent to-transparent"></div>
                                    
                                    <!-- Badge -->
                                    <span class="absolute top-4 left-4 bg-black/60 backdrop-blur-md border border-white/10 px-3 py-1 rounded-full text-[11px] font-bold text-slate-200">
                                        ${car.badge}
                                    </span>

                                    <!-- Favorite Button -->
                                    <button onclick="toggleFavorite(${car.id})" class="absolute top-4 right-4 w-9 h-9 rounded-full bg-black/60 backdrop-blur-md border border-white/10 flex items-center justify-center text-slate-300 hover:text-red-500 transition-colors">
                                        <i class="${isFav ? 'fa-solid text-red-500' : 'fa-regular'} fa-heart"></i>
                                    </button>

                                    <!-- Year Badge -->
                                    <span class="absolute bottom-3 right-4 text-xs font-semibold text-slate-400 bg-dark-950/80 px-2.5 py-1 rounded-md border border-slate-800">
                                        Ano ${car.year}
                                    </span>
                                </div>

                                <!-- Card Details Body -->
                                <div class="p-6">
                                    <span class="text-xs font-extrabold text-gold-400 uppercase tracking-widest">${car.brand}</span>
                                    <h3 class="text-xl font-bold text-white mb-4">${car.model}</h3>

                                    <!-- Key Performance Grid -->
                                    <div class="grid grid-cols-2 gap-2 text-xs bg-dark-850 p-3.5 rounded-2xl border border-slate-800/80 mb-5">
                                        <div class="text-slate-400">
                                            <i class="fa-solid fa-gauge-high text-gold-400 mr-1.5"></i> ${car.hp} cv
                                        </div>
                                        <div class="text-slate-400">
                                            <i class="fa-solid fa-stopwatch text-gold-400 mr-1.5"></i> 0-100: ${car.acceleration}
                                        </div>
                                        <div class="text-slate-400 col-span-2 truncate">
                                            <i class="fa-solid fa-engine text-gold-400 mr-1.5"></i> ${car.engine}
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <!-- Card Footer Action -->
                            <div class="px-6 pb-6 pt-0 flex items-center justify-between border-t border-slate-800/60 mt-auto pt-4">
                                <div>
                                    <span class="text-[10px] uppercase text-slate-500 font-bold block">Preço VIP</span>
                                    <span class="text-lg font-black text-white">${formattedPrice}</span>
                                </div>
                                <button onclick="openModal(${car.id})" class="px-4 py-2 bg-dark-800 hover:bg-gold-500 hover:text-black border border-slate-700 hover:border-gold-500 text-slate-200 text-xs font-bold rounded-xl transition-all">
                                    Ficha Técnica
                                </button>
                            </div>
                        </div>
                    `;
                    grid.innerHTML += cardHTML;
                });
            }
        }

        // EVENT LISTENERS & FILTERS
        function setupEventListeners() {
            // Category Buttons
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    document.querySelectorAll('.category-btn').forEach(b => {
                        b.classList.remove('bg-gold-500', 'text-black', 'shadow-glow-gold');
                        b.classList.add('bg-dark-900', 'text-slate-400');
                    });
                    
                    const target = e.currentTarget;
                    target.classList.remove('bg-dark-900', 'text-slate-400');
                    target.classList.add('bg-gold-500', 'text-black', 'shadow-glow-gold');

                    activeCategory = target.getAttribute('data-category');
                    renderCars();
                });
            });

            // Search Inputs
            const searchHandler = (e) => {
                searchQuery = e.target.value;
                renderCars();
            };

            document.getElementById('catalog-search').addEventListener('input', searchHandler);
            document.getElementById('header-search').addEventListener('input', (e) => {
                searchQuery = e.target.value;
                renderCars();
                document.getElementById('showroom').scrollIntoView({ behavior: 'smooth' });
            });
            document.getElementById('header-search-mobile').addEventListener('input', (e) => {
                searchQuery = e.target.value;
                renderCars();
                document.getElementById('showroom').scrollIntoView({ behavior: 'smooth' });
            });

            // Sort Selector
            document.getElementById('sort-select').addEventListener('change', (e) => {
                sortBy = e.target.value;
                renderCars();
            });

            // Mobile Navigation Toggle
            const mobileBtn = document.getElementById('mobile-menu-btn');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileBtn.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            // Simulator Controls
            document.getElementById('sim-car-select').addEventListener('change', (e) => {
                const selectedCar = carsData.find(c => c.id == e.target.value);
                if (selectedCar) {
                    document.getElementById('sim-price-range').value = selectedCar.price;
                    updateSimulation();
                }
            });

            document.getElementById('sim-price-range').addEventListener('input', updateSimulation);
            document.getElementById('sim-entry-range').addEventListener('input', updateSimulation);

            // Term Buttons
            document.querySelectorAll('.term-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    document.querySelectorAll('.term-btn').forEach(b => {
                        b.className = 'term-btn py-2.5 rounded-xl border border-slate-800 bg-dark-850 text-xs font-bold text-slate-300 hover:border-gold-500';
                    });
                    const target = e.currentTarget;
                    target.className = 'term-btn active py-2.5 rounded-xl border border-gold-500 bg-gold-500 text-black font-extrabold text-xs';
                    selectedTermMonths = parseInt(target.getAttribute('data-months'));
                    updateSimulation();
                });
            });
        }

        // FAVORITES TOGGLE
        function toggleFavorite(id) {
            if (favorites.has(id)) {
                favorites.delete(id);
                showToast('Veículo removido dos favoritos');
            } else {
                favorites.add(id);
                showToast('Veículo adicionado aos favoritos!', 'success');
            }
            document.getElementById('fav-count').innerText = favorites.size;
            renderCars();
        }

        function scrollToShowroomWithFavorites() {
            activeCategory = 'favs';
            renderCars();
            document.getElementById('showroom').scrollIntoView({ behavior: 'smooth' });
        }

        function resetFilters() {
            activeCategory = 'all';
            searchQuery = '';
            sortBy = 'default';
            document.getElementById('catalog-search').value = '';
            document.getElementById('header-search').value = '';
            document.getElementById('sort-select').value = 'default';
            renderCars();
        }

        // SIMULATOR CALCULATIONS
        function updateSimulation() {
            const price = parseFloat(document.getElementById('sim-price-range').value);
            const entryPercent = parseFloat(document.getElementById('sim-entry-range').value);

            const entryAmount = price * (entryPercent / 100);
            const financedAmount = price - entryAmount;

            // Interest rate ~0.99% per month
            const monthlyRate = 0.0099;
            const months = selectedTermMonths;

            // PMT Calculation Formula
            const monthlyPayment = (financedAmount * monthlyRate * Math.pow(1 + monthlyRate, months)) / (Math.pow(1 + monthlyRate, months) - 1);

            // DOM Updates
            document.getElementById('sim-price-display').innerText = price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });
            document.getElementById('sim-entry-percent').innerText = entryPercent;
            document.getElementById('sim-entry-val').innerText = entryAmount.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });

            document.getElementById('summary-total').innerText = price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });
            document.getElementById('summary-entry').innerText = entryAmount.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });
            document.getElementById('summary-financed').innerText = financedAmount.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });
            document.getElementById('summary-monthly').innerText = monthlyPayment.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 2 });
        }

        // POPULATE DROPDOWNS
        function populateSelectOptions() {
            const simSelect = document.getElementById('sim-car-select');
            const tdSelect = document.getElementById('td-car-select');
            
            simSelect.innerHTML = '';
            tdSelect.innerHTML = '';

            carsData.forEach(car => {
                const optText = `${car.brand} ${car.model} (${car.year}) - R$ ${car.price.toLocaleString('pt-BR')}`;
                simSelect.innerHTML += `<option value="${car.id}">${optText}</option>`;
                tdSelect.innerHTML += `<option value="${car.brand} ${car.model}">${car.brand} ${car.model}</option>`;
            });
        }

        // MODAL OPEN / CLOSE
        function openModal(id) {
            const car = carsData.find(c => c.id === id);
            if (!car) return;

            const modal = document.getElementById('car-modal');
            const content = document.getElementById('modal-content');

            const formattedPrice = car.price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', maximumFractionDigits: 0 });

            content.innerHTML = `
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div>
                        <div class="rounded-2xl overflow-hidden bg-slate-900 border border-slate-800 h-72">
                            <img id="modal-main-img" src="${car.image}" alt="${car.model}" class="w-full h-full object-cover">
                        </div>
                        <div class="flex gap-3 mt-4">
                            ${car.gallery.map(img => `
                                <button onclick="document.getElementById('modal-main-img').src='${img}'" class="w-20 h-16 rounded-xl overflow-hidden border border-slate-800 hover:border-gold-500">
                                    <img src="${img}" class="w-full h-full object-cover">
                                </button>
                            `).join('')}
                        </div>
                    </div>

                    <div class="space-y-4">
                        <div>
                            <span class="text-xs font-bold text-gold-400 uppercase tracking-widest">${car.brand}</span>
                            <h2 class="text-3xl font-extrabold text-white">${car.model}</h2>
                            <span class="text-2xl font-black text-white block mt-1">${formattedPrice}</span>
                        </div>

                        <p class="text-slate-400 text-xs leading-relaxed border-y border-slate-800 py-3">${car.description}</p>

                        <!-- Tech Specs Grid -->
                        <div class="grid grid-cols-2 gap-3 text-xs">
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Potência Max</span>
                                <span class="font-bold text-white text-sm">${car.hp} cv</span>
                            </div>
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Aceleração (0-100)</span>
                                <span class="font-bold text-white text-sm">${car.acceleration}</span>
                            </div>
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Velocidade Máxima</span>
                                <span class="font-bold text-white text-sm">${car.topSpeed}</span>
                            </div>
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Transmissão</span>
                                <span class="font-bold text-white text-sm">${car.transmission}</span>
                            </div>
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Tração</span>
                                <span class="font-bold text-white text-sm">${car.drive}</span>
                            </div>
                            <div class="bg-dark-850 p-3 rounded-xl border border-slate-800">
                                <span class="text-slate-500 block">Combustível</span>
                                <span class="font-bold text-white text-sm">${car.fuel}</span>
                            </div>
                        </div>

                        <div class="pt-4 flex gap-3">
                            <button onclick="bookCarFromModal('${car.brand} ${car.model}')" class="flex-1 py-3.5 gold-gradient-bg text-black font-extrabold text-xs uppercase tracking-wider rounded-xl hover:opacity-90 transition-opacity">
                                Agendar Test Drive
                            </button>
                        </div>
                    </div>
                </div>
            `;

            modal.classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }

        function closeModal() {
            const modal = document.getElementById('car-modal');
            modal.classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        function bookCarFromModal(carFullName) {
            closeModal();
            const select = document.getElementById('td-car-select');
            select.value = carFullName;
            document.getElementById('agendamento').scrollIntoView({ behavior: 'smooth' });
            showToast(`Modelo ${carFullName} selecionado no agendamento.`, 'info');
        }

        function applyFinancingProposal() {
            showToast('Proposta de financiamento enviada! Nosso consultor VIP entrará em contato.', 'success');
        }

        function handleTestDriveSubmit(event) {
            event.preventDefault();
            showToast('Test drive solicitado com sucesso! Confirmação enviada via WhatsApp.', 'success');
            event.target.reset();
        }

        // TOAST NOTIFICATION SYSTEM
        function showToast(message, type = 'info') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            
            const isSuccess = type === 'success';
            
            toast.className = `pointer-events-auto flex items-center gap-3 px-4 py-3 rounded-xl backdrop-blur-xl border text-xs font-bold shadow-2xl transition-all duration-300 opacity-0 translate-y-2 ${
                isSuccess 
                ? 'bg-dark-900/90 border-gold-500 text-gold-400' 
                : 'bg-dark-900/90 border-slate-700 text-slate-200'
            }`;

            toast.innerHTML = `
                <i class="fa-solid ${isSuccess ? 'fa-circle-check text-gold-400' : 'fa-circle-info text-cyan-400'} text-base"></i>
                <span>${message}</span>
            `;

            container.appendChild(toast);

            setTimeout(() => {
                toast.classList.remove('opacity-0', 'translate-y-2');
            }, 10);

            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 4000);
        }

        function filterByCategory(category) {
            activeCategory = category;
            renderCars();
        }
    </script>
</body>
</html>
