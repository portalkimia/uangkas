# 💰 Website Pencatatan Kas Kelas X-3 (GitHub Pages + Google Sheets Backend)

Aplikasi web modern untuk pencatatan dan transparansi uang kas kelas X-3. Dibuat agar bebas dari kendala/keterbatasan iframe Google Apps Script dengan meng-hosting tampilan di **GitHub Pages** (gratis, cepat, dan responsif), sementara **Google Sheets & Google Drive** tetap berfungsi di balik layar sebagai database dan media penyimpanan foto nota bukti pengeluaran.

---

## 🌟 Keunggulan Hosting di GitHub Pages

1. **Bebas Masalah Iframe / Sandbox Google**: Tidak ada masalah tombol macet, scroll terpotong, atau error CSP.
2. **Sangat Cepat & Responsif**: Tampilan langsung terbuka seketika di HP, tablet, maupun laptop.
3. **URL Bersih & Keren**: Alamat website Anda menjadi `https://[username-anda].github.io/kas-kelas-x3/`.
4. **Keamanan Peran**:
   - **Mode Siswa (Default)**: Seluruh siswa dan orang tua dapat memantau saldo, melihat status pembayaran siapa yang sudah/belum bayar, dan melihat foto bukti nota (Read-only).
   - **Mode Walas (Pengelola)**: Memasukkan password Walas (`kelashebat`). Password tidak ditampilkan di layar. Walas dapat menginput kas, menambah kolom tanggal, dan mencatat pengeluaran beserta foto nota.

---

## 🚀 Langkah 1: Upload ke GitHub & Aktifkan GitHub Pages (3 Menit)

1. Buka [github.com](https://github.com/) dan login ke akun GitHub Anda.
2. Klik tombol hijau **New** (atau kunjungi [github.com/new](https://github.com/new)) untuk membuat repository baru:
   - **Repository name**: `kas-kelas-x3`
   - Pilih: **Public**
   - Centang: **Add a README file** (opsional)
   - Klik **Create repository**.
3. Di halaman repository yang baru dibuat:
   - Klik tombol **Add file** > pilih **Upload files**.
   - Seret (drag & drop) file yang ada di folder ini:
     - `index.html`
     - `Code.gs`
     - `README.md`
   - Klik tombol hijau **Commit changes** di bagian bawah.
4. **Aktifkan GitHub Pages**:
   - Klik tab **Settings** di kanan atas repository Anda.
   - Pada menu sebelah kiri, klik **Pages**.
   - Pada bagian **Build and deployment > Branch**:
     - Ubah dropdown dari `None` menjadi **`main`** (atau `master`).
     - Folder biarkan tetap **`/(root)`**.
     - Klik tombol **Save**.
5. Tunggu sekitar 1-2 menit, lalu segarkan (refresh) halaman Settings > Pages. Anda akan melihat link website Anda aktif, contoh:
   👉 **`https://username-anda.github.io/kas-kelas-x3/`**

---

## 📊 Langkah 2: Siapkan Google Sheets & Dapatkan API URL

Agar website di GitHub Pages dapat menyimpan data langsung ke Google Spreadsheet dan menyimpan foto nota ke Google Drive Anda:

1. Buka [Google Sheets](https://sheets.new) baru. Beri judul spreadsheet Anda: **`Kas Kelas X-3`**.
2. Klik menu **Ekstensi** (Extensions) > **Apps Script**.
3. Buka file `Code.gs` di editor Apps Script, hapus isinya, lalu salin seluruh isi file [`Code.gs`](./Code.gs).
4. Klik tombol **Save** (`Ctrl + S`).
5. Pada dropdown fungsi di bagian atas, pilih fungsi **`setupDatabase`**, lalu klik tombol **Run** (Jalankan ▶️):
   - Izinkan hak akses saat diminta (*Review Permissions* > Akun Anda > *Advanced* > *Go to untitled project* > *Allow*).
   - Tunggu hingga proses selesai. Sheet `Kas_Masuk` (dengan 30 siswa kelas X-3), `Pengeluaran`, dan folder Google Drive *"Bukti Kas Kelas X-3"* akan dibuat otomatis.
6. **Publikasikan API (Deploy Web App)**:
   - Di kanan atas Apps Script, klik tombol biru **Deploy** > **New deployment**.
   - Klik ikon gerigi ⚙️ di samping *"Select type"* > pilih **Web app**.
   - Konfigurasi:
     - **Description**: `API Kas Kelas`
     - **Execute as**: **Me (emailanda@gmail.com)**
     - **Who has access**: **Anyone** (Siapa saja)
   - Klik **Deploy**.
   - Salin **Web app URL** yang dihasilkan (contoh: `https://script.google.com/macros/s/.../exec`).

---

## 🔗 Langkah 3: Langsung Akses Tanpa Perlu Setting Per-Perangkat!

Website ini **sudah langsung terhubung permanen** dengan Google Apps Script dan Spreadsheet Anda (`AKfycbzmIDG...`). 

1. Begitu GitHub Pages aktif (Langkah 1), cukup buka link website Anda di HP, tablet, maupun laptop:
   👉 **`https://username-anda.github.io/kas-kelas-x3/`**
2. Data siswa, saldo kas, kolom tanggal, dan riwayat pengeluaran akan **otomatis tersinkronisasi seketika** di perangkat apa pun!
3. Tidak perlu memasukkan link API lagi secara manual di masing-masing HP atau laptop.

---

## 🔑 Informasi Hak Akses

- **Mode Siswa (Default)**:
  - Otomatis aktif saat website dibuka.
  - Siswa/wali murid dapat melihat siapa saja yang sudah atau belum membayar kas, rekap saldo, serta foto nota pengeluaran (read-only).
  - Jika siswa mengklik kotak nominal, sistem akan menginformasikan bahwa data hanya dapat diubah oleh Wali Kelas.

- **Mode Walas (Wali Kelas & Bendahara)**:
  - Klik tombol **Masuk Mode Walas** di pojok kanan atas.
  - Masukkan password:
    ```text
    kelashebat
    ```
  - *(Password ini tidak ditampilkan di website agar privasi terjaga).*
  - Setelah masuk, tombol tambah kolom tanggal, tambah pengeluaran (dengan foto nota), dan edit nominal kas siswa akan aktif.

