<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Royal Restobar — Ultra Premium</title>
<meta name="description" content="Royal Restobar — Luxury dining, handcrafted cocktails, reservations, and more.">

<style>
:root{
  --bg:#0b0b0b;
  --card:#0f0f12;
  --muted:#cfc7d9;
  --accent:gold;
  --accent-2:#ffd700;
  --glass: rgba(255,255,255,0.06);
  --glass-border: rgba(255,255,255,0.06);
  --glass-blur: 10px;
  --radius:14px;
}
body.wine-theme{
  --bg:#0b0206;
  --card:#12060a;
  --muted:#f0dbe3;
  --accent:#b52b3a;
  --accent-2:#ff9fb0;
  --glass: rgba(255,240,240,0.03);
  --glass-border: rgba(255,255,255,0.04);
}

*{box-sizing:border-box;}
body{
  margin:0;
  font-family:Inter, "Poppins", sans-serif;
  background:var(--bg);
  color:#fff;
  overflow-x:hidden;
  scroll-behavior:smooth;
}
.container{max-width:1200px;margin:0 auto;padding:0 20px}
.center{text-align:center;}
.h1{font-size:clamp(28px,4vw,56px);margin-bottom:12px;}
.h2{font-size:clamp(20px,2.2vw,32px);margin-bottom:10px;color:var(--accent-2);}
.p-muted{color:var(--muted);font-size:16px;margin-bottom:18px;}
.header{
  position:fixed;top:0;left:0;width:100%;z-index:100;
  background:linear-gradient(180deg, rgba(0,0,0,0.5), rgba(0,0,0,0.15));
  border-bottom:1px solid rgba(255,255,255,0.04);
  backdrop-filter: blur(10px);
}
.header .nav-inner{display:flex;justify-content:space-between;align-items:center;padding:16px 20px;}
.brand{font-weight:800;letter-spacing:1px;color:var(--accent);font-size:20px;}
.nav-links{display:flex;gap:20px;align-items:center;}
.nav-links a{color:var(--muted);text-decoration:none;padding:8px 10px;border-radius:8px;font-weight:600;}
.nav-links a:hover{color:#fff;background:rgba(255,255,255,0.03);}
.toggle-btn{cursor:pointer;padding:8px;border-radius:10px;background:var(--glass);border:1px solid var(--glass-border);color:var(--muted);font-weight:700;margin-left:12px;}
.hero{
  position:relative;height:92vh;display:flex;align-items:center;justify-content:center;overflow:hidden;padding-top:64px;
}
.hero-slider{position:absolute;inset:0;}
.hero-slide{
  position:absolute;inset:0;background-size:cover;background-position:center;opacity:0;transform:scale(1.03);transition:1s ease;filter:brightness(0.55);
}
.hero-slide.show{opacity:1;transform:scale(1);filter:brightness(0.55) contrast(1.02);}
.hero::after{
  content:"";position:absolute;inset:0;
  background:linear-gradient(120deg, rgba(90,12,110,0.12), rgba(20,6,50,0.08));
  mix-blend-mode: overlay;pointer-events:none;
}
.particles{
  position:absolute;inset:0;pointer-events:none;opacity:0.5;
  background-image: radial-gradient(rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 80px 80px;
}
.hero-card{
  position:relative;z-index:10;max-width:980px;margin:auto;background:var(--glass);
  border-radius:var(--radius);padding:36px;border:1px solid var(--glass-border);backdrop-filter: blur(var(--glass-blur));
  display:flex;gap:24px;align-items:center;justify-content:space-between;box-shadow:0 10px 40px rgba(0,0,0,0.6);
}
.hero-left{flex:1;}
.hero-right{width:320px;max-width:35%;min-width:240px;}
.hero-left .eyebrow{color:var(--muted);font-weight:700;letter-spacing:1px;font-size:12px;margin-bottom:8px;}
.hero-left h1{font-size:36px;margin:6px 0;color:var(--accent);}
.btn-primary{
  background:linear-gradient(90deg,var(--accent), #ffd97a);
  color:#111;border:none;padding:12px 20px;border-radius:999px;font-weight:700;cursor:pointer;
  box-shadow:0 4px 20px rgba(255,215,0,0.5);
  transition:0.3s;
}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 6px 25px rgba(255,215,0,0.7);}
.small-cta{display:inline-block;margin-top:10px;color:var(--muted);font-size:14px;}
.section{padding:80px 0;opacity:0;transform:translateY(40px);transition:0.8s ease;}
.section.show{opacity:1;transform:translateY(0);}
.features-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:20px;margin-top:28px;}
.feature{background:var(--card);padding:20px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);backdrop-filter:blur(6px);transition:0.3s;box-shadow:0 10px 30px rgba(0,0,0,0.5);}
.feature:hover{transform:translateY(-8px);box-shadow:0 18px 40px rgba(0,0,0,0.7);}
.feature h3{color:var(--accent-2);margin-bottom:8px;}
.feature p{color:var(--muted);}
.gallery{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:22px;}
.card{position:relative;border-radius:12px;overflow:hidden;border:1px solid rgba(255,255,255,0.04);cursor:pointer;transition:0.3s;}
.card img{width:100%;height:220px;object-fit:cover;transition:transform .5s;}
.card:hover img{transform:scale(1.06);}
.card .meta{position:absolute;left:12px;bottom:12px;background:linear-gradient(90deg, rgba(0,0,0,0.45), rgba(0,0,0,0.25));padding:10px;border-radius:8px;}
.card .meta h4{margin:0;color:var(--accent);font-size:16px;}
.card .meta p{margin:4px 0 0;color:var(--muted);font-size:13px;}
.lightbox{position:fixed;inset:0;background:rgba(0,0,0,0.85);display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:0.3s;z-index:200;}
.lightbox.show{opacity:1;pointer-events:auto;}
.lightbox img{max-width:90%;max-height:80%;border-radius:12px;box-shadow:0 10px 50px rgba(0,0,0,0.7);}
.testimonials{position:relative;overflow:hidden;margin-top:20px;}
.t-slide{min-height:140px;padding:18px;background:var(--card);border-radius:12px;border:1px solid rgba(255,255,255,0.03);color:var(--muted);display:none;}
.t-slide.active{display:block;}
.t-controls{display:flex;gap:10px;justify-content:center;margin-top:12px;}
.t-dot{width:10px;height:10px;border-radius:50%;background:rgba(255,255,255,0.08);cursor:pointer;}
.t-dot.active{background:var(--accent);}
.chef{display:flex;gap:22px;align-items:center;margin-top:24px;}
.chef img{width:220px;height:220px;object-fit:cover;border-radius:12px;border:1px solid rgba(255,255,255,0.04);}
.chef .bio{color:var(--muted);}
.form-card{max-width:700px;margin:20px auto;background:var(--glass);padding:24px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);backdrop-filter:blur(var(--glass-blur));}
.form-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;}
.form-grid .full{grid-column:1/-1;}
input,select,textarea{width:100%;padding:12px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:#fff;}
textarea{min-height:110px;resize:vertical;}
input::placeholder,textarea::placeholder{color:rgba(255,255,255,0.35);}
.modal,.lightbox{transition:0.3s;}
.modal-card{background:var(--glass);padding:22px;border-radius:12px;border:1px solid rgba(255,255,255,0.06);max-width:720px;width:90%;}
.whatsapp{position:fixed;right:20px;bottom:20px;background:#25d366;color:#fff;width:54px;height:54px;border-radius:50%;display:flex;align-items:center;justify-content:center;box-shadow:0 8px 30px rgba(0,0,0,0.6);z-index:70;cursor:pointer;}
.map-wrap{margin-top:18px;border-radius:10px;overflow:hidden;border:1px solid rgba(255,255,255,0.03);}
@media (max-width:900px){.gallery{grid-template-columns:repeat(2,1fr);}.hero-card{flex-direction:column;gap:16px;padding:22px}.hero-right{width:100%;max-width:100%}.chef{flex-direction:column}.form-grid{grid-template-columns:1fr}}
@media (max-width:520px){.gallery{grid-template-columns:1fr}.hero-left h1{font-size:26px}.nav-links{display:none}}

</style>
</head>
<body>
<header class="header">
  <div class="nav-inner container">
    <div class="brand flex"><div style="font-size:20px;margin-right:12px">🍷</div>Royal Restobar</div>
    <nav class="nav-links">
      <a href="#hero">Home</a>
      <a href="#menu">Menu</a>
      <a href="#about">About</a>
      <a href="#reservation">Reserve</a>
      <a href="#contact">Contact</a>
      <button class="toggle-btn" id="themeToggle">Wine Theme</button>
    </nav>
  </div>
</header>
<section id="hero" class="hero">
  <div class="hero-slider">
    <div class="hero-slide show" style="background-image:url('https://images.unsplash.com/photo-1552566626-52f8b828add9')"></div>
    <div class="hero-slide" style="background-image:url('https://images.unsplash.com/photo-1528605248644-14dd04022da1')"></div>
    <div class="hero-slide" style="background-image:url('https://images.unsplash.com/photo-1514933651103-005eec06c04b')"></div>
  </div>
  <div class="particles"></div>
  <div class="hero-card container">
    <div class="hero-left">
      <div class="eyebrow">Luxury • Cocktails • Fine Dining</div>
      <h1>Fine Dining & Exquisite Cocktails</h1>
      <p class="p-muted">Indulge in a curated culinary experience. Fresh ingredients, handcrafted recipes, and a warm luxurious ambience.</p>
      <div>
        <button class="btn-primary" onclick="document.getElementById('reservation').scrollIntoView({behavior:'smooth'})">Reserve a Table</button>
        <a class="small-cta" href="#menu" style="margin-left:14px">See today's menu →</a>
      </div>
    </div>
    <div class="hero-right">
      <div class="mini-card">
        <h4>Chef’s Special</h4>
        <div class="mini-item"><span>Seared Salmon</span><strong>$28</strong></div>
        <div class="mini-item"><span>Truffle Risotto</span><strong>$24</strong></div>
        <div class="mini-item"><span>Espresso Martini</span><strong>$12</strong></div>
      </div>
      <div style="height:12px"></div>
      <div class="mini-card">
        <h4>Hours</h4>
        <div style="color:var(--muted)">Mon - Sun</div>
        <div style="font-weight:700;margin-top:6px">5:00 PM — 12:00 AM</div>
      </div>
    </div>
  </div>
</section>
<section class="section container" id="features">
  <div class="center">
    <h3 class="h2">What Makes Us Special</h3>
    <p class="p-muted">A blend of premium flavors, elegant presentation, and impeccable service.</p>
  </div>
  <div class="features-grid">
    <div class="feature"><h3>Premium Ingredients</h3><p>We source seasonal and sustainable produce.</p></div>
    <div class="feature"><h3>Signature Cocktails</h3><p>Expertly mixed drinks with house-made syrups.</p></div>
    <div class="feature"><h3>Private Events</h3><p>Customized menus and private dining suites.</p></div>
  </div>
</section>
<section id="menu" class="section container">
  <div class="center">
    <h3 class="h2">Chef's Gallery</h3>
    <p class="p-muted">A peek at our delights — hover to preview and click to view larger.</p>
  </div>
  <div class="gallery">
    <div class="card" data-full="https://images.unsplash.com/photo-1600891964599-f61ba0e24092"><img src="https://images.unsplash.com/photo-1600891964599-f61ba0e24092" alt="Dish 1"><div class="meta"><h4>Signature Steak</h4><p>Grilled to perfection</p></div></div>
    <div class="card" data-full="https://images.unsplash.com/photo-1533777324565-a040eb52fac1"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoM2PT71H9_FAL6Tbf5XxMBlPizZ3yWrIRRwcWgpouxkEkpdsXG9aUXj4&s" alt="Dish 2"><div class="meta"><h4>Golden Cocktail</h4><p>Handcrafted mixer</p></div></div>
    <div class="card" data-full="https://images.unsplash.com/photo-1525755662778-989d0524087e"><img src="https://images.unsplash.com/photo-1525755662778-989d0524087e" alt="Dish 3"><div class="meta"><h4>Seafood Platter</h4><p>Fresh & seasonal</p></div></div>
  </div>
</section>
<section class="section container" id="testimonials">
  <div class="center">
    <h3 class="h2">What Guests Say</h3>
    <p class="p-muted">Real reviews from guests who loved the experience.</p>
  </div>
  <div class="testimonials">
    <div class="t-slide active"><strong>“Amazing experience — food and service were impeccable.”</strong><div style="margin-top:8px;color:var(--muted)">— Anita R.</div></div>
    <div class="t-slide"><strong>“The cocktails were creative, and the ambience was perfect.”</strong><div style="margin-top:8px;color:var(--muted)">— Marco P.</div></div>
    <div class="t-slide"><strong>“Perfect for celebrations. Staff went above and beyond.”</strong><div style="margin-top:8px;color:var(--muted)">— L. Chen</div></div>
    <div class="t-controls">
      <div class="t-dot active" data-dot="0"></div>
      <div class="t-dot" data-dot="1"></div>
      <div class="t-dot" data-dot="2"></div>
    </div>
  </div>
</section>
<section class="section container" id="about">
  <div class="center">
    <h3 class="h2">Meet the Chef</h3>
    <p class="p-muted">Our award-winning culinary director combines classic technique with modern flavours.</p>
  </div>
  <div class="chef">
    <img src="https://images.unsplash.com/photo-1544025162-d76694265947" alt="Chef portrait">
    <div class="bio">
      <h3>Chef Lorenzo Martín</h3>
      <p class="p-muted">With 18 years of experience across Michelin-star kitchens, Lorenzo crafts tasting menus that surprise and delight.</p>
    </div>
  </div>
</section>
<section id="reservation" class="section container">
  <div class="center">
    <h3 class="h2">Reserve Your Table</h3>
    <p class="p-muted">Quick and easy — your booking is confirmed instantly (demo).</p>
  </div>
  <div class="form-card">
    <form id="reservationForm" onsubmit="submitReservation(event)">
      <div class="form-grid">
        <input type="text" name="name" placeholder="Full Name" required>
        <input type="tel" name="phone" placeholder="Phone" required>
        <input type="date" name="date" required>
        <input type="time" name="time" required>
        <select name="guests" required>
          <option value="">Guests</option>
          <option>1</option><option>2</option><option>3</option><option>4</option><option>5+</option>
        </select>
        <input type="text" name="occasion" placeholder="Occasion (optional)">
        <textarea name="notes" placeholder="Special requests" class="full"></textarea>
      </div>
      <div style="margin-top:12px;display:flex;gap:12px;align-items:center;justify-content:center">
        <button type="submit" class="btn-primary">Confirm Reservation</button>
      </div>
    </form>
  </div>
</section>
<div class="whatsapp" onclick="window.open('https://wa.me/1234567890','_blank')">💬</div>
<div class="lightbox" id="lightbox"><img src="" alt="Dish"></div>
<script>
let slides=document.querySelectorAll('.hero-slide');let current=0;
setInterval(()=>{slides[current].classList.remove('show');current=(current+1)%slides.length;slides[current].classList.add('show');},5000);
const lightbox=document.getElementById('lightbox');document.querySelectorAll('.card').forEach(card=>{
  card.addEventListener('click',()=>{lightbox.querySelector('img').src=card.dataset.full;lightbox.classList.add('show');});
});
lightbox.addEventListener('click',()=>{lightbox.classList.remove('show');});
const tSlides=document.querySelectorAll('.t-slide');const tDots=document.querySelectorAll('.t-dot');let tIndex=0;
function showTestimonial(i){tSlides.forEach(s=>s.classList.remove('active'));tDots.forEach(d=>d.classList.remove('active'));tSlides[i].classList.add('active');tDots[i].classList.add('active');}
tDots.forEach(d=>d.addEventListener('click',()=>{tIndex=parseInt(d.dataset.dot);showTestimonial(tIndex);}));
setInterval(()=>{tIndex=(tIndex+1)%tSlides.length;showTestimonial(tIndex);},6000);
document.getElementById('themeToggle').addEventListener('click',()=>{document.body.classList.toggle('wine-theme');});
function submitReservation(e){e.preventDefault();alert('Reservation confirmed! Thank you.');e.target.reset();}
const sections=document.querySelectorAll('.section');window.addEventListener('scroll',()=>{sections.forEach(s=>{if(s.getBoundingClientRect().top<window.innerHeight-100){s.classList.add('show');}});});
</script>

</body>
</html>
