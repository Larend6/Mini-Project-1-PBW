# 🎬 LAREND - Portfolio Website

Portfolio website pribadi untuk **Larend**, seorang AMV (Anime Music Video) Maker dengan fokus pada editing style jugg, flow, dan aesthetic.

---

## 📋 Daftar Isi
1. [Tentang Proyek](#tentang-proyek)
2. [Teknologi Digunakan](#teknologi-digunakan)
3. [Tampilan & Penjelasan Setiap Section](#tampilan--penjelasan-setiap-section)
4. [Penjelasan Code](#penjelasan-code)
5. [Cara Menggunakan](#cara-menggunakan)

---

## 📌 Tentang Proyek

Proyek ini adalah sebuah portfolio website responsif yang menampilkan:
- Profil dan biodata dari Larend
- Skill & expertise dalam video editing
- Portfolio AMV (Anime Music Video) projects
- Sertifikat dan penghargaan yang telah diraih
- Media sosial dan kontak langsung

Website ini dibangun dengan teknologi modern yang mengutamakan user experience dan responsive design.

---

## 🛠️ Teknologi Digunakan

| Teknologi | Versi | Fungsi |
|-----------|-------|--------|
| **HTML** | 5 | Struktur dan semantik halaman |
| **CSS** | 3 | Styling dan animasi visual |
| **Bootstrap** | 5.3.2 | Framework responsive CSS |
| **Vue.js** | 3 | Framework JavaScript untuk interaktivitas |
| **JavaScript** | ES6 | Logic dan interaksi dinamis |

---

## 🎨 Tampilan & Penjelasan Setiap Section

### 1. **Navbar (Navigation Bar)**

#### 📸 Tampilan
Navbar fixed di bagian atas dengan background hitam (`bg-dark`), berisi:
- Logo "LAREND" di sebelah kiri
- Menu navigasi di sebelah kanan (Home, About, Projects, Certificates)
- Responsive toggle button untuk mobile

#### 📝 Penjelasan Code

```html
<!-- Navbar Section -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
        <!-- Logo -->
        <a class="navbar-brand larend-logo" href="#">
            <div class="logo-top">LAR</div>
            <div class="logo-bottom">END</div>
        </a>
        
        <!-- Toggle Button (Mobile) -->
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        
        <!-- Navigation Menu -->
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ms-auto">
                <li class="nav-item"><a class="nav-link" href="#home">Home</a></li>
                <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
                <li class="nav-item"><a class="nav-link" href="#projects">Projects</a></li>
                <li class="nav-item"><a class="nav-link" href="#certificates">Certificates</a></li>
            </ul>
        </div>
    </div>
</nav>
```

**Penjelasan:**
- `navbar-expand-lg`: Navbar akan collapse pada ukuran layar < 992px
- `fixed-top`: Navbar tetap di posisi atas saat scroll
- `ms-auto`: Menu navigation berada di sebelah kanan (margin-start auto)
- `data-bs-toggle="collapse"`: Mengaktifkan toggle collapse menu

**CSS Styling:**
```css
.larend-logo {
    display: flex;
    flex-direction: column;
    line-height: 1;
    text-decoration: none;
}

.logo-top {
    font-size: 1.2rem;
    font-weight: 800;
    letter-spacing: 4px;
    color: white;
}

.logo-bottom {
    font-size: 1.2rem;
    font-weight: 800;
    letter-spacing: 4px;
    color: #ff003c; /* Red Color */
}

.nav-link:hover {
    color: #ff1a1a !important; /* Hover effect */
}
```

---

### 2. **Hero Section (Home)**

#### 📸 Tampilan
Full-screen section dengan:
- Video background dengan blur effect
- Gradient overlay untuk kontras text
- Animated title "LAREND"
- Typing effect untuk tagline
- Call-to-action buttons
- Animated particles effect di background

#### 📝 Penjelasan Code

```html
<!-- Hero Section -->
<section id="home" class="hero-section d-flex align-items-center">
    <!-- Video Background -->
    <video autoplay muted loop playsinline class="hero-video">
        <source src="videos/bg-anime2.mp4" type="video/mp4">
    </video>

    <!-- Overlay -->
    <div class="hero-overlay"></div>

    <!-- Particles Animation -->
    <div class="particles"></div>

    <!-- Content -->
    <div class="container text-center hero-content">
        <!-- Title (Vue Data Binding) -->
        <h1 class="hero-title reveal">{{ name }}</h1>
        
        <!-- Typing Effect -->
        <p class="hero-tagline">
            <span id="typing"></span>
        </p>

        <!-- Buttons -->
        <div class="mt-4 reveal delay-2">
            <a href="#projects" class="btn btn-danger btn-lg me-3">Watch My Edits</a>
            <a href="#about" class="btn btn-outline-light btn-lg">About Me</a>
        </div>
    </div>
</section>
```

**Penjelasan:**
- `d-flex align-items-center`: Flexbox untuk center content vertikal
- `{{ name }}`: Vue.js data binding (menampilkan nama dari data Vue)
- `<span id="typing"></span>`: Placeholder untuk typing effect JavaScript
- `reveal delay-2`: CSS class untuk animation effect

**CSS Styling Utama:**
```css
.hero-section {
    height: 100vh; /* Full viewport height */
    position: relative;
    overflow: hidden;
}

.hero-video {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: blur(8px) brightness(0.4); /* Blur dan darkening */
    z-index: 1;
}

.hero-overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: linear-gradient(to bottom right, rgba(0,0,0,0.7), rgba(20,0,0,0.7));
    z-index: 2; /* Di atas video */
}

.hero-content {
    position: relative;
    z-index: 3; /* Di atas overlay */
}

.reveal {
    opacity: 0;
    transform: translateY(40px);
    animation: revealAnim 1s forwards; /* Fade-in animation */
}

@keyframes revealAnim {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
```

**JavaScript untuk Typing Effect:**
```javascript
const text = "AMV Maker | Lazy Editor | Always Late From Deadline";
let i = 0;
const speed = 50; // Milliseconds per character

function typingEffect() {
    if (i < text.length) {
        document.getElementById("typing").innerHTML += text.charAt(i);
        i++;
        setTimeout(typingEffect, speed); // Recursive call
    }
}

document.addEventListener("DOMContentLoaded", typingEffect);

// Parallax effect untuk video
window.addEventListener("scroll", function() {
    const scrollPosition = window.pageYOffset;
    document.querySelector(".hero-video").style.transform =
        "translateY(" + scrollPosition * 0.4 + "px)";
});
```

---

### 3. **About Section**

#### 📸 Tampilan
Section yang menampilkan:
- Foto profil di sebelah kiri
- Deskripsi singkat tentang diri
- Skill bars untuk software editing (Kinemaster, Alight Motion, After Effects)
- Skill bars untuk editing style (Aesthetic, Typography, Jugg, Flow)

#### 📝 Penjelasan Code

```html
<!-- About Section -->
<section id="about" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5">About Me</h2>

        <div class="row align-items-center">
            <!-- Profile Image -->
            <div class="col-lg-4 text-center mb-4 mb-lg-0">
                <div class="profile-wrapper">
                    <img src="images/profile.jpg" alt="Profile"
                         class="profile-img img-fluid">
                </div>
            </div>

            <!-- Profile Description & Skills -->
            <div class="col-lg-8">
                <p class="about-description mb-4">
                    Hai, aku Narendra Augusta atau panggil aja Larend,
                    AMV maker yang berfokus pada style edit jugg,
                    flow, dan aesthetic. Hobbyku dalam ngedit
                    awalnya hanyalah sebuah kegabutan saja...
                </p>

                <div class="row">
                    <!-- Software Editing Skills -->
                    <div class="col-md-6">
                        <h5 class="mb-3">Software Editing</h5>

                        <div class="skill mb-3">
                            <span>Kinemaster</span>
                            <div class="progress">
                                <div class="progress-bar bg-danger" style="width:90%">90%</div>
                            </div>
                        </div>

                        <div class="skill mb-3">
                            <span>Alight Motion</span>
                            <div class="progress">
                                <div class="progress-bar bg-warning" style="width:75%">75%</div>
                            </div>
                        </div>

                        <div class="skill mb-3">
                            <span>Adobe After Effects</span>
                            <div class="progress">
                                <div class="progress-bar bg-success" style="width:20%">20%</div>
                            </div>
                        </div>
                    </div>

                    <!-- Editing Style Skills -->
                    <div class="col-md-6">
                        <h5 class="mb-3">Editing Style</h5>

                        <div class="skill mb-3">
                            <span>Aesthetic</span>
                            <div class="progress">
                                <div class="progress-bar bg-danger" style="width:90%">90%</div>
                            </div>
                        </div>

                        <div class="skill mb-3">
                            <span>Marginal/Typography</span>
                            <div class="progress">
                                <div class="progress-bar bg-warning" style="width:85%">85%</div>
                            </div>
                        </div>
                        
                        <!-- Additional skills... -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

**Penjelasan:**
- `row align-items-center`: Grid row dengan vertical center alignment
- `col-lg-4 / col-lg-8`: Responsive columns (4 untuk image, 8 untuk content pada layar besar)
- `.progress`: Bootstrap progress bar component
- `style="width:90%"`: Inline style untuk mengubah persentase bar
- `bg-danger, bg-warning, bg-success`: Bootstrap color utility classes

**CSS Styling:**
```css
.about-description {
    max-width: 750px;
    margin: 0 auto;
    color: #cccccc;
    font-size: 1.1rem;
    line-height: 1.6;
}

.progress {
    height: 10px;
    background-color: #1f1f1f; /* Dark background */
}

.skill {
    margin-bottom: 20px;
}

.skill span {
    display: block;
    margin-bottom: 5px;
}
```

---

### 4. **Projects Section (AMV Projects)**

#### 📸 Tampilan
Section dengan grid 3 kolom menampilkan:
- Video preview dari setiap AMV project
- Title dan deskripsi project
- Hover effect (video unmuted, card lift)

#### 📝 Penjelasan Code

```html
<!-- Projects Section -->
<section id="projects" class="py-5 bg-dark text-light">
    <div class="container">
        <h2 class="text-center mb-4">AMV Projects</h2>

        <div class="row">
            <!-- Project Card (Loop dengan Vue.js) -->
            <div class="col-md-4 mb-4" v-for="(video, index) in videos" :key="index">
                <div class="card bg-secondary text-light shadow h-100 project-card">

                    <!-- Video Preview -->
                    <video class="w-100 preview-video"
                        autoplay
                        loop
                        muted
                        playsinline
                        preload="auto"
                        @mouseover="unmute($event)"
                        @mouseleave="mute($event)">
                        
                        <source :src="video.file" type="video/mp4">
                    </video>

                    <!-- Card Body -->
                    <div class="card-body">
                        <h5 class="card-title">{{ video.title }}</h5>
                        <p class="card-text">{{ video.desc }}</p>
                    </div>

                </div>
            </div>
        </div>
    </div>
</section>
```

**Penjelasan:**
- `v-for="(video, index) in videos"`: Vue.js loop untuk render setiap video
- `:key="index"`: Key untuk Vue.js list rendering
- `@mouseover="unmute($event)"`: Event listener Vue untuk unmute video saat hover
- `:src="video.file"`: Dynamic binding untuk src attribute
- `h-100`: Bootstrap utility untuk full height card

**Vue.js Data & Methods:**
```javascript
data() {
    return {
        videos: [
            {
                title: "Attack on Titan AMV",
                desc: "First time scale edit in Kinemaster",
                file: "videos/amv1.mp4"
            },
            {
                title: "Kamisato Ayaka AMV",
                desc: "My favorite simple typo-ish edit",
                file: "videos/amv2.mp4"
            },
            {
                title: "Tamako Love Story AMV",
                desc: "First Alight Motion Edit",
                file: "videos/amv3.mp4"
            }
        ]
    }
},
methods: {
    unmute(event) {
        const video = event.target;
        video.muted = false; // Unmute
        video.volume = 1;    // Set volume ke max

        if (video.paused) {
            video.play();    // Play jika paused
        }
    },
    mute(event) {
        const video = event.target;
        video.muted = true;  // Mute
    }
}
```

**CSS Styling:**
```css
.project-card {
    background-color: #1a1a1a !important;
    border: 1px solid #330000; /* Dark red border */
    transition: 0.3s ease;
}

.project-card:hover {
    transform: translateY(-5px); /* Lift effect */
    box-shadow: 0 0 20px rgba(255, 0, 0, 0.6); /* Red glow */
}

.preview-video {
    height: 250px;
    object-fit: cover;
    border-bottom: 2px solid #ff1a1a; /* Red bottom border */
    transition: transform 0.3s ease, filter 0.3s ease;
}

.project-card:hover .preview-video {
    transform: scale(1.05); /* Zoom effect */
    filter: brightness(1.2); /* Brighten */
}
```

---

### 5. **Certificates Section**

#### 📸 Tampilan
Grid 3 kolom menampilkan:
- Gambar/thumbnail sertifikat
- Judul sertifikat
- Tahun perolehan
- Hover effect dengan shadow dan lift

#### 📝 Penjelasan Code

```html
<!-- Certificates Section -->
<section id="certificates" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5">Certificates</h2>

        <div class="row g-4">
            <!-- Certificate Card (Loop dengan Vue.js) -->
            <div class="col-lg-4 col-md-6" v-for="(cert, index) in certificates" :key="index">
                <div class="card certificate-card h-100 text-center p-3">
                    <!-- Certificate Image -->
                    <img :src="cert.image" class="img-fluid mb-3" alt="Certificate">
                    
                    <!-- Certificate Title -->
                    <h5 class="mb-2">{{ cert.title }}</h5>
                    
                    <!-- Certificate Year -->
                    <p class="small text-secondary">{{ cert.year }}</p>
                </div>
            </div>
        </div>
    </div>
</section>
```

**Penjelasan:**
- `g-4`: Bootstrap gap utility untuk spacing antara grid items
- `col-lg-4 col-md-6`: Responsive - 3 kolom di desktop, 2 kolom di tablet
- `p-3`: Padding Bootstrap (padding 1rem)
- `:src="cert.image"`: Dynamic image binding

**Vue.js Data:**
```javascript
certificates: [
    {
        title: "UI/UX Design Bootcamp",
        year: "2025",
        image: "images/cert1.png"
    },
    {
        title: "Panitia Study Club UI/UX Design",
        year: "2025",
        image: "images/cert2.png"
    },
    // ... lebih banyak certificates
]
```

**CSS Styling:**
```css
.certificate-card {
    background: #111;
    border: none;
    color: white;
    transition: 0.3s;
}

.certificate-card img {
    height: 180px;
    object-fit: cover; /* Crop image maintain aspect ratio */
    border-radius: 5px;
}

.certificate-card:hover {
    transform: translateY(-8px); /* Lift */
    box-shadow: 0 0 20px rgba(255, 0, 0, 0.6); /* Red glow */
}
```

---

### 6. **Footer**

#### 📸 Tampilan
Bagian bawah halaman dengan:
- Nama dan deskripsi singkat
- Social media links (YouTube, Instagram, TikTok)
- Copyright information

#### 📝 Penjelasan Code

```html
<!-- Footer -->
<footer class="footer-section text-light py-4">
    <div class="container">
        <div class="row align-items-center">

            <!-- Left Side - Name & Description -->
            <div class="col-md-6 text-center text-md-start mb-3 mb-md-0">
                <h5 class="fw-bold mb-1">Larend</h5>
                <small>AMV Maker | Lazy Editor | Always Late From Deadline</small>
            </div>

            <!-- Right Side - Social Links -->
            <div class="col-md-6 text-center text-md-end">
                <a href="https://www.youtube.com/@kloudyr/featured" class="footer-link">YouTube</a>
                <a href="https://www.instagram.com/kloudyr/" class="footer-link">Instagram</a>
                <a href="https://www.tiktok.com/@reugustt" class="footer-link">TikTok</a>
            </div>

        </div>

        <hr class="my-3 border-secondary">

        <!-- Copyright -->
        <div class="text-center small">
            © 2025 Larend. All Rights Reserved.
        </div>
    </div>
</footer>
```

**Penjelasan:**
- `text-md-start / text-md-end`: Bootstrap responsive text alignment
- `fw-bold`: Font weight bold
- `footer-link`: Custom class untuk styling links

**CSS Styling:**
```css
.footer-section {
    background: #0d0d0d; /* Sedikit lebih terang dari body */
}

.footer-link {
    color: #bbb;
    margin-left: 15px;
    text-decoration: none;
    transition: 0.3s;
}

.footer-link:hover {
    color: #ff3c3c; /* Berubah merah saat hover */
}
```

---

## 📝 Penjelasan Code

### Vue.js Instance (Main App)

```javascript
const { createApp } = Vue;

createApp({
    data() {
        return {
            // Data yang digunakan dalam template
            name: "LAREND",
            tagline: "AMV Maker | Lazy Editor | Always Late From Deadline",
            videos: [ /* Array video data */ ],
            certificates: [ /* Array certificate data */ ]
        }
    },
    methods: {
        // Fungsi untuk unmute video saat hover
        unmute(event) {
            const video = event.target;
            video.muted = false;
            video.volume = 1;
            if (video.paused) {
                video.play();
            }
        },
        // Fungsi untuk mute video saat mouse leave
        mute(event) {
            const video = event.target;
            video.muted = true;
        }
    },
}).mount('#app'); // Mount ke element dengan id="app"
```

### CSS Grid & Responsive Design

Proyek ini menggunakan **Bootstrap 5** untuk responsive design:

```css
/* Desktop - 3 columns */
.col-md-4 { flex: 0 0 33.333%; }

/* Tablet - 2 columns */
@media (max-width: 768px) {
    .col-md-4 { flex: 0 0 50%; }
}

/* Mobile - 1 column */
@media (max-width: 576px) {
    .col-md-4 { flex: 0 0 100%; }
}
```

### Color Scheme

Website menggunakan color palette modern:
- **Primary**: Dark Black (`#0d0d0d` - `#1a1a1a`)
- **Accent**: Bright Red (`#ff003c` - `#ff1a1a`)
- **Text**: Light Gray (`#cccccc` - `#f5f5f5`)

```css
body {
    background-color: #0d0d0d;
    color: #f5f5f5;
}

h2 {
    color: #ff1a1a; /* Red untuk heading */
}

.btn-danger {
    background-color: #ff003c;
}
```

---

## 🚀 Cara Menggunakan

### 1. **Struktur Folder**
```
minpro_1/
├── index.html          # File utama HTML
├── style.css           # File CSS untuk styling
├── images/             # Folder untuk gambar
│   ├── profile.jpg     # Foto profil
│   ├── cert1.png       # Sertifikat 1
│   └── ...             # Sertifikat lainnya
└── videos/             # Folder untuk video
    ├── bg-anime2.mp4   # Video background hero
    ├── amv1.mp4        # Video project 1
    └── ...             # Video project lainnya
```

### 2. **Setup Awal**
1. Siapkan semua gambar profil dan sertifikat di folder `images/`
2. Siapkan semua video AMV di folder `videos/`
3. Update data di dalam script Vue.js (nama, deskripsi, daftar video, daftar sertifikat)

### 3. **Menjalankan Website**
- Buka file `index.html` di browser web favorit
- Atau gunakan Live Server (VS Code Extension) untuk development
- Atau upload ke server hosting untuk production

### 4. **Customization**

**Mengubah Nama & Tagline:**
```javascript
data() {
    return {
        name: "NAMA_ANDA",
        tagline: "YOUR_TAGLINE_HERE",
        // ...
    }
}
```

**Menambah Video Project:**
```javascript
videos: [
    {
        title: "Video Title",
        desc: "Deskripsi singkat",
        file: "videos/namafile.mp4"
    },
    // Tambah yang baru di sini
]
```

**Menambah Sertifikat:**
```javascript
certificates: [
    {
        title: "Nama Sertifikat",
        year: "2025",
        image: "images/cert_name.png"
    },
    // Tambah yang baru di sini
]
```

### 5. **Modifikasi Styling**

Edit `style.css` untuk mengubah:
- Warna: Cari dan ganti color codes
- Font: Update font-family
- Spacing: Ubah padding dan margin values
- Effects: Modifikasi animations dan transitions

---

## 🎯 Fitur Utama

✅ **Fully Responsive** - Mobile, Tablet, Desktop  
✅ **Smooth Scrolling** - Navigasi yang mulus  
✅ **Video Background** - Hero section dengan video  
✅ **Typing Effect** - Animasi text di hero  
✅ **Parallax Effect** - Video bergerak saat scroll  
✅ **Interactive Videos** - Video unmute on hover  
✅ **Animated Cards** - Hover effects pada projects dan certificates  
✅ **Modern Design** - Dark theme dengan accent color merah  
✅ **Vue.js Powered** - Dynamic content rendering  
✅ **Bootstrap 5** - Professional UI framework  

---

## 📱 Browser Support

| Browser | Support |
|---------|---------|
| Chrome | ✅ |
| Firefox | ✅ |
| Safari | ✅ |
| Edge | ✅ |
| Opera | ✅ |

---

## 📧 Informasi Kontak

- **YouTube**: [@kloudyr](https://www.youtube.com/@kloudyr/featured)
- **Instagram**: [@kloudyr](https://www.instagram.com/kloudyr/)
- **TikTok**: [@reugustt](https://www.tiktok.com/@reugustt)

---

## 📄 Lisensi

© 2025 Larend. All Rights Reserved.

---

**Dibuat dengan ❤️ untuk Portfolio Larend**
