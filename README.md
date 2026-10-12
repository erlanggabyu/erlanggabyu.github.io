# Website CV — "Editorial Minimalis"

Website CV/profil pribadi 5 halaman, dibuat dengan **HTML + CSS + Bootstrap 5** (file lokal di `css/bootstrap.min.css` dan `js/bootstrap.bundle.min.js`).
Tidak ada JavaScript buatan sendiri; `bootstrap.bundle.min.js` hanya dipakai untuk komponen bawaan Bootstrap (navbar collapse dan modal foto).

```
/
├── index.html          Home: nama besar, positioning, foto, status, 3 pengalaman unggulan
├── tentang.html        Tentang: cerita, pendidikan, nilai & minat (dua kolom ala majalah)
├── pengalaman.html     Pengalaman: studi kasus + galeri foto + modal Bootstrap
├── keahlian.html       Keahlian: Hard Skill, Tools, Soft Skill, Bahasa (level Dasar/Menengah/Mahir)
├── kontak.html         Kontak: email besar, tautan sosial, form, Download CV
├── css/style.css       Satu-satunya file CSS kustom (diberi daftar isi & komentar per bagian)
├── css/bootstrap.min.css      Bootstrap 5.3.3 (file lokal, jangan diedit)
├── js/bootstrap.bundle.min.js Bootstrap 5.3.3 JS untuk navbar collapse & modal
├── assets/
│   ├── img/
│   │   ├── logo.svg              Logo monogram (satu warna, otomatis terang di dark mode)
│   │   ├── favicon.svg           Favicon (+ favicon-32.png & apple-touch-icon.png)
│   │   ├── hero-visual.svg       Banner abstrak geometris
│   │   ├── placeholder.svg       Latar bingkai foto sebelum foto dimuat
│   │   ├── og-image.png          Gambar preview link (1200×630)
│   │   ├── profil.jpg            ← GANTI dengan foto Anda (placeholder)
│   │   ├── tentang.jpg           ← GANTI dengan foto Anda (placeholder)
│   │   └── pengalaman/
│   │       └── pengalaman-1-foto-1.jpg … pengalaman-3-foto-3.jpg   ← GANTI
│   └── cv/
│       └── CV-Erlangga-Bayu.pdf   ← GANTI dengan CV asli Anda (placeholder)
└── README.md
```

---

## 1. Konsep desain

**Editorial Minimalis** — terinspirasi tata letak majalah desain dan portofolio studio kreatif. Tipografi menjadi elemen utama, bukan dekorasi.

| Elemen | Penerapan |
|---|---|
| **Warna** | Off-white `#f5f3ef`, teks `#141414`, abu-abu `#6b6b6b`, dan **satu** aksen burnt orange `#d4552b`. Semua disimpan sebagai CSS variables di `:root` (bagian 01 di `style.css`). |
| **Dark mode** | Otomatis lewat `@media (prefers-color-scheme: dark)`: latar `#111`, teks `#eee`, aksen tetap. Logo & banner SVG ikut berganti warna. |
| **Tipografi** | Judul: *Fraunces* (serif) berukuran besar dengan `clamp()`. Body: *Inter*. Label & nomor: *JetBrains Mono* kapital dengan spasi huruf lebar. |
| **Grid & garis** | Grid Bootstrap yang tegas, banyak whitespace, garis 1px sebagai pemisah section. |
| **Penomoran** | Gaya editorial: "01 — Tentang", "02 — Pengalaman", dst. Nomor juga muncul di navbar. |
| **Foto** | Grayscale → berwarna saat hover, `object-fit: cover`, rasio konsisten (4:5 potret, 4:3 dokumentasi). |
| **Interaksi** | Garis bawah link "tumbuh" dari kiri; panah tombol bergeser sedikit; hamburger berubah jadi "X". |
| **Animasi** | Fade + naik sedikit dengan `@keyframes` dan jeda bertahap (`.d-1` … `.d-6`). Dimatikan otomatis bila pengguna memilih `prefers-reduced-motion`. |
| **Tekstur** | Grain sangat tipis dari SVG noise (`feTurbulence`) di `body::before`. |
| **Keahlian** | Tanpa progress bar persentase. Level ditampilkan sebagai teks + 3 kotak kecil (Dasar / Menengah / Mahir). |
| **Aksesibilitas** | Struktur heading berurutan, `alt` deskriptif, fokus keyboard terlihat (outline oranye), tautan "Lewati ke konten", `aria-current="page"` untuk menu aktif. |

---

## 2. Cara mengedit

Semua bagian yang perlu diganti diberi komentar `<!-- GANTI ... -->` atau `<!-- GANTI FOTO: ... -->`.
Tips: di VS Code tekan **Ctrl+Shift+F** lalu cari `GANTI` untuk melihat semuanya.

### a. Data diri (nama, email, sosial media)
Gunakan **Find & Replace di semua file** (VS Code: `Ctrl+Shift+H`):

| Cari | Ganti dengan |
|---|---|
| `Nama Lengkap` | Nama asli Anda |
| `nama@email.com` | Email Anda |
| `linkedin.com/in/username` | URL LinkedIn Anda |
| `github.com/username` | URL GitHub Anda |
| `instagram.com/username` | URL Instagram Anda |
| `username.github.io` | Alamat website Anda (untuk Open Graph) |
| `Universitas Nama Kampus` | Nama kampus |

Lalu edit teks lainnya langsung di HTML: kalimat positioning (`index.html`), cerita & pendidikan (`tentang.html`), studi kasus (`pengalaman.html`), dan daftar skill (`keahlian.html`).

> ⚠️ Angka dampak di halaman Pengalaman (mis. "−33%", "2×") hanya **contoh**. Ganti dengan angka nyata yang bisa Anda jelaskan saat wawancara, atau hapus.

### b. Mengubah level skill (`keahlian.html`)
Setiap skill punya 3 kotak `<i>`. Jumlah `class="on"` menentukan level:
```html
<span class="level" aria-hidden="true"><i class="on"></i><i class="on"></i><i></i></span>Menengah
```
1 = Dasar, 2 = Menengah, 3 = Mahir. Untuk **Mahir**, tambahkan class `lvl-3` pada `<li>` agar kotaknya berwarna oranye.

### c. Mengganti foto
Cukup **timpa file dengan nama yang sama** — tidak perlu mengubah HTML.

| File | Ukuran disarankan |
|---|---|
| `assets/img/profil.jpg` | Potret 4:5, mis. 800×1000 px |
| `assets/img/tentang.jpg` | Potret 4:5, mis. 800×1000 px |
| `assets/img/pengalaman/pengalaman-X-foto-Y.jpg` | Lanskap 4:3, mis. 1200×900 px |

- Simpan sebagai **.jpg**, kompres dulu (mis. di squoosh.app) agar di bawah ±300 KB.
- Nama file **huruf kecil semua** — GitHub Pages membedakan huruf besar/kecil (`Profil.JPG` ≠ `profil.jpg`).
- Perbarui juga teks `alt` agar sesuai isi foto.
- Ingin menambah foto? Salin satu blok `<button class="gallery-btn">` **dan** satu blok `<div class="modal">` di bawah halaman, lalu ganti `id`/`data-bs-target`-nya (mis. `foto-1-4`).

### d. Mengganti file CV
Timpa `assets/cv/CV-Erlangga-Bayu.pdf` dengan CV Anda. Jika ingin nama file lain (mis. `CV-Budi-Santoso.pdf`), cari & ganti `CV-Erlangga-Bayu.pdf` di semua file HTML.

### e. Mengganti logo, favicon, dan og-image
- **Logo & favicon:** buka `assets/img/logo.svg` dan `favicon.svg` di text editor, ganti teks `NL` dengan inisial Anda.
- **favicon-32.png & apple-touch-icon.png:** buat ulang dari favicon (mis. di realfavicongenerator.net), atau biarkan — browser modern memakai `favicon.svg`.
- **og-image.png (1200×630):** buat ulang dengan nama Anda di Canva/Figma memakai warna yang sama (`#f5f3ef`, `#141414`, `#d4552b`), lalu timpa file.

### f. Mengganti warna aksen
Ubah satu baris di `css/style.css` bagian 01: `--accent: #d4552b;`

---

## 3. Publish ke GitHub Pages (untuk pemula)

### Langkah 0 — Tips nama repository
Beri nama repo **`username.github.io`** (ganti `username` dengan username GitHub Anda, persis sama, huruf kecil).
Hasilnya link pendek dan profesional:

| Nama repo | Alamat website |
|---|---|
| `budisantoso.github.io` ✅ | `https://budisantoso.github.io` |
| `website-cv` | `https://budisantoso.github.io/website-cv/` |

Karena itu, pilih username GitHub yang profesional (mis. nama asli), bukan nama panggilan/game.

### Langkah 1 — Buat repository
1. Login ke [github.com](https://github.com) → klik **+** (kanan atas) → **New repository**.
2. Repository name: `username.github.io`.
3. Pilih **Public** → klik **Create repository**.

### Langkah 2 — Upload file (cara termudah, tanpa Git)
1. Di halaman repo, klik **uploading an existing file**.
2. Buka folder proyek ini di File Explorer, pilih **isi folder** (`index.html`, `css`, `assets`, dll — bukan folder induknya), lalu seret ke halaman GitHub.
3. Pastikan `index.html` berada di **paling atas** (root) repo, bukan di dalam subfolder.
4. Klik **Commit changes**.

<details>
<summary>Alternatif: memakai Git di terminal</summary>

```bash
git init
git add .
git commit -m "Website CV pertama"
git branch -M main
git remote add origin https://github.com/username/username.github.io.git
git push -u origin main
```
</details>

### Langkah 3 — Aktifkan GitHub Pages
1. Di repo, buka **Settings** → **Pages**.
2. *Source*: **Deploy from a branch**. *Branch*: **main**, folder **/ (root)** → **Save**.
3. Tunggu 1–3 menit, lalu buka `https://username.github.io`.
   (Repo bernama `username.github.io` biasanya sudah aktif otomatis.)

### Langkah 4 — Cek sebelum dikirim ke recruiter
- [ ] Semua halaman terbuka dari navbar, tidak ada gambar yang hilang.
- [ ] Tombol **Download CV** mengunduh CV asli Anda.
- [ ] Email & tautan sosial benar.
- [ ] Buka di HP — menu hamburger berfungsi.
- [ ] Ganti `username.github.io` di meta `og:url` / `og:image`, lalu tes preview link di [opengraph.xyz](https://www.opengraph.xyz) atau [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/).
      WhatsApp menyimpan preview lama di cache; jika belum berubah, coba kirim link dengan tambahan `?v=2`.

### Memperbarui website
Edit file → upload ulang ke repo (atau `git add . && git commit -m "update" && git push`). Perubahan tampil dalam beberapa menit.

---

## 4. Menjalankan secara lokal
Cukup klik dua kali `index.html`, atau pakai ekstensi **Live Server** di VS Code.
(Folder `.claude/` hanya konfigurasi preview lokal dan boleh dihapus/tidak di-upload.)
