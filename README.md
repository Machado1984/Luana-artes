[luana-arte.html](https://github.com/user-attachments/files/30622155/luana-arte.html)

<!DOCTYPE html>
<html lang="pt-PT">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Luana — Pintura & Estudo</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400&family=Work+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#171018;
    --plum:#1E1620;
    --plum-2:#241a27;
    --ivory:#F3ECE2;
    --ivory-dim:#C9BFB2;
    --gold:#C79A56;
    --gold-soft:#8f7245;
    --umber:#5B3A29;
    --line: rgba(243,236,226,0.14);
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--plum);
    color:var(--ivory);
    font-family:'Work Sans', sans-serif;
    font-weight:300;
    overflow-x:hidden;
  }
  h1,h2,h3, .display{
    font-family:'Cormorant Garamond', serif;
    font-weight:500;
    letter-spacing:0.01em;
  }
  a{color:inherit;}

  /* subtle canvas texture */
  body::before{
    content:"";
    position:fixed; inset:0;
    background-image:
      radial-gradient(circle at 20% 30%, rgba(199,154,86,0.05), transparent 40%),
      radial-gradient(circle at 80% 70%, rgba(199,154,86,0.04), transparent 45%);
    pointer-events:none;
    z-index:0;
  }

  /* ---------- NAV ---------- */
  header{
    position:fixed; top:0; left:0; right:0;
    display:flex; justify-content:space-between; align-items:center;
    padding:28px 6vw;
    z-index:50;
    mix-blend-mode:normal;
    background:linear-gradient(to bottom, rgba(23,16,24,0.85), transparent);
  }
  .brand{
    font-family:'Cormorant Garamond', serif;
    font-size:1.5rem;
    letter-spacing:0.06em;
  }
  nav ul{list-style:none; display:flex; gap:2.4rem;}
  nav a{
    text-decoration:none;
    font-size:0.78rem;
    letter-spacing:0.14em;
    text-transform:uppercase;
    color:var(--ivory-dim);
    transition:color .25s ease;
    position:relative;
  }
  nav a:hover, nav a:focus-visible{color:var(--gold);}
  nav a:focus-visible{outline:1px solid var(--gold); outline-offset:4px;}

  /* ---------- HERO ---------- */
  .hero{
    min-height:100vh;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center;
    padding:120px 6vw 60px;
    position:relative;
    z-index:1;
  }
  .eyebrow{
    font-size:0.75rem;
    letter-spacing:0.3em;
    text-transform:uppercase;
    color:var(--gold);
    margin-bottom:1.6rem;
  }
  .hero h1{
    font-size:clamp(2.8rem, 8vw, 6.4rem);
    line-height:0.98;
    max-width:16ch;
  }
  .hero h1 em{
    font-style:italic;
    color:var(--gold);
  }
  .hero p{
    margin-top:1.8rem;
    max-width:42ch;
    color:var(--ivory-dim);
    font-size:1.05rem;
    line-height:1.7;
  }

  .signature-wrap{
    margin-top:3.2rem;
    width:min(320px, 60vw);
  }
  .signature-wrap svg{width:100%; height:auto; display:block; margin:0 auto;}
  .sig-path{
    fill:none;
    stroke:var(--gold);
    stroke-width:2.2;
    stroke-linecap:round;
    stroke-linejoin:round;
    stroke-dasharray:900;
    stroke-dashoffset:900;
    animation:draw 2.6s 0.4s ease forwards;
  }
  @keyframes draw{to{stroke-dashoffset:0;}}
  .sig-label{
    display:block;
    margin-top:0.6rem;
    text-align:center;
    font-size:0.68rem;
    letter-spacing:0.28em;
    text-transform:uppercase;
    color:var(--ivory-dim);
    opacity:0;
    animation:fadein 1s 2.6s ease forwards;
  }
  @keyframes fadein{to{opacity:1;}}

  .scroll-cue{
    position:absolute; bottom:36px; left:50%; transform:translateX(-50%);
    font-size:0.68rem; letter-spacing:0.2em; text-transform:uppercase;
    color:var(--ivory-dim);
    display:flex; flex-direction:column; align-items:center; gap:10px;
  }
  .scroll-cue::after{
    content:"";
    width:1px; height:34px;
    background:linear-gradient(var(--gold), transparent);
    animation:pulse 2s ease infinite;
  }
  @keyframes pulse{0%,100%{opacity:0.3;} 50%{opacity:1;}}

  /* ---------- SECTION HEADERS ---------- */
  .section{
    padding:120px 6vw;
    position:relative;
    z-index:1;
  }
  .section-head{
    display:flex; align-items:baseline; gap:1.6rem;
    margin-bottom:4rem;
  }
  .section-head .num{
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    color:var(--gold-soft);
    font-size:1rem;
  }
  .section-head h2{
    font-size:clamp(2rem, 4vw, 3rem);
  }
  .section-head .rule{
    flex:1; height:1px; background:var(--line);
  }

  /* ---------- GALLERY ---------- */
  .gallery{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(300px, 1fr));
    gap:3.4rem 2.2rem;
  }
  .frame{
    position:relative;
    background:var(--plum-2);
    border:1px solid var(--line);
    padding:14px 14px 20px;
    transition:transform .5s cubic-bezier(.2,.7,.2,1), border-color .4s ease;
  }
  .frame:hover{
    transform:translateY(-6px);
    border-color:rgba(199,154,86,0.4);
  }
  .canvas{
    aspect-ratio:4/5;
    width:100%;
    overflow:hidden;
    background:var(--ink);
  }
  .canvas svg{width:100%; height:100%; display:block;}
  .caption{
    display:flex; justify-content:space-between; align-items:flex-end;
    margin-top:16px;
    padding:0 2px;
  }
  .caption h3{
    font-size:1.3rem;
    color:var(--ivory);
  }
  .caption .meta{
    font-size:0.72rem;
    letter-spacing:0.06em;
    color:var(--ivory-dim);
    text-align:right;
    line-height:1.5;
  }
  .mini-sig{
    position:absolute;
    bottom:34px; right:22px;
    width:52px; opacity:0.85;
    pointer-events:none;
  }
  .mini-sig path{
    fill:none; stroke:var(--gold); stroke-width:2.4;
    stroke-linecap:round; stroke-linejoin:round;
  }

  /* ---------- ABOUT ---------- */
  .about{
    display:grid;
    grid-template-columns:0.9fr 1.1fr;
    gap:5vw;
    align-items:center;
  }
  .about-portrait{
    aspect-ratio:3/4;
    background:
      radial-gradient(circle at 30% 20%, rgba(199,154,86,0.25), transparent 55%),
      linear-gradient(160deg, #2a1e2c, #140d16);
    border:1px solid var(--line);
    position:relative;
    overflow:hidden;
  }
  .about-portrait svg{position:absolute; inset:0; width:100%; height:100%;}
  .about-text p{
    color:var(--ivory-dim);
    line-height:1.85;
    font-size:1.02rem;
    margin-bottom:1.3rem;
    max-width:56ch;
  }
  .about-text p:first-of-type::first-letter{
    font-family:'Cormorant Garamond', serif;
    font-size:3.4rem;
    float:left;
    line-height:0.8;
    margin:0.08em 0.09em 0 0;
    color:var(--gold);
  }
  .stats{
    display:flex; gap:2.6rem;
    margin-top:2.2rem;
    padding-top:2.2rem;
    border-top:1px solid var(--line);
  }
  .stats div strong{
    display:block;
    font-family:'Cormorant Garamond', serif;
    font-size:1.9rem;
    color:var(--gold);
  }
  .stats div span{
    font-size:0.68rem;
    letter-spacing:0.12em;
    text-transform:uppercase;
    color:var(--ivory-dim);
  }

  /* ---------- CONTACT ---------- */
  .contact{
    text-align:center;
  }
  .contact h2{
    font-size:clamp(2.2rem, 5vw, 3.6rem);
    max-width:20ch;
    margin:0 auto 1.4rem;
  }
  .contact p{color:var(--ivory-dim); max-width:44ch; margin:0 auto 2.6rem; line-height:1.7;}
  .btn{
    display:inline-block;
    padding:16px 38px;
    border:1px solid var(--gold);
    color:var(--gold);
    text-decoration:none;
    font-size:0.78rem;
    letter-spacing:0.16em;
    text-transform:uppercase;
    transition:background .3s ease, color .3s ease;
  }
  .btn:hover, .btn:focus-visible{background:var(--gold); color:var(--ink);}

  footer{
    padding:40px 6vw;
    display:flex; justify-content:space-between; align-items:center;
    border-top:1px solid var(--line);
    font-size:0.72rem;
    letter-spacing:0.08em;
    color:var(--ivory-dim);
  }

  @media (max-width:760px){
    header{padding:22px 6vw;}
    nav ul{gap:1.3rem;}
    nav a{font-size:0.68rem;}
    .about{grid-template-columns:1fr;}
    .about-portrait{max-width:320px; margin:0 auto;}
    footer{flex-direction:column; gap:10px; text-align:center;}
  }

  @media (prefers-reduced-motion: reduce){
    .sig-path{animation:none; stroke-dashoffset:0;}
    .sig-label{animation:none; opacity:1;}
    .scroll-cue::after{animation:none;}
    .frame{transition:none;}
  }
</style>
</head>
<body>

<header>
  <div class="brand">Luana</div>
  <nav>
    <ul>
      <li><a href="#obras">Obras</a></li>
      <li><a href="#sobre">Sobre</a></li>
      <li><a href="#contacto">Contacto</a></li>
    </ul>
  </nav>
</header>

<section class="hero">
  <div class="eyebrow">Pintura & Estudo em Cor</div>
  <h1>A cor é a<br><em>linguagem</em> que fica<br>quando as palavras saem</h1>
  <p>Um pequeno acervo de trabalhos autorais — texturas, gestos e camadas construídas à mão, tela após tela.</p>

  <div class="signature-wrap">
    <svg viewBox="0 0 320 120" xmlns="http://www.w3.org/2000/svg">
      <path class="sig-path" d="M20,80 C20,55 30,40 42,40 C54,40 54,70 46,85 C40,96 30,90 34,78 C40,60 60,35 78,45 C90,52 82,75 70,80 C90,80 96,55 96,45 C96,35 100,60 108,70 C114,78 120,60 122,48 M140,80 C140,55 150,42 158,55 C164,65 150,85 142,78 C136,72 150,50 165,48 C172,47 168,62 168,80 M190,45 L190,80 M190,55 C200,45 214,45 214,58 C214,68 202,72 194,68 M232,30 C232,55 232,80 232,80 M232,55 C240,48 254,50 254,62 C254,72 240,76 232,68 M270,55 C278,46 292,48 290,60 C288,70 274,72 270,64 C266,55 276,44 288,46" />
    </svg>
    <span class="sig-label">Assinado por Luana</span>
  </div>

  <div class="scroll-cue">Deslizar</div>
</section>

<section class="section" id="obras">
  <div class="section-head">
    <span class="num">I.</span>
    <h2>Obras</h2>
    <span class="rule"></span>
  </div>

  <div class="gallery">

    <!-- Artwork 1 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <linearGradient id="g1" x1="0" y1="0" x2="1" y2="1">
              <stop offset="0%" stop-color="#0f2f3a"/>
              <stop offset="100%" stop-color="#16506b"/>
            </linearGradient>
          </defs>
          <rect width="400" height="500" fill="url(#g1)"/>
          <path d="M0,320 C100,260 150,380 260,300 C330,250 400,320 400,320 L400,500 L0,500 Z" fill="#0a1f27" opacity="0.85"/>
          <path d="M0,380 C120,340 200,420 320,360 C360,340 400,380 400,380 L400,500 L0,500 Z" fill="#08161c"/>
          <circle cx="300" cy="110" r="46" fill="#e7cf9a" opacity="0.9"/>
          <circle cx="300" cy="110" r="46" fill="none" stroke="#f3ece2" stroke-width="1" opacity="0.4"/>
          <path d="M40,200 Q120,150 200,210 T360,190" stroke="#c79a56" stroke-width="2" fill="none" opacity="0.5"/>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20"/></svg>
      <div class="caption">
        <h3>Maré Baixa</h3>
        <div class="meta">Acrílico sobre tela<br>80 × 100 cm</div>
      </div>
    </article>

    <!-- Artwork 2 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <linearGradient id="g2" x1="0" y1="0" x2="0" y2="1">
              <stop offset="0%" stop-color="#3a1210"/>
              <stop offset="100%" stop-color="#7a2f18"/>
            </linearGradient>
          </defs>
          <rect width="400" height="500" fill="url(#g2)"/>
          <path d="M200,0 L260,240 L400,260 L230,320 L280,500 L200,380 L120,500 L170,320 L0,260 L140,240 Z" fill="#c96a2e" opacity="0.55"/>
          <path d="M200,60 L240,250 L360,270 L225,320 L260,470 L200,370 L140,470 L175,320 L40,270 L160,250 Z" fill="#e8b25e" opacity="0.5"/>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20"/></svg>
      <div class="caption">
        <h3>Incêndio Suave</h3>
        <div class="meta">Óleo sobre tela<br>70 × 90 cm</div>
      </div>
    </article>

    <!-- Artwork 3 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="500" fill="#12241a"/>
          <g opacity="0.8">
            <rect x="20" y="60" width="90" height="360" fill="#1c3f2b"/>
            <rect x="130" y="20" width="60" height="440" fill="#2c5c3d"/>
            <rect x="210" y="90" width="110" height="330" fill="#183828"/>
            <rect x="340" y="40" width="40" height="420" fill="#4f7d52"/>
          </g>
          <path d="M0,460 Q200,420 400,460 L400,500 L0,500 Z" fill="#0a1a12"/>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20"/></svg>
      <div class="caption">
        <h3>Floresta Vertical</h3>
        <div class="meta">Técnica mista<br>60 × 80 cm</div>
      </div>
    </article>

    <!-- Artwork 4 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="500" fill="#e9e2d4"/>
          <circle cx="200" cy="240" r="150" fill="none" stroke="#171018" stroke-width="1.5" opacity="0.5"/>
          <circle cx="200" cy="240" r="100" fill="none" stroke="#171018" stroke-width="1.5" opacity="0.6"/>
          <circle cx="200" cy="240" r="50" fill="#171018" opacity="0.85"/>
          <path d="M60,60 L340,420 M340,60 L60,420" stroke="#c79a56" stroke-width="1" opacity="0.4"/>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40" style="filter:invert(0);"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20" stroke="#171018"/></svg>
      <div class="caption">
        <h3>Silêncio Circular</h3>
        <div class="meta">Grafite e nanquim<br>50 × 65 cm</div>
      </div>
    </article>

    <!-- Artwork 5 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="g5" cx="50%" cy="35%" r="70%">
              <stop offset="0%" stop-color="#5a2a5f"/>
              <stop offset="60%" stop-color="#2a1440"/>
              <stop offset="100%" stop-color="#140a22"/>
            </radialGradient>
          </defs>
          <rect width="400" height="500" fill="url(#g5)"/>
          <path d="M0,300 Q100,200 200,290 T400,270 L400,500 L0,500 Z" fill="#1a0f2c" opacity="0.7"/>
          <g fill="#f3ece2">
            <circle cx="80" cy="90" r="1.4"/>
            <circle cx="140" cy="130" r="1"/>
            <circle cx="260" cy="70" r="1.6"/>
            <circle cx="320" cy="140" r="1.1"/>
            <circle cx="190" cy="50" r="1.3"/>
            <circle cx="350" cy="90" r="1"/>
          </g>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20"/></svg>
      <div class="caption">
        <h3>Aurora Interior</h3>
        <div class="meta">Acrílico sobre madeira<br>60 × 90 cm</div>
      </div>
    </article>

    <!-- Artwork 6 -->
    <article class="frame">
      <div class="canvas">
        <svg viewBox="0 0 400 500" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="500" fill="#241a15"/>
          <g stroke="#c79a56" stroke-width="2" opacity="0.7" fill="none">
            <path d="M40,460 C60,300 50,180 90,60"/>
            <path d="M90,460 C110,320 95,200 130,50"/>
            <path d="M150,460 C170,300 150,190 190,70"/>
            <path d="M220,460 C230,320 210,210 250,60"/>
            <path d="M290,460 C300,300 280,180 320,50"/>
            <path d="M350,460 C360,320 340,200 370,80"/>
          </g>
        </svg>
      </div>
      <svg class="mini-sig" viewBox="0 0 100 40"><path d="M6,26 C6,16 12,12 16,18 C19,22 12,30 8,26 C24,18 30,10 32,20 C33,26 26,28 24,24 C34,14 46,14 46,24 C46,30 38,30 38,24 M56,10 L56,26 M56,16 C62,10 70,12 68,20 C66,26 58,26 58,20 M76,16 C82,10 90,12 88,20 C86,26 78,26 78,20"/></svg>
      <div class="caption">
        <h3>Raízes</h3>
        <div class="meta">Tinta sobre linho cru<br>75 × 95 cm</div>
      </div>
    </article>

  </div>
</section>

<section class="section" id="sobre">
  <div class="section-head">
    <span class="num">II.</span>
    <h2>Sobre</h2>
    <span class="rule"></span>
  </div>

  <div class="about">
    <div class="about-portrait">
      <svg viewBox="0 0 300 400" xmlns="http://www.w3.org/2000/svg">
        <circle cx="150" cy="150" r="70" fill="#c79a56" opacity="0.15"/>
        <path d="M40,380 C40,280 90,230 150,230 C210,230 260,280 260,380 Z" fill="#c79a56" opacity="0.1"/>
        <path d="M20,40 L280,40 M20,90 L280,90 M20,140 L280,140" stroke="#c79a56" stroke-width="0.5" opacity="0.2"/>
      </svg>
    </div>
    <div class="about-text">
      <p>Luana trabalha com camadas — de tinta, de tempo, de memória. Cada tela começa sem plano fixo: um gesto puxa o seguinte, e a cor vai encontrando o seu próprio caminho até parar.</p>
      <p>O atelier fica cheio de esboços inacabados, potes de tinta reaproveitados e uma janela que muda a luz sobre o trabalho ao longo do dia. É nesse espaço, sem pressa, que nascem as peças que aqui ficam guardadas.</p>
      <div class="stats">
        <div><strong>12+</strong><span>Anos de prática</span></div>
        <div><strong>60</strong><span>Obras originais</span></div>
        <div><strong>8</strong><span>Exposições</span></div>
      </div>
    </div>
  </div>
</section>

<section class="section contact" id="contacto">
  <div class="section-head" style="justify-content:center;">
    <span class="rule"></span>
    <span class="num">III.</span>
  </div>
  <h2>Interessado numa peça ou numa encomenda?</h2>
  <p>Escreva a contar o que procura — tamanho, paleta, espaço onde a obra vai viver — e responderei com disponibilidade e valores.</p>
  <a class="btn" href="mailto:contacto@luana-arte.com">Enviar mensagem</a>
</section>

<footer>
  <span>© 2026 Luana — Todas as obras originais</span>
  <span>Atelier, Porto</span>
</footer>

</body>
</html>
