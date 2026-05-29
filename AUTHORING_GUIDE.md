# Panduan Authoring Modul IT30713

Panduan ini dipakai oleh penulis atau agen yang melanjutkan modul
**IT30713 -- Enterprise & Platform Architecture**. Dokumen ini bukan silabus
baru. Sumber kebenaran utamanya tetap `syllabus.md` untuk arah mata kuliah dan
`alur.md` untuk alur generik setiap bab.

## 0. Wajib Dibaca Sebelum Menulis

Sebelum membuat atau mengubah bab apa pun, penulis **wajib membaca
`syllabus.md` dan `alur.md` terlebih dahulu**. Jangan hanya mengandalkan
ingatan, ringkasan lama, atau contoh bab sebelumnya.

Urutan kerja minimum:

1. Baca `syllabus.md` untuk memastikan topik sesi, CLO, metode pembelajaran,
   luaran makalah, rubrik, dan penilaian tetap konsisten.
2. Baca `alur.md` untuk memastikan bab mengikuti 14 fungsi utama: kepala bab,
   tujuan, ringkasan, skenario, konsep, kerangka, konteks Indonesia, studi
   kasus, langkah analisis, integrasi makalah, diskusi kritis, latihan,
   ringkasan/refleksi/jembatan, dan bacaan/lampiran.
3. Baru setelah itu gunakan `AUTHORING_GUIDE.md`, `module/pendahuluan.tex`,
   dan bab yang sudah ada sebagai panduan implementasi LaTeX.

Jika terjadi perbedaan antara dokumen, prioritaskan `syllabus.md` untuk arah
mata kuliah dan `alur.md` untuk struktur bab. `AUTHORING_GUIDE.md` berfungsi
sebagai panduan kerja teknis dan gaya penulisan.

Status saat panduan ini diperbarui:

- `module/pendahuluan.tex` sudah berisi identitas mata kuliah, CLO, luaran,
  penilaian, dan linimasa 14 sesi.
- `module/chapter01.tex` sudah menjadi rujukan gaya penulisan bab.
- Bab 2 sampai Bab 14 dapat ditambahkan bertahap sebagai `chapter02.tex`
  sampai `chapter14.tex`.
- Luaran utama mata kuliah adalah satu **makalah publikasi individu** dengan
  bobot **100%**. Artefak lain hanya berfungsi sebagai bahan pendukung makalah.

---

## 1. Prinsip Dasar

Setiap bab harus membantu mahasiswa membangun makalah ilmiah secara bertahap.
Karena pembaca utama adalah mahasiswa magister Indonesia berlatar belakang
non-IT, tulisan harus terasa seperti buku ajar manajerial: jelas, runtut,
berbasis kasus, dan tidak tenggelam dalam detail teknis.

Pegang prinsip berikut ketika menulis:

- Mulai dari masalah organisasi, bukan dari teknologi.
- Gunakan bahasa Indonesia yang natural; istilah teknis dijelaskan dengan
  analogi, contoh, atau keputusan manajerial yang konkret.
- Pastikan konteks Indonesia muncul nyata, misalnya regulasi, organisasi,
  kapasitas SDM, anggaran, budaya organisasi, dan realitas sektor publik atau
  swasta.
- Semua latihan bersifat individual. Tidak ada proyek kelompok.
- Setiap rekomendasi memuat alasan, dampak, risiko, prioritas, dan implikasi.
- Setiap artefak harus dapat dipakai dalam makalah, baik sebagai gambar, tabel,
  lampiran, maupun dasar argumen.
- Etika akademik harus eksplisit: sitasi benar, kemiripan naskah Turnitin
  maksimal 25%, data sensitif dianonimkan, dan penggunaan AI dicantumkan pada
  bagian `Acknowledgement` bila digunakan sebagai alat bantu.

---

## 2. Struktur Proyek

```text
it30713_enterprise_and_platform_architecture/
├── AUTHORING_GUIDE.md
├── syllabus.md
├── alur.md
├── figures/
│   ├── building.png
│   └── logo_universitas.png
└── module/
    ├── enterprise-platform-architecture.tex
    ├── titlepage.tex
    ├── pendahuluan.tex
    ├── chapter01.tex
    ├── hyphenation.tex
    ├── references.bib
    ├── fonts/
    └── enterprise-platform-architecture.pdf
```

Catatan kerja:

- `enterprise-platform-architecture.tex` adalah file utama. Ubah bagian
  `\include{...}` untuk menambahkan bab baru. Jangan mengubah preamble kecuali
  benar-benar diperlukan.
- `hyphenation.tex` berisi pola pemenggalan kata untuk mengurangi teks yang
  melewati margin kanan. File ini dipanggil dari preamble dengan
  `\input{hyphenation}`.
- `titlepage.tex` cukup diubah jika identitas, branding, atau desain sampul
  perlu disesuaikan.
- `pendahuluan.tex` harus konsisten dengan `syllabus.md`; jangan mengubah CLO atau
  bobot penilaian tanpa alasan akademik yang jelas.
- `chapter01.tex` adalah contoh gaya narasi, struktur latihan, visual TikZ,
  dan cara mengaitkan bab dengan makalah.
- `references.bib` menjadi tempat semua entri BibTeX. Jangan mengganti kunci
  yang sudah dipakai; tambahkan entri baru bila perlu.
- File hasil build seperti `.aux`, `.bbl`, `.blg`, `.fdb_latexmk`, `.fls`,
  `.log`, `.out`, `.toc`, `.xdv`, dan `.pdf` bukan naskah sumber.

---

## 3. Pemetaan Sesi ke Bab

Pola modul adalah **1 sesi = 1 bab**. Topik dan keluaran mengikuti
`pendahuluan.tex` dan `syllabus.md`.

| Bab | Topik | Keluaran untuk Makalah |
|---:|---|---|
| 1 | Orientasi EA, Platform & Penulisan Akademik | Pernyataan topik, kandidat target publikasi, motivasi awal |
| 2 | Strategi Bisnis & Rumusan Masalah | Rumusan masalah, pertanyaan penelitian (RQ), kontribusi awal |
| 3 | TOGAF-lite, ADM & Literature Review | Visi arsitektur, bibliografi awal minimal 10 rujukan |
| 4 | Business Architecture | Peta kapabilitas, value stream, tinjauan pustaka v1 |
| 5 | Data Architecture | Peta data konseptual, draf metode atau pendekatan |
| 6 | Application Architecture | Portofolio aplikasi, draf analisis |
| 7 | Technology Architecture & Kerangka Final | Arsitektur teknologi acuan, kerangka final makalah |
| 8 | Klinik Proposal Makalah | Proposal makalah v1 sebagai penanda kemajuan formatif |
| 9 | API Strategy: API sebagai Produk | Draf analisis bagian strategi API |
| 10 | API Design, Lifecycle & Governance | Spesifikasi API, daftar periksa tata kelola |
| 11 | Platform Economy & Model Bisnis | Draf diskusi bagian platform |
| 12 | Platform Governance, Etika & Regulasi | Piagam tata kelola, draf diskusi dan kesimpulan |
| 13 | Lokakarya Pra-Pengajuan | Draf final makalah, bahan presentasi, daftar periksa pengajuan |
| 14 | Presentasi Konferensi & Finalisasi | Naskah final makalah 100% |

Bab 8 dan Bab 13 adalah titik kendali penting. Bab 8 membantu mahasiswa
memastikan proposal makalah sudah layak dilanjutkan. Bab 13 membantu mahasiswa
menyiapkan naskah mendekati format target publikasi.

---

## 4. Alur Bab

Gunakan `alur.md` sebagai pola utama. Setiap bab perlu mencakup 14 fungsi di
bawah ini. Bentuk LaTeX boleh disesuaikan, tetapi fungsi akademiknya jangan
hilang. Misalnya, "Ringkasan Bab" dapat hadir sebagai bagian awal
`Pendahuluan`, dan "Glosarium Mini" dapat ditempatkan setelah konsep inti.

| # | Fungsi | Bentuk LaTeX yang Disarankan | Catatan |
|---:|---|---|---|
| 1 | Kepala bab | `\chapter{...}` dan `\label{ch:...}` | Judul memberi sinyal manfaat manajerial. |
| 2 | Tujuan pembelajaran | `\section*{Tujuan Pembelajaran}` | 3 sampai 5 tujuan dengan kata kerja terukur. |
| 3 | Ringkasan bab | `\section{Pendahuluan}` | Jelaskan posisi bab dalam perjalanan makalah. |
| 4 | Skenario pembuka & pertanyaan pemandu | `\section{Skenario Pembuka: ...}` dan `\subsection*{Pertanyaan Pemandu Bab Ini}` | Gunakan kasus Indonesia yang realistis. |
| 5 | Konsep inti & glosarium mini | `\section{Kerangka Konseptual: ...}` dan `\section{Glosarium Mini}` | Mulai dari definisi manajerial, baru teknis. |
| 6 | Kerangka berpikir | Bagian atau subbagian konseptual | Tampilkan alur analisis yang bisa diikuti pembaca. |
| 7 | Konteks Indonesia | `\section{Konteks Indonesia: ...}` | Sertakan regulasi, praktik organisasi, dan kendala lokal. |
| 8 | Studi kasus utama | `\section{Studi Kasus Mini: ...}` | Boleh menggunakan kasus anonim, nyata, atau hipotetis-realistis. |
| 9 | Langkah analisis & artefak pendukung | `\section{Langkah ...}` | Beri 6 sampai 8 langkah praktis dan artefak yang dihasilkan. |
| 10 | Integrasi ke makalah publikasi | `\section{Integrasi ke Makalah Publikasi}` | Jelaskan bagian makalah yang diperkuat bab ini. |
| 11 | Diskusi kritis, trade-off & perangkap umum | `\section{Diskusi Kritis dan Perangkap Umum}` | Bahas kompromi, risiko, dan kesalahan yang sering terjadi. |
| 12 | Latihan terapan individual | `\section{Latihan Terapan Individual}` | Latihan harus menghasilkan artefak atau narasi untuk makalah. |
| 13 | Ringkasan, refleksi & jembatan | `\section{Ringkasan Bab}` dan `\section{Jembatan ke Bab Berikutnya}` | Tutup bab dengan arah kerja berikutnya. |
| 14 | Bacaan lanjutan & lampiran | `\section{Bacaan Lanjutan}` | Gunakan `\cite{...}` ke entri di `references.bib`. |

Panjang indikatif satu bab adalah 18 sampai 25 halaman B5, termasuk gambar,
tabel, latihan, dan bacaan lanjutan. Bab pengantar, Bab 8, dan Bab 13 boleh
lebih panjang bila membutuhkan daftar periksa atau contoh format.

---

## 5. Peta Bab ke Bagian Makalah

Bagian "Integrasi ke Makalah Publikasi" pada setiap bab harus eksplisit. Jangan
hanya mengatakan bahwa materi "bermanfaat"; jelaskan bagian naskah yang
diperkuat dan bagaimana artefaknya berubah menjadi argumen.

| Bab | Bagian Makalah yang Diperkuat |
|---:|---|
| 1 | Pendahuluan, pemilihan topik, dan arah target publikasi |
| 2 | Pendahuluan: masalah, RQ, dan kontribusi |
| 3 | Tinjauan pustaka, kerangka konseptual, dan metode awal |
| 4 | Tinjauan pustaka dan analisis domain bisnis |
| 5 | Metode atau pendekatan analisis dan analisis domain data |
| 6 | Analisis domain aplikasi |
| 7 | Analisis domain teknologi dan kerangka akhir naskah |
| 8 | Konsolidasi proposal makalah v1 |
| 9 | Analisis strategi API |
| 10 | Analisis desain API, siklus hidup, dan tata kelola |
| 11 | Diskusi strategi platform dan model bisnis |
| 12 | Diskusi, kesimpulan, risiko, tata kelola, dan implikasi |
| 13 | Naskah lengkap, daftar periksa pengajuan, dan bahan presentasi |
| 14 | Naskah final setelah umpan balik presentasi |

---

## 6. Gaya Bahasa

Tulisan harus terasa seperti buku ajar Indonesia yang ditulis oleh pengajar
manusia: hangat, jelas, dan tegas. Hindari kalimat yang terasa seperti
terjemahan langsung.

Gunakan pilihan kata berikut secara konsisten:

| Hindari | Gunakan |
|---|---|
| venue | target publikasi |
| output | keluaran |
| deliverable | hasil kerja atau keluaran |
| milestone | penanda kemajuan |
| peer review | tinjauan sejawat |
| defense | pertanggungjawaban akademik atau presentasi konferensi |
| template | templat |
| submit / submission | diajukan / pengajuan |
| ready-to-submit / siap-submit | siap diajukan |
| disclosure AI | keterangan penggunaan AI |
| similarity | kemiripan naskah |
| feedback | umpan balik |

Istilah disiplin boleh tetap berbahasa Inggris jika lebih lazim atau menjadi
istilah teknis baku, misalnya `Enterprise Architecture`, `Business
Architecture`, `Application Architecture`, `API`, `platform`, `TOGAF-lite`,
`BDAT`, `Literature Review`, `network effects`, `OAuth2`, dan `REST`. Saat
istilah muncul pertama kali, beri penjelasan singkat dalam bahasa Indonesia.

Hindari:

- Paragraf yang hanya berisi definisi kamus.
- Daftar istilah panjang tanpa contoh.
- Klaim normatif seperti "harus digital" tanpa alasan dan risiko.
- Kalimat promosi yang tidak terhubung dengan analisis.
- Penjelasan teknis mendalam yang tidak membantu keputusan manajerial.

---

## 7. Konvensi LaTeX

### 7.1 Kepala Bab

Gunakan pola berikut sebagai awal file bab:

```latex
\chapter{<Judul Manajerial>: <Fokus Strategis>}
\label{ch:<slug>}

\section*{Tujuan Pembelajaran}
\begin{itemize}
  \item ...
  \item ...
  \item ...
\end{itemize}

\section{Pendahuluan}
...
```

Slug label dibuat singkat dan stabil, misalnya `ch:strategi-bisnis`,
`ch:data-arch`, atau `ch:api-governance`.

### 7.2 Daftar dan Penekanan

- Gunakan `itemize` untuk daftar tanpa urutan.
- Gunakan `enumerate` untuk langkah, latihan, atau pertanyaan bernomor.
- Hindari daftar bertingkat lebih dari dua level.
- Gunakan `\textbf{...}` untuk istilah kunci atau penekanan penting.
- Gunakan `\emph{...}` untuk istilah teknis atau nuansa.
- Tanda kutip dalam LaTeX ditulis sebagai ``...''.
- Karakter khusus perlu di-escape: `\&`, `\%`, `\$`.

### 7.3 Tabel

Gunakan `tabularx` untuk tabel yang menyesuaikan lebar halaman.

```latex
\begin{table}[htbp]
\centering
\scriptsize
\caption{...}
\label{tab:<slug>}
\begin{tabularx}{\textwidth}{@{}c X X@{}}
\hline
\textbf{Kolom 1} & \textbf{Kolom 2} & \textbf{Kolom 3} \\
\hline
... & ... & ... \\
\hline
\end{tabularx}
\end{table}
```

### 7.4 Sitasi

- Semua rujukan yang dikutip harus ada di `module/references.bib`.
- Gunakan `\cite{key}` di dalam teks.
- Kunci BibTeX sebaiknya pendek dan stabil, misalnya `ross2006enterprise`,
  `togaf2022standard`, atau `parker2016platform`.
- Jangan mengganti kunci BibTeX lama yang sudah dipakai di bab lain.

### 7.5 Pemenggalan Kata

Pola pemenggalan kata disimpan di `module/hyphenation.tex`, bukan ditulis
langsung di `enterprise-platform-architecture.tex`. Jika build LaTeX memberi
peringatan `Overfull \hbox` karena kata panjang melewati margin kanan, tambahkan
kata tersebut ke `hyphenation.tex` dengan tanda hubung pada titik pemenggalan
yang wajar.

Contoh:

```latex
\hyphenation{
  en-ter-prise
  ar-chi-tec-ture
  di-per-tang-gung-ja-wab-kan
}
```

Catatan penting:

- Jangan memasukkan tanda baca, angka, atau perintah LaTeX ke dalam
  `\hyphenation{...}`.
- Untuk kata yang muncul dalam `\texttt{...}`, URL, judul halaman berjalan,
  atau teks monospace, `\hyphenation{...}` sering tidak cukup. Kasus seperti
  itu biasanya perlu dirapikan dengan penulisan ulang, pemendekan judul, atau
  penanganan URL.
- Tambahkan hanya kata yang benar-benar muncul dalam peringatan build atau
  berpotensi panjang; jangan mengubah daftar ini menjadi kamus umum.

---

## 8. Konvensi Visual

TikZ diutamakan untuk gambar konseptual karena hasilnya konsisten dengan gaya
buku dan mudah dibangun bersama LaTeX. Gunakan gambar eksternal hanya bila
memang lebih tepat, misalnya tangkapan layar resmi, peta, atau ilustrasi yang
memiliki lisensi jelas.

Pola gambar TikZ:

```latex
\begin{figure}[htbp]
\centering
\scalebox{0.95}{
\begin{tikzpicture}[
  font=\small\bfseries,
  node distance=12mm
]
  ...
\end{tikzpicture}
}
\caption{<Keterangan gambar yang menjelaskan pesan visual>}
\label{fig:<slug>}
\end{figure}
```

Warna yang sudah tersedia di file utama:

- `praditagreen` untuk elemen strategis atau institusional.
- `orange!15` sampai `orange!25` untuk proses utama atau sorotan.
- `blue!10` sampai `blue!15` untuk teknologi, aplikasi, atau elemen sekunder.
- `gray!12` sampai `gray!18` untuk latar atau elemen netral.

Gambar yang baik untuk modul ini harus dapat dibaca oleh pembaca non-IT. Lebih
baik satu diagram sederhana dengan pesan jelas daripada diagram lengkap yang
terlalu padat.

---

## 9. Arahan Khusus Bab 8 dan Bab 13

### Bab 8: Klinik Proposal Makalah

Bab ini berfungsi sebagai titik pemeriksaan tengah semester. Isi yang perlu
muncul:

- anatomi proposal makalah v1;
- daftar periksa kelayakan masalah, RQ, kontribusi, metode, dan konteks kasus;
- cara menilai keterhubungan artefak BDAT dengan argumen makalah;
- panduan tinjauan sejawat yang tetap menghormati kerja individual;
- rubrik formatif dan catatan revisi.

Bab 8 tidak boleh berubah menjadi tugas kelompok. Tinjauan sejawat adalah
forum umpan balik, sedangkan naskah dan analisis tetap milik masing-masing
mahasiswa.

### Bab 13: Lokakarya Pra-Pengajuan

Bab ini menyiapkan mahasiswa menuju naskah siap diajukan. Isi yang perlu
muncul:

- daftar periksa struktur naskah dan templat target publikasi;
- kualitas gambar, tabel, abstrak, kata kunci, sitasi, dan daftar pustaka;
- batas kemiripan naskah dan cara membaca laporan Turnitin secara etis;
- surat pengantar bila dibutuhkan target publikasi;
- daftar revisi final sebelum Bab 14.

---

## 10. Cara Menambah Bab Baru

1. Buat file baru di `module/`, misalnya `chapter02.tex`.
2. Gunakan `chapter01.tex` sebagai rujukan gaya, bukan sebagai teks untuk
   disalin mentah.
3. Tambahkan atau aktifkan baris `\include{chapter02}` pada
   `module/enterprise-platform-architecture.tex`.
4. Tambahkan entri baru di `references.bib` bila ada rujukan baru.
5. Jalankan build dan periksa PDF.
6. Pastikan daftar isi, gambar, tabel, label, dan sitasi muncul benar.

Urutan `\include{...}` di file utama harus mengikuti urutan bab. Jangan
menambahkan bab baru di luar struktur 14 sesi kecuali memang diminta.

---

## 11. Cara Build

Jalankan dari direktori `module/`:

```bash
latexmk -xelatex -interaction=nonstopmode enterprise-platform-architecture.tex
```

Gunakan `xelatex`, bukan `pdflatex`, karena modul memakai `fontspec` dan font
TitilliumWeb lokal. `latexmk` akan menjalankan pass yang diperlukan untuk
daftar isi, label, dan bibliografi.

Setelah build:

- PDF utama berada di `module/enterprise-platform-architecture.pdf`.
- Jika ada peringatan `overfull` atau `underfull`, periksa apakah tabel,
  gambar, atau baris panjang perlu dirapikan.
- Jika `overfull` disebabkan kata panjang biasa, tambahkan pola pemenggalannya
  ke `module/hyphenation.tex`.
- Jika muncul `Citation ... undefined`, pastikan kunci BibTeX ada di
  `references.bib` dan build dijalankan ulang.
- Jika gambar tidak muncul, cek `\graphicspath{{../figures/}}` dan nama file.

---

## 12. Rujukan Isi

Gunakan urutan sumber berikut ketika menulis bab:

1. `syllabus.md` untuk identitas mata kuliah, CLO, penilaian, rubrik, dan topik 14
   sesi.
2. `alur.md` untuk fungsi 14 bagian setiap bab.
3. `module/pendahuluan.tex` untuk versi LaTeX yang sudah diselaraskan.
4. `module/chapter01.tex` untuk contoh gaya narasi, struktur, TikZ, dan
   integrasi ke makalah.
5. `module/references.bib` untuk rujukan yang sudah tersedia.

Jika membutuhkan rujukan baru, pilih sumber yang relevan dan dapat
dipertanggungjawabkan, lalu masukkan ke `references.bib`.

---

## 13. Verifikasi URL dan Keaslian Referensi

Setiap URL atau entri rujukan yang muncul dalam naskah maupun di
`references.bib` **harus diverifikasi** sebelum bab dinyatakan selesai.
Verifikasi mencakup dua hal: (a) sumbernya nyata dan tidak dihalusinasi, dan
(b) URL dapat diakses (tidak 404, NXDOMAIN, atau redirect ke halaman tidak
relevan).

### 13.1 Sumber rujukan yang nyata

Sebelum menambahkan entri ke `references.bib`:

- Pastikan buku, artikel jurnal, prosiding, regulasi, atau dokumen resmi
  benar-benar pernah diterbitkan. Tanda yang sering muncul pada referensi
  halusinasi: judul yang terdengar masuk akal namun tidak ditemukan di
  Google Books, Scopus, IEEE Xplore, atau Garuda; nomor ISBN/DOI yang tidak
  cocok dengan judul; tahun terbit yang tidak konsisten dengan edisi.
- Ketika memungkinkan, sertakan ISBN untuk buku, DOI untuk artikel
  jurnal/prosiding, dan nomor Lembaran Negara untuk regulasi Indonesia.
- Untuk regulasi Indonesia gunakan portal resmi
  `peraturan.bpk.go.id` (Badan Pemeriksa Keuangan) dengan format URL
  `https://peraturan.bpk.go.id/Details/<id>/<slug>` -- portal ini stabil
  dan dapat dirujuk lintas tahun.
- Jika sumber referensi tidak dapat diverifikasi, ganti dengan referensi
  paling relevan yang dapat diverifikasi. Lebih baik menyitasi 12 referensi
  yang valid daripada 15 referensi yang sebagian dihalusinasi.

### 13.2 Verifikasi URL dengan `curl`

Jalankan perintah berikut dari `module/` untuk memverifikasi seluruh URL
yang dipakai di naskah dan bibliografi:

```bash
UA="Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 \
(KHTML, like Gecko) Chrome/120.0 Safari/537.36"

# Ekstrak URL dari semua file .tex dan .bib
grep -hoE "https?://[^[:space:][:punct:]]+" \
  *.tex references.bib AUTHORING_GUIDE.md 2>/dev/null \
  | sed 's/[\.,;:)}]\+$//' | sort -u | while read url; do
    code=$(curl -k -sIL -A "$UA" -o /dev/null -w "%{http_code}" \
                --max-time 12 "$url" 2>/dev/null)
    echo "$code  $url"
done
```

Harapkan kode HTTP `200` (OK) atau `301`/`302` (redirect permanen).

Kode yang harus diaudit:

- `404` -- URL mati. Cari URL alternatif yang resmi.
- `403` -- sering muncul pada situs penerbit (MIT Press, HarperCollins) yang
  memblokir bot. Tambahkan User-Agent seperti pada perintah di atas; jika
  tetap 403, sumber masih sah selama dapat dibuka di peramban biasa.
- `000` -- DNS atau koneksi gagal. Jika berulang, kemungkinan domain telah
  pindah; cari domain baru.

### 13.3 Pelajaran dari migrasi domain Indonesia

Pada Oktober 2024 Kementerian dipecah dan beberapa portal akademik nasional
berpindah subdomain. Daftar yang sudah pernah diperbarui dalam modul ini:

| Domain Lama (sudah mati) | Domain Baru (aktif, terverifikasi) |
|---|---|
| `sinta.kemdikbud.go.id` | `sinta.kemdiktisaintek.go.id` |
| `garuda.kemdikbud.go.id` | `garuda.kemdiktisaintek.go.id` |

Bila menambahkan rujukan ke portal pemerintah Indonesia, periksa terlebih
dahulu apakah subdomain `kemdikbud` sudah perlu diganti menjadi
`kemdiktisaintek` atau subdomain kementerian baru lainnya.

### 13.4 Sumber yang dapat dipercaya untuk verifikasi cepat

| Tipe rujukan | Tempat verifikasi |
|---|---|
| Buku berbahasa Inggris | Google Books `https://books.google.com/books?isbn=<isbn>`; situs penerbit (MIT Press, O'Reilly, W. W. Norton) |
| Artikel jurnal | DOI di `https://doi.org/<doi>`; Scopus; IEEE Xplore; ACM Digital Library |
| Jurnal/konferensi Indonesia | SINTA `sinta.kemdiktisaintek.go.id`; Garuda `garuda.kemdiktisaintek.go.id` |
| Regulasi Indonesia | `peraturan.bpk.go.id`; situs kementerian terkait |
| Standar industri/nasional | Situs resmi Bank Indonesia (`bi.go.id`), OJK (`ojk.go.id`), BSSN (`bssn.go.id`), The Open Group (`opengroup.org`) |

### 13.5 Batas penggunaan URL non-resmi

Hindari menjadikan tautan utama:

- Blog pribadi tanpa atribusi yang jelas (kecuali blog penulis terkenal
  seperti Sam Newman atau Martin Fowler yang relevan dengan topik).
- Repositori Wikipedia sebagai sumber sitasi akademik. Wikipedia boleh
  dipakai sebagai pintu masuk, tetapi sitasi formal harus mengarah ke
  sumber primer.
- URL yang berisi token, parameter sesi, atau bersifat sementara.

### 13.6 Pencatatan hasil verifikasi

Setelah verifikasi selesai, catat ringkasan di pesan commit atau di catatan
revisi bab dengan format:

```
Verifikasi URL bab N: 12/12 200 OK, 0 dead.
```

Jika ada URL yang tetap tidak dapat diverifikasi (misalnya gateway lokal
yang menolak koneksi dari lingkungan kerja), catat sebagai pengecualian
dan minta penulis pendamping atau dosen untuk konfirmasi manual.

---

## 14. Checklist Sebelum Bab Dianggap Selesai

- [ ] Tujuan pembelajaran berada tepat setelah `\chapter`.
- [ ] Bab mencakup 14 fungsi dari `alur.md`, walaupun beberapa fungsi dapat
  digabung dalam satu bagian LaTeX.
- [ ] Skenario pembuka memakai konteks Indonesia yang realistis.
- [ ] Konsep utama dijelaskan dengan bahasa manajerial dan contoh konkret.
- [ ] Ada pembahasan eksplisit tentang konteks Indonesia.
- [ ] Ada studi kasus, tabel, atau gambar yang membantu analisis.
- [ ] Bagian "Integrasi ke Makalah Publikasi" menyebut bagian naskah yang
  diperkuat.
- [ ] Latihan terapan individual menghasilkan artefak atau narasi untuk
  makalah.
- [ ] Bacaan lanjutan memakai `\cite{...}` dan entri BibTeX tersedia.
- [ ] Setiap rujukan baru di `references.bib` punya ISBN atau DOI dan URL
  yang sudah diverifikasi (lihat Bagian 13).
- [ ] Setiap URL pada teks naskah (`\url{...}`, `\href{...}`, footnote)
  sudah diverifikasi dengan `curl` -- tidak ada 404, NXDOMAIN, atau
  redirect ke halaman tidak relevan.
- [ ] Tidak ada tugas kelompok atau bobot penilaian tambahan.
- [ ] Tidak ada istilah campuran yang terasa seperti terjemahan langsung.
- [ ] Kata panjang yang menyebabkan `Overfull \hbox` sudah ditambahkan ke
  `module/hyphenation.tex` bila dapat diselesaikan dengan pemenggalan kata.
- [ ] Build `latexmk -xelatex` selesai tanpa error fatal.
- [ ] PDF dicek sekilas untuk memastikan gambar, tabel, dan daftar isi tampil
  wajar.

---

## 15. Catatan Akhir untuk Penulis

Modul ini harus menjaga keseimbangan: cukup akademik untuk mengantar mahasiswa
menulis makalah publikasi, tetapi cukup praktis agar mahasiswa non-IT dapat
menggunakannya untuk membaca masalah organisasi. Jika ragu memilih isi, pilih
materi yang membantu mahasiswa menulis argumen yang lebih tajam, bukan materi
yang hanya menambah istilah.
