# Rancangan Slide Presentasi Skripsi

## Strategi Presentasi

Presentasi tidak sebaiknya mengikuti urutan "Bab 1, Bab 2, Bab 3, dan seterusnya". Bangun satu cerita utama:

> Integrasi DFIG-WT memperlemah redaman dan margin pembebanan, sedangkan PMSG-WT cenderung mempertahankan kestabilan karena *full converter decoupling*—tetapi hasilnya tetap dipengaruhi lokasi integrasi.

Targetkan presentasi selesai dalam 18 menit agar tersedia cadangan dua menit dari batas maksimal 20 menit.

## Slide Utama — 13 Slide

### 1. Judul — 30 detik

Isi:

- Judul penelitian
- Nama dan NIM
- Program studi
- Dosen pembimbing

Tidak perlu membuat slide agenda khusus untuk presentasi 20 menit.

### 2. Latar Belakang dan Urgensi — 1 menit 15 detik

Tampilkan hanya tiga gagasan:

- Kapasitas PLTB Indonesia akan meningkat.
- PLTB menggantikan sebagian generator sinkron.
- DFIG dan PMSG mempunyai antarmuka serta dinamika yang berbeda sehingga dampaknya terhadap *small signal stability* (SSS) belum tentu sama.

Visual yang disarankan:

```text
Integrasi PLTB meningkat
        ↓
Generator sinkron tergantikan
        ↓
Inersia dan dinamika sistem berubah
        ↓
Damping dan stabilitas sinyal kecil berubah
```

Boleh tambahkan satu atau dua angka dari Bab 1, misalnya potensi angin 154,6 GW dan target penambahan PLTB 5 GW hingga 2030. Jangan memenuhi slide dengan statistik energi.

### 3. Celah Penelitian dan Tujuan — 1 menit

Celah penelitian:

> Belum banyak perbandingan DFIG-WT dan PMSG-WT pada sistem acuan yang sama dengan variasi lokasi integrasi, kondisi pembebanan, serta evaluasi *eigenvalue*, *damping ratio* (DR), dan *participation factor* (PRF) secara bersamaan.

Ringkas tujuan menjadi:

1. Menilai dampak DFIG-WT.
2. Menilai dampak PMSG-WT.
3. Membandingkan teknologi, lokasi integrasi, dan margin pembebanannya.

### 4. Mengapa DFIG dan PMSG Dapat Memberikan Hasil Berbeda? — 1 menit 15 detik

Gunakan perbandingan dua kolom:

| DFIG-WT | PMSG-WT |
|---|---|
| Konverter parsial 25–30% | Konverter berdaya penuh |
| Stator langsung terhubung ke jaringan | Generator dipisahkan dari jaringan |
| Dinamika rotor dan poros dapat masuk ke mode sistem | Dinamika mekanik relatif terisolasi |
| Model kontrol lebih kompleks | Antarmuka jaringan didominasi konverter |

Visual dapat mengambil model sederhana DFIG dan FRC dari Bab 3. Jangan tampilkan seluruh diagram kontrol pada slide utama.

Pesan lisan:

> Perbedaan struktur ini menjadi dugaan awal mengapa DFIG dan PMSG menghasilkan karakteristik modal yang berbeda.

### 5. Sistem Uji dan Konfigurasi Integrasi — 1 menit 30 detik

Gunakan `contents/chapter-3/NineBusModel.png`.

Beri penanda warna:

- G1: *slack bus*, tidak diganti.
- G2: 163 MW, titik penggantian melalui Bus 7.
- G3: 85 MW, titik penggantian melalui Bus 9.
- Beban A: Bus 5.
- Beban B: Bus 6.

Tambahkan dua konfigurasi kecil:

```text
Konfigurasi 1: G3 → PLTB 85 MW
Konfigurasi 2: G2 → PLTB 163 MW
```

Tidak perlu menampilkan tabel lengkap saluran, transformator, dan parameter generator.

### 6. Desain Skenario Penelitian — 1 menit 15 detik

Jangan menyalin tabel panjang Bab 3. Buat matriks tiga dimensi:

| Kelompok | Teknologi | Posisi/kondisi |
|---|---|---|
| Acuan | Tanpa PLTB | Nominal, Beban A, Beban B |
| Integrasi nominal | DFIG/PMSG | G3–Bus 9 atau G2–Bus 7 |
| Uji pembebanan | DFIG/PMSG | Peningkatan Beban A atau B |

Di bagian bawah:

> Variabel yang dibandingkan: *eigenvalue*, *damping ratio*, frekuensi, *participation factor*, dan batas pembebanan.

### 7. Metode Analisis — 1 menit 15 detik

Buat diagram sederhana:

```text
Model PowerFactory
        ↓
Load flow dan titik operasi
        ↓
Linearisasi → matriks A
        ↓
Eigenvalue λ = σ ± jω
        ↓
DR dan frekuensi
        ↓
Participation factor
        ↓
Identifikasi komponen dominan
```

Tampilkan hanya dua kriteria:

- \(\sigma<0\): stabil.
- \(\zeta\geq5\%\): redaman memadai.

Persamaan lengkap dipindahkan ke appendix.

### 8. Hasil Utama 1: Dampak pada Kondisi Nominal — 2 menit

Ini salah satu slide terpenting. Gunakan grafik batang:

| Konfigurasi | DR minimum |
|---|---:|
| Tanpa PLTB | 7,22% |
| DFIG mengganti G3 | 4,04% |
| DFIG mengganti G2 | 4,05% |
| PMSG mengganti G3 | 7,25% |
| PMSG mengganti G2 | 8,73% |

Tambahkan garis horizontal pada 5%.

Pesan utama:

- DFIG menurunkan redaman hingga sekitar 4,04%.
- Lokasi DFIG hampir tidak mengubah hasil.
- PMSG mempertahankan atau meningkatkan redaman.
- Seluruh mode stabil dominan merupakan *local area mode*, sekitar 1,38–1,86 Hz.

Tidak perlu menampilkan lima tabel *eigenvalue* satu per satu.

### 9. Hasil Utama 2: Siapa yang Mendominasi Mode? — 1 menit 45 detik

Gunakan dua kolom.

**DFIG-WT**

- Mode nominal didominasi dinamika poros \(\Delta\delta_{12}\).
- Pada pembebanan kritis, \(\varphi_m\), poros \(x_H\), dan kontrol kecepatan menjadi dominan.
- Artinya, PLTB DFIG ikut terlibat langsung dalam mode lemah sistem.

**PMSG-WT**

- Mode dominan tetap terutama terkait rotor generator sinkron yang tersisa.
- Variabel mekanik PMSG tidak dominan.
- Hal tersebut mendukung mekanisme *full converter decoupling*.

Gunakan satu grafik PRF DFIG dan satu grafik PRF PMSG, bukan seluruh grafik.

### 10. Hasil Utama 3: Margin Kestabilan Beban — 2 menit

Berdasarkan pembahasan rinci Bab 4, grafik yang disarankan:

| Beban | Tanpa PLTB | DFIG-WT | PMSG-WT |
|---|---:|---:|---:|
| Beban A | 247% | 83% | Stabil pada 237% |
| Beban B | 373% | 123% | Tidak stabil pada 237% |

Untuk PMSG pada Beban A, jangan menyatakan 237% sebagai batas. Tuliskan:

> Masih stabil pada titik pengujian +237%; batas sebenarnya belum ditemukan.

Pesan utama:

- DFIG mempersempit margin secara drastis.
- PMSG lebih kuat daripada DFIG.
- Hasil PMSG sangat dipengaruhi posisi relatif pembangkit dan beban.

### 11. Mekanisme Ketidakstabilan — 1 menit 45 detik

Bandingkan dua karakteristik berikut.

**DFIG-WT**

- Muncul *eigenvalue* riil positif.
- DR = −100%.
- Ketidakstabilan bersifat aperiodik: respons menyimpang tanpa berosilasi.
- Didominasi \(\varphi_m\) dan dinamika poros DFIG.

**PMSG-WT**

- Pada Beban B +237%: DR sekitar −0,63%.
- Ketidakstabilannya sangat dekat dengan batas marginal.
- Mode didominasi generator sinkron G1, bukan dinamika mekanik PMSG.

Gunakan satu plot *eigenvalue* DFIG kritis dan satu plot PMSG kritis.

### 12. Sintesis Perbandingan — 1 menit 30 detik

| Aspek | DFIG-WT | PMSG-WT |
|---|---|---|
| DR nominal | Turun menjadi ±4,04% | 7,25–8,73% |
| Pengaruh lokasi | Kecil pada kondisi nominal | Cukup signifikan |
| Margin pembebanan | Menurun tajam | Lebih baik, tetapi bergantung lokasi |
| Komponen dominan | Poros, rotor, dan kontrol DFIG | Generator sinkron yang tersisa |
| Mekanisme | Masih terkopel dengan jaringan | Terpisah melalui konverter penuh |

Akhiri slide dengan:

> Teknologi konverter dan lokasi integrasi sama pentingnya dengan kapasitas PLTB.

### 13. Kesimpulan dan Rekomendasi — 1 menit

Kesimpulan:

1. DFIG-WT memperlemah DR dan mempersempit margin pembebanan.
2. PMSG-WT mempertahankan atau meningkatkan DR karena pemisahan dinamika generator dari jaringan.
3. PRF menunjukkan ketidakstabilan DFIG berasal dari dinamika internal DFIG, sedangkan PMSG tetap didominasi generator sinkron.

Rekomendasi:

- Tambahkan *supplementary damping controller* pada DFIG.
- Kaji AVR/PSS pada generator sinkron.
- Uji variasi penetrasi, kecepatan angin, dan sistem tenaga yang lebih besar.

Tutup dengan satu kalimat:

> Integrasi PLTB tidak cukup dinilai berdasarkan kapasitas; teknologi dan lokasi integrasinya harus dipertimbangkan dalam perencanaan stabilitas.

## Slide Appendix/Hidden untuk Tanya Jawab

Tempatkan seluruh slide berikut setelah slide penutup dan sembunyikan dari alur presentasi normal.

### A1. Definisi dan Ruang Lingkup SSS

Isi:

- Gangguan kecil dan linearisasi sekitar titik operasi.
- Perbedaan SSS, stabilitas transien, dan stabilitas tegangan.
- Klasifikasi *local mode*, *inter-area mode*, dan *control mode*.

Berguna jika ditanya mengapa penelitian hanya membahas SSS.

### A2. Persamaan Modal

Tampilkan:

\[
\Delta\dot{x}=A\Delta x
\]

\[
\lambda=\sigma\pm j\omega_d
\]

\[
\zeta=\frac{-\sigma}{\sqrt{\sigma^2+\omega_d^2}},
\qquad
f_d=\frac{\omega_d}{2\pi}
\]

Sertakan ilustrasi bidang kompleks kiri dan kanan.

### A3. Participation Factor

Isi:

\[
p_{ki}=\phi_{ki}\psi_{ik}
\]

Jelaskan perbedaan:

- *Eigenvalue*: mode apa yang kritis?
- DR: seberapa baik mode diredam?
- PRF: komponen apa yang menyebabkan mode tersebut?

### A4. Persamaan Ayunan dan Verifikasi Analitis

Tampilkan:

- Persamaan ayunan.
- Matriks elektromekanik \(2\times2\).
- Contoh verifikasi Skenario 1.1.
- Hasil PowerFactory dibandingkan hasil perhitungan.

Ini berguna jika penguji mempertanyakan apakah hasil hanya merupakan keluaran perangkat lunak.

### A5. Parameter Lengkap IEEE 9-Bus

Masukkan:

- Daya dan inersia G1, G2, dan G3.
- Data Beban A, B, dan C.
- Diagram posisi Bus 7 dan Bus 9.
- Alasan G1 tidak diganti karena merupakan *slack bus*.

### A6. Detail Model DFIG-WT

Gunakan `contents/chapter-3/DFIGControlModel.png` dan tampilkan:

- RSC, GSC, PLL, *pitch control*, PQ control, *speed controller*, dan poros dua massa.
- Variabel keadaan penting: \(\varphi_m\), \(\omega_r\), \(x_H\), dan \(\Delta\delta_{12}\).

### A7. Detail Model PMSG/FRC

Gunakan `contents/chapter-3/PMSGControlModel.png` dan tampilkan:

- PLL, PQ controller, dan *current controller*.
- Alasan model direpresentasikan sebagai *static generator* pada sisi jaringan.
- Konsep *full decoupling*.

### A8. Tabel Lengkap Skenario

Tampilkan seluruh Skenario 1.1 sampai 5.2. Slide ini berguna ketika penguji menanyakan konfigurasi spesifik.

### A9. Data Eigenvalue Lengkap

Sebaiknya dibagi menjadi tiga slide tersembunyi:

- A9a: sistem acuan.
- A9b: DFIG dan PMSG pada kondisi nominal.
- A9c: kondisi pembebanan kritis.

Tandai mode kritis dengan warna merah. Jangan menampilkan tabel mentah tanpa penanda.

### A10. Participation Factor Lengkap

Sediakan grafik PRF untuk:

- DFIG nominal.
- DFIG pada batas tidak stabil.
- PMSG nominal.
- PMSG pada kondisi pembebanan.

### A11. Penentuan Batas Pembebanan

Jelaskan:

- Beban dinaikkan secara bertahap.
- Pada setiap titik dilakukan *load flow* dan *modal analysis*.
- Batas ditentukan ketika bagian riil *eigenvalue* pertama berpindah ke kanan.
- Cantumkan titik terakhir stabil dan titik pertama tidak stabil.

### A12. Perbandingan dengan Penelitian Terdahulu

Ringkas tiga atau empat studi:

- Temuan DFIG dari Mehta atau Gautam.
- Temuan *full converter decoupling* dari Wu.
- Posisi kontribusi penelitian ini terhadap studi tersebut.

### A13. Asumsi dan Keterbatasan

Siapkan jawaban untuk:

- Model dan kontroler bawaan PowerFactory.
- Kecepatan angin konstan.
- Penggantian langsung, bukan penetrasi parsial.
- Tanpa AVR/PSS.
- Tanpa harmonik.
- Penggunaan sistem IEEE 9-bus.
- Belum divalidasi pada sistem tenaga praktis.

### A14. Jumlah Variabel Keadaan dan Orde Model

Tampilkan perbedaan kompleksitas model:

- Sistem konvensional.
- Sistem dengan PMSG.
- Sistem dengan DFIG.

Hubungkan peningkatan orde dengan tambahan PLL, kontrol arus, kontrol kecepatan, *pitch*, dan poros.

## Materi yang Tidak Perlu Masuk Slide Utama

- Spesifikasi laptop.
- Seluruh persamaan DFIG dan PMSG.
- Semua parameter transmisi dan transformator.
- Tabel *eigenvalue* setiap skenario.
- Tinjauan pustaka panjang.
- Perhitungan analitis langkah demi langkah.
- Semua grafik PRF.
- Diagram kontrol PowerFactory berukuran penuh.

Materi tersebut lebih cocok dijadikan amunisi pada slide appendix.

## Hal yang Wajib Diselaraskan Sebelum Membuat Slide

Naskah saat ini masih memiliki beberapa versi hasil:

- Bab 4 rinci menyatakan batas DFIG sebesar 83% dan 123%.
- Abstrak dan kesimpulan masih menyebut 63% dan 86%.
- Pemetaan Beban A/B pada Skenario 4 dan 5 belum konsisten.
- Ringkasan Bab 4 masih memuat nilai DR lama, sedangkan analisis terbaru menunjukkan DR −100% untuk mode riil positif DFIG.
- Tabel dan paragraf PRF Skenario 3.2 perlu disamakan.
- Batasan penelitian menyatakan tidak menggunakan domain waktu, tetapi metode dan Bab 4 menyebut *load event/time-domain simulation*.

Tentukan satu versi hasil yang benar dari PowerFactory terlebih dahulu. Slide harus mengikuti data tersebut, kemudian abstrak, Bab 3, Bab 4, dan kesimpulan perlu diselaraskan. Penguji biasanya cepat menangkap angka yang berubah antarbagian.
