# index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chef Quality – Jaedon Evans</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
  :root {
    --gold: #C9A84C;
    --gold-light: #E8C97A;
    --cream: #F5EFE0;
    --dark: #0D0D0B;
    --charcoal: #1A1A17;
    --mid: #2C2C28;
    --text-muted: #8A8472;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--cream);
    font-family: 'Montserrat', sans-serif;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow-x: hidden;
  }

  /* Grain overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.6;
  }

  .page {
    position: relative;
    z-index: 1;
    width: 100%;
    max-width: 480px;
    padding: 2rem 1.5rem 3rem;
    animation: fadeUp 1s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Top ornament */
  .ornament {
    text-align: center;
    margin-bottom: 2rem;
    animation: fadeUp 1s 0.1s ease both;
  }

  .ornament svg {
    width: 180px;
    opacity: 0.65;
  }

  /* Card */
  .card {
    background: var(--charcoal);
    border: 1px solid rgba(201,168,76,0.25);
    border-radius: 2px;
    padding: 2.5rem 2rem;
    position: relative;
    box-shadow:
      0 0 0 1px rgba(201,168,76,0.06),
      0 30px 80px rgba(0,0,0,0.6),
      inset 0 1px 0 rgba(201,168,76,0.12);
  }

  /* Corner accents */
  .card::before, .card::after {
    content: '';
    position: absolute;
    width: 24px;
    height: 24px;
    border-color: var(--gold);
    border-style: solid;
    opacity: 0.5;
  }
  .card::before { top: 10px; left: 10px; border-width: 1px 0 0 1px; }
  .card::after  { bottom: 10px; right: 10px; border-width: 0 1px 1px 0; }

  .brand-line {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.6rem;
    letter-spacing: 0.35em;
    color: var(--gold);
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 0.6rem;
    animation: fadeUp 1s 0.2s ease both;
  }

  h1 {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: 2.8rem;
    text-align: center;
    letter-spacing: 0.05em;
    line-height: 1.1;
    color: var(--cream);
    margin-bottom: 0.2rem;
    animation: fadeUp 1s 0.3s ease both;
  }

  .tagline {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 1.05rem;
    color: var(--gold-light);
    text-align: center;
    letter-spacing: 0.08em;
    margin-bottom: 2rem;
    animation: fadeUp 1s 0.4s ease both;
  }

  .divider {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    margin: 1.6rem 0;
    animation: fadeUp 1s 0.45s ease both;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(201,168,76,0.35), transparent);
  }

  .divider-diamond {
    width: 5px;
    height: 5px;
    background: var(--gold);
    transform: rotate(45deg);
    opacity: 0.6;
    flex-shrink: 0;
  }

  /* Contact links */
  .contact-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 0.75rem 1rem;
    border: 1px solid rgba(201,168,76,0.1);
    border-radius: 1px;
    background: rgba(255,255,255,0.02);
    text-decoration: none;
    color: var(--cream);
    transition: all 0.3s ease;
    animation: fadeUp 1s ease both;
  }

  .contact-item:nth-child(1) { animation-delay: 0.5s; }
  .contact-item:nth-child(2) { animation-delay: 0.6s; }
  .contact-item:nth-child(3) { animation-delay: 0.7s; }
  .contact-item:nth-child(4) { animation-delay: 0.8s; }
  .contact-item:nth-child(5) { animation-delay: 0.9s; }

  .contact-item:hover {
    border-color: rgba(201,168,76,0.4);
    background: rgba(201,168,76,0.06);
    transform: translateX(4px);
  }

  .contact-icon {
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid rgba(201,168,76,0.25);
    border-radius: 1px;
    flex-shrink: 0;
  }

  .contact-icon svg {
    width: 16px;
    height: 16px;
    fill: var(--gold);
  }

  .contact-text {
    display: flex;
    flex-direction: column;
    gap: 0.1rem;
  }

  .contact-label {
    font-size: 0.58rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-muted);
    font-weight: 500;
  }

  .contact-value {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1rem;
    font-weight: 400;
    color: var(--cream);
    letter-spacing: 0.02em;
  }

  /* QR Section */
  .qr-section {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    animation: fadeUp 1s 1.0s ease both;
  }

  .qr-label {
    font-size: 0.58rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--text-muted);
  }

  .qr-frame {
    padding: 12px;
    background: #fff;
    border: 1px solid rgba(201,168,76,0.3);
    position: relative;
  }

  /* Corner ticks on QR frame */
  .qr-frame::before, .qr-frame::after {
    content: '';
    position: absolute;
    width: 16px;
    height: 16px;
    border-color: var(--gold);
    border-style: solid;
  }
  .qr-frame::before { top: -4px; left: -4px; border-width: 2px 0 0 2px; }
  .qr-frame::after  { bottom: -4px; right: -4px; border-width: 0 2px 2px 0; }

  #qrcode canvas, #qrcode img {
    display: block;
  }

  .bottom-mark {
    margin-top: 2.5rem;
    text-align: center;
    font-size: 0.55rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: rgba(138,132,114,0.4);
    animation: fadeUp 1s 1s ease both;
  }
</style>
</head>
<body>

<div class="page">

  <!-- Ornamental top rule -->
  <div class="ornament">
    <svg viewBox="0 0 300 30" fill="none" xmlns="http://www.w3.org/2000/svg">
      <line x1="0" y1="15" x2="115" y2="15" stroke="#C9A84C" stroke-width="0.5"/>
      <polygon points="130,15 138,9 146,15 138,21" fill="none" stroke="#C9A84C" stroke-width="0.6"/>
      <polygon points="150,15 155,10 160,15 155,20" fill="#C9A84C" opacity="0.5"/>
      <polygon points="154,15 162,9 170,15 162,21" fill="none" stroke="#C9A84C" stroke-width="0.6"/>
      <line x1="185" y1="15" x2="300" y2="15" stroke="#C9A84C" stroke-width="0.5"/>
    </svg>
  </div>

  <div class="card">
    <p class="brand-line">Culinary Artistry &amp; Catering</p>
    <h1>Jaedon Evans</h1>
    <p class="tagline">" Chef Quality "</p>

    <div class="divider">
      <div class="divider-line"></div>
      <div class="divider-diamond"></div>
      <div class="divider-line"></div>
    </div>

    <ul class="contact-list">
      <a class="contact-item" href="tel:7072082519">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M6.6 10.8c1.4 2.8 3.8 5.1 6.6 6.6l2.2-2.2c.3-.3.7-.4 1-.2 1.1.4 2.3.6 3.6.6.6 0 1 .4 1 1V20c0 .6-.4 1-1 1-9.4 0-17-7.6-17-17 0-.6.4-1 1-1h3.5c.6 0 1 .4 1 1 0 1.3.2 2.5.6 3.6.1.3 0 .7-.2 1L6.6 10.8z"/>
          </svg>
        </div>
        <div class="contact-text">
          <span class="contact-label">Phone</span>
          <span class="contact-value">(707) 208-2519</span>
        </div>
      </a>

      <a class="contact-item" href="mailto:chefquality23@gmail.com">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
          </svg>
        </div>
        <div class="contact-text">
          <span class="contact-label">Email</span>
          <span class="contact-value">chefquality23@gmail.com</span>
        </div>
      </a>

      <a class="contact-item" href="https://www.instagram.com/chefquality_?igsh=NTc4MTIwNjQ2YQ%3D%3D&utm_source=qr" target="_blank">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/>
          </svg>
        </div>
        <div class="contact-text">
          <span class="contact-label">Instagram</span>
          <span class="contact-value">@chefquality_</span>
        </div>
      </a>

      <a class="contact-item" href="https://yelp.to/sGu4S9tjjD" target="_blank">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 2C6.477 2 2 6.477 2 12s4.477 10 10 10 10-4.477 10-10S17.523 2 12 2zm-1.2 14.4l-3.6-2.1.9-1.5 2.7 1.575V8.4h1.8v8.1l-1.8-.1zm4.35-.525l-1.65-3.825 1.65-.675 1.65 3.825-1.65.675zm1.5-5.4l-3.45 1.425-.675-1.65 3.45-1.425.675 1.65zm-6.9-2.55l1.65 3.825-1.65.675-1.65-3.825 1.65-.675z"/>
          </svg>
        </div>
        <div class="contact-text">
          <span class="contact-label">Yelp</span>
          <span class="contact-value">Quality's Cuisine &amp; Catering</span>
        </div>
      </a>

      <a class="contact-item" href="https://www.facebook.com/profile.php?id=61578154060346&mibextid=wwXIfr" target="_blank">
        <div class="contact-icon">
          <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
          </svg>
        </div>
        <div class="contact-text">
          <span class="contact-label">Facebook</span>
          <span class="contact-value">Quality's Cuisine &amp; Catering</span>
        </div>
      </a>
    </ul>

    <div class="divider" style="margin-top:1.8rem;">
      <div class="divider-line"></div>
      <div class="divider-diamond"></div>
      <div class="divider-line"></div>
    </div>

    <div class="qr-section">
      <span class="qr-label">Scan to Connect</span>
      <div class="qr-frame">
        <div id="qrcode"></div>
      </div>
    </div>

  </div>

  <p class="bottom-mark">Quality's Cuisine &amp; Catering &nbsp;·&nbsp; Est. 2024</p>
</div>

<script>
  // Build a vCard data URL — QR links to a page that opens contact info.
  // We embed all info as a vCard in a data URI so no hosting is needed.
  const vcard = `BEGIN:VCARD
VERSION:3.0
FN:Jaedon Evans
ORG:Chef Quality
TEL;TYPE=CELL:+17072082519
EMAIL:chefquality23@gmail.com
URL;TYPE=Instagram:https://www.instagram.com/chefquality_
URL;TYPE=Facebook:https://www.facebook.com/profile.php?id=61578154060346
URL;TYPE=Yelp:https://yelp.to/sGu4S9tjjD
NOTE:Quality's Cuisine & Catering
END:VCARD`;

  new QRCode(document.getElementById("qrcode"), {
    text: vcard,
    width: 180,
    height: 180,
    colorDark: "#0D0D0B",
    colorLight: "#ffffff",
    correctLevel: QRCode.CorrectLevel.M
  });
</script>
</body>
</html>
