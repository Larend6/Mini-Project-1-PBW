<img width="1200" height="230" alt="banner pbw" src="https://github.com/user-attachments/assets/ecfa1707-34e3-4d01-9b13-0175cd38bd7f" />

# Narendra Augusta - Portfolio Website

## 📌 Tentang Proyek

Proyek ini adalah sebuah portfolio website yang menampilkan:
- Profil dan biodata
- Skill & expertise
- Portfolio projects
- Sertifikat
- Media sosial

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

#### Tampilan
<img width="1891" height="97" alt="image" src="https://github.com/user-attachments/assets/0a7dbacb-674d-4022-80ae-038538f1fcfa" />

#### Penjelasan Code

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
        <a class="navbar-brand larend-logo" href="#">
            <div class="logo-top">LAR</div>
            <div class="logo-bottom">END</div>
        </a>

        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>

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
    color: #ff003c;
}

.nav-link:hover {
    color: #ff1a1a !important;
}
```

---

### 2. **Hero Section (Home)**

#### Tampilan
<<img width="1891" height="992" alt="image" src="https://github.com/user-attachments/assets/5b48a572-9e6f-4cd5-b8fc-3eec5d761295" />

#### Penjelasan Code

```html
<section id="home" class="hero-section d-flex align-items-center">
    <video autoplay muted loop playsinline class="hero-video">
        <source src="videos/bg-anime2.mp4" type="video/mp4">
    </video>

    <div class="hero-overlay"></div>

    <div class="particles"></div>

    <div class="container text-center hero-content">
        <h1 class="hero-title reveal">{{ name }}</h1>

        <p class="hero-tagline">
            <span id="typing"></span>
        </p>

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
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.hero-video {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: blur(8px) brightness(0.4);
    z-index: 1;
}

.hero-overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: linear-gradient(to bottom right, rgba(0,0,0,0.7), rgba(20,0,0,0.7));
    z-index: 2;
}

.hero-content {
    position: relative;
    z-index: 3;
}

.reveal {
    opacity: 0;
    transform: translateY(40px);
    animation: revealAnim 1s forwards;
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
const speed = 50;

function typingEffect() {
    if (i < text.length) {
        document.getElementById("typing").innerHTML += text.charAt(i);
        i++;
        setTimeout(typingEffect, speed); // Recursive call
    }
}

document.addEventListener("DOMContentLoaded", typingEffect);

window.addEventListener("scroll", function() {
    const scrollPosition = window.pageYOffset;
    document.querySelector(".hero-video").style.transform =
        "translateY(" + scrollPosition * 0.4 + "px)";
});
```

---

### 3. **About Section**

#### Tampilan
<img width="1892" height="996" alt="image" src="https://github.com/user-attachments/assets/2b26a4d2-8058-4799-ac45-144f5502c459" />

#### Penjelasan Code

```html
<section id="about" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5">About Me</h2>

        <div class="row align-items-center">
            <div class="col-lg-4 text-center mb-4 mb-lg-0">
                <div class="profile-wrapper">
                    <img src="images/profile.jpg" alt="Profile"
                         class="profile-img img-fluid">
                </div>
            </div>

            <div class="col-lg-8">
                <p class="about-description mb-4">
                    Hai, aku Narendra Augusta atau panggil aja Larend,
                    AMV maker yang berfokus pada style edit jugg,
                    flow, dan aesthetic. Hobbyku dalam ngedit
                    awalnya hanyalah sebuah kegabutan saja...
                </p>

                <div class="row">
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
    background-color: #1f1f1f;
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

### 4. **Projects Section**

#### Tampilan
<img width="1886" height="993" alt="image" src="https://github.com/user-attachments/assets/7d60972d-be9a-41cf-853e-87542f98bae8" />

#### Penjelasan Code

```html
<section id="projects" class="py-5 bg-dark text-light">
    <div class="container">
        <h2 class="text-center mb-4">AMV Projects</h2>

        <div class="row">
            <div class="col-md-4 mb-4" v-for="(video, index) in videos" :key="index">
                <div class="card bg-secondary text-light shadow h-100 project-card">

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
        video.muted = false;
        video.volume = 1; 

        if (video.paused) {
            video.play(); 
        }
    },
    mute(event) {
        const video = event.target;
        video.muted = true;
    }
}
```

**CSS Styling:**
```css
.project-card {
    background-color: #1a1a1a !important;
    border: 1px solid #330000;
    transition: 0.3s ease;
}

.project-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 0 20px rgba(255, 0, 0, 0.6);
}

.preview-video {
    height: 250px;
    object-fit: cover;
    border-bottom: 2px solid #ff1a1a;
    transition: transform 0.3s ease, filter 0.3s ease;
}

.project-card:hover .preview-video {
    transform: scale(1.05);
    filter: brightness(1.2);
}
```

---

### 5. **Certificates Section**

#### Tampilan
<img width="1895" height="999" alt="image" src="https://github.com/user-attachments/assets/8a7b332b-eef3-4c55-b944-0093d553f8cb" />

#### Penjelasan Code

```html
<section id="certificates" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5">Certificates</h2>

        <div class="row g-4">
            <div class="col-lg-4 col-md-6" v-for="(cert, index) in certificates" :key="index">
                <div class="card certificate-card h-100 text-center p-3">
                    <img :src="cert.image" class="img-fluid mb-3" alt="Certificate">

                    <h5 class="mb-2">{{ cert.title }}</h5>

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
    object-fit: cover;
    border-radius: 5px;
}

.certificate-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 0 20px rgba(255, 0, 0, 0.6);
}
```

---

### 6. **Footer**

#### Tampilan
<img width="1893" height="219" alt="image" src="https://github.com/user-attachments/assets/9ed62b18-a3bf-468a-b395-322682156f86" />

#### Penjelasan Code

```html
<footer class="footer-section text-light py-4">
    <div class="container">
        <div class="row align-items-center">

            <div class="col-md-6 text-center text-md-start mb-3 mb-md-0">
                <h5 class="fw-bold mb-1">Larend</h5>
                <small>AMV Maker | Lazy Editor | Always Late From Deadline</small>
            </div>

            <div class="col-md-6 text-center text-md-end">
                <a href="https://www.youtube.com/@kloudyr/featured" class="footer-link">YouTube</a>
                <a href="https://www.instagram.com/kloudyr/" class="footer-link">Instagram</a>
                <a href="https://www.tiktok.com/@reugustt" class="footer-link">TikTok</a>
            </div>

        </div>

        <hr class="my-3 border-secondary">

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
    background: #0d0d0d;
}

.footer-link {
    color: #bbb;
    margin-left: 15px;
    text-decoration: none;
    transition: 0.3s;
}

.footer-link:hover {
    color: #ff3c3c;
}
```

---

## Penjelasan Code

### Vue.js Instance (Main App)

```javascript
const { createApp } = Vue;

createApp({
    data() {
        return {
            name: "LAREND",
            tagline: "AMV Maker | Lazy Editor | Always Late From Deadline",
            videos: [],
            certificates: []
        }
    },
    methods: {
        unmute(event) {
            const video = event.target;
            video.muted = false;
            video.volume = 1;
            if (video.paused) {
                video.play();
            }
        },
        mute(event) {
            const video = event.target;
            video.muted = true;
        }
    },
}).mount('#app');
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
    color: #ff1a1a;
}

.btn-danger {
    background-color: #ff003c;
}
```

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

## 📄 Lisensi

© 2025 Larend. All Rights Reserved.

---

**Muchas gracias 🩶**
