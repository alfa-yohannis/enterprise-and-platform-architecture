# Alur Bab Buku

**Mata kuliah:** IT30713 -- Enterprise & Platform Architecture

Dokumen ini adalah templat generik untuk menulis 14 bab buku ajar. Pola
dasarnya adalah **1 sesi kuliah = 1 bab**. Pembaca utama adalah mahasiswa
magister Indonesia berlatar belakang non-IT. Luaran akhir mata kuliah adalah
**makalah publikasi individu**, sehingga setiap bab harus berkontribusi pada
penyusunan makalah tersebut.

## Prinsip Utama

1. Mulai dari masalah organisasi, bukan teknologi.
2. Gunakan bahasa manajerial; jelaskan jargon dengan analogi.
3. Jaga konteks Indonesia secara konsisten: regulasi, organisasi, kapasitas,
   anggaran, dan budaya.
4. Setiap bab menghasilkan artefak atau narasi yang masuk ke bagian makalah.
5. Kerja bersifat individual, bukan kelompok.
6. Setiap rekomendasi disertai alasan, dampak, risiko, prioritas, dan
   implikasi.
7. Etika akademik harus eksplisit: sitasi benar, kemiripan naskah maksimal
   25%, anonimisasi data sensitif, dan keterangan penggunaan AI bila digunakan.

## Estimasi Panjang

Setiap bab ditargetkan sekitar **18-25 halaman A4** atau **4.000-6.000 kata**,
termasuk gambar, tabel, latihan, dan referensi.

Komposisi indikatif:

| Komponen | Porsi |
|---|---:|
| Konsep dan kerangka | 35% |
| Konteks Indonesia dan studi kasus | 25% |
| Langkah analisis dan artefak | 20% |
| Integrasi makalah dan latihan | 15% |
| Ringkasan dan bacaan lanjutan | 5% |

## Struktur Bab

Setiap bab mencakup 14 bagian berikut:

1. Kepala Bab
2. Tujuan Pembelajaran
3. Ringkasan Bab
4. Skenario Pembuka dan Pertanyaan Pemandu
5. Konsep Inti dan Glosarium Mini
6. Kerangka Berpikir
7. Konteks Indonesia
8. Studi Kasus Utama
9. Langkah Analisis dan Artefak Pendukung
10. Integrasi ke Makalah Publikasi
11. Diskusi Kritis, Trade-off, dan Perangkap Umum
12. Latihan Terapan Individual
13. Ringkasan, Refleksi, dan Jembatan
14. Bacaan Lanjutan dan Lampiran

## Detail Tiap Bagian

### 1. Kepala Bab

**Fungsi:** memberi identitas bab dan menunjukkan keterhubungan dengan mata
kuliah.

Isi yang perlu ada:

- Nomor dan judul bab. Judul mengandung sinyal manfaat manajerial, bukan hanya
  istilah teknis.
- Subjudul strategis.
- Sesi kuliah terkait.
- CLO yang didukung.
- Prasyarat dari bab sebelumnya.
- Estimasi waktu baca dan waktu latihan.
- Keluaran bab: artefak dan bagian makalah yang diperkuat.

Template judul:

```text
Bab [x] - [Topik]: [Fokus Strategis/Manajerial]
```

Contoh:

```text
Bab 9 - API Strategy: API sebagai Produk Digital dan Pengungkit Ekosistem
```

### 2. Tujuan Pembelajaran

**Fungsi:** menjelaskan kemampuan yang diharapkan setelah pembaca menyelesaikan
bab. Letakkan tepat setelah Kepala Bab.

Format:

- 3-5 tujuan pembelajaran.
- Gunakan kata kerja Bloom yang terukur.
- Pemetaan ke CLO mata kuliah harus eksplisit.

Template:

```text
Setelah membaca bab ini, pembaca mampu:
1. Menjelaskan [konsep utama] dalam konteks transformasi digital.
2. Menganalisis [objek/kasus] menggunakan [kerangka].
3. Menerapkan [langkah analisis] pada organisasi studi kasus.
4. Menyusun [artefak] untuk mendukung digital blueprint.
5. Menghubungkan [artefak] dengan argumen makalah publikasi.
```

Contoh pemetaan CLO:

```text
Tujuan 1-2 mendukung CLO 3; Tujuan 3-5 mendukung CLO 4 dan CLO 7.
```

### 3. Ringkasan Bab

**Fungsi:** memberi gambaran 150-250 kata tentang masalah, konsep, contoh,
artefak, dan kontribusi bab terhadap makalah.

Template:

```text
Bab ini membahas [topik] sebagai bagian dari Enterprise Architecture dan
transformasi digital. Pembahasan dimulai dari [masalah organisasi],
memperkenalkan [konsep inti] sebagai kerangka analisis, dan melalui contoh
dalam konteks Indonesia mengarahkan pembaca menyusun [artefak] yang memperkuat
bagian [bagian makalah].
```

### 4. Skenario Pembuka dan Pertanyaan Pemandu

**Fungsi:** membuka bab dengan masalah nyata dan memandu pembaca.

Skenario pembuka sepanjang 1/2 sampai 1 halaman memuat:

- Jenis organisasi: kampus, BPR, rumah sakit, pemerintah daerah, logistik UMKM,
  agribisnis, BUMN, dan sebagainya.
- Kondisi saat ini.
- Masalah transformasi digital.
- Dilema manajerial.
- Tidak harus ditutup dengan solusi.

Pertanyaan pemandu terdiri dari 3-5 pertanyaan, misalnya:

- Mengapa topik ini penting bagi organisasi?
- Keputusan apa yang harus diambil manajemen?
- Bukti atau data apa yang dibutuhkan?
- Artefak apa yang membantu analisis?
- Bagaimana hasil analisis menjadi argumen akademik?

Sertakan paragraf pendek tentang mengapa topik ini penting bagi pembaca non-IT:
detail teknis dapat dibantu spesialis, tetapi arah, prioritas, tata kelola,
dan trade-off tetap harus dipahami pengambil keputusan.

### 5. Konsep Inti dan Glosarium Mini

**Fungsi:** menjelaskan teori dan istilah utama dengan bahasa yang ramah untuk
pembaca non-IT.

Aturan:

- Maksimal 3-5 konsep utama.
- Mulai dari definisi manajerial sebelum definisi teknis.
- Gunakan analogi organisasi.
- Berikan contoh konkret setelah konsep abstrak.

Untuk setiap konsep, jelaskan:

- Definisi singkat.
- Mengapa konsep itu penting.
- Analogi manajerial.
- Contoh penerapan.
- Hubungan dengan Enterprise Architecture dan makalah.

Glosarium mini berisi 3-7 istilah, masing-masing 1-2 kalimat.

### 6. Kerangka Berpikir

**Fungsi:** memberi struktur analisis yang dapat diikuti pembaca.

Template umum:

```text
Masalah organisasi -> konsep inti -> artefak analisis ->
keputusan arsitektur -> trade-off -> implikasi makalah
```

Kerangka yang dapat digunakan sesuai bab:

- **TOGAF-lite:** vision, baseline, target, gap, roadmap.
- **BDAT:** Business, Data, Application, Technology.
- **API Strategy:** user, value proposition, lifecycle, governance, risk.
- **Platform Strategy:** actor, value exchange, network effect, monetization,
  governance.
- **Academic Writing:** problem, literature, method, analysis, discussion,
  conclusion.

Sajikan rujukan utama, versi ringan untuk pembaca non-IT, diagram sederhana,
serta kapan kerangka cocok dan tidak cocok.

### 7. Konteks Indonesia

**Fungsi:** menempatkan konsep ke realitas implementasi lokal.

Komponen:

- Regulasi atau standar relevan: UU PDP, UU ITE, PP 71/2019, Permenkominfo
  PSE, OJK, BSSN, SNAP BI, Satu Data Indonesia.
- Praktik industri: Gojek, Tokopedia, BCA Open API, BRIAPI, Dana, Halodoc,
  Ruangguru, Telkom Indonesia, Kementerian PANRB, koperasi/BPR, BUMN.
- Tantangan lokal: kapasitas SDM, anggaran, kematangan vendor, infrastruktur
  tidak merata, regulasi sektor, budaya organisasi, integrasi sistem lama.
- Implikasi terhadap keputusan arsitektur.

### 8. Studi Kasus Utama

**Fungsi:** menunjukkan penerapan konsep pada satu organisasi.

Struktur:

1. Profil singkat: visi, model bisnis, tantangan, pemangku kepentingan.
2. Kondisi saat ini.
3. Arah target.
4. Analisis menggunakan kerangka bab.
5. Diagram atau tabel hasil.
6. Trade-off yang muncul.
7. Pelajaran untuk pembaca.

Studi kasus boleh nyata, anonim, atau hipotetis-realistis. Jangan menampilkan
data internal sensitif tanpa izin.

### 9. Langkah Analisis dan Artefak Pendukung

**Fungsi:** mengubah konsep menjadi proses kerja dan keluaran visual.

Langkah analisis umum:

1. Tentukan ruang lingkup.
2. Identifikasi pemangku kepentingan dan concern.
3. Kumpulkan data atau bukti.
4. Petakan kondisi saat ini.
5. Rumuskan target atau rekomendasi.
6. Identifikasi gap, risiko, dan trade-off.
7. Susun artefak.
8. Tulis narasi akademik untuk makalah.

Untuk setiap langkah, jelaskan tujuan, input, aktivitas, keluaran, dan
kesalahan umum.

Artefak yang dapat digunakan sesuai bab:

- Architecture vision.
- Stakeholder map.
- Capability map.
- Value stream.
- Baseline architecture.
- Target BDAT.
- Conceptual data map.
- Application portfolio.
- Technology reference architecture.
- API portfolio, contract, atau governance checklist.
- Platform ecosystem map.
- Platform business model canvas.
- Platform governance charter.
- Gap analysis.
- Roadmap 12-24 bulan.

Kriteria artefak yang baik:

- Relevan dengan research question.
- Mudah dipahami audiens non-IT.
- Menunjukkan sebab-akibat, prioritas, atau keputusan.
- Konsisten dengan narasi makalah.
- Sumber data atau asumsi jelas.
- Tidak hanya dekoratif.

### 10. Integrasi ke Makalah Publikasi

**Fungsi:** menjelaskan bagaimana isi bab masuk ke makalah.

Bagian makalah yang mungkin diperkuat:

- Introduction.
- Literature Review.
- Method.
- Analysis/Results.
- Discussion.
- Conclusion.

Struktur klaim akademik:

```text
Klaim -> bukti -> analisis -> implikasi
```

Template integrasi:

```text
Materi bab ini memperkuat bagian [section]. Artefak [nama] ditempatkan sebagai
[gambar/tabel/lampiran] dan dijelaskan sebagai bukti bahwa [argumen utama].
```

Berikan satu contoh paragraf akademik konkret per bab.

### 11. Diskusi Kritis, Trade-off, dan Perangkap Umum

**Fungsi:** melatih pembaca menghasilkan argumen, bukan sekadar deskripsi.

Pertanyaan diskusi yang dapat dipilih:

- Apa manfaat utama?
- Apa risiko atau efek samping?
- Asumsi apa yang perlu diuji?
- Apa keterbatasan analisis?
- Trade-off apa yang muncul?
- Apa implikasinya bagi manajemen, SDM, regulasi, anggaran, dan budaya?
- Bagaimana konteks Indonesia memengaruhi kelayakan?

Format trade-off:

| Keputusan | Alternatif | Manfaat | Risiko | Prioritas | Alasan Rekomendasi |
|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... |

Perangkap umum:

1. Memulai dari teknologi, bukan masalah organisasi.
2. Diagram terlalu teknis untuk pembaca non-IT.
3. Artefak tidak terhubung dengan research question.
4. Mengabaikan regulasi dan kapasitas organisasi.
5. Roadmap tanpa prioritas dan dependensi.
6. Rekomendasi tanpa bukti.
7. Literature review hanya merangkum, tidak mensintesis.

### 12. Latihan Terapan Individual

**Fungsi:** menghasilkan keluaran yang dapat langsung masuk ke makalah.

Struktur:

- Latihan pemanasan: 15-30 menit, 1-2 latihan.
- Latihan inti: artefak dan 2-4 paragraf akademik yang menjelaskan konteks
  masalah, hasil analisis, rekomendasi, implikasi, dan hubungan ke RQ makalah.
- Pertanyaan refleksi kritis: 3-5 pertanyaan.
- Tantangan lanjutan opsional.

Keluaran latihan:

- Artefak pendukung.
- Narasi akademik.
- Daftar asumsi.
- Daftar data yang masih perlu dilengkapi.
- Catatan revisi untuk makalah.

Rubrik mini:

- Relevansi masalah.
- Ketepatan konsep.
- Kejelasan artefak.
- Kekuatan argumen.
- Kelayakan implementasi.
- Keterhubungan ke makalah.

### 13. Ringkasan, Refleksi, dan Jembatan

**Fungsi:** menutup bab dan menjembatani ke bab berikutnya.

Komponen:

- Poin kunci: 5-8 bullet.
- Jawaban ringkas atas pertanyaan pemandu pada Bagian 4.
- Pertanyaan uji mandiri:
  - 5-8 pertanyaan konseptual.
  - 2-3 pertanyaan aplikatif.
  - 1-2 pertanyaan reflektif untuk makalah pembaca sendiri.
- Paragraf jembatan: bagaimana bab berikutnya menggunakan hasil bab ini.

### 14. Bacaan Lanjutan dan Lampiran

#### Bacaan Lanjutan

Sertakan:

- Referensi inti yang disitir, dengan gaya APA atau IEEE yang konsisten.
- Bacaan untuk memperdalam: 1-2 buku, 2-3 jurnal/konferensi, 1-2 white paper.
- Sumber Indonesia: jurnal SINTA, prosiding nasional, laporan BSSN/OJK/PANRB/BI,
  atau studi kasus lokal.

#### Lampiran

Lampiran bersifat opsional. Jika diperlukan, gunakan untuk:

- Template worksheet.
- Contoh artefak lengkap yang sudah dianonimkan.
- Checklist dan rubrik mini.
- Glosarium tambahan.
- Contoh paragraf makalah.

## Perlakuan Khusus untuk Bab Tertentu

| Jenis Bab | Penekanan |
|---|---|
| Bab konseptual (1-3) | Perbesar konsep inti, kerangka, dan diskusi kritis. |
| Bab arsitektur BDAT (4-7) | Perbesar langkah analisis, artefak, studi kasus, dan integrasi ke makalah. |
| Bab API dan Platform (9-12) | Perbesar konteks Indonesia, ekosistem, tata kelola, monetisasi, dan regulasi. |
| Bab 8 - Klinik Proposal Makalah | Wajib memuat checklist proposal makalah, rubrik formatif, panduan tinjauan sejawat, dan contoh umpan balik. |
| Bab 13 - Lokakarya Pra-Pengajuan | Wajib memuat checklist pengajuan, checklist gambar, checklist referensi, checklist kemiripan naskah, panduan surat pengantar, dan rencana revisi final. |

## Alokasi Halaman Per Bab

Alokasi berikut bersifat indikatif untuk bab sekitar 20 halaman.

| Bagian | Estimasi Halaman |
|---|---:|
| Kepala bab | 1 |
| Tujuan pembelajaran | 1/2 |
| Ringkasan bab | 1/2 |
| Skenario dan pertanyaan pemandu | 2 |
| Konsep inti dan glosarium | 4 |
| Kerangka berpikir | 2 |
| Konteks Indonesia | 2 |
| Studi kasus utama | 3 |
| Langkah analisis dan artefak | 3 |
| Integrasi ke makalah | 1-2 |
| Diskusi kritis dan perangkap | 1-2 |
| Latihan individual | 2 |
| Ringkasan, refleksi, dan jembatan | 1 |
| Bacaan lanjutan dan lampiran | 1 |

## Checklist Final Bab

Sebelum bab dianggap selesai, pastikan:

1. Judul, tujuan pembelajaran, dan pemetaan CLO jelas.
2. Skenario pembuka relevan dengan konteks Indonesia.
3. Konsep dijelaskan untuk pembaca non-IT dengan analogi manajerial, bukan
   jargon.
4. Kerangka disajikan dalam versi praktis.
5. Ada regulasi, standar, atau praktik Indonesia yang relevan.
6. Studi kasus menunjukkan penerapan konsep, bukan hanya cerita.
7. Artefak memiliki fungsi jelas dalam analisis.
8. Ada panduan eksplisit untuk mengubah artefak menjadi argumen makalah.
9. Trade-off dan risiko dibahas.
10. Latihan individual menghasilkan keluaran nyata yang dapat masuk ke makalah.
11. Ada uji mandiri konseptual, aplikatif, dan reflektif.
12. Referensi konsisten dan layak untuk literature review.
13. Tidak ada tugas kelompok.
14. Artefak diposisikan sebagai pendukung, bukan luaran utama. Luaran utama
    tetap makalah publikasi individu.
