# 💌 Cute Birthday Website Template

*[Read this in English](README.md)*

Website ulang tahun digital yang cute, interaktif, dan bisa kamu edit sendiri buat pacar/orang tersayang kamu — nggak perlu jago coding! Ini cocok dipakai sebagai **template**: tinggal ganti foto, GIF, dan teksnya, terus deploy.

**Demo alurnya:** halaman pembuka → galeri foto interaktif → "100 alasan kenapa aku sayang kamu" → surat ulang tahun + confetti 🎉

Ada juga tombol musik (lagu ikut muter walau pindah halaman) dan tombol catatan kecil yang bisa diisi oleh pasangan kamu, isinya tersimpan otomatis di browser-nya.

---

## 📁 Struktur folder

```
my-birthday-site/
├── index.html          → Halaman 1: pembuka / hero
├── gallery.html         → Halaman 2: galeri foto interaktif (geser/klik)
├── reasons.html          → Halaman 3: "100 reasons why i love you"
├── letter.html           → Halaman 4: surat ulang tahun + confetti
├── css/
│   └── style.css         → semua styling & warna, dipakai semua halaman
├── js/
│   ├── script.js          → logic yang jalan di semua halaman (transisi, musik, catatan, surat, confetti)
│   ├── gallery.js          → logic khusus galeri foto
│   └── reasons.js          → logic khusus halaman 100 reasons (lightbox foto + auto-scroll)
├── assets/                → taruh GIF & musik di sini
│   ├── hero.gif
│   ├── sparkle1.gif
│   ├── sparkle2.gif
│   ├── celebration.gif
│   ├── gif1.gif
│   ├── gif2.gif
│   └── music.mp3
└── photos/                → taruh foto-foto kamu di sini
    ├── photo1.jpg ... photo4.jpg      (buat galeri)
    └── reason1.jpg ... reason6.jpg     (buat halaman 100 reasons)
```

> Semua file GIF, foto, dan musik yang sudah ada sekarang itu **dummy/placeholder** (kotak warna pastel bertuliskan "GANTI AKU"), supaya kamu tahu persis apa yang perlu diganti.

---

## 🚀 Cara pakai untuk pemula (step-by-step)

### 1. Download project ini
Kalau kamu dapat ini dari GitHub, klik **Code → Download ZIP**, lalu extract ke folder manapun di komputer kamu.

### 2. Ganti foto & GIF-nya
Buka folder `photos/` dan `assets/`, lalu **timpa file yang sudah ada dengan nama yang sama persis** (termasuk huruf besar/kecilnya!). Contoh:
- Mau ganti foto galeri? Timpa `photos/photo1.jpg`, `photo2.jpg`, dst dengan foto kamu (boleh `.jpg` atau `.png`, tapi kalau ganti ekstensi, ingat juga ubah nama file-nya di HTML — lihat poin 4).
- Mau ganti GIF hero di halaman pembuka? Timpa `assets/hero.gif`.
- Mau ganti lagu? Timpa `assets/music.mp3` dengan lagu kamu sendiri (format mp3).

**Kalau nama filenya beda / ekstensinya beda**, kamu tinggal cari komentar `<!-- GANTI DI SINI -->` di file HTML terkait dan ubah bagian `src="..."`-nya.

### 3. Edit semua teksnya
Ini bagian paling personal — semua teks ada di beberapa tempat:

| Mau edit apa? | Buka file | Cari bagian |
|---|---|---|
| Judul & subjudul halaman pembuka | `index.html` | `<h1 class="hero-title">` dan `<p class="hero-subtitle">` |
| Caption di tiap foto galeri | `js/gallery.js` | array `photos` di bagian paling atas |
| Isi "100 reasons" | `reasons.html` | cari `<ol class="reasons-list">`, tiap alasan itu satu baris `<li>...</li>` — sekarang isinya masih placeholder "reason 1", "reason 2", dst, ganti sesuai maunya kamu (boleh kurang dari 100 juga, tinggal hapus baris `<li>`-nya) |
| Surat ulang tahun (efek ngetik) | `js/script.js` | variabel `letterMessage` di bagian tengah file |
| Tanda tangan di surat | `letter.html` | `<p class="signature">` |

### 4. Coba buka di browser (testing lokal)
Double-click aja `index.html`, biasanya langsung kebuka di browser default kamu.

⚠️ **Catatan penting:** fitur musik yang "nyambung" antar halaman dan status tombol catatan itu pakai `sessionStorage`/`localStorage` browser. Kalau kamu buka file-nya dengan cara **double-click** (`file://...`), sebagian browser (terutama Chrome) menganggap tiap file sebagai "tempat" yang beda-beda, jadi fitur itu mungkin belum nyambung sempurna pas ditest lokal. Ini **normal** dan akan otomatis lancar begitu situsnya sudah di-deploy (langkah 5) karena semua halaman jadi satu alamat website yang sama.

Kalau mau test lokal yang lebih akurat, jalankan local server sederhana. Kalau sudah install Python, buka terminal di folder project ini lalu jalankan:
```
python3 -m http.server
```
lalu buka `http://localhost:8000` di browser.

### 5. Deploy ke Netlify (gratis)
Cara paling gampang:
1. Buka [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag folder project ini (isi foldernya, pastikan ada `index.html` di paling atas/root) ke halaman itu
3. Netlify otomatis kasih kamu link, misalnya `nama-acak.netlify.app`
4. Kamu bisa ganti nama link-nya lewat **Site settings → Change site name**

Kalau mau lebih rapi (auto-update tiap kamu push perubahan), upload project ini ke GitHub repo, lalu di Netlify pilih **Add new site → Import an existing project** dan hubungkan ke repo-nya. Nggak perlu build command apapun karena ini situs statis biasa.

---

## 🎨 Ganti warna tema

Semua warna diatur di satu tempat: buka `css/style.css`, cari bagian paling atas (`:root { ... }`). Ganti kode warnanya (format hex, misal `#ffd6e8`) sesuai selera — otomatis berubah di semua halaman.

---

## ❓ FAQ / Troubleshooting

**GIF/foto-ku nggak muncul, cuma kotak putih/rusak.**
Cek nama file-nya harus sama PERSIS dengan yang ada di kode (termasuk huruf besar-kecil dan ekstensi file — `.jpg` beda dengan `.JPG` di beberapa sistem). Pastikan juga filenya beneran ada di folder `assets/` atau `photos/`.

**Musiknya nggak otomatis muter pas halaman dibuka.**
Ini disengaja — kebijakan browser modern biasanya blokir audio otomatis sebelum ada interaksi klik dari pengguna. Makanya musiknya baru muter begitu tombol musik (🎵, pojok kanan bawah) diklik.

**Catatan yang diisi di tombol 📝 kok nggak sinkron antara HP dan laptop?**
Wajar — catatan itu tersimpan di browser masing-masing device (`localStorage`), bukan di server/database. Jadi kalau dia isi dari HP, isinya cuma ada di HP itu aja. Kalau nanti mau versi yang sinkron ke semua device, itu butuh backend/database kecil tambahan (di luar cakupan template statis ini).

**Aku mau tambah/kurangi jumlah foto di galeri atau di jemuran 100 reasons.**
- Galeri (`gallery.html`): edit array `photos` di `js/gallery.js`, tambah/kurangi object di dalamnya. Jangan lupa sesuaikan juga jumlah tombol `<button class="dot">` di `gallery.html`.
- Jemuran foto 100 reasons (`reasons.html`): tambah/hapus blok `<div class="hang-photo">...</div>` di dalam `.hanging-photos`.

---

## 📜 Lisensi

Bebas dipakai, diedit, dan dibagikan buat keperluan personal (bikin kejutan buat orang tersayang!). Kalau kamu develop ini jadi lebih bagus lagi, feel free buat fork & share juga ke yang lain 💕
