# 🏛️ Aplikasi 1: Portal Ruang Meeting, E-Doc & Peminjaman Mobil
### PT Pratama Nusantara Sakti — Google Apps Script (Versi Ringan ~80 KB)

Aplikasi ini difokuskan khusus untuk layanan operasional utama perusahaan:
1. **🏛️ Ruang Meeting**:
   - Booking Ruangan (Besar, Kecil, Virtual)
   - Matrix Okupansi Jam (08:00 – 18:00) anti-bentrok
   - Kalender & monitoring jadwal hari ini
2. **📹 Meeting Virtual (Zoom Pro)**:
   - Pengajuan akun Zoom Pro korporat & pembagian tautan meeting
3. **🚗 Peminjaman Mobil Dinas**:
   - Request armada pool kendaraan (Toyota Innova, Avanza, Hilux 4x4, Gran Max)
   - Status approval & penugasan driver
4. **📦 Pengiriman E-Doc & Cetak Tanda Terima 3-per-A4 Landscape**:
   - Formulir pengiriman dokumen keluar & pencatatan dokumen masuk
   - Checklist multi-select dokumen + tombol "Pilih Semua"
   - **Bilah Aksi Cetak Massal (*Bulk Print*)**: Cetak tanda terima presisi **3 kolom per lembar A4 landscape** langsung dari browser tanpa membutuhkan server PHP!
5. **👥 Kelola Akun Pengguna (Admin Only)**:
   - Manajemen 28 karyawan aktif PNS, reset PIN ke 1234, toggle status aktif.

---

## 📁 Struktur File di Google Apps Script (`script.google.com`)

Buka Google Sheet untuk Aplikasi 1 (atau buat Spreadsheet baru), buka **Extensions > Apps Script**, lalu salin file dari folder `kode_google_app1/`:

| Nama File di Folder | Nama File di Apps Script | Tipe File | Keterangan |
|:---|:---|:---:|:---|
| **`Code.gs`** | `Code.gs` | Script | Backend API Router khusus Meeting, Edoc & Mobil |
| **`SheetDB.gs`** | `SheetDB.gs` | Script | Database engine cepat dengan RAM Cache |
| **`SetupSheet.gs`** | `SetupSheet.gs` | Script | Generator 1-Klik untuk membuat 8 sheet operasional |
| **`Index.html`** | `Index.html` | HTML | Antarmuka pengguna (Dashboard, Booking, E-Doc, Cetak) |
| **`CSS.html`** | `CSS.html` | HTML | Styling korporat PNS, Light/Dark mode, Print 3-per-A4 |
| **`JS.html`** | `JS.html` | HTML | Logika client-side & modal print receipt mandiri |
| **`appsscript.json`** | `appsscript.json` | Manifest | Konfigurasi Web App |

---

## ⚡ Langkah Cepat Deployment (Hanya 2 Langkah):

1. **Jalankan Fungsi Setup Database (1-Klik)**:
   - Di toolbar Apps Script atas, pilih fungsi: **`setupAllSheets`**.
   - Klik **Run (Jalankan)** dan berikan otorisasi izin Google.
   - Selesai! Seluruh 8 sheet (`users`, `rooms`, `bookings`, `edoc_requests`, `car_requests`, `car_vehicles`, `virtual_meetings`, `holidays`) otomatis dibuat dan terisi data awal.

2. **Deploy Sebagai Web App**:
   - Klik tombol **Deploy > New deployment**.
   - Pilih tipe: **Web app**.
   - **Execute as:** `Me (email Anda)`
   - **Who has access:** `Anyone`
   - Klik **Deploy** dan salin URL Web App yang muncul.
