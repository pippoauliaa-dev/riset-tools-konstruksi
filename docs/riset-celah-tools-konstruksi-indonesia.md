# Riset Celah Tools di Industri Konstruksi Indonesia

**Tanggal:** 18 September 2026  
**Jenis:** Desk research dan opportunity discovery  
**Fokus:** Kontraktor dan subkontraktor kecil-menengah di Indonesia

> **Status temuan:** Ini adalah hipotesis peluang berbasis desk research. Belum dapat dianggap sebagai hasil validasi pelanggan atau ukuran pasar. Langkah berikutnya adalah wawancara pengguna dan concierge MVP.

## 1. Ringkasan eksekutif

Celah terbesar bukan pada ketiadaan “software konstruksi” secara umum, melainkan pada putusnya aliran informasi antara lapangan, biaya, material, perubahan pekerjaan, dan penagihan.

Banyak perusahaan sudah memakai Excel, WhatsApp, Google Drive, PDF, dan aplikasi desain. Masalahnya, alat-alat tersebut tidak membentuk satu alur bukti proyek. Akibatnya, informasi penting terlambat, tercecer, atau baru diketahui ketika uang sudah hilang.

Peluang produk paling rasional untuk divalidasi lebih dahulu adalah:

> **Project Margin Control untuk kontraktor spesialis** — tools ringan yang menghubungkan RAB, progress lapangan, biaya aktual, pekerjaan tambah, dan bukti penagihan agar margin proyek tidak bocor tanpa diketahui.

## 2. Kriteria penilaian peluang

| Kriteria | Pertanyaan |
|---|---|
| Frekuensi | Apakah masalah muncul setiap minggu atau hanya sesekali? |
| Dampak | Apakah menyebabkan kehilangan uang, keterlambatan, rework, atau risiko hukum? |
| Pemilik masalah | Apakah jelas siapa yang merasakan dan bisa membeli tools? |
| Kemudahan adopsi | Apakah bisa dipakai tanpa mengubah seluruh sistem perusahaan? |
| Kemudahan MVP | Apakah bisa dibuat tanpa BIM, IoT, marketplace, atau integrasi rumit? |
| Bukti | Apakah ada studi/laporan yang mendukung, atau baru asumsi? |

Prioritas diberikan pada masalah yang sudah diselesaikan secara manual, meninggalkan jejak data, memiliki dampak finansial langsung, dan dapat dimulai dari satu proyek.

## 3. Temuan masalah utama

### 3.1 Rework dan perubahan pekerjaan menggerus margin

Studi tentang cost overrun di Indonesia mengidentifikasi 15 faktor, antara lain:

- perubahan pekerjaan;
- rework;
- performa subkontraktor/vendor;
- keterlambatan approval;
- ketidakakuratan budgeting;
- perencanaan sumber daya;
- fluktuasi harga material;
- keterlambatan pembayaran;
- cash flow lemah;
- cuaca; dan
- persyaratan tambahan dari owner.

Dalam studi tersebut, owner dan kontraktor sama-sama menilai rework sebagai faktor utama cost overrun.

Di lapangan, perubahan kecil sering masuk melalui WhatsApp, instruksi lisan, coretan gambar, foto, rapat, revisi PDF, atau permintaan owner yang belum memiliki nomor instruksi resmi. Ketika penagihan atau perselisihan terjadi, kontraktor kesulitan membuktikan kapan pekerjaan diminta, siapa yang meminta, berapa volumenya, dan berapa dampaknya terhadap waktu serta biaya.

**Celah tool: Variation Order & Rework Evidence Tracker**

Fitur minimum:

- catat instruksi perubahan;
- hubungkan ke item BOQ/RAB;
- simpan foto sebelum/sesudah;
- catat pihak yang meminta;
- estimasi dampak biaya dan waktu;
- status draft → diajukan → disetujui → dikerjakan → ditagihkan;
- ekspor laporan klaim.

### 3.2 Perencanaan dan pengendalian biaya belum tersambung ke lapangan

Studi di Aceh menemukan 60 faktor keterlambatan. Sebanyak 30 indikator masuk kategori sangat berpengaruh dan 29 masuk kategori berpengaruh tinggi.

Studi lain menunjukkan perbedaan persepsi antara owner dan kontraktor:

- owner menilai tambahan kebutuhan owner sebagai faktor cost overrun utama;
- kontraktor menilai rework sebagai faktor utama;
- owner menyoroti budgeting/resource planning untuk keterlambatan;
- kontraktor menyoroti keterlambatan pembebasan lahan.

Ini menunjukkan akumulasi deviasi kecil sering tidak terlihat secara dini:

- volume aktual berbeda dari RAB;
- material lebih mahal;
- pekerjaan diulang;
- approval terlambat;
- tenaga kerja tidak sesuai rencana;
- perubahan pekerjaan tidak segera dimasukkan ke forecast.

**Celah tool: RAB-to-Actual Cost Control**

Fitur minimum:

- impor RAB/BOQ dari Excel;
- pecah anggaran berdasarkan pekerjaan dan material;
- masukkan pembelian aktual;
- masukkan progress aktual;
- bandingkan budget, committed cost, actual cost, dan forecast;
- tampilkan item yang mulai bocor;
- peringatan ketika biaya aktual lebih tinggi daripada progress.

Contoh peringatan yang bernilai:

> Pekerjaan pasangan bata sudah 62%, tetapi biaya material sudah 81% dari anggaran.

### 3.3 Laporan harian ada, tetapi tidak menjadi data keputusan

Laporan harian proyek sering dibuat lewat pesan WhatsApp, foto tanpa keterangan lengkap, Excel, Word, atau format berbeda-beda antar site engineer. Kantor pusat kemudian sulit menjawab:

- pekerjaan apa yang benar-benar selesai hari ini;
- berapa tenaga kerja yang hadir;
- apa penyebab deviasi;
- apakah pekerjaan tertunda karena material, tenaga kerja, cuaca, atau instruksi;
- apakah progress sudah diverifikasi;
- apakah foto berasal dari lokasi dan tanggal yang dimaksud.

**Celah tool: Daily Site Evidence Tool**

Input minimum:

- proyek;
- tanggal dan waktu;
- item pekerjaan;
- volume/progress;
- tenaga kerja;
- material yang digunakan;
- kendala;
- foto;
- lokasi;
- pihak yang memverifikasi.

Output:

- laporan harian otomatis;
- progress mingguan;
- daftar isu terbuka;
- keterlambatan berdasarkan penyebab;
- dokumentasi untuk rapat atau klaim.

Jangan memulai dari “AI laporan proyek”. Mulai dari input yang cepat, foto dan catatan terstruktur, validasi sederhana, dan laporan otomatis.

### 3.4 Procurement material tidak sinkron dengan jadwal kerja

Masalah yang perlu divalidasi:

- permintaan material terlambat;
- material dipesan tanpa mengacu pada kebutuhan aktual;
- spesifikasi berubah tetapi purchase order tidak berubah;
- material tiba terlalu cepat dan rusak/menumpuk;
- material tiba terlambat dan tenaga kerja menganggur;
- harga vendor sulit dibandingkan;
- penggunaan aktual tidak dibandingkan dengan volume RAB;
- pembelian darurat lebih mahal.

**Celah tool: Material Request-to-Delivery Tracker**

Alur:

```text
Kebutuhan pekerjaan
        ↓
Material request
        ↓
Permintaan penawaran vendor
        ↓
Perbandingan harga dan waktu kirim
        ↓
Purchase order
        ↓
Pengiriman
        ↓
Penerimaan dan pemeriksaan
        ↓
Penggunaan aktual
        ↓
Rekonsiliasi dengan RAB
```

MVP tidak perlu menjadi marketplace. Lebih aman dimulai sebagai alat kontrol internal kontraktor.

### 3.5 Progress subkontraktor sulit direkonsiliasi dengan pembayaran

Kontraktor utama sering harus menggabungkan progress dari subkontraktor, opname, volume yang disetujui, retensi, uang muka, material yang dipinjamkan, pekerjaan tambah-kurang, invoice, dan back charge.

Kesalahan kecil dapat menyebabkan pembayaran berlebih, pembayaran tertunda, konflik, cash flow terganggu, dan pekerjaan berikutnya tersendat.

**Celah tool: Subcontractor Progress & Payment Reconciliation**

Fitur:

- kontrak dan item pekerjaan;
- progress claim;
- foto bukti;
- opname;
- approval berjenjang;
- variation order;
- retensi dan uang muka;
- rekonsiliasi invoice;
- histori performa subkontraktor.

### 3.6 Keselamatan menghadapi konflik produksi dan keselamatan

Studi safety climate di industri konstruksi Indonesia dengan data 311 pekerja menemukan masalah di sekitar:

- konflik target produksi dan keselamatan;
- trade-off biaya dengan prioritas proyek lain;
- komunikasi buruk;
- kondisi kerja tidak mendukung;
- pelaporan dan monitoring lemah;
- pelatihan tidak memadai;
- lingkungan yang membuat pekerja enggan bekerja aman;
- rendahnya pemberdayaan dan akuntabilitas pekerja.

**Celah tool: Safety & Near-Miss Workflow**

Fitur:

- toolbox meeting dan attendance;
- checklist berdasarkan jenis pekerjaan;
- laporan near miss;
- foto kondisi berbahaya;
- penanggung jawab tindakan korektif;
- tenggat perbaikan;
- eskalasi bila tidak selesai;
- histori keselamatan per proyek/vendor.

Peluang ini nyata, tetapi pembeliannya lebih sulit untuk kontraktor kecil kecuali ada persyaratan HSE owner, audit, risiko penghentian proyek, atau penalti.

### 3.7 BIM bermanfaat, tetapi aksesnya berat untuk kontraktor lokal

Studi adopsi BIM di Indonesia menemukan manfaat seperti clash detection, simulasi, pengurangan rework, dan pemakaian sumber daya yang lebih baik. Hambatannya meliputi biaya software/hardware, kurangnya tenaga ahli, kurangnya pemahaman manfaat, resistensi perubahan, belum konsistennya permintaan owner, dan budaya organisasi.

**Celah yang lebih realistis: BIM-lite/document-lite**

- penampil gambar dan revisi;
- penanda lokasi masalah di denah/PDF;
- hubungan gambar, item pekerjaan, foto, dan issue;
- log perubahan dokumen;
- approval revisi;
- distribusi gambar terbaru ke lapangan.

Jangan membangun BIM baru. Buat workflow yang tetap berguna meskipun perusahaan belum memiliki model BIM 3D.

## 4. Ranking peluang awal

Skala 1–5: Pain = dampak masalah, Frequency = frekuensi, Pay = potensi dibayar, Reach = kemudahan menjangkau pembeli, MVP = kemudahan membuat versi awal.

| Peluang | Pain | Frequency | Pay | Reach | MVP | Total indikatif |
|---|---:|---:|---:|---:|---:|---:|
| RAB-to-actual cost control | 5 | 5 | 5 | 4 | 4 | **23** |
| Daily site evidence/reporting | 4 | 5 | 4 | 5 | 5 | **23** |
| Variation order & claim evidence | 5 | 4 | 5 | 4 | 4 | **22** |
| Material request-to-delivery | 5 | 5 | 4 | 4 | 4 | **22** |
| Quality punchlist/NCR | 4 | 4 | 4 | 4 | 5 | **21** |
| Subcontractor progress/payment | 5 | 4 | 5 | 3 | 3 | **20** |
| Workforce attendance/productivity | 4 | 5 | 3 | 4 | 4 | **20** |
| Safety/near-miss workflow | 5 | 4 | 3 | 3 | 4 | **19** |
| Handover/warranty/defect management | 3 | 3 | 3 | 4 | 5 | **18** |
| Drawing revision/BIM-lite | 4 | 3 | 3 | 3 | 3 | **16** |

Skor ini bukan ukuran pasar. Fungsinya menentukan urutan validasi.

## 5. Tiga peluang terbaik

### 5.1 Construction Cost Leakage Control

**Masalah:** kontraktor tahu nilai kontrak dan budget awal, tetapi terlambat mengetahui bagian proyek yang melewati budget, pekerjaan tambah yang belum ditagihkan, rework, dan kebutuhan cash sampai proyek selesai.

**Pengguna awal:** kontraktor kecil-menengah, project manager, quantity surveyor, owner kontraktor, dan finance proyek.

**MVP:**

1. buat proyek;
2. impor RAB/BOQ Excel;
3. masukkan biaya aktual;
4. catat progress per item;
5. catat perubahan pekerjaan;
6. tampilkan budget vs actual vs forecast;
7. ekspor laporan Excel/PDF.

**Kelebihan:** dampak uang langsung, ROI mudah dijelaskan, tidak perlu mengganti software desain, dapat digunakan per proyek.

**Risiko:** disiplin data biaya rendah, definisi progress tidak seragam, pengguna berharap software otomatis menghitung seluruh RAB, integrasi akuntansi memperbesar scope.

### 5.2 Bukti perubahan pekerjaan dan klaim

**Masalah:** pekerjaan sudah dikerjakan, tetapi instruksi belum resmi, volume belum terukur, harga belum disepakati, foto tidak terorganisasi, approval sulit ditemukan, dan kontraktor kehilangan kesempatan menagih.

**Pengguna awal:** kontraktor spesialis, kontraktor interior, MEP contractor, subcontractor, QS, dan project manager.

**MVP:** issue/change register, foto dan dokumen, pihak pemberi instruksi, estimasi biaya/waktu, status approval, link ke RAB, dan laporan klaim.

**Risiko:** approval tetap bergantung pada relasi dan politik proyek; tool tidak dapat memaksa owner membayar; hindari klaim sebagai nasihat hukum.

### 5.3 Material Control untuk proyek

**Masalah:** material tidak tersedia saat dibutuhkan, pembelian darurat mahal, stok tidak akurat, material diterima tidak sesuai, dan pembelian aktual tidak dibandingkan dengan RAB.

**Pengguna awal:** kontraktor renovasi, kontraktor rumah tinggal, kontraktor MEP, kontraktor finishing, dan procurement proyek.

**MVP:** material request, tanggal dibutuhkan, quotation vendor, PO sederhana, penerimaan, stok masuk/keluar, foto surat jalan, dan perbandingan pembelian dengan budget.

**Risiko:** kompetisi dari inventory/procurement umum, variasi proses antar jenis pekerjaan, dan data penggunaan material yang tidak disiplin.

## 6. Rekomendasi produk

### Project Margin Control untuk Kontraktor Spesialis

Positioning:

> Tahu lebih cepat bagian proyek mana yang mulai menghabiskan margin—sebelum terlambat ditagihkan atau diperbaiki.

Alur inti:

```text
RAB / BOQ
   ↓
Progress lapangan
   ↓
Biaya pembelian dan subkontrak
   ↓
Perubahan pekerjaan
   ↓
Rework / issue
   ↓
Forecast margin
   ↓
Laporan owner dan penagihan
```

Laporan harian sebaiknya menjadi input untuk kontrol biaya dan klaim, bukan produk utama yang hanya membuat laporan lebih rapi.

### Modul MVP

#### Setup proyek

- nama proyek;
- owner;
- kontrak;
- tanggal mulai/selesai;
- nilai kontrak;
- RAB/BOQ Excel;
- daftar pengguna.

#### Pencatatan lapangan

- pekerjaan;
- volume;
- foto;
- kendala;
- material;
- tenaga kerja;
- status pekerjaan.

#### Pemeriksaan komersial

- pekerjaan awal dan pekerjaan baru;
- alasan perubahan;
- pemberi instruksi;
- estimasi volume dan harga;
- dampak durasi;
- lampiran bukti;
- status approval.

#### Kontrol biaya

```text
Budget
+ approved variation
- actual cost
= remaining budget

Progress value
- actual cost
= indikasi margin sementara
```

Sistem harus menandai biaya tinggi tetapi progress rendah, item rework, material yang melewati budget, pekerjaan yang sudah dilakukan tanpa variation order, dan invoice tanpa bukti lengkap.

## 7. Fitur yang jangan dibuat dahulu

### BIM 3D penuh

Pasar lebih kompleks, biaya implementasi tinggi, dan hambatan keahlian besar.

### Marketplace material

Memerlukan jaringan vendor, verifikasi kualitas, logistik, pembayaran, wilayah operasional, dan network effect.

### AI estimator akurasi tinggi

Tanpa database harga lokal, standar item konsisten, gambar terstruktur, histori proyek, dan definisi spesifikasi yang jelas, AI estimator berisiko menghasilkan angka tampak pintar tetapi salah.

### ERP konstruksi lengkap

Scope cepat melebar ke akuntansi, payroll, inventory, procurement, CRM, project management, document management, dan compliance.

### Safety app yang hanya checklist

Checklist tanpa penanggung jawab, deadline, eskalasi, dan bukti penutupan hanya mengubah kertas menjadi PDF.

## 8. Rencana validasi pelanggan

Jangan mengandalkan survei opini online. Lakukan wawancara berbasis proyek dan minta izin melihat workflow aktual.

### Target awal

- 5 kontraktor spesialis;
- 3 kontraktor umum kecil-menengah;
- 3 site engineer/project manager;
- 3 QS atau estimator;
- 2 finance/admin proyek;
- 2 subkontraktor.

Total awal: 18 orang.

### Pertanyaan wawancara

1. Ceritakan proyek terakhir yang marginnya turun.
2. Bagian mana yang pertama kali menyebabkan masalah?
3. Kapan masalah itu disadari?
4. Data apa yang dipakai untuk mengetahuinya?
5. Boleh lihat file atau chat yang dipakai untuk memantau masalah itu?
6. Pernahkah ada pekerjaan tambahan yang tidak tertagihkan?
7. Berapa lama membuat laporan mingguan?
8. Siapa yang memeriksa progress dan biaya?
9. Bagian mana yang masih harus dicari dari WhatsApp?
10. Jika masalah itu tidak terjadi lagi, berapa nilainya bagi perusahaan?

Hindari pertanyaan seperti “Apakah Anda tertarik menggunakan aplikasi kontrol proyek?” karena jawaban positif tidak membuktikan willingness to pay.

### Concierge MVP

Sebelum membuat aplikasi penuh:

1. minta satu proyek mengirim RAB dan laporan harian;
2. gunakan spreadsheet terstruktur;
3. bantu mengidentifikasi deviasi;
4. buat laporan mingguan manual;
5. catat pekerjaan tambah dan risiko biaya yang ditemukan;
6. minta pelanggan membayar pilot.

Jika pelanggan belum mau membayar versi manual yang memberi manfaat, kemungkinan besar mereka belum akan membayar software-nya.

### Indikator lanjut

Dalam 4–6 minggu, cari bukti berikut:

- minimal tiga perusahaan bersedia menjalankan pilot;
- minimal dua bersedia membayar;
- pengguna mengirim data proyek secara rutin;
- ditemukan pekerjaan tambah atau cost leakage nyata;
- laporan menghemat waktu administrasi;
- owner proyek menggunakan output dalam rapat atau penagihan.

## 9. Keterbatasan riset

- Belum ada customer interview langsung.
- Studi akademik yang ditemukan banyak memakai survei dengan sampel terbatas atau konteks wilayah tertentu.
- Desk research tidak dapat mengukur willingness to pay secara akurat.
- Tidak semua workflow kontraktor Indonesia seragam.
- Skor peluang adalah prioritisasi hipotesis, bukan estimasi TAM/SAM/SOM.
- Daftar kompetitor komersial perlu diperbarui melalui mystery shopping dan uji coba produk.

## 10. Sumber utama

1. [PLOS ONE — Causes of delays in construction projects in the Province of Aceh, Indonesia](https://doi.org/10.1371/journal.pone.0263337)
2. [IOP — Cost Overrun in Construction Projects in Indonesia](https://doi.org/10.1088/1755-1315/506/1/012039)
3. [IOP — Cost overrun and time delay of construction project in Indonesia](https://doi.org/10.1088/1742-6596/1444/1/012050)
4. [IJERPH — A Safety Climate Framework for Improving Health and Safety in the Indonesian Construction Industry](https://doi.org/10.3390/ijerph17207462)
5. [MATEC — Investigating Building Information Modelling Adoption in Indonesia Construction Industry](https://doi.org/10.1051/matecconf/201925802006)
6. [The Barrier and Driver Factors of Building Information Modelling Adoption in Indonesia](https://doi.org/10.12962/j23546026.y2019i5.6291)
7. [Implementing BIM in AEC companies: local contractors in Palembang](https://doi.org/10.14424/ijcscm901019-20-34)
8. [Automation in Construction — Artificial intelligence in the construction industry](https://doi.org/10.1016/j.autcon.2021.103299)

## 11. Tindak lanjut yang disarankan

1. Wawancarai kontraktor spesialis, bukan pengguna software secara umum.
2. Pilih satu workflow paling mahal: cost leakage atau variation order.
3. Jalankan concierge MVP berbasis spreadsheet selama satu proyek.
4. Ukur uang yang terselamatkan, pekerjaan tambah yang tertagihkan, dan waktu laporan yang dihemat.
5. Bangun software hanya setelah ada pelanggan yang membayar pilot.
