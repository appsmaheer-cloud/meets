# 📋 PANDUAN RESMI: DUAL SPREADSHEET VIA IMPORT EXCEL
### Portal Layanan GS & Sistem Inventaris ATK / Gudang Persediaan
**PT Pratama Nusantara Sakti (PNS)**

---

## 🌟 1. Konsep Arsitektur Baru: Excel to Google Sheet

Untuk menghindari data tertukar, format berantakan, atau script error, kita menggunakan pendekatan **Master Excel yang Langsung Di-Import ke Google Drive**:

```
 ┌───────────────────────────────┐         ┌───────────────────────────────┐
 │     01_DATABASE_GS.xlsx       │         │     02_DATABASE_ATK.xlsx      │
 │  (Users, Ruangan, Bookings,   │         │  (218 SKU Stok, Masuk, Keluar,│
 │   Mobil, Zoom, E-Doc, dll)    │         │   Formula SUMIF, Karyawan)    │
 └───────────────┬───────────────┘         └───────────────┬───────────────┘
                 │ (Upload & Buka)                         │ (Upload & Buka)
                 ▼                                         ▼
   [ Google Spreadsheet 1 (GS) ]             [ Google Spreadsheet 2 (ATK) ]
         ID: Salin dari URL                        ID: Salin dari URL
                 │                                         │
                 └───────────────────┬─────────────────────┘
                                     ▼
                     ┌───────────────────────────────┐
                     │          kode_google          │
                     │  (SheetDB.gs: Pasang 2 ID)    │
                     │  (CekKoneksi.gs: Verifikasi)  │
                     └───────────────┬───────────────┘
                                     ▼
                     ┌───────────────────────────────┐
                     │          kode_git             │
                     │   (Web App / GitHub Pages)    │
                     └───────────────────────────────┘
```

---

## 📁 2. Dua File Master Excel yang Tersedia di Folder `FINAL/`

1. **`01_DATABASE_GS.xlsx`** (Layanan Operasional Kantor):
   - `users` (28 data user, admin, PIN)
   - `rooms` (3 ruang rapat)
   - `bookings` (771 riwayat booking ruang rapat)
   - `car_vehicles` (4 unit kendaraan dinas)
   - `car_requests` (25 data permohonan mobil)
   - `virtual_meetings` (25 agenda Zoom meeting)
   - `edoc_requests` (25 log pengiriman dokumen / surat jalan)
   - `support_tickets` (tiket kendala GS)
   - `holidays` (daftar libur & cuti bersama)
   - `system_settings` (konfigurasi aplikasi)

2. **`02_DATABASE_ATK.xlsx`** (Inventaris & Gudang Persediaan):
   - `Master & Saldo Stok` (218 item SKU barang, satuan, harga, rumus SUMIF)
   - `Barang Masuk` (12 kolom data PO / TPB Logistik)
   - `Barang Keluar` (16 kolom data BKB & Cost Object)
   - `data_karyawan` (34 data karyawan & daftar Cost Object)

---

## 🚀 3. Langkah Setup (Mudah, Hanya 3 Menit)

### Langkah 1: Upload 2 File Excel ke Google Drive
1. Buka [Google Drive](https://drive.google.com).
2. Buat folder baru (misal: `Database Portal PNS`).
3. Upload kedua file dari folder `FINAL/`:
   - `01_DATABASE_GS.xlsx`
   - `02_DATABASE_ATK.xlsx`
4. **Jadikan Google Spreadsheet:**
   - Klik kanan pada `01_DATABASE_GS.xlsx` $\rightarrow$ **Open with (Buka dengan)** $\rightarrow$ **Google Sheets**.
   - Klik kanan pada `02_DATABASE_ATK.xlsx` $\rightarrow$ **Open with (Buka dengan)** $\rightarrow$ **Google Sheets**.

---

### Langkah 2: ID Spreadsheet Anda yang Sudah Terpasang
- **Spreadsheet 1 (Layanan GS):**
  - URL: `https://docs.google.com/spreadsheets/d/1MCmYmM02bZwIzTVlHiVNNANw3omBovagOecpxqf5eW8/edit`
  - ID: `1MCmYmM02bZwIzTVlHiVNNANw3omBovagOecpxqf5eW8`
- **Spreadsheet 2 (Inventaris ATK):**
  - URL: `https://docs.google.com/spreadsheets/d/1enq0j_Q1IK3uIZ4o-VPp5rDmUQn9mvtdaTBFgwZdd-s/edit`
  - ID: `1enq0j_Q1IK3uIZ4o-VPp5rDmUQn9mvtdaTBFgwZdd-s`

---

### Langkah 3: Konfigurasi di `SheetDB.gs` (Sudah Terpasang Otomatis)
Buka file `FINAL/kode_google/SheetDB.gs`:

```javascript
  // 1. Spreadsheet Layanan GS (Di-import dari 01_DATABASE_GS.xlsx)
  var SPREADSHEET_ID_GS = '1MCmYmM02bZwIzTVlHiVNNANw3omBovagOecpxqf5eW8'; 

  // 2. Spreadsheet Inventaris ATK & Persediaan (Di-import dari 02_DATABASE_ATK.xlsx)
  var SPREADSHEET_ID_ATK = '1enq0j_Q1IK3uIZ4o-VPp5rDmUQn9mvtdaTBFgwZdd-s'; 
```

---

### Langkah 4: Uji Koneksi dengan 1-Klik (`CekKoneksi.gs`)
1. Buka **Extensions** $\rightarrow$ **Apps Script** pada Google Sheet Anda (atau di Apps Script standalone project).
2. Di dropdown fungsi bagian atas, pilih fungsi **`CekKoneksiDatabase`**.
3. Klik **▶ Run**.
4. Buka **Execution Log**. Anda akan langsung melihat laporan apakah seluruh data GS dan ATK berhasil terbaca dengan status hijau:
   ```
   ✅ STATUS GS: TERHUBUNG & VALID!
      • users : 28 baris
      • rooms : 3 ruangan
      • bookings : 771 data booking
      ...
   ✅ STATUS ATK: TERHUBUNG & VALID!
      • Master & Saldo Stok : 218 item SKU
      • Barang Masuk : ...
      • Barang Keluar : ...
   ```

---

### Langkah 5: Deploy Web App
1. Klik **Deploy** $\rightarrow$ **New deployment** (Penerapan Baru).
2. Pilih jenis **Web app**.
3. Atur:
   - **Execute as:** *Me (email Anda)*
   - **Who has access:** *Anyone (Siapa saja)*
4. Klik **Deploy** dan salin **Web app URL** yang dihasilkan.
5. Selesai! Web app siap digunakan baik langsung dari Google Apps Script maupun dihubungkan ke GitHub Pages (`kode_git`).
