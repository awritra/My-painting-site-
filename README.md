# My-painting-site-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>χάρμα • Home</title>
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <header>
    <a href="index.html" class="logo">χάρμα</a>
    <nav>
      <a href="index.html">Home</a>
      <a href="gallery.html">Gallery</a>
      <a href="about.html">About</a>
      <a href="contact.html">Contact</a>
    </nav>
  </header>
  <main>
    <section class="hero">
      <h1>Welcome to χάρμα</h1>
      <p>A selection of my finest paintings awaits.</p>
      <a href="gallery.html" class="cta">View Gallery</a>
    </section>
  </main>
  <footer>© 2025 χάρμα. All rights reserved.</footer>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>χάρμα • Gallery</title>
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <header>
    <a href="index.html" class="logo">χάρμα</a>
    <nav>...</nav>
  </header>
  <main>
    <section class="filters">
      <button data-filter="all" class="active">All</button>
      <button data-filter="sale">For Sale</button>
      <button data-filter="sold">Sold</button>
    </section>

    <section class="gallery-grid">
      <!-- Replace src & data-* with your painting details -->
      <div class="painting-item" data-status="sale">
        <img src="images/painting1.jpg" alt="Title" />
        <h3>Title 1</h3>
        <p>Year: 2020</p>
        <p>Price: $500</p>
        <p>Short description of the painting.</p>
      </div>
      <!-- Repeat similar blocks for painting2–5 -->
    </section>
  </main>
  <footer>...</footer>
  <script src="js/scripts.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>…</head>
<body>
  <header>…</header>
  <main>
    <h2>About Me</h2>
    <p>Introduce yourself—your background, inspiration, style, etc.</p>
  </main>
  <footer>…</footer>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>…</head>
<body>
  <header>…</header>
  <main>
    <h2>Contact Me</h2>
    <form action="https://formspree.io/f/your-form-id" method="POST">
      <label>Name <input type="text" name="name" required></label>
      <label>Email <input type="email" name="email" required></label>
      <label>Message <textarea name="message" required></textarea></label>
      <button type="submit">Send</button>
    </form>
  </main>
  <footer>…</footer>
</body>
</html>
/* Reset & base */
* { margin:0; padding:0; box-sizing:border-box; }
body { font-family: Georgia, serif; color:#333; background:#fafafa; }

/* Header, logo & nav */
header { display:flex; justify-content:space-between; align-items:center; padding:1rem 2rem; background:#fff; border-bottom:1px solid #ddd; }
.logo { font-family: "Times New Roman", serif; font-size:1.8rem; color:#222; text-decoration:none; }
nav a { margin-left:1rem; color:#555; text-decoration:none; }
nav a:hover { color:#000; }

/* Hero */
.hero { text-align:center; padding:4rem 2rem; }
.hero h1 { font-size:2.5rem; margin-bottom:1rem; }
.hero .cta { margin-top:1.5rem; display:inline-block; padding:.75rem 1.5rem; background:#b08b4f; color:#fff; text-decoration:none; font-weight:bold; border-radius:4px; }
.hero .cta:hover { background:#a07a44; }

/* Gallery */
.filters { text-align:center; margin:2rem 0; }
.filters button { margin:0 .5rem; padding:.5rem 1rem; border:1px solid #b08b4f; background:#fff; color:#b08b4f; cursor:pointer; }
.filters button.active,
.filters button:hover { background:#b08b4f; color:#fff; }

.gallery-grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(240px,1fr)); gap:1.5rem; padding:0 2rem; }
.painting-item { background:#fff; padding:1rem; border:1px solid #ddd; border-radius:4px; transition:transform .3s; }
.painting-item:hover { transform:scale(1.02); }
.painting-item img { width:100%; display:block; cursor:pointer; border-radius:4px; }

/* Footer */
footer { text-align:center; padding:1rem; background:#fff; border-top:1px solid #ddd; font-size:.9rem; }

/* Contact form */
form { max-width:500px; margin:2rem auto; display:flex; flex-direction:column; gap:1rem; }
input, textarea { padding:.75rem; border:1px solid #ccc; border-radius:4px; font-size:1rem; width:100%; }

/* Responsive */
@media(max-width:600px) {
  .hero h1 { font-size:2rem; }
  header { flex-direction:column; align-items:start; }
  nav { margin-top:.5rem; }
}
document.addEventListener("DOMContentLoaded", () => {
  // Filter buttons
  const filters = document.querySelectorAll(".filters button");
  const items = document.querySelectorAll(".painting-item");
  filters.forEach(btn => {
    btn.addEventListener("click", () => {
      filters.forEach(b => b.classList.remove("active"));
      btn.classList.add("active");
      const f = btn.dataset.filter;
      items.forEach(item => {
        item.style.display = (f === "all" || item.dataset.status === f) ? "" : "none";
      });
    });
  });

  // Lightbox
  items.forEach(item => {
    const img = item.querySelector("img");
    img.addEventListener("click", () => {
      const overlay = document.createElement("div");
      overlay.id = "lightbox-overlay";
      overlay.innerHTML = `<div class="lightbox-content"><img src="${img.src}" alt="${img.alt}"><span class="close-btn">&times;</span></div>`;
      document.body.appendChild(overlay);
      overlay.addEventListener("click", e => e.target.id === "lightbox-overlay" && overlay.remove());
    });
  });
});

/* Lightbox overlay */
#lightbox-overlay {
  position:fixed; top:0; left:0; width:100%; height:100%;
  background:rgba(0,0,0,0.8); display:flex; justify-content:center; align-items:center;
}
.lightbox-content { position:relative; }
.lightbox-content img { max-width:90vw; max-height:90vh; border-radius:4px; }
.close-btn {
  position:absolute; top:-10px; right:-10px;
  background:#fff; border-radius:50%; padding:.25rem .5rem;
  font-size:1.5rem; cursor:pointer;
}
