# blasting.me

🌐 **Live Demo:** [https://homeprint-developer.github.io/blasting.me/](https://homeprint-developer.github.io/blasting.me/)

**blasting.me** adalah aplikasi web statis *single-page* yang dirancang untuk memfasilitasi pengiriman pesan WhatsApp massal (*Broadcast*) secara dinamis. Mengusung gaya antarmuka bersih dan minimalis ala **Laravel 12 Basic**, alat ini memecahkan masalah pemblokiran *pop-up browser* saat mengirim banyak pesan sekaligus dengan menerapkan sistem antrean manual (Queue System) yang aman dan terkendali.

---

## Fitur Utama

### 📱 Integrasi Buku Kontak (Contact Picker API)
Mendukung interaksi langsung dengan buku telepon (Phonebook) bawaan perangkat. Pengguna *mobile* dapat langsung menekan tombol **"Ambil dari Kontak"** untuk memilih puluhan nomor secara bersamaan *(Multi-Select)*. Sistem akan mengekstrak nomor tersebut, membersihkan formatnya (menghapus spasi dan simbol), dan menambahkannya secara otomatis ke dalam antrean tanpa menimpa nomor yang sudah ada. *(Catatan: Fitur ini otomatis hanya muncul pada browser mobile yang mendukung dan berada di protokol HTTPS).*

### 🚀 Sistem Antrean Cerdas (Queue Array System)
Menggunakan pendekatan metode *Pop & Shift Array* pada JavaScript, pengguna dapat menempelkan (*copy-paste*) puluhan nomor sekaligus. Sistem akan menahan nomor dalam antrean (*textarea*) dan memproses pengiriman satu per satu setiap kali tombol diklik.

### 🎨 Desain UI/UX ala Laravel 12
Antarmuka dirancang menyerupai *starter kit* modern Laravel (Breeze/Jetstream):
- Menggunakan tipografi bawaan Laravel, yaitu font **Figtree**.
- Gaya *Card* yang sangat *clean* dengan *border-radius* mulus (`rounded-2xl`) dan *shadow* minimal.
- Tombol dinamis (*Dynamic Button*) yang akan berubah warna (dari *Dark Gray* ke *Amber/Warning*) dan menampilkan sisa jumlah antrean ketika proses *blasting* sedang berjalan.

### 🛡️ Validasi Ketat & Penanganan Eror Visual (SweetAlert2)
Tidak ada lagi eror notifikasi melayang yang tersembunyi. Jika terdapat kesalahan input, sistem akan menampilkan *pop-up modal* besar di tengah layar yang berisi rincian spesifik:
- Mendeteksi dan memblokir nomor yang mengandung huruf atau simbol (*Regex Validation*).
- Mendeteksi nomor yang kurang dari 11 digit.
- Memberitahu secara visual **nomor mana saja** di dalam tumpukan *textarea* yang tidak valid agar pengguna dapat langsung memperbaikinya.

### ⚠️ Proteksi Keamanan (Spam Disclaimer & Session Memory)
Menampilkan peringatan risiko *spam* dan pernyataan lepas tanggung jawab (*disclaimer*) mengenai risiko pemblokiran nomor oleh WhatsApp sebelum sesi *blasting* pertama dimulai. Dilengkapi dengan **sistem memori sesi (Flagging)**, sehingga *pop-up* persetujuan ini hanya akan muncul **satu kali** di awal sesi agar tidak mengganggu kenyamanan pengguna saat mengklik tombol "Kirim Berikutnya".

### 🌍 Koreksi Kode Negara Otomatis
Logika pintar yang secara otomatis mendeteksi jika nomor diawali dengan angka `0` atau tanpa kode negara, dan langsung menormalisasinya menjadi format standar internasional Indonesia (`62`) agar API WhatsApp terbuka dengan sempurna.

---

## Teknologi yang Digunakan

Proyek ini tidak memerlukan *backend*, dibangun sepenuhnya dengan teknologi sisi klien (*Client-Side*):
- **Markup**: HTML5
- **Styling**: Tailwind CSS (via CDN) dengan kustomisasi konfigurasi *theme* bawaan.
- **Font**: Figtree (Google Fonts / Bunny Fonts).
- **Pop-up Interaktif**: SweetAlert2.
- **Native Device Access**: Web Contact Picker API (`navigator.contacts`).
- **Gateway Komunikasi**: WhatsApp API resmi (`wa.me`).

---

## Struktur File Proyek

Proyek ini dibuat seringkas mungkin untuk performa maksimal.
- `index.html` — Berisi seluruh antarmuka (UI), penataan gaya (Tailwind), integrasi SweetAlert2, deteksi dukungan perangkat, dan logika JavaScript pengirim pesan (*Single Page Application*).

---

## Konfigurasi dan Instalasi

Karena ini adalah aplikasi web statis murni tanpa *database*, Anda dapat langsung menggunakannya di perangkat apapun tanpa instalasi *server*.

1. **Klon Repositori**
   ```bash
   git clone [https://github.com/homeprint-developer/blasting.me.git](https://github.com/homeprint-developer/blasting.me.git)