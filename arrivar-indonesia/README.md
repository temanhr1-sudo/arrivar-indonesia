# 🏢 Arrivar Indonesia — Website

Website resmi perusahaan Arrivar Indonesia, bergerak di bidang **Financial**, **Bisnis**, dan **Human Resource**.

---

## 📁 Struktur Folder

```
arrivar-indonesia/
│
├── index.html              ← Halaman utama (homepage)
│
├── css/
│   ├── reset.css           ← CSS Reset & normalisasi
│   ├── variables.css       ← Design tokens (warna, font, spacing)
│   ├── base.css            ← Global styles & utility classes
│   ├── navbar.css          ← Navbar & mobile menu
│   ├── hero.css            ← Hero section
│   ├── sections.css        ← About, Services, Why, Team, Process, Testimonials, Contact
│   ├── components.css      ← Form, cards, cookie banner
│   ├── footer.css          ← Footer
│   ├── responsive.css      ← Breakpoints & media queries
│   └── animations.css      ← Keyframes & scroll reveal
│
├── js/
│   ├── data.js             ← Semua data konten website (edit di sini!)
│   ├── security.js         ← Keamanan: XSS prevention, rate limit, sanitization
│   ├── navbar.js           ← Scroll behavior, mobile menu, active link
│   ├── reveal.js           ← Scroll reveal via IntersectionObserver
│   ├── render.js           ← Render dynamic content dari data.js
│   ├── form.js             ← Validasi & submit form kontak
│   └── main.js             ← Entry point, cookie banner, lazy images
│
├── images/
│   ├── logo-icon.svg       ← Logo ikon (navbar & footer)
│   ├── favicon.svg         ← Favicon website
│   └── og-image.png        ← Open Graph image (untuk social media)
│
└── pages/
    ├── privacy.html        ← Kebijakan Privasi
    ├── terms.html          ← Syarat & Ketentuan
    ├── karir.html          ← Halaman Karir (siap dikembangkan)
    └── blog.html           ← Halaman Blog (siap dikembangkan)
```

---

## 🎨 Panduan Warna

| Token            | Nilai       | Kegunaan               |
|------------------|-------------|------------------------|
| `--navy`         | `#1a2744`   | Background utama       |
| `--navy-deep`    | `#0f1929`   | Background gelap       |
| `--gold`         | `#c9a84c`   | Aksen utama (CTA, link)|
| `--gold-light`   | `#e8c97a`   | Gradasi gold           |
| `--white`        | `#fafaf8`   | Background terang      |
| `--gray-light`   | `#f0ede6`   | Section bergantian     |

---

## ✏️ Cara Update Konten

Semua konten website (layanan, tim, testimoni, dll) tersimpan di **`js/data.js`**.
Cukup edit file tersebut — tidak perlu menyentuh HTML.

```javascript
// Contoh: Tambah anggota tim baru
team: [
  {
    initials: 'JD',
    name: 'John Doe',
    role: 'Senior Consultant',
    desc: 'Deskripsi singkat tentang anggota tim.',
  },
  // ...
]
```

---

## 🔒 Fitur Keamanan

- ✅ **Anti-Clickjacking** — `X-Frame-Options: DENY`
- ✅ **XSS Prevention** — sanitasi input di `security.js` & `render.js`
- ✅ **Rate Limiting** — maksimal 3 submit form per 5 menit
- ✅ **Honeypot** — deteksi bot otomatis
- ✅ **Input Sanitization** — strip karakter `< >` dari semua field
- ✅ **Secure Headers** — meta tags security di `index.html`
- ✅ **Console Warning** — peringatan social engineering di browser console

---

## 📱 Responsive Breakpoints

| Breakpoint    | Ukuran      |
|---------------|-------------|
| Desktop       | > 1024px    |
| Tablet        | ≤ 1024px    |
| Mobile        | ≤ 768px     |
| Small Mobile  | ≤ 480px     |
| Large Desktop | ≥ 1440px    |

---

## 🚀 Cara Deploy

### Opsi 1: File Statis (Paling Mudah)
Upload seluruh folder ke hosting apapun (Netlify, Vercel, cPanel, dll).

### Opsi 2: GitHub Pages
1. Push ke GitHub repository
2. Aktifkan GitHub Pages di Settings → Pages
3. Pilih branch `main` dan folder `/root`

### Opsi 3: Nginx
```nginx
server {
    listen 80;
    server_name arrivar.co.id www.arrivar.co.id;
    root /var/www/arrivar-indonesia;
    index index.html;

    # Security headers
    add_header X-Frame-Options "DENY";
    add_header X-Content-Type-Options "nosniff";
    add_header X-XSS-Protection "1; mode=block";
    add_header Referrer-Policy "strict-origin-when-cross-origin";
    add_header Content-Security-Policy "default-src 'self' https://fonts.googleapis.com https://fonts.gstatic.com; script-src 'self'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com;";

    # Gzip compression
    gzip on;
    gzip_types text/css application/javascript image/svg+xml;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

---

## 📬 Integrasi Form Kontak

Edit bagian ini di `js/form.js` untuk menghubungkan form ke backend:

```javascript
// Ganti bagian simulasi dengan API call nyata:
const response = await fetch('/api/contact', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(data),
});

// Atau gunakan email service seperti EmailJS:
// https://www.emailjs.com/
```

---

## 🛠️ Tech Stack

- **HTML5** — Semantic & accessible markup
- **CSS3** — Custom properties, Grid, Flexbox, Animations
- **Vanilla JavaScript** — No framework dependencies
- **Google Fonts** — Cormorant Garamond + DM Sans
- **IntersectionObserver API** — Performant scroll reveal

---

*© 2024 Arrivar Indonesia. Dibuat dengan ❤️ untuk kesuksesan bisnis Indonesia.*
