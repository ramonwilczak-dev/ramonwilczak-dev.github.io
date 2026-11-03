<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Cafuné — Cardápio Premium</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Lato:wght@300;400;700&display=swap" rel="stylesheet"/>
    <style>
        * { margin:0; padding:0; box-sizing:border-box; }
        html, body { width:100%; background:#F9F4F2; font-family:'Lato', sans-serif; color: #3D1A1A; scroll-behavior: smooth; }

        /* Navegação */
        nav { background:#7D2E2E; display:flex; align-items:center; justify-content:space-between; padding:0 4rem; height:70px; position:sticky; top:0; z-index:100; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        nav .logo { font-family:'Playfair Display', serif; color:#EFBCB0; font-size:26px; font-style:italic; letter-spacing:2px; text-decoration: none; }
        nav .nav-links { display:flex; gap:2rem; }
        nav .nav-links a { color:#F9F4F2; font-size:13px; letter-spacing:1px; text-transform:uppercase; text-decoration:none; opacity:0.8; transition: 0.3s; }
        nav .nav-links a:hover { opacity:1; color:#EFBCB0; }

        /* Banner de Destaque (Hero) */
        .hero { background:#7D2E2E; display:flex; align-items:center; justify-content:center; padding:4rem 6rem; min-height:500px; gap: 4rem; overflow: hidden; }
        .hero-text { max-width: 500px; }
        .hero-text .eyebrow { font-family:'Playfair Display', serif; font-style:italic; color:#EFBCB0; font-size:20px; margin-bottom:10px; }
        .hero-text h1 { font-family:'Playfair Display', serif; font-style:italic; color:#F9F4F2; font-size:72px; line-height:1; margin-bottom:20px; }
        .hero-text .subtitle { font-weight:700; color:#EFBCB0; font-size:12px; letter-spacing:4px; text-transform:uppercase; margin-bottom:30px; display: block; }
        .hero-price { display:inline-block; border: 2px solid #EFBCB0; color:#EFBCB0; font-weight:700; font-size:24px; padding:12px 30px; border-radius:50px; font-family:'Playfair Display', serif; }
        
        .hero-plate { position: relative; flex-shrink:0; }
        .hero-plate img { width: 450px; filter: drop-shadow(0 30px 40px rgba(0,0,0,0.4)); transform: rotate(-8deg); transition: transform 0.6s ease; }
        .hero-plate:hover img { transform: rotate(0deg) scale(1.05); }

        /* Seção do Cardápio */
        .container { max-width: 1200px; margin: 0 auto; padding: 5rem 2rem; }
        .section-header { text-align: center; margin-bottom: 4rem; }
        .section-header h2 { font-family:'Playfair Display', serif; font-size: 42px; color: #7D2E2E; margin-bottom: 10px; }
        .divider { width: 60px; height: 3px; background: #EFBCB0; margin: 0 auto; }

        /* Grid de Pratos */
        .menu-grid { display:grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }
        
        .card { background:#fff; border-radius:20px; overflow:hidden; border:1px solid #F0DDD9; transition: 0.4s ease; display: flex; flex-direction: column; }
        .card:hover { transform:translateY(-10px); box-shadow:0 20px 40px rgba(125,46,46,0.1); }
        
        .card-img-wrapper { width:100%; height:240px; background: #fdfaf9; display:flex; align-items:center; justify-content:center; overflow: hidden; }
        .card-img-wrapper img { width: 100%; height: 100%; object-fit: cover; transition: 0.8s; }
        .card:hover .card-img-wrapper img { transform: scale(1.1); }
        
        .card-content { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
        .card-tag { font-size:10px; font-weight:700; letter-spacing:2px; text-transform:uppercase; color:#D4837A; margin-bottom:8px; }
        .card-name { font-family:'Playfair Display', serif; font-size:22px; font-weight:700; color:#3D1A1A; margin-bottom:10px; }
        .card-desc { font-size:14px; color:#777; line-height:1.6; margin-bottom: 20px; flex-grow: 1; }
        
        .card-footer { display:flex; align-items:center; justify-content:space-between; padding-top: 15px; border-top: 1px solid #F9F4F2; }
        .card-price { font-family:'Playfair Display', serif; font-size:22px; font-weight:700; color:#7D2E2E; }
        .btn-order { background:#7D2E2E; color:#F9F4F2; padding:10px 20px; border-radius:8px; font-size:12px; font-weight:700; text-decoration: none; transition: 0.3s; }
        .btn-order:hover { background:#3D1A1A; }

        /* Rodapé */
        footer { background:#3D1A1A; color:#EFBCB0; text-align:center; padding:4rem 2rem; }
        footer .f-logo { font-family:'Playfair Display', serif; font-style:italic; font-size:32px; color:#F9F4F2; margin-bottom:15px; }

        @media(max-width:992px) {
            .hero { flex-direction: column; text-align: center; padding: 4rem 2rem; }
            .hero-plate img { width: 320px; }
        }
    </style>
</head>
<body>

<nav>
    <a href="#" class="logo">Cafuné</a>
    <div class="nav-links">
        <a href="#menu">Cardápio</a>
        <a href="#contato">Contato</a>
    </div>
</nav>

<header class="hero">
    <div class="hero-text">
        <span class="eyebrow">Destaque da Semana</span>
        <h1>Lombo com Cereja</h1>
        <span class="subtitle">A harmonização perfeita de sabores intensos</span>
        <div class="hero-price">R$ 325,50</div>
    </div>
    <div class="hero-plate">
        <img src="lomb.png" alt="Lombo com Cereja Destaque">
    </div>
</header>

<main class="container" id="menu">
    <div class="section-header">
        <h2>Nosso Cardápio</h2>
        <div class="divider"></div>
    </div>

    <div class="menu-grid">
        <article class="card">
            <div class="card-img-wrapper">
                <img src="lombo.jpeg" alt="Lombo Gourmet">
            </div>
            <div class="card-content">
                <span class="card-tag">Especialidade</span>
                <h3 class="card-name">Lombo Gourmet</h3>
                <p class="card-desc">Corte suíno premium acompanhado de arroz de grãos e uma deliciosa redução de frutas vermelhas.</p>
                <div class="card-footer">
                    <span class="card-price">R$ 250,00</span>
                    <a href="#" class="btn-order">Pedir Agora</a>
                </div>
            </div>
        </article>

        <article class="card">
            <div class="card-img-wrapper">
                <img src="alcatra.jpg" alt="Alcatra Assada">
            </div>
            <div class="card-content">
                <span class="card-tag">Sugestão</span>
                <h3 class="card-name">Alcatra Assada</h3>
                <p class="card-desc">Miolo de alcatra selecionado, assado lentamente na brasa com sal grosso, servido suculento e fatiado.</p>
                <div class="card-footer">
                    <span class="card-price">R$ 290,00</span>
                    <a href="#" class="btn-order">Pedir Agora</a>
                </div>
            </div>
        </article>

        <article class="card">
            <div class="card-img-wrapper">
                <img src="mignom.jpeg" alt="Medalhão Mignon">
            </div>
            <div class="card-content">
                <span class="card-tag">Favorito</span>
                <h3 class="card-name">Medalhão Mignon</h3>
                <p class="card-desc">Dois medalhões grelhados no ponto perfeito, aromatizados com alecrim e pimentas selecionadas.</p>
                <div class="card-footer">
                    <span class="card-price">R$ 258,00</span>
                    <a href="#" class="btn-order">Pedir Agora</a>
                </div>
            </div>
        </article>

        <article class="card">
            <div class="card-img-wrapper">
                <img src="jamon.jpeg" alt="Jamón Serrano">
            </div>
            <div class="card-content">
                <span class="card-tag">Entrada Especial</span>
                <h3 class="card-name">Jamón Serrano</h3>
                <p class="card-desc">Lâminas de presunto cru espanhol com queijo de cabra, hortelã fresca e um toque de balsâmico.</p>
                <div class="card-footer">
                    <span class="card-price">R$ 325,50</span>
                    <a href="#" class="btn-order">Pedir Agora</a>
                </div>
            </div>
        </article>

        <article class="card">
            <div class="card-img-wrapper">
                <img src="picanha.jpeg" alt="Picanha Premium">
            </div>
            <div class="card-content">
                <span class="card-tag">Corte Nobre</span>
                <h3 class="card-name">Picanha Premium</h3>
                <p class="card-desc">Picanha de altíssima qualidade grelhada, mantendo a suculência e o sabor original da carne.</p>
                <div class="card-footer">
                    <span class="card-price">R$ 380,00</span>
                    <a href="#" class="btn-order">Pedir Agora</a>
                </div>
            </div>
        </article>
    </div>
</main>

<footer>
    <div class="f-logo">Cafuné</div>
    <p>Curitiba, Paraná · (41) 99999-0000</p>
    <p>© 2026 Restaurante Cafuné</p>
</footer>

</body>
</html>
