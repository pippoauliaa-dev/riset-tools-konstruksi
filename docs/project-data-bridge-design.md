# Project Data Bridge — Design Spec

**Tanggal:** 18 September 2026  
**Status:** Baseline desain disetujui untuk ditulis; belum diimplementasikan  
**Platform MVP:** Android PWA  
**Target awal:** Kontraktor dan tim proyek yang masih mengandalkan WhatsApp pribadi, Excel, foto, dan PDF

## 1. Ringkasan

Project Data Bridge adalah integrator ringan yang mengubah pesan, foto, voice note, PDF, dan file yang dipilih pengguna dari WhatsApp pribadi menjadi record proyek formal.

Produk tidak menggantikan WhatsApp. Produk juga tidak membaca histori chat, kontak, atau percakapan lain. Pengguna secara sadar memilih konten di WhatsApp dan menekan **Share → Project Data Bridge**.

```text
WhatsApp / Excel / PDF / foto
              ↓
        Project Data Bridge
              ↓
      Data proyek terstruktur
              ↓
Progress · Issue/Rework · Material · Potential VO
```

### Hipotesis nilai

> Informasi proyek yang sekarang berhenti di chat dapat diubah menjadi bukti, tugas, approval, dan output administrasi tanpa memaksa seluruh perusahaan mengganti Excel atau WhatsApp.

## 2. Masalah yang ditargetkan

Dalam proyek konstruksi, informasi penting sering muncul sebagai pesan, foto, file, atau instruksi informal. Informasi tersebut kemudian sulit ditemukan kembali ketika dibutuhkan untuk:

- memverifikasi progress;
- melacak issue dan rework;
- mengecek material;
- menyusun variation order;
- menilai dampak biaya/waktu;
- membuat progress billing;
- menjawab pertanyaan owner;
- menyelesaikan sengketa atau audit.

Produk ini tidak mengklaim dapat menyelesaikan penyebab struktural seperti konflik lahan, cuaca, inflasi, atau keputusan owner. Produk hanya membantu membuat deviasi, bukti, konteks, dan dampaknya lebih terlihat lebih awal.

## 3. Prinsip desain

1. **WhatsApp tetap menjadi pintu masuk.** Pengguna tidak dipaksa mengubah kebiasaan komunikasi untuk memulai.
2. **Excel tetap menjadi format kerja awal.** RAB/BOQ dapat diimpor dan hasil dapat diekspor kembali.
3. **Explicit share only.** Tidak ada pembacaan histori atau scraping chat.
4. **Evidence-first.** Bukti asli disimpan dan tidak boleh diubah diam-diam.
5. **Human verification.** AI, jika ditambahkan kemudian, hanya memberi saran; manusia memutuskan klasifikasi dan approval.
6. **One evidence, many links.** Satu foto/pesan dapat ditautkan ke beberapa record tanpa menggandakan file.
7. **Role-based visibility.** Mandor, QS, finance, dan owner tidak otomatis melihat data yang sama.
8. **Exportable.** Data dapat diekspor ke XLSX/PDF agar tidak terkunci di produk.
9. **Mobile-first.** Input utama harus praktis dari Android di lapangan.
10. **Bukan ERP.** Accounting, BIM, payroll, marketplace, dan chat replacement berada di luar MVP.

## 4. Sasaran pengguna dan peran

Semua pihak dapat memakai workflow yang sama, tetapi tidak semuanya harus menjadi pembeli pertama.

| Peran | Kebutuhan utama | Akses MVP |
|---|---|---|
| Mandor | Mengirim foto, progress, issue, material | Membuat record dan melihat tugas miliknya |
| Site engineer | Memeriksa bukti dan konteks lapangan | Membuat, mengedit draft, memverifikasi teknis |
| QS/estimator | Menghubungkan record ke BOQ dan menghitung dampak | Mengisi volume, harga, dan draft VO |
| Project manager | Mengendalikan seluruh proyek | Melihat, mengassign, approve/reject, eskalasi |
| Finance | Menyusun billing dan memantau tagihan | Melihat approved record, biaya, dan status billing |
| Owner | Melihat hasil dan memberi keputusan | Melihat scope yang dibagikan, komentar, approve/reject VO |
| Admin perusahaan | Mengelola organisasi dan proyek | Mengatur user, role, proyek, dan kebijakan data |

### Aturan akses utama

- Mandor tidak dapat melihat margin internal atau harga vendor privat.
- Owner melihat data yang dibagikan untuk mereka, bukan catatan internal otomatis.
- Finance tidak dapat mengubah bukti teknis yang sudah dikunci.
- Record yang sudah approved tidak diedit langsung; perubahan dibuat sebagai amendment.
- Semua akses dan perubahan field penting dicatat di audit log.

## 5. Workflow MVP

### 5.1 Capture dari WhatsApp

```text
Pengguna memilih pesan/foto/file di WhatsApp
        ↓
Menekan Share
        ↓
Memilih Project Data Bridge
        ↓
PWA menerima text, title, URL, dan/atau files
        ↓
Payload masuk Unified Inbox
```

Jenis payload prioritas:

- teks;
- foto JPG/PNG;
- PDF;
- XLSX/DOCX;
- voice note/audio sebagai file asli;
- video pendek dengan batas ukuran yang dikonfigurasi.

Aplikasi tidak menjanjikan bahwa WhatsApp/Android akan meneruskan semua metadata. Timestamp asli, nama chat, pesan sebelum/sesudah, lokasi, dan metadata foto dapat tidak tersedia. Konteks penting diminta secara eksplisit di tahap berikutnya.

### 5.2 Unified Inbox

Inbox menyimpan payload mentah sebelum menjadi record formal.

Contoh:

```text
“Pak, gambar kamar mandi lantai 2 berubah.
Tukang sudah bongkar keramik lama.”

Dikirim oleh: Budi
Diterima: 18 Sep 2026, 10:42
Status: Needs context
```

Pengguna melengkapi:

- proyek;
- lokasi;
- tipe record;
- urgensi;
- pihak terkait;
- visibilitas owner;
- catatan tambahan.

Satu InboxItem dapat dikonversi menjadi lebih dari satu record:

```text
Potential VO + Issue/Rework + Progress impact
```

Evidence asli tetap disimpan sekali.

### 5.3 Empat tipe record

#### Progress

- pekerjaan;
- BOQ item;
- volume dan satuan;
- persentase;
- foto/video;
- tenaga kerja;
- tanggal/lokasi;
- status verifikasi.

#### Issue/Rework

- masalah;
- penyebab;
- pekerjaan terdampak;
- evidence;
- estimasi biaya/waktu;
- penanggung jawab;
- deadline;
- resolusi dan verifikasi penutupan.

#### Material

- material dan spesifikasi;
- jumlah dan satuan;
- supplier;
- kebutuhan/pemesanan/penerimaan;
- surat jalan/evidence;
- kekurangan;
- kondisi;
- status delivery.

#### Potential Variation Order

- pemberi instruksi;
- scope awal dan scope baru;
- BOQ item;
- volume dan harga;
- estimasi biaya/durasi;
- evidence;
- approval status;
- billing status.

### 5.4 Status

Status umum:

```text
Captured → Needs context → In review → Verified → Approved/Rejected → Closed
```

Status khusus Potential VO:

```text
Draft → Costed → Submitted → Approved/Rejected → Billed → Paid
```

Status khusus Issue/Rework:

```text
Open → Assigned → In progress → Resolved → Verified closed
```

## 6. Model data konseptual

### Project

```text
id
company_id
name
code
owner_name
start_date
end_date
contract_value
status
created_at
updated_at
```

### ProjectMember

```text
id
project_id
user_id
role
visibility_scope
joined_at
```

### InboxItem

Payload asli dari share.

```text
id
project_id                  nullable saat capture
submitted_by
source                      whatsapp_share
raw_text
raw_title
raw_url
received_at
classification              nullable
status
visibility
created_at
```

### Evidence

```text
id
inbox_item_id
file_name
mime_type
size_bytes
storage_key
checksum
captured_at                 nullable
uploaded_at
uploaded_by
```

### ProjectRecord

Entitas umum untuk empat workflow.

```text
id
project_id
inbox_item_id
type                        progress | issue_rework | material | potential_vo
title
description
location
reported_by
assigned_to
status
priority
occurred_at
verified_at
verified_by
created_at
updated_at
```

### ProgressDetail

```text
record_id
boq_item_id
quantity
unit
percentage
workforce_count
weather
```

### IssueDetail

```text
record_id
issue_type
root_cause
affected_boq_item_id
estimated_cost_impact
estimated_delay_days
resolution_due_at
resolution_notes
```

### MaterialDetail

```text
record_id
material_name
specification
quantity
unit
supplier
delivery_status
delivery_date
shortage_quantity
condition
```

### VariationOrderDetail

```text
record_id
instruction_by
original_scope
new_scope
boq_item_id
estimated_quantity
estimated_unit_price
estimated_cost
estimated_delay_days
approval_status
billed_status
```

### AuditEvent

```text
id
entity_type
entity_id
action
old_value
new_value
actor_id
created_at
```

## 7. Arsitektur teknis MVP

```text
Android PWA
   ↓ HTTPS
Backend API
   ↓
PostgreSQL
   +
Object storage untuk file/evidence
```

Rekomendasi:

- frontend: PWA mobile-first;
- manifest Web Share Target;
- service worker untuk menerima share dan queue offline;
- IndexedDB untuk payload yang belum ter-upload;
- backend API: FastAPI atau framework web setara;
- database: PostgreSQL;
- object storage dengan signed URL;
- auth: email/OTP atau magic link;
- export: XLSX dan PDF;
- deployment: satu cloud application sederhana.

Tidak perlu microservices pada MVP.

### Share Target

Manifest mendaftarkan target dengan endpoint multipart. Payload yang diterima minimal:

```text
text
 title
 url
 files[]
```

Service worker melakukan:

1. validasi tipe dan ukuran;
2. menyimpan payload sementara ke IndexedDB;
3. mengarahkan pengguna ke `/inbox/new`;
4. mengunggah saat koneksi tersedia;
5. menampilkan status queued/synced/failed.

## 8. Offline dan reliabilitas

- Capture yang dilakukan tanpa koneksi disimpan lokal.
- UI menunjukkan status `Queued` sampai server mengonfirmasi.
- Upload diulang dengan backoff sederhana.
- Checksum mencegah file yang sama terduplikasi.
- Pengguna dapat retry atau membatalkan upload yang gagal.
- Record tidak disebut `Verified` hanya karena upload berhasil.
- Konflik edit diselesaikan dengan optimistic concurrency/version number; jangan menimpa perubahan orang lain diam-diam.

## 9. Privasi, keamanan, dan governance

Payload WhatsApp pribadi dapat mengandung nomor telepon, wajah, dokumen kontrak, harga vendor, dan informasi owner.

MVP wajib memiliki:

- consent dan privacy notice yang jelas;
- pemisahan tenant/company;
- role-based access control;
- HTTPS;
- signed URL dengan masa berlaku;
- encryption at rest dari storage yang dipakai;
- audit log akses dan perubahan;
- kebijakan retensi/penghapusan;
- penghapusan evidence sesuai hak admin dan kebijakan organisasi;
- backup dan restore yang diuji;
- larangan memakai data pelanggan untuk training tanpa persetujuan terpisah.

Voice note disimpan sebagai evidence asli. Transkripsi, jika ada nanti, hanya data bantu yang dapat dikoreksi.

### Batas keamanan produk

- Tidak membaca histori WhatsApp.
- Tidak mengakses kontak atau chat lain.
- Tidak mengirim pesan WhatsApp otomatis pada MVP.
- Tidak memakai WhatsApp Web scraping atau API tidak resmi.
- Tidak menyatakan foto/pesan sebagai fakta sebelum verifikasi.
- Tidak memberi nasihat hukum atau menjamin klaim dibayar.

## 10. Export dan output

Output minimum:

- rekap progress per proyek;
- daftar issue/rework terbuka;
- daftar material dan statusnya;
- draft/approved variation order;
- evidence register;
- audit trail dasar;
- export XLSX;
- export PDF;
- link read-only berumur terbatas untuk owner.

Format harus tetap berguna di luar produk. Export mencantumkan ID record, sumber evidence, status verifikasi, timestamp, dan pihak yang mengubah.

## 11. Acceptance criteria MVP

### Capture

- Pengguna Android dapat memilih teks dan foto dari WhatsApp lalu mengirimkannya melalui Share ke PWA.
- File PDF/XLSX yang valid dapat diterima.
- Payload tanpa koneksi tidak hilang dan berubah status menjadi `Queued`.
- Payload yang sama tidak menggandakan evidence saat retry.

### Context

- Pengguna wajib memilih proyek dan tipe record sebelum konversi.
- Sistem menolak record formal tanpa proyek, tipe, pengirim, dan evidence/text minimum.
- Inbox menyimpan payload asli yang dapat dibuka kembali.

### Workflow

- Empat tipe record dapat dibuat dari satu InboxItem.
- Record dapat diassign ke anggota proyek.
- Site engineer/QS dapat memverifikasi atau mengembalikan record.
- PM dapat approve/reject sesuai role.
- Record approved menyimpan audit event dan tidak dapat diubah tanpa amendment.

### Visibility

- Mandor tidak dapat membaca cost field privat.
- Owner hanya melihat record yang dibagikan untuk owner.
- Anggota proyek tidak dapat membaca proyek lain.
- Signed URL tidak dapat dipakai setelah kadaluarsa.

### Output

- XLSX dan PDF dapat diunduh untuk empat tipe record.
- Export mencantumkan status, evidence ID, dan histori perubahan utama.
- Link owner read-only tidak membuka data internal perusahaan.

## 12. Out of scope MVP

- iOS Share Target.
- WhatsApp Business/API resmi.
- WhatsApp bot, scraping, atau chat replacement.
- AI classification otomatis yang mengubah data tanpa konfirmasi.
- Voice transcription.
- Accounting dan payment processing.
- Payroll dan BPJS/PPh.
- Marketplace vendor/material.
- BIM 3D dan clash detection.
- Advanced analytics/predictive delay.
- OCR penuh untuk seluruh dokumen.
- Public marketplace atau network effect.

## 13. Rencana validasi sebelum coding penuh

Lakukan pilot concierge dengan spreadsheet dan folder evidence pada 1–3 proyek.

Wawancarai dan amati:

- kontraktor spesialis;
- kontraktor umum kecil-menengah;
- mandor;
- site engineer;
- QS;
- finance proyek;
- owner.

Minta contoh nyata:

- RAB/BOQ;
- laporan harian;
- chat perubahan pekerjaan;
- foto progress;
- progress claim;
- invoice;
- daftar rework;
- purchase request/surat jalan.

Lanjut ke implementasi jika ditemukan:

- minimal tiga proyek bersedia pilot;
- minimal dua calon pelanggan bersedia membayar;
- pengguna mengirim evidence rutin;
- minimal satu VO atau rework dapat ditelusuri lebih baik daripada workflow lama;
- export dipakai dalam rapat, approval, atau billing.

## 14. Keputusan desain yang ditunda

- Segmen pembeli pertama: kontraktor spesialis vs kontraktor umum.
- Model harga: per perusahaan, per proyek, per user, atau per volume evidence.
- Cloud region/data residency.
- Provider object storage.
- Email/OTP vs magic link.
- Batas ukuran video/audio.
- Kapan integrasi accounting dan WhatsApp Business layak ditambahkan.

Keputusan ini perlu ditentukan dari pilot, bukan diasumsikan di awal.
