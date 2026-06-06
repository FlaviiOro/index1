<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Atousa G — House of G$ at Halcyon</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,500;1,300;1,400&family=Bebas+Neue&family=Space+Mono&display=swap" rel="stylesheet"/>
<style>
  *{box-sizing:border-box;margin:0;padding:0}
  :root{
    --black:#060606;
    --near:#0e0e0e;
    --char:#191919;
    --gun:#242428;
    --silver:#b0b0bc;
    --bright:#e0e0ea;
    --gold:#c4a24a;
    --gold2:#dfc07a;
    --teal:#00e8c8;
    --white:#f0f0ee;
    --dim:#555;
  }
  html{scroll-behavior:smooth}
  body{background:var(--black);color:var(--silver);font-family:'Cormorant Garamond','Georgia',serif;-webkit-font-smoothing:antialiased;overflow-x:hidden}

  /* NOISE */
  body::after{content:'';position:fixed;inset:0;background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");pointer-events:none;z-index:999;opacity:.5}

  .bebas{font-family:'Bebas Neue','Impact',sans-serif}
  .mono{font-family:'Space Mono','Courier New',monospace}

  /* TOP RULE */
  .top-rule{height:1px;background:linear-gradient(90deg,transparent,rgba(196,162,74,.5),transparent)}

  /* HEADER */
  .header{padding:80px 32px 52px;text-align:center;position:relative}
  .header::before{content:'';position:absolute;bottom:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,rgba(255,255,255,.04),transparent)}
  .eyebrow{font-family:'Space Mono',monospace;font-size:9px;letter-spacing:.42em;color:var(--gold);text-transform:uppercase;margin-bottom:18px;display:block}
  .main-title{font-size:clamp(52px,12vw,108px);letter-spacing:.04em;color:var(--white);line-height:.9;text-shadow:0 0 80px rgba(196,162,74,.1)}
  .main-title span{color:var(--gold)}
  .subtitle{font-style:italic;font-size:clamp(16px,2.5vw,20px);color:#666;max-width:440px;margin:20px auto 0;line-height:1.65}

  /* DOWNLOADS */
  .section{max-width:820px;margin:0 auto;padding:52px 24px}
  .section-label{font-family:'Space Mono',monospace;font-size:8px;letter-spacing:.38em;color:var(--dim);text-transform:uppercase;margin-bottom:16px;display:block}
  .dl-list{display:flex;flex-direction:column;gap:10px;margin-bottom:0}
  .dl-link{display:flex;align-items:center;gap:16px;padding:20px 22px;background:var(--near);border:1px solid rgba(255,255,255,.06);border-left:3px solid var(--gold);text-decoration:none;transition:background .25s,transform .25s}
  .dl-link:hover{background:var(--char);transform:translateX(4px)}
  .dl-icon{font-size:20px;flex-shrink:0}
  .dl-text strong{display:block;font-family:'Bebas Neue',sans-serif;font-size:17px;color:var(--white);letter-spacing:.06em;line-height:1}
  .dl-text em{font-size:13px;color:#555;font-style:italic;margin-top:2px;display:block}
  .dl-arrow{font-family:'Space Mono',monospace;font-size:10px;color:var(--gold);margin-left:auto;flex-shrink:0}

  /* FILTERS */
  .filters{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px}
  .filter-btn{font-family:'Space Mono',monospace;font-size:8px;letter-spacing:.28em;text-transform:uppercase;background:none;border:1px solid rgba(255,255,255,.1);color:#555;padding:7px 16px;cursor:pointer;transition:all .2s}
  .filter-btn:hover,.filter-btn.active{border-color:var(--gold);color:var(--gold);background:rgba(196,162,74,.07)}

  /* GRID */
  .grid-wrap{max-width:1100px;margin:0 auto;padding:0 12px 80px}
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:10px}

  /* CARD */
  .card{position:relative;overflow:hidden;background:var(--char);cursor:pointer;display:block}
  .card img{width:100%;aspect-ratio:3/4;object-fit:cover;display:block;transition:transform .5s ease}
  .card:hover img{transform:scale(1.04)}
  .card-placeholder{width:100%;aspect-ratio:3/4;background:linear-gradient(135deg,var(--char),var(--near));display:flex;flex-direction:column;justify-content:flex-end;padding:16px}
  .card-base{position:absolute;bottom:0;left:0;right:0;background:linear-gradient(to top,rgba(0,0,0,.85),transparent);padding:36px 14px 12px;transition:opacity .3s}
  .card-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.93) 0%,rgba(0,0,0,.2) 55%,transparent 100%);opacity:0;transition:opacity .3s;display:flex;flex-direction:column;justify-content:flex-end;padding:20px}
  .card:hover .card-overlay{opacity:1}
  .card:hover .card-base{opacity:0}
  .card-tag{font-family:'Space Mono',monospace;font-size:7px;color:var(--gold);letter-spacing:.28em;text-transform:uppercase;margin-bottom:3px;display:block}
  .card-venue{font-family:'Bebas Neue',sans-serif;font-size:14px;color:var(--white);letter-spacing:.05em;line-height:1.1}
  .card-caption{font-style:italic;font-size:13px;color:#ccc;line-height:1.5;margin-top:7px}

  /* LIGHTBOX */
  #lightbox{position:fixed;inset:0;background:rgba(0,0,0,.94);z-index:500;display:none;align-items:center;justify-content:center;padding:20px}
  #lightbox.open{display:flex}
  .lb-inner{max-width:660px;width:100%;background:var(--near);border:1px solid rgba(196,162,74,.15);overflow:hidden}
  .lb-inner img{width:100%;max-height:62vh;object-fit:cover;display:block}
  .lb-body{padding:22px 26px}
  .lb-meta{font-family:'Space Mono',monospace;font-size:8px;color:var(--gold);letter-spacing:.28em;margin-bottom:10px;display:block}
  .lb-caption{font-style:italic;font-size:19px;color:var(--bright);line-height:1.55}
  .lb-close{display:block;width:100%;padding:13px;background:rgba(196,162,74,.04);border:none;border-top:1px solid rgba(196,162,74,.1);color:var(--dim);font-family:'Space Mono',monospace;font-size:9px;letter-spacing:.32em;cursor:pointer;text-transform:uppercase;transition:background .2s}
  .lb-close:hover{background:rgba(196,162,74,.08)}

  /* VENUES */
  .venues{border-top:1px solid rgba(255,255,255,.04);border-bottom:1px solid rgba(255,255,255,.04);background:var(--near);padding:40px 28px;text-align:center}
  .venues-list{display:flex;gap:20px 36px;flex-wrap:wrap;justify-content:center;margin-top:20px}
  .venues-list span{font-style:italic;font-size:14px;color:#3a3a3a}

  /* FOOTER */
  .footer{padding:60px 28px;text-align:center}
  .footer p{font-style:italic;font-size:18px;color:#444;margin-bottom:20px}
  .footer a{display:inline-block;padding:13px 34px;border:1px solid var(--gold);color:var(--gold);font-family:'Space Mono',monospace;font-size:9px;letter-spacing:.32em;text-decoration:none;transition:background .25s}
  .footer a:hover{background:rgba(196,162,74,.07)}
  .bottom-rule{height:1px;background:linear-gradient(90deg,transparent,rgba(196,162,74,.2),transparent)}

  /* FADE IN */
  @keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
  .header,.section,.grid-wrap{animation:fadeUp .8s ease both}

  @media(max-width:600px){
    .header{padding:56px 20px 40px}
    .section{padding:40px 16px}
    .grid{grid-template-columns:repeat(2,1fr);gap:6px}
    .grid-wrap{padding:0 6px 60px}
  }
</style>
</head>
<body>

<div class="top-rule"></div>

<!-- HEADER -->
<div class="header">
  <span class="eyebrow">The Space · The Pieces · The Night</span>
  <h1 class="bebas main-title">HOUSE OF G$<br><span>AT HALCYON</span></h1>
  <p class="subtitle">Upstairs, where the racks glow under club lights and every piece has somewhere to be.</p>
</div>

<!-- DOWNLOADS -->
<div class="section">
  <span class="section-label">Press Assets</span>
  <div class="dl-list">
    <a class="dl-link" href="https://drive.google.com/file/d/1TaikUTr0R8ZHuiPVkiTy0m1J013Lb4Rg/view" target="_blank">
      <span class="dl-icon">📖</span>
      <div class="dl-text"><strong>2026 Lookbook</strong><em>Full collection, editorial photography</em></div>
      <span class="dl-arrow">↗</span>
    </a>
    <a class="dl-link" href="https://drive.google.com/file/d/1pMhoxjIGRVAyXpfIUGV5Dcs4kTzFQcC3/view" target="_blank">
      <span class="dl-icon">📁</span>
      <div class="dl-text"><strong>2026 Press Kit</strong><em>Brand story, product descriptions, hi-res assets</em></div>
      <span class="dl-arrow">↗</span>
    </a>
    <a class="dl-link" href="https://pem.sdy.mybluehost.me/wp-content/uploads/2026/01/A2SAG-PRESS-DECK-2023.pdf" target="_blank">
      <span class="dl-icon">🗃</span>
      <div class="dl-text"><strong>2023 Press Deck</strong><em>The archive — the brand before the brand</em></div>
      <span class="dl-arrow">↗</span>
    </a>
  </div>
</div>

<!-- FILTERS + GRID -->
<div class="section" style="padding-bottom:0">
  <span class="section-label">Browse by</span>
  <div class="filters">
    <button class="filter-btn active" data-filter="all">All</button>
    <button class="filter-btn" data-filter="space">The Space</button>
    <button class="filter-btn" data-filter="collection">Collection</button>
    <button class="filter-btn" data-filter="editorial">Editorial</button>
    <button class="filter-btn" data-filter="event">Events</button>
  </div>
</div>

<div class="grid-wrap">
  <div class="grid" id="grid">

    <div class="card" data-type="space"
      data-tag="The Sign" data-venue="Halcyon · Level Two · SF"
      data-caption="She set up the sign herself. 'UPSTAIRS. ATOUSA G. HOUSE OF G$. POP UP SHOP.' — and that was the entire marketing campaign."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4953.webp?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4953.webp?resize=700%2C900&ssl=1" alt="The Sign" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE SIGN</span><span class="card-venue bebas">Halcyon · Level Two · SF</span></div>
      <div class="card-base"><span class="card-tag">The Sign</span><span class="card-venue">Halcyon · Level Two · SF</span></div>
      <div class="card-overlay"><span class="card-tag">The Sign</span><span class="card-venue">Halcyon · Level Two · SF</span><p class="card-caption">She set up the sign herself. The whole marketing campaign in one letter board.</p></div>
    </div>

    <div class="card" data-type="space"
      data-tag="The Racks" data-venue="House of G$ · Opening Night"
      data-caption="Sequins against black curtain. Neons against metallics. A whole archive moved from LA and hung under club lights."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4945.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4945.jpg?resize=700%2C900&ssl=1" alt="The Racks" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE RACKS</span><span class="card-venue bebas">House of G$ · Opening Night</span></div>
      <div class="card-base"><span class="card-tag">The Racks</span><span class="card-venue">House of G$ · Opening Night</span></div>
      <div class="card-overlay"><span class="card-tag">The Racks</span><span class="card-venue">House of G$ · Opening Night</span><p class="card-caption">Sequins against black curtain. A whole archive moved from LA and hung under club lights.</p></div>
    </div>

    <div class="card" data-type="space"
      data-tag="The Lounge" data-venue="The Whole World · Upstairs"
      data-caption="Two racks. A geometric ottoman. LED strips on the floor. Mirror panels above reflecting everything back at you. This is where you come upstairs."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/Screenshot-2026-01-19-at-9.05.51-PM.png?fit=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/Screenshot-2026-01-19-at-9.05.51-PM.png?fit=700%2C900&ssl=1" alt="The Lounge" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE LOUNGE</span><span class="card-venue bebas">The Whole World · Upstairs</span></div>
      <div class="card-base"><span class="card-tag">The Lounge</span><span class="card-venue">The Whole World · Upstairs</span></div>
      <div class="card-overlay"><span class="card-tag">The Lounge</span><span class="card-venue">The Whole World · Upstairs</span><p class="card-caption">Two racks. A geometric ottoman. LED strips on the floor. Mirror panels above. This is where you come upstairs.</p></div>
    </div>

    <div class="card" data-type="collection"
      data-tag="The Hats" data-venue="Accessories · House of G$"
      data-caption="Looking down through the railing to the Halcyon floor below. Two worlds, one staircase, one building."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_5008.jpg?fit=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_5008.jpg?fit=700%2C900&ssl=1" alt="The Hats" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE HATS</span><span class="card-venue bebas">Accessories · House of G$</span></div>
      <div class="card-base"><span class="card-tag">The Hats</span><span class="card-venue">Accessories · House of G$</span></div>
      <div class="card-overlay"><span class="card-tag">The Hats</span><span class="card-venue">Accessories · House of G$</span><p class="card-caption">Looking down through the railing to the club floor below. Two worlds, one staircase.</p></div>
    </div>

    <div class="card" data-type="editorial"
      data-tag="The Piece" data-venue="A Line Called K · Statement Hat"
      data-caption="Gold chain fringe. Wide brim. Cascades over the face and hides nothing. One of those pieces that ends conversations and starts nights."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4950.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4950.jpg?resize=700%2C900&ssl=1" alt="The Piece" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE PIECE</span><span class="card-venue bebas">A Line Called K · Statement Hat</span></div>
      <div class="card-base"><span class="card-tag">The Piece</span><span class="card-venue">A Line Called K · Statement Hat</span></div>
      <div class="card-overlay"><span class="card-tag">The Piece</span><span class="card-venue">A Line Called K · Statement Hat</span><p class="card-caption">Gold chain fringe. Cascades over the face and hides nothing. One of those pieces that ends conversations.</p></div>
    </div>

    <div class="card" data-type="event"
      data-tag="Downstairs" data-venue="Halcyon Main Floor · SF"
      data-caption="Laser beams through smoke haze. The HALCYON sign glowing blue-white. The world you come from — before you find the lounge upstairs."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4956.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4956.jpg?resize=700%2C900&ssl=1" alt="Halcyon Floor" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">DOWNSTAIRS</span><span class="card-venue bebas">Halcyon Main Floor · SF</span></div>
      <div class="card-base"><span class="card-tag">Downstairs</span><span class="card-venue">Halcyon Main Floor · SF</span></div>
      <div class="card-overlay"><span class="card-tag">Downstairs</span><span class="card-venue">Halcyon Main Floor · SF</span><p class="card-caption">Laser beams through smoke. The world you come from before you find the lounge upstairs.</p></div>
    </div>

    <div class="card" data-type="editorial"
      data-tag="A2SA × Kastle" data-venue="Collaboration · Limited Capsule"
      data-caption="Two creative forces. One limited capsule. The crossover that felt inevitable once it happened."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4955.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4955.jpg?resize=700%2C900&ssl=1" alt="Collaboration" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">A2SA × KASTLE</span><span class="card-venue bebas">Collaboration · Limited Capsule</span></div>
      <div class="card-base"><span class="card-tag">A2SA × Kastle</span><span class="card-venue">Collaboration · Limited Capsule</span></div>
      <div class="card-overlay"><span class="card-tag">A2SA × Kastle</span><span class="card-venue">Collaboration · Limited Capsule</span><p class="card-caption">Two creative forces. One limited capsule. The crossover that felt inevitable.</p></div>
    </div>

    <div class="card" data-type="collection"
      data-tag="New Drop" data-venue="LA Archive → SF"
      data-caption="Straight from the LA archive. Limited. Sequins, metallics, movement. Meant for one woman each."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_8286-scaled.jpeg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_8286-scaled.jpeg?resize=700%2C900&ssl=1" alt="New Drop" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">NEW DROP</span><span class="card-venue bebas">LA Archive → SF</span></div>
      <div class="card-base"><span class="card-tag">New Drop</span><span class="card-venue">LA Archive → SF</span></div>
      <div class="card-overlay"><span class="card-tag">New Drop</span><span class="card-venue">LA Archive → SF</span><p class="card-caption">Straight from the LA archive. Limited. Meant for one woman each.</p></div>
    </div>

  </div>
</div>

<!-- VENUES STRIP -->
<div class="venues">
  <span class="section-label" style="margin-bottom:0">Seen at</span>
  <div class="venues-list">
    <span>Halcyon · SF</span>
    <span>Do Not Sit On The Furniture · Miami</span>
    <span>Great Northern · SF</span>
    <span>Monarch · SF</span>
    <span>BPM Festival</span>
    <span>Sunset Campout</span>
    <span>SXM Festival</span>
    <span>Symbiosis</span>
  </div>
</div>

<!-- FOOTER -->
<div class="footer">
  <p>Press inquiries &amp; collaborations</p>
  <a href="mailto:press@atousag.com">Contact for Press</a>
</div>
<div class="bottom-rule"></div>

<!-- LIGHTBOX -->
<div id="lightbox">
  <div class="lb-inner">
    <img id="lb-img" src="" alt=""/>
    <div class="lb-body">
      <span class="lb-meta" id="lb-meta"></span>
      <p class="lb-caption" id="lb-caption"></p>
    </div>
    <button class="lb-close" onclick="closeLightbox()">Close ✕</button>
  </div>
</div>

<script>
  // FILTERS
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const f = btn.dataset.filter;
      document.querySelectorAll('.card').forEach(card => {
        card.style.display = (f === 'all' || card.dataset.type === f) ? 'block' : 'none';
      });
    });
  });

  // LIGHTBOX OPEN
  document.querySelectorAll('.card').forEach(card => {
    card.addEventListener('click', () => {
      const lb = document.getElementById('lightbox');
      document.getElementById('lb-img').src = card.dataset.src;
      document.getElementById('lb-meta').textContent = card.dataset.tag + ' · ' + card.dataset.venue;
      document.getElementById('lb-caption').textContent = '"' + card.dataset.caption + '"';
      lb.classList.add('open');
      document.body.style.overflow = 'hidden';
    });
  });

  // LIGHTBOX CLOSE
  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('open');
    document.body.style.overflow = '';
  }
  document.getElementById('lightbox').addEventListener('click', function(e) {
    if (e.target === this) closeLightbox();
  });
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeLightbox(); });
</script>
</body>
</html>
