# 🐙 PANDUAN DEPLOYMENT GITHUB PAGES (`kode_git`)
### Repositori: `https://github.com/appsmaheer-cloud/meets`
**PT Pratama Nusantara Sakti (PNS)**

---

## 🌟 URL GitHub Pages Resmi Anda:
👉 **`https://appsmaheer-cloud.github.io/meets/`**  
*(Pengaturan Pages: `https://github.com/appsmaheer-cloud/meets/settings/pages`)*

---

## 📋 File yang Di-Upload ke Repositori GitHub (`meets`):

Upload semua file berikut langsung ke root repositori Anda:

```text
📂 appsmaheer-cloud/meets (Root Repository)
│
├── 📄 index.html      <-- Portal Terpadu (Meeting, Mobil, E-Doc, Zoom, ATK Persediaan)
├── 📄 admin.html      <-- Dashboard Administrator GS & Logistik
├── 🖼️ favicon.ico     <-- Icon tab browser
├── 🖼️ favicon.png     <-- Logo resmi resolusi tinggi
├── 🖼️ bg.jpg          <-- Background landscape PNS
├── 🎥 video.mp4       <-- Video latar operasional kantor
└── 📄 README.md        <-- Dokumentasi Repositori
```

---

## 🚀 Cara Upload / Sinkronisasi ke Repositori `meets`:

### Cara 1: Lewat Web Browser (Paling Cepat & Mudah)
1. Buka repositori Anda di browser:  
   👉 **`https://github.com/appsmaheer-cloud/meets`**
2. Klik tombol **Add file** $\rightarrow$ pilih **Upload files**.
3. Tarik (*drag & drop*) seluruh file dari folder:  
   `c:\laragon\www\mr\kode_git\` (atau `FINAL\kode_git\`)
4. Di bagian bawah, masukkan pesan commit: `Deploy Portal PNS Dual-Sheet ke repo meets`, lalu klik tombol hijau **Commit changes**.

---

### Cara 2: Lewat Git Command Line (Terminal / CMD)
```bash
cd c:\laragon\www\mr\kode_git
git init
git remote add origin https://github.com/appsmaheer-cloud/meets.git
git add .
git commit -m "Deploy Portal PNS Dual-Sheet ke repo meets"
git branch -M main
git push -u origin main --force
```

---

## ⚙️ Pengaturan GitHub Pages (1-Kali Saja)
1. Buka: `https://github.com/appsmaheer-cloud/meets/settings/pages`
2. Di bagian **Build and deployment**:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` / `root`
3. Klik **Save**.
4. Dalam 1 menit, website langsung online di:  
   👉 **`https://appsmaheer-cloud.github.io/meets/`**
