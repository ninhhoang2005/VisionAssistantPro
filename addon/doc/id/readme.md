Dokumentasi Vision Assistant Pro

# Vision Assistant Pro

**Vision Assistant Pro** adalah asisten AI multi-modal canggih untuk NVDA. Add-on ini memanfaatkan model Gemini dari Google untuk menyediakan fitur pembacaan layar cerdas, penerjemahan, dikte suara, dan kemampuan analisis dokumen.

_Add-on ini dirilis untuk komunitas sebagai penghormatan terhadap Hari Disabilitas Internasional._

## 1. Pengaturan & Konfigurasi

Buka **Menu NVDA > Preferensi > Pengaturan > Vision Assistant Pro**.

- **API Key:** Wajib diisi. Dapatkan kunci gratis dari [Google AI Studio](https://aistudio.google.com/).
- **Model:** Pilih `gemini-2.5-flash-lite` (Tercepat) atau model Flash standar.
- **Bahasa:** Atur bahasa Sumber, Target, dan Respons AI.
- **Smart Swap:** Secara otomatis menukar bahasa jika teks sumber cocok dengan bahasa target.

## 2. Pintasan Global

Untuk memastikan kompatibilitas maksimal dengan tata letak laptop, semua pintasan menggunakan **NVDA + Control + Shift**.

| Pintasan            | Fungsi               | Deskripsi                                                                 |
|---------------------|----------------------|---------------------------------------------------------------------------|
| NVDA+Ctrl+Shift+T   | Penerjemah Cerdas    | Menerjemahkan teks di bawah kursor navigator. Memprioritaskan teks yang dipilih. |
| NVDA+Ctrl+Shift+Y   | Penerjemah Clipboard | Menerjemahkan isi papan klip (clipboard).                                 |
| NVDA+Ctrl+Shift+S   | Dikte Cerdas         | Mengubah ucapan menjadi teks. Tekan sekali untuk mulai, tekan lagi untuk berhenti dan mengetik. |
| NVDA+Ctrl+Shift+R   | Penyempurna Teks     | Meringkas, Memperbaiki Tata Bahasa, Menjelaskan, atau menjalankan **Prompt Kustom**. |
| NVDA+Ctrl+Shift+C   | Pemecah CAPTCHA      | Menangkap dan memecahkan CAPTCHA secara otomatis.                         |
| NVDA+Ctrl+Shift+V   | Penglihatan Objek    | Mendeskripsikan objek navigator dengan obrolan tindak lanjut.             |
| NVDA+Ctrl+Shift+O   | Penglihatan Layar Penuh | Menganalisis tata letak dan konten seluruh layar.                       |
| NVDA+Ctrl+Shift+D   | Analisis Dokumen     | Tanya jawab dengan file PDF/TXT/MD/PY.                                      |
| NVDA+Ctrl+Shift+F   | OCR File             | OCR langsung dari file gambar/PDF.                                        |
| NVDA+Ctrl+Shift+A   | Transkripsi Audio    | Mentranskripsikan file MP3/WAV/OGG.                                       |
| NVDA+Ctrl+Shift+L   | Terjemahan Terakhir  | Membaca ulang terjemahan terakhir tanpa menggunakan API.                  |
| NVDA+Ctrl+Shift+U   | Cek Pembaruan        | Memeriksa GitHub untuk versi terbaru.                                     |
| NVDA+Ctrl+Shift+I   | Laporan Status       | Mengumumkan status saat ini (misalnya, "Mengunggah...", atau "Sedang tidak digunakan").          |

## 3. Prompt Kustom & Variabel

Buat perintah di Pengaturan dengan format: `Nama:Teks Prompt` (pisahkan dengan `|` atau baris baru).

### Variabel yang Tersedia

| Variabel         | Deskripsi                                        | Tipe Masukan     |
|------------------|--------------------------------------------------|------------------|
| `[selection]`    | Teks yang sedang dipilih                         | Teks             |
| `[clipboard]`    | Konten clipboard                                 | Teks             |
| `[screen_obj]`   | Tangkapan layar objek navigator                  | Gambar           |
| `[screen_full]`  | Tangkapan layar penuh                            | Gambar           |
| `[file_ocr]`     | Pilih gambar/PDF/TIFF (default ke "Ekstrak teks")| Gambar, PDF, TIFF|
| `[file_read]`    | Pilih dokumen teks                               | TXT, Kode, PDF   |
| `[file_audio]`   | Pilih file audio                                 | MP3, WAV, OGG    |

### Contoh Prompt Kustom

- **OCR Cepat:** `OCR Saya:[file_ocr]`
- **Terjemahkan Gambar:** `Terjemahkan Gbr:Ekstrak teks dari gambar ini dan terjemahkan ke bahasa Indonesia. [file_ocr]`
- **Analisis Audio:** `Ringkas Audio:Dengarkan rekaman ini dan ringkas poin-poin utamanya. [file_audio]`
- **Debugger Kode:** `Debug:Temukan bug dalam kode ini dan jelaskan: [selection]`

**Catatan:** Koneksi internet aktif diperlukan untuk semua fitur AI. File TIFF multi-halaman diproses secara otomatis.

## Perubahan untuk 3.1.0
*   **Mode Output Langsung:** Menambahkan opsi untuk melewati dialog obrolan dan mendengar respons AI secara langsung melalui ucapan agar lebih cepat dan efisien.
*   **Integrasi Clipboard:** Menambahkan pengaturan baru untuk menyalin respons AI ke clipboard secara otomatis.

## Perubahan untuk 3.0
*   **Bahasa Baru:** Menambahkan terjemahan **Persia** dan **Vietnam**.
*   **Model AI yang Diperluas:** Mengatur ulang daftar pemilihan model dengan awalan yang jelas (`[Free]`, `[Pro]`, `[Auto]`) untuk membantu pengguna membedakan antara model gratis dan berbayar (rate-limited). Menambahkan dukungan untuk **Gemini 3.0 Pro** dan **Gemini 2.0 Flash Lite**.
*   **Stabilitas Dikte:** Meningkatkan stabilitas Dikte Cerdas secara signifikan. Menambahkan pemeriksaan keamanan untuk mengabaikan klip audio yang lebih pendek dari 1 detik, mencegah halusinasi AI dan error kosong.
*   **Penanganan File:** Memperbaiki masalah kegagalan saat mengunggah file dengan nama non-Inggris.
*   **Optimasi Prompt:** Meningkatkan logika Terjemahan dan hasil Penglihatan yang terstruktur.

## Perubahan untuk 2.9
*   **Menambahkan terjemahan Prancis dan Turki.**
*   **Tampilan Terformat:** Menambahkan tombol "Lihat Terformat" pada dialog chat untuk melihat percakapan dengan gaya yang tepat (Judul, Tebal, Kode) di jendela peramban standar.
*   **Pengaturan Markdown:** Menambahkan opsi baru "Bersihkan Markdown di Chat" di Pengaturan. Jika tidak dicentang, pengguna dapat melihat sintaks Markdown mentah (misalnya, `**`, `#`) di jendela chat.
*   **Manajemen Dialog:** Memperbaiki masalah di mana jendela "Penyempurna Teks" atau chat terbuka ganda atau gagal fokus.
*   **Peningkatan UX:** Menstandarkan judul dialog file menjadi "Open" dan menghapus pengumuman ucapan yang berlebihan (misalnya, "Opening menu...") agar lebih nyaman.

## Perubahan untuk 2.8
* Menambahkan terjemahan Italia.
* **Pelaporan Status:** Menambahkan perintah baru (NVDA+Control+Shift+I) untuk mengumumkan status add-on saat ini (misalnya, "Mengunggah...", "Menganalisis...").
* **Ekspor HTML:** Tombol "Simpan Konten" di dialog hasil sekarang menyimpan output sebagai file HTML yang diformat, mempertahankan gaya seperti judul dan teks tebal.
* **UI Pengaturan:** Memperbaiki tata letak panel Pengaturan dengan pengelompokan yang aksesibel.
* **Model Baru:** Menambahkan dukungan untuk gemini-flash-latest dan gemini-flash-lite-latest.
* **Bahasa:** Menambahkan bahasa Nepal ke daftar yang didukung.
* **Logika Menu Refine:** Memperbaiki bug kritis di mana perintah "Refine Text" gagal jika bahasa antarmuka NVDA bukan bahasa Inggris.
* **Dikte:** Meningkatkan deteksi keheningan untuk mencegah output teks yang salah saat tidak ada suara.
* **Pengaturan Pembaruan:** "Periksa pembaruan saat startup" sekarang dinonaktifkan secara default untuk mematuhi kebijakan Toko Add-on.
* Pembersihan Kode.

## Perubahan untuk 2.7
* Migrasi struktur proyek ke Template Add-on NV Access resmi untuk standar yang lebih baik.
* Menerapkan logika percobaan ulang otomatis untuk kesalahan HTTP 429 (Batas Tarif) untuk memastikan keandalan saat lalu lintas tinggi.
* Mengoptimalkan prompt terjemahan untuk akurasi yang lebih tinggi dan penanganan logika "Smart Swap" yang lebih baik.
* Memperbarui terjemahan Rusia.

## Perubahan untuk 2.6
* Menambahkan dukungan terjemahan Rusia (Terima kasih kepada nvda-ru).
* Memperbarui pesan kesalahan untuk memberikan umpan balik yang lebih deskriptif mengenai konektivitas.
* Mengubah bahasa target default menjadi Bahasa Inggris.

## Perubahan untuk 2.5
* Menambahkan Perintah OCR File Asli (NVDA+Control+Shift+F).
* Menambahkan tombol "Simpan Chat" ke dialog hasil.
* Menerapkan dukungan lokalisasi penuh (i18n).
* Migrasi umpan balik audio ke modul nada asli NVDA.
* Beralih ke Gemini File API untuk penanganan file PDF dan audio yang lebih baik.
* Memperbaiki crash saat menerjemahkan teks yang mengandung kurung kurawal.

## Perubahan untuk 2.1.1
* Memperbaiki masalah di mana variabel [file_ocr] tidak berfungsi dengan benar dalam Prompt Kustom.

## Perubahan untuk 2.1
* Menstandarkan semua pintasan untuk menggunakan NVDA+Control+Shift guna menghilangkan konflik dengan tata letak Laptop NVDA dan hotkey sistem.

## Perubahan untuk 2.0
* Menerapkan sistem Pembaruan Otomatis bawaan.
* Menambahkan Cache Terjemahan Cerdas untuk pengambilan instan teks yang sebelumnya diterjemahkan.
* Menambahkan Memori Percakapan untuk menyempurnakan hasil secara kontekstual dalam dialog chat.
* Menambahkan perintah Terjemahan Clipboard Khusus (NVDA+Control+Shift+Y).
* Mengoptimalkan prompt AI untuk secara ketat memaksakan output bahasa target.
* Memperbaiki crash yang disebabkan oleh karakter khusus dalam teks input.

## Perubahan untuk 1.5
* Menambahkan dukungan untuk lebih dari 20 bahasa baru.
* Menerapkan Dialog Refine Interaktif untuk pertanyaan tindak lanjut.
* Menambahkan fitur Dikte Cerdas Asli.
* Menambahkan kategori "Vision Assistant" ke dialog Input Gestures NVDA.
* Memperbaiki crash COMError di aplikasi tertentu seperti Firefox dan Word.
* Menambahkan mekanisme percobaan ulang otomatis untuk kesalahan server.

## Perubahan untuk 1.0
* Rilis awal.