<!doctype html>
<html lang="pt-PT">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Scratch na Sala de Aula | Recursos e Cenários</title>
  <meta name="description" content="Site responsivo com recursos, imagens e cenários de aula para ensinar Scratch." />
  <style>
    :root{
      --bg: #0b1020;
      --panel: rgba(255,255,255,.06);
      --panel2: rgba(255,255,255,.09);
      --text: rgba(255,255,255,.92);
      --muted: rgba(255,255,255,.72);
      --line: rgba(255,255,255,.14);
      --accent: #ff9f1c;
      --accent2:#2ec4b6;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 18px;
      --max: 1100px;
      --focus: 0 0 0 4px rgba(46,196,182,.35);
    }

    *{ box-sizing:border-box; }
    html, body{ height:100%; }
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, "Helvetica Neue", Arial, "Noto Sans", "Liberation Sans", sans-serif;
      color: var(--text);
      background:
        radial-gradient(1100px 700px at 18% 12%, rgba(255,159,28,.18), transparent 60%),
        radial-gradient(900px 600px at 72% 18%, rgba(46,196,182,.16), transparent 55%),
        radial-gradient(900px 800px at 70% 92%, rgba(255,255,255,.06), transparent 60%),
        linear-gradient(180deg, #070a14, var(--bg));
      line-height: 1.5;
    }

    a{ color: inherit; }
    a:focus-visible, button:focus-visible, input:focus-visible{
      outline: none;
      box-shadow: var(--focus);
      border-radius: 10px;
    }

    .skip{
      position:absolute; left:-999px; top:10px;
      background:#fff; color:#000; padding:.6rem .8rem; border-radius:10px;
      z-index:9999;
    }
    .skip:focus{ left:10px; }

    header{
      position: sticky;
      top: 0;
      z-index: 50;
      backdrop-filter: blur(10px);
      background: rgba(7,10,20,.55);
      border-bottom: 1px solid var(--line);
    }

    .wrap{ max-width: var(--max); margin: 0 auto; padding: 0 1rem; }

    .topbar{
      display:flex; align-items:center; justify-content:space-between;
      padding: .9rem 0;
      gap: 1rem;
    }

    .brand{
      display:flex; align-items:center; gap:.7rem; text-decoration:none;
      font-weight: 800; letter-spacing:.2px;
    }
    .logo{
      width:38px; height:38px; border-radius: 12px;
      background: linear-gradient(135deg, rgba(255,159,28,.95), rgba(46,196,182,.95));
      box-shadow: var(--shadow);
      display:grid; place-items:center;
    }
    .logo svg{ width:24px; height:24px; }
    .brand small{ display:block; font-weight:600; color: var(--muted); letter-spacing:0; }

    nav{
      display:flex; align-items:center; gap: .6rem;
    }
    nav a{
      text-decoration:none;
      padding:.55rem .7rem;
      border: 1px solid transparent;
      border-radius: 12px;
      color: var(--muted);
    }
    nav a:hover{ background: rgba(255,255,255,.06); color: var(--text); }
    nav a[aria-current="page"]{ border-color: var(--line); color: var(--text); background: rgba(255,255,255,.05); }

    .btn{
      appearance:none; border: 1px solid var(--line);
      background: rgba(255,255,255,.04);
      color: var(--text);
      border-radius: 14px;
      padding:.65rem .85rem;
      cursor:pointer;
      display:inline-flex; align-items:center; gap:.55rem;
    }
    .btn:hover{ background: rgba(255,255,255,.08); }
    .btn.primary{
      border-color: transparent;
      background: linear-gradient(135deg, rgba(255,159,28,.95), rgba(255,159,28,.75));
      color:#1a1205;
      font-weight: 800;
    }
    .btn.primary:hover{ filter: brightness(1.03); }

    .menuBtn{ display:none; }
    .navPanel{
      display:none;
      padding: .6rem 0 1rem 0;
    }
    .navPanel a{
      display:block;
      padding:.75rem .9rem;
      margin:.35rem 0;
      border-radius: 14px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.03);
      text-decoration:none;
      color: var(--muted);
    }
    .navPanel a:hover{ color: var(--text); background: rgba(255,255,255,.06); }

    main{ padding: 1.2rem 0 3rem; }

    .hero{
      display:grid;
      grid-template-columns: 1.25fr .75fr;
      gap: 1.2rem;
      align-items: stretch;
      margin-top: 1.1rem;
    }
    .card{
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
    }
    .hero .left{ padding: 1.3rem 1.2rem; }
    .hero h1{
      margin:.2rem 0 .55rem;
      font-size: clamp(1.6rem, 3.2vw, 2.55rem);
      line-height: 1.15;
      letter-spacing: .2px;
    }
    .hero p{ margin:.2rem 0; color: var(--muted); font-size: 1.02rem; }
    .badges{
      display:flex; flex-wrap:wrap; gap:.5rem; margin: 1rem 0 1.2rem;
    }
    .badge{
      display:inline-flex; align-items:center; gap:.45rem;
      padding:.45rem .65rem;
      border-radius: 999px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.03);
      color: var(--muted);
      font-weight: 650;
      font-size: .92rem;
    }
    .badge b{ color: var(--text); }
    .ctaRow{ display:flex; flex-wrap:wrap; gap:.7rem; margin-top: 1rem; }

    .hero .right{
      overflow:hidden;
      position: relative;
      min-height: 260px;
    }
    .heroArt{
      position:absolute; inset:0;
      display:grid; place-items:center;
      background:
        radial-gradient(500px 280px at 40% 35%, rgba(255,159,28,.25), transparent 60%),
        radial-gradient(520px 320px at 70% 55%, rgba(46,196,182,.22), transparent 60%),
        linear-gradient(135deg, rgba(255,255,255,.05), rgba(255,255,255,.02));
    }
    .heroArt svg{ width:min(360px, 92%); height:auto; filter: drop-shadow(0 20px 30px rgba(0,0,0,.35)); }

    section{ margin-top: 1.4rem; }
    .sectionHead{
      display:flex; align-items:flex-end; justify-content:space-between; gap:1rem;
      margin: 1.4rem 0 .7rem;
    }
    .sectionHead h2{ margin:0; font-size: 1.25rem; letter-spacing:.2px; }
    .sectionHead p{ margin:0; color: var(--muted); }

    .grid3{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1rem;
    }
    .grid2{
      display:grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 1rem;
    }

    .tile{
      padding: 1rem;
      position: relative;
      overflow:hidden;
      min-height: 190px;
    }
    .tile h3{ margin:.1rem 0 .35rem; font-size: 1.05rem; }
    .tile p{ margin:0; color: var(--muted); }
    .tile .meta{
      display:flex; flex-wrap:wrap; gap:.5rem;
      margin-top: .8rem;
    }
    .chip{
      font-size: .88rem;
      padding:.35rem .55rem;
      border-radius: 999px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.03);
      color: var(--muted);
    }
    .tile .thumb{
      position:absolute;
      right:-16px;
      bottom:-18px;
      width: 160px;
      opacity: .95;
      transform: rotate(3deg);
    }

    .lesson{
      padding: 1rem;
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      align-items: start;
    }
    .lesson h3{ margin:.1rem 0 .25rem; }
    .lesson p{ margin:.2rem 0; color: var(--muted); }
    .lesson ul{ margin:.5rem 0 0; padding-left: 1.1rem; color: var(--muted); }
    .lesson li{ margin:.25rem 0; }
    .imgBox{
      border-radius: 16px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.03);
      overflow:hidden;
      min-height: 220px;
      display:grid; place-items:center;
    }
    .imgBox svg{ width:100%; height:auto; display:block; }
    .tools{
      display:flex; flex-wrap:wrap; gap:.6rem; margin-top: .9rem;
    }

    .resources{
      padding: 1rem;
    }
    .resources .row{
      display:flex; flex-wrap:wrap; gap:.6rem;
      margin-top: .8rem;
    }
    .resources label{
      display:block; color: var(--muted); font-weight:650; margin-bottom:.35rem;
    }
    .resources input{
      width: 100%;
      padding: .75rem .85rem;
      border-radius: 14px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.04);
      color: var(--text);
    }

    .gallery{
      padding: 1rem;
    }
    .galleryGrid{
      display:grid;
      grid-template-columns: repeat(4, 1fr);
      gap: .9rem;
      margin-top: .85rem;
    }
    figure{
      margin:0;
      border-radius: 16px;
      border: 1px solid var(--line);
      background: rgba(255,255,255,.03);
      overflow:hidden;
      cursor:pointer;
    }
    figure:hover{ background: rgba(255,255,255,.06); }
    figure .cap{
      padding:.65rem .75rem;
      color: var(--muted);
      font-size: .92rem;
      border-top: 1px solid var(--line);
    }
    figure svg{ width:100%; height:auto; display:block; }

    footer{
      border-top: 1px solid var(--line);
      padding: 1.2rem 0 2rem;
      color: var(--muted);
    }
    footer .foot{
      display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:.8rem;
    }

    /* Modal */
    dialog{
      width: min(980px, 96vw);
      border: 1px solid var(--line);
      border-radius: 18px;
      background: rgba(10,14,28,.92);
      color: var(--text);
      box-shadow: 0 30px 70px rgba(0,0,0,.55);
      padding: 0;
      overflow:hidden;
    }
    dialog::backdrop{ background: rgba(0,0,0,.55); }
    .modalHead{
      display:flex; align-items:center; justify-content:space-between; gap:1rem;
      padding: .9rem 1rem;
      border-bottom: 1px solid var(--line);
      background: rgba(255,255,255,.03);
    }
    .modalHead strong{ letter-spacing:.2px; }
    .modalBody{ padding: 1rem; }
    .modalBody svg{ width:100%; height:auto; display:block; border-radius: 14px; border:1px solid var(--line); }
    .modalBody p{ color: var(--muted); margin:.7rem 0 0; }

    /* Responsivo */
    @media (max-width: 980px){
      .hero{ grid-template-columns: 1fr; }
      .hero .right{ min-height: 240px; }
      .grid3{ grid-template-columns: 1fr 1fr; }
      .galleryGrid{ grid-template-columns: 1fr 1fr; }
      .lesson{ grid-template-columns: 1fr; }
    }
    @media (max-width: 720px){
      nav{ display:none; }
      .menuBtn{ display:inline-flex; }
      .navPanel{ display:block; }
      .grid3{ grid-template-columns: 1fr; }
      .grid2{ grid-template-columns: 1fr; }
      .galleryGrid{ grid-template-columns: 1fr; }
    }

    /* Redução de movimento */
    @media (prefers-reduced-motion: reduce){
      *{ scroll-behavior: auto !important; transition: none !important; animation: none !important; }
    }
  </style>
</head>

<body>
  <a class="skip" href="#conteudo">Saltar para o conteúdo principal</a>

  <header>
    <div class="wrap">
      <div class="topbar">
        <a class="brand" href="#inicio" aria-label="Scratch na Sala de Aula">
          <span class="logo" aria-hidden="true">
            <svg viewBox="0 0 24 24" fill="none">
              <path d="M8.2 15.6c.6 1.7 2.3 2.9 4.3 2.9 2.6 0 4.8-2.1 4.8-4.8 0-1.9-1.1-3.6-2.8-4.3" stroke="rgba(0,0,0,.75)" stroke-width="2" stroke-linecap="round"/>
              <path d="M6.6 13.8c-1.7-.6-2.9-2.3-2.9-4.3C3.7 6.9 5.8 4.7 8.5 4.7c1.9 0 3.6 1.1 4.3 2.8" stroke="rgba(0,0,0,.75)" stroke-width="2" stroke-linecap="round"/>
            </svg>
          </span>
          <span>
            Scratch na Sala de Aula
            <small>imagens + cenários prontos para ensinar</small>
          </span>
        </a>

        <nav aria-label="Navegação principal">
          <a href="#cenarios">Cenários</a>
          <a href="#aulas">Planos de aula</a>
          <a href="#galeria">Galeria</a>
          <a href="#recursos">Recursos</a>
        </nav>

        <button class="btn menuBtn" id="menuBtn" aria-expanded="false" aria-controls="navPanel">
          ☰ Menu
        </button>
      </div>

      <div class="navPanel" id="navPanel" hidden>
        <a href="#cenarios">Cenários</a>
        <a href="#aulas">Planos de aula</a>
        <a href="#galeria">Galeria</a>
        <a href="#recursos">Recursos</a>
      </div>
    </div>
  </header>

  <main id="conteudo">
    <div class="wrap" id="inicio">
      <div class="hero">
        <div class="card left">
          <h1>Ensinar Scratch com projectos curtos, criativos e avaliáveis</h1>
          <p>
            Este site reúne <strong>cenários</strong> (situações-problema), <strong>imagens</strong> e
            <strong>planos de aula</strong> para apoiar o ensino de programação por blocos.
          </p>

          <div class="badges" aria-label="Destaques">
            <span class="badge"><b>Responsivo</b> (telemóvel/PC)</span>
            <span class="badge"><b>Acessível</b> (skip link + foco visível)</span>
            <span class="badge"><b>Cenários</b> por níveis</span>
            <span class="badge"><b>Ideias</b> de avaliação</span>
          </div>

          <div class="ctaRow">
            <a class="btn primary" href="#aulas">Ver planos de aula</a>
            <a class="btn" href="#galeria">Explorar imagens</a>
            <a class="btn" href="#recursos">Checklist de recursos</a>
          </div>
        </div>

        <div class="card right" aria-label="Ilustração Scratch">
          <div class="heroArt" aria-hidden="true">
            <!-- Ilustração (SVG) -->
            <svg viewBox="0 0 800 520" role="img" aria-label="Ilustração: palco, sprite e blocos">
              <defs>
                <linearGradient id="g1" x1="0" y1="0" x2="1" y2="1">
                  <stop offset="0" stop-color="rgba(255,159,28,.95)"/>
                  <stop offset="1" stop-color="rgba(46,196,182,.95)"/>
                </linearGradient>
              </defs>
              <rect x="70" y="70" width="440" height="330" rx="26" fill="rgba(255,255,255,.08)" stroke="rgba(255,255,255,.18)"/>
              <rect x="95" y="105" width="390" height="250" rx="22" fill="rgba(0,0,0,.25)" stroke="rgba(255,255,255,.14)"/>
              <circle cx="215" cy="190" r="48" fill="url(#g1)" opacity=".95"/>
              <path d="M200 182c18-18 38-10 45 8 8 20-10 45-35 45-25 0-37-26-25-43z" fill="rgba(0,0,0,.55)"/>
              <rect x="540" y="92" width="190" height="45" rx="14" fill="rgba(255,255,255,.08)" stroke="rgba(255,255,255,.18)"/>
              <rect x="540" y="150" width="240" height="55" rx="18" fill="rgba(255,159,28,.22)" stroke="rgba(255,159,28,.45)"/>
              <rect x="540" y="220" width="220" height="55" rx="18" fill="rgba(46,196,182,.20)" stroke="rgba(46,196,182,.45)"/>
              <rect x="540" y="290" width="260" height="55" rx="18" fill="rgba(255,255,255,.07)" stroke="rgba(255,255,255,.16)"/>
              <rect x="540" y="360" width="200" height="55" rx="18" fill="rgba(255,255,255,.06)" stroke="rgba(255,255,255,.14)"/>
              <path d="M130 330c45-70 80-55 110-20 25 30 55 15 85-25 30-40 70-55 130-10" fill="none" stroke="rgba(255,255,255,.28)" stroke-width="10" stroke-linecap="round"/>
              <circle cx="460" cy="130" r="10" fill="rgba(255,255,255,.35)"/>
              <circle cx="140" cy="140" r="7" fill="rgba(255,255,255,.25)"/>
            </svg>
          </div>
        </div>
      </div>

      <!-- Cenários -->
      <section id="cenarios" aria-labelledby="h-cenarios">
        <div class="sectionHead">
          <div>
            <h2 id="h-cenarios">Cenários para o ensino</h2>
            <p>Escolhe um cenário e adapta ao teu ano/turma.</p>
          </div>
          <a class="btn" href="#aulas">Ir para planos de aula</a>
        </div>

        <div class="grid3">
          <article class="card tile">
            <h3>1) Histórias Interactivas</h3>
            <p>Diálogos, escolhas do utilizador e finais alternativos.</p>
            <div class="meta">
              <span class="chip">Nível: inicial</span>
              <span class="chip">Conceitos: eventos</span>
              <span class="chip">Conceitos: mensagens</span>
            </div>
            <svg class="thumb" viewBox="0 0 220 180" aria-hidden="true">
              <rect x="18" y="22" width="170" height="120" rx="18" fill="rgba(255,159,28,.18)" stroke="rgba(255,159,28,.5)"/>
              <path d="M40 62h110" stroke="rgba(255,255,255,.35)" stroke-width="10" stroke-linecap="round"/>
              <path d="M40 92h85" stroke="rgba(255,255,255,.25)" stroke-width="10" stroke-linecap="round"/>
              <path d="M40 122h100" stroke="rgba(255,255,255,.25)" stroke-width="10" stroke-linecap="round"/>
              <circle cx="180" cy="120" r="18" fill="rgba(46,196,182,.35)" stroke="rgba(46,196,182,.7)"/>
            </svg>
          </article>

          <article class="card tile">
            <h3>2) Jogo de Reflexos</h3>
            <p>Pontos, tempo, dificuldade e feedback imediato.</p>
            <div class="meta">
              <span class="chip">Nível: intermédio</span>
              <span class="chip">Conceitos: variáveis</span>
              <span class="chip">Conceitos: colisões</span>
            </div>
            <svg class="thumb" viewBox="0 0 220 180" aria-hidden="true">
              <rect x="18" y="22" width="170" height="120" rx="18" fill="rgba(46,196,182,.16)" stroke="rgba(46,196,182,.55)"/>
              <circle cx="78" cy="82" r="18" fill="rgba(255,159,28,.55)"/>
              <circle cx="120" cy="110" r="12" fill="rgba(255,255,255,.25)"/>
              <path d="M145 60l18 18-18 18" fill="none" stroke="rgba(255,255,255,.35)" stroke-width="10" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M60 130h90" stroke="rgba(255,255,255,.2)" stroke-width="10" stroke-linecap="round"/>
            </svg>
          </article>

          <article class="card tile">
            <h3>3) Simulação / Ciência</h3>
            <p>Movimento, parâmetros e interpretação de resultados.</p>
            <div class="meta">
              <span class="chip">Nível: avançado</span>
              <span class="chip">Conceitos: clones</span>
              <span class="chip">Conceitos: listas</span>
            </div>
            <svg class="thumb" viewBox="0 0 220 180" aria-hidden="true">
              <rect x="18" y="22" width="170" height="120" rx="18" fill="rgba(255,255,255,.06)" stroke="rgba(255,255,255,.2)"/>
              <path d="M45 120c30-50 55-35 70-10 12 20 25 12 40-10 15-22 30-30 55-5" fill="none" stroke="rgba(255,159,28,.45)" stroke-width="10" stroke-linecap="round"/>
              <path d="M45 95c25-35 45-25 58-8 10 13 20 7 33-8 12-14 25-18 50-2" fill="none" stroke="rgba(46,196,182,.5)" stroke-width="10" stroke-linecap="round"/>
            </svg>
          </article>
        </div>
      </section>

      <!-- Planos de aula -->
      <section id="aulas" aria-labelledby="h-aulas">
        <div class="sectionHead">
          <div>
            <h2 id="h-aulas">Planos de aula (prontos a usar)</h2>
            <p>Objectivos + passos + avaliação rápida.</p>
          </div>
          <button class="btn" id="printBtn" type="button">🖨️ Imprimir</button>
        </div>

        <article class="card lesson" aria-labelledby="a1">
          <div>
            <h3 id="a1">Aula 1 — “Conta uma história com escolhas”</h3>
            <p><strong>Duração:</strong> 45–60 min · <strong>Conceitos:</strong> eventos, mensagens, diálogos</p>
            <p><strong>Objectivo:</strong> criar uma narrativa onde o utilizador escolhe (teclas/botões) e a história reage.</p>
            <ul>
              <li>Criar 2 cenários (fundo A/B) e 2 personagens.</li>
              <li>Usar “quando a bandeira for clicada”, “perguntar e esperar” e “difundir mensagem”.</li>
              <li>Adicionar um final alternativo (bom/mau final).</li>
              <li><strong>Critério rápido:</strong> há pelo menos 2 escolhas e 2 finais.</li>
            </ul>
            <div class="tools">
              <button class="btn" type="button" data-modal="Histórias interactivas">Ver imagem do cenário</button>
              <a class="btn" href="#recursos">Checklist de materiais</a>
            </div>
          </div>
          <div class="imgBox" aria-label="Imagem do cenário: história">
            <svg viewBox="0 0 900 520" role="img" aria-label="Cenário: sala de aula com quadro e balões de texto">
              <rect width="900" height="520" fill="rgba(0,0,0,.2)"/>
              <rect x="70" y="90" width="520" height="310" rx="26" fill="rgba(255,255,255,.08)" stroke="rgba(255,255,255,.18)"/>
              <rect x="110" y="140" width="440" height="210" rx="18" fill="rgba(0,0,0,.25)" stroke="rgba(255,255,255,.14)"/>
              <rect x="640" y="120" width="200" height="80" rx="26" fill="rgba(255,159,28,.18)" stroke="rgba(255,159,28,.55)"/>
              <rect x="610" y="230" width="250" height="110" rx="26" fill="rgba(46,196,182,.16)" stroke="rgba(46,196,182,.55)"/>
              <circle cx="205" cy="250" r="55" fill="rgba(255,159,28,.85)"/>
              <circle cx="385" cy="270" r="45" fill="rgba(46,196,182,.85)"/>
              <path d="M675 200l-20 18" stroke="rgba(255,159,28,.55)" stroke-width="10" stroke-linecap="round"/>
              <path d="M660 345l-20 20" stroke="rgba(46,196,182,.55)" stroke-width="10" stroke-linecap="round"/>
              <path d="M165 430h320" stroke="rgba(255,255,255,.2)" stroke-width="12" stroke-linecap="round"/>
              <path d="M165 458h260" stroke="rgba(255,255,255,.16)" stroke-width="12" stroke-linecap="round"/>
            </svg>
          </div>
        </article>

        <article class="card lesson" aria-labelledby="a2">
          <div>
            <h3 id="a2">Aula 2 — “Jogo de apanhar pontos”</h3>
            <p><strong>Duração:</strong> 60–90 min · <strong>Conceitos:</strong> variáveis, colisões, temporizador</p>
            <p><strong>Objectivo:</strong> um objecto cai/anda e o jogador apanha para ganhar pontos (com tempo limite).</p>
            <ul>
              <li>Variáveis: <em>pontos</em> e <em>tempo</em>.</li>
              <li>Se tocar no jogador: +1 ponto e reposicionar.</li>
              <li>Quando tempo = 0: mostrar “Fim do jogo” e parar.</li>
              <li><strong>Extensão:</strong> aumentar velocidade ao longo do tempo.</li>
            </ul>
            <div class="tools">
              <button class="btn" type="button" data-modal="Jogo de reflexos">Ver imagem do cenário</button>
              <a class="btn" href="#galeria">Sprites e fundos</a>
            </div>
          </div>
          <div class="imgBox" aria-label="Imagem do cenário: jogo">
            <svg viewBox="0 0 900 520" role="img" aria-label="Cenário: jogo com pontos e alvo">
              <rect width="900" height="520" fill="rgba(0,0,0,.2)"/>
              <rect x="70" y="90" width="720" height="330" rx="26" fill="rgba(255,255,255,.07)" stroke="rgba(255,255,255,.18)"/>
              <circle cx="200" cy="220" r="42" fill="rgba(46,196,182,.75)"/>
              <circle cx="520" cy="260" r="26" fill="rgba(255,159,28,.85)"/>
              <circle cx="620" cy="170" r="18" fill="rgba(255,255,255,.25)"/>
              <rect x="120" y="120" width="180" height="52" rx="16" fill="rgba(255,159,28,.18)" stroke="rgba(255,159,28,.55)"/>
              <rect x="320" y="120" width="180" height="52" rx="16" fill="rgba(46,196,182,.16)" stroke="rgba(46,196,182,.55)"/>
              <path d="M150 148h120" stroke="rgba(255,255,255,.32)" stroke-width="10" stroke-linecap="round"/>
              <path d="M350 148h120" stroke="rgba(255,255,255,.28)" stroke-width="10" stroke-linecap="round"/>
              <path d="M140 390h610" stroke="rgba(255,255,255,.14)" stroke-width="12" stroke-linecap="round"/>
            </svg>
          </div>
        </article>

        <article class="card lesson" aria-labelledby="a3">
          <div>
            <h3 id="a3">Aula 3 — “Simulação: trânsito/meteorologia/plantas”</h3>
            <p><strong>Duração:</strong> 90 min · <strong>Conceitos:</strong> clones, regras, recolha de dados</p>
            <p><strong>Objectivo:</strong> simular um fenómeno com parâmetros (ex.: carros, gotas de chuva, crescimento de plantas).</p>
            <ul>
              <li>Clones para criar muitos elementos (carros/gotas).</li>
              <li>Parâmetro (deslizador): intensidade/velocidade.</li>
              <li>Registar resultados (lista ou variável acumulada).</li>
              <li><strong>Discussão:</strong> o que muda quando alteramos o parâmetro?</li>
            </ul>
            <div class="tools">
              <button class="btn" type="button" data-modal="Simulação">Ver imagem do cenário</button>
              <a class="btn" href="#recursos">Modelo de rubrica</a>
            </div>
          </div>
          <div class="imgBox" aria-label="Imagem do cenário: simulação">
            <svg viewBox="0 0 900 520" role="img" aria-label="Cenário: estrada com partículas">
              <rect width="900" height="520" fill="rgba(0,0,0,.2)"/>
              <rect x="90" y="110" width="720" height="300" rx="26" fill="rgba(255,255,255,.07)" stroke="rgba(255,255,255,.18)"/>
              <rect x="120" y="250" width="660" height="120" rx="22" fill="rgba(0,0,0,.25)" stroke="rgba(255,255,255,.12)"/>
              <path d="M160 310h580" stroke="rgba(255,255,255,.18)" stroke-width="10" stroke-dasharray="28 18" stroke-linecap="round"/>
              <circle cx="220" cy="210" r="16" fill="rgba(46,196,182,.75)"/>
              <circle cx="320" cy="190" r="10" fill="rgba(255,159,28,.85)"/>
              <circle cx="420" cy="220" r="14" fill="rgba(46,196,182,.55)"/>
              <circle cx="550" cy="200" r="9" fill="rgba(255,255,255,.25)"/>
              <circle cx="650" cy="225" r="12" fill="rgba(255,159,28,.7)"/>
              <rect x="140" y="140" width="250" height="60" rx="18" fill="rgba(255,255,255,.05)" stroke="rgba(255,255,255,.16)"/>
              <path d="M165 170h200" stroke="rgba(255,255,255,.28)" stroke-width="10" stroke-linecap="round"/>
            </svg>
          </div>
        </article>
      </section>

      <!-- Galeria -->
      <section id="galeria" aria-labelledby="h-galeria">
        <div class="sectionHead">
          <div>
            <h2 id="h-galeria">Galeria de imagens (fundos e sprites)</h2>
            <p>Clica para ampliar (útil para discutir cenários com a turma).</p>
          </div>
          <span class="chip" aria-label="Dica">Dica: usa estas imagens como inspiração</span>
        </div>

        <div class="card gallery">
          <div class="galleryGrid" role="list">
            <figure role="listitem" tabindex="0" data-title="Palco: Floresta">
              <svg viewBox="0 0 700 420" role="img" aria-label="Fundo: floresta">
                <rect width="700" height="420" fill="rgba(0,0,0,.18)"/>
                <circle cx="120" cy="120" r="70" fill="rgba(255,159,28,.35)"/>
                <rect x="0" y="260" width="700" height="160" fill="rgba(46,196,182,.14)"/>
                <path d="M80 330c20-70 40-90 55-10" stroke="rgba(255,255,255,.25)" stroke-width="18" stroke-linecap="round"/>
                <path d="M180 360c20-90 45-120 70-10" stroke="rgba(255,255,255,.18)" stroke-width="18" stroke-linecap="round"/>
                <path d="M540 340c22-85 44-105 68-12" stroke="rgba(255,255,255,.18)" stroke-width="18" stroke-linecap="round"/>
              </svg>
              <div class="cap">Fundo: floresta (missão: encontrar um objecto)</div>
            </figure>

            <figure role="listitem" tabindex="0" data-title="Palco: Cidade">
              <svg viewBox="0 0 700 420" role="img" aria-label="Fundo: cidade">
                <rect width="700" height="420" fill="rgba(0,0,0,.18)"/>
                <rect x="0" y="260" width="700" height="160" fill="rgba(255,255,255,.06)"/>
                <rect x="70" y="160" width="110" height="160" rx="8" fill="rgba(255,159,28,.20)"/>
                <rect x="210" y="120" width="130" height="200" rx="8" fill="rgba(46,196,182,.18)"/>
                <rect x="370" y="150" width="110" height="170" rx="8" fill="rgba(255,255,255,.07)"/>
                <rect x="510" y="110" width="120" height="210" rx="8" fill="rgba(255,159,28,.14)"/>
                <circle cx="560" cy="90" r="35" fill="rgba(255,159,28,.28)"/>
              </svg>
              <div class="cap">Fundo: cidade (missão: atravessar com regras)</div>
            </figure>

            <figure role="listitem" tabindex="0" data-title="Sprite: Personagem">
              <svg viewBox="0 0 700 420" role="img" aria-label="Sprite: personagem">
                <rect width="700" height="420" fill="rgba(0,0,0,.18)"/>
                <circle cx="360" cy="180" r="80" fill="rgba(46,196,182,.65)"/>
                <rect x="300" y="260" width="120" height="120" rx="26" fill="rgba(255,159,28,.55)"/>
                <circle cx="330" cy="170" r="12" fill="rgba(0,0,0,.55)"/>
                <circle cx="390" cy="170" r="12" fill="rgba(0,0,0,.55)"/>
                <path d="M332 205c20 18 45 18 65 0" fill="none" stroke="rgba(0,0,0,.45)" stroke-width="12" stroke-linecap="round"/>
              </svg>
              <div class="cap">Sprite: personagem (diálogo / controlos)</div>
            </figure>

            <figure role="listitem" tabindex="0" data-title="Sprite: Objecto/Alvo">
              <svg viewBox="0 0 700 420" role="img" aria-label="Sprite: alvo">
                <rect width="700" height="420" fill="rgba(0,0,0,.18)"/>
                <circle cx="350" cy="220" r="120" fill="rgba(255,255,255,.06)" stroke="rgba(255,255,255,.18)" stroke-width="8"/>
                <circle cx="350" cy="220" r="80" fill="rgba(255,159,28,.18)" stroke="rgba(255,159,28,.55)" stroke-width="8"/>
                <circle cx="350" cy="220" r="40" fill="rgba(46,196,182,.20)" stroke="rgba(46,196,182,.55)" stroke-width="8"/>
              </svg>
              <div class="cap">Sprite: alvo (pontuação e colisão)</div>
            </figure>
          </div>
        </div>
      </section>

      <!-- Recursos -->
      <section id="recursos" aria-labelledby="h-recursos">
        <div class="sectionHead">
          <div>
            <h2 id="h-recursos">Recursos e checklist (para preparar a aula)</h2>
            <p>Gera uma lista rápida para levar para a sala.</p>
          </div>
        </div>

        <div class="grid2">
          <div class="card resources">
            <label for="turma">Turma / Ano</label>
            <input id="turma" type="text" placeholder="Ex.: 7.º A / TIC" />

            <div style="height:.8rem"></div>

            <label for="objetivo">Objectivo principal</label>
            <input id="objetivo" type="text" placeholder="Ex.: usar variáveis e colisões num mini-jogo" />

            <div class="row" style="margin-top:1rem">
              <button class="btn primary" type="button" id="genBtn">Gerar checklist</button>
              <button class="btn" type="button" id="copyBtn">Copiar</button>
            </div>

            <div style="height:.9rem"></div>
            <label for="out">Checklist gerada</label>
            <input id="out" type="text" readonly value="Preenche os campos e clica em Gerar checklist." />
            <p style="margin:.7rem 0 0; color: var(--muted); font-size:.95rem;">
              Sugestão: acrescenta “rubrica 0–4” (funciona bem para avaliação rápida).
            </p>
          </div>

          <div class="card resources">
            <h3 style="margin:.1rem 0 .35rem;">Rubrica rápida (0–4)</h3>
            <p style="margin:.2rem 0 .7rem; color: var(--muted);">
              Usa esta grelha para avaliar sem complicar:
            </p>
            <ul style="margin:.2rem 0 0; color: var(--muted); padding-left: 1.1rem;">
              <li><strong>Funciona (0–4):</strong> o projecto corre sem erros e cumpre o cenário.</li>
              <li><strong>Lógica (0–4):</strong> uso correcto de eventos/variáveis/mensagens.</li>
              <li><strong>Interacção (0–4):</strong> controlos, feedback e objectivos claros.</li>
              <li><strong>Criatividade (0–4):</strong> narrativa/arte/sons e personalização.</li>
              <li><strong>Explicação (0–4):</strong> consegue explicar as decisões e melhorias.</li>
            </ul>
            <div class="row" style="margin-top:1rem">
              <a class="btn" href="#aulas">Voltar aos planos</a>
              <button class="btn" type="button" id="helpBtn">Dicas de diferenciação</button>
            </div>
          </div>
        </div>
      </section>

      <dialog id="imgModal" aria-labelledby="modalTitle">
        <div class="modalHead">
          <strong id="modalTitle">Imagem</strong>
          <button class="btn" id="closeModal" type="button">Fechar ✕</button>
        </div>
        <div class="modalBody" id="modalBody">
          <!-- conteúdo injectado por JS -->
        </div>
      </dialog>
    </div>
  </main>

  <footer>
    <div class="wrap">
      <div class="foot">
        <div>
          <strong>Scratch na Sala de Aula</strong><br/>
          <span>Site demo (HTML/CSS/JS) — pronto para personalizar.</span>
        </div>
        <div class="chip">Acessibilidade: foco visível · navegação por teclado · modal com ESC</div>
      </div>
    </div>
  </footer>

  <script>
    // Menu mobile
    const menuBtn = document.getElementById('menuBtn');
    const navPanel = document.getElementById('navPanel');
    menuBtn?.addEventListener('click', () => {
      const expanded = menuBtn.getAttribute('aria-expanded') === 'true';
      menuBtn.setAttribute('aria-expanded', String(!expanded));
      navPanel.hidden = expanded;
    });

    // Impressão
    document.getElementById('printBtn')?.addEventListener('click', () => window.print());

    // Checklist
    const turma = document.getElementById('turma');
    const objetivo = document.getElementById('objetivo');
    const out = document.getElementById('out');

    document.getElementById('genBtn')?.addEventListener('click', () => {
      const t = (turma.value || 'Turma').trim();
      const o = (objetivo.value || 'Objectivo').trim();

      const items = [
        `✅ ${t}: computadores/Internet e Scratch (web/app) a funcionar`,
        `✅ Pastas de projecto: nome do aluno + versão`,
        `✅ ${o}: critérios (Funciona, Lógica, Interacção, Criatividade, Explicação)`,
        `✅ Cenário: 1 fundo + 2 sprites (mín.)`,
        `✅ Extensão: som/tempo/dificuldade (para quem termina cedo)`,
        `✅ Partilha final: 2 min por grupo para demonstrar e explicar`
      ];
      out.value = items.join(' | ');
    });

    document.getElementById('copyBtn')?.addEventListener('click', async () => {
      try{
        await navigator.clipboard.writeText(out.value);
        out.value = 'Copiado! ' + out.value;
      }catch(e){
        out.value = 'Não foi possível copiar automaticamente. Selecciona e copia manualmente: ' + out.value;
      }
    });

    // Dicas de diferenciação
    document.getElementById('helpBtn')?.addEventListener('click', () => {
      alert(
        'Diferenciação rápida:\\n' +
        '• Apoio: dar um guião com 6 blocos essenciais (evento → movimento → colisão → pontos).\\n' +
        '• Médio: adicionar tempo e nível de dificuldade.\\n' +
        '• Avançado: clones, power-ups, ecrã inicial e tabela de pontuações.'
      );
    });

    // Modal de imagens (galeria + botões)
    const modal = document.getElementById('imgModal');
    const modalTitle = document.getElementById('modalTitle');
    const modalBody = document.getElementById('modalBody');
    const closeModal = document.getElementById('closeModal');

    function openModal(title, svgMarkup, desc){
      modalTitle.textContent = title;
      modalBody.innerHTML = svgMarkup + `<p>${desc}</p>`;
      modal.showModal();
      closeModal.focus();
    }

    closeModal?.addEventListener('click', () => modal.close());
    modal?.addEventListener('click', (e) => {
      // fecha ao clicar fora do conteúdo
      const rect = modal.getBoundingClientRect();
      const inDialog =
        e.clientX >= rect.left && e.clientX <= rect.right &&
        e.clientY >= rect.top && e.clientY <= rect.bottom;
      if(!inDialog) modal.close();
    });
    document.addEventListener('keydown', (e) => {
      if(e.key === 'Escape' && modal?.open) modal.close();
    });

    // Galeria: abre SVG ampliado
    const figures = document.querySelectorAll('figure[tabindex="0"]');
    figures.forEach(fig => {
      const open = () => {
        const title = fig.getAttribute('data-title') || 'Imagem';
        const svg = fig.querySelector('svg')?.outerHTML || '';
        openModal(title, svg, 'Podes usar esta imagem como inspiração para fundos/sprites no Scratch.');
      };
      fig.addEventListener('click', open);
      fig.addEventListener('keydown', (e) => {
        if(e.key === 'Enter' || e.key === ' ') { e.preventDefault(); open(); }
      });
    });

    // Botões "Ver imagem do cenário" nos planos
    document.querySelectorAll('button[data-modal]').forEach(btn => {
      btn.addEventListener('click', () => {
        const title = btn.getAttribute('data-modal') || 'Cenário';
        // Reaproveita a imagem do lado direito do plano (svg mais próximo)
        const parent = btn.closest('.lesson');
        const svg = parent?.querySelector('.imgBox svg')?.outerHTML || '';
        openModal('Cenário: ' + title, svg, 'Sugestão: começa com uma versão mínima e evolui por iterações (v1, v2, v3).');
      });
    });
  </script>
</body>
</html>
