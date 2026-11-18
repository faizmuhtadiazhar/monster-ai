# 🐉 MONSTER.AI
### Pengembangan Makhluk Virtual Interaktif dengan Klasifikasi Elemen Berbasis CNN dan Evolusi Karakter Dinamis

---

## 👨‍💻 Identitas Pengembang

| Informasi | Keterangan |
|---|---|
| Nama | Faiz Muhtadi Azhar |
| NIM | 101022330224 |

---

## 1. Deskripsi Proyek

MONSTER.AI merupakan proyek pengembangan makhluk virtual interaktif yang mengintegrasikan teknologi Convolutional Neural Network (CNN) dengan sistem pengolahan berbasis FPGA.

Proyek ini dirancang untuk mengenali berbagai objek visual yang merepresentasikan elemen tertentu, seperti Fire, Water, Electric, Plant, dan Rock. Hasil klasifikasi citra digunakan sebagai dasar interaksi antara pengguna dan karakter virtual.

Berbeda dengan sistem klasifikasi citra pada umumnya yang hanya menghasilkan label prediksi, MONSTER.AI memanfaatkan hasil pengenalan tersebut untuk memengaruhi atribut, kemampuan, respons, dan perkembangan karakter virtual.

Pengguna dapat memperlihatkan objek nyata atau gambar melalui kamera USB. Sistem kemudian memproses gambar menggunakan CNN dan menghasilkan respons yang memengaruhi perkembangan karakter monster.

Proyek ini menggabungkan pengembangan algoritma AI menggunakan Python dengan implementasi arsitektur hardware menggunakan Verilog pada board DE10-Standard.

## 2. Latar Belakang

Perkembangan teknologi Artificial Intelligence memungkinkan sistem komputer mengenali dan mengklasifikasikan objek berdasarkan informasi visual.

Salah satu metode yang banyak digunakan dalam pengolahan citra adalah Convolutional Neural Network (CNN), yang mampu mempelajari karakteristik visual suatu objek melalui proses training.

Namun, implementasi AI tidak hanya terbatas pada perangkat lunak. Pengembangan hardware accelerator berbasis FPGA memungkinkan proses inferensi CNN diimplementasikan secara langsung pada perangkat keras.

MONSTER.AI dikembangkan sebagai penerapan integrasi antara AI dan FPGA melalui pendekatan yang interaktif dan menarik.

Sistem ini tidak hanya menampilkan hasil klasifikasi, tetapi juga mengubah hasil pengenalan objek menjadi mekanisme interaksi dan evolusi karakter virtual.

## 3. Tujuan Proyek

1. Mengembangkan sistem klasifikasi citra menggunakan CNN.
2. Mengimplementasikan proses inferensi CNN menggunakan Verilog pada FPGA.
3. Mengintegrasikan kamera USB sebagai perangkat input gambar.
4. Mengembangkan sistem interaksi antara hasil klasifikasi dan karakter virtual.
5. Menerapkan mekanisme perubahan atribut dan evolusi karakter berdasarkan elemen yang dikenali.
6. Mengevaluasi performa algoritma dan implementasi hardware FPGA.

## 4. Konsep dan Mekanisme Sistem

MONSTER.AI menggunakan lima kelas elemen utama:

| Kelas | Representasi | Efek pada Monster |
|---|---|---|
| FIRE | Api | Meningkatkan kekuatan api |
| WATER | Air | Meningkatkan kekuatan air |
| ELECTRIC | Baterai, perangkat elektronik, petir | Meningkatkan kekuatan listrik |
| PLANT | Daun dan tanaman | Meningkatkan kekuatan alam |
| ROCK | Batu dan bebatuan | Meningkatkan pertahanan |

Kelas ELECTRIC dirancang mencakup dua jenis representasi visual, yaitu perangkat elektronik/baterai dan petir/percikan listrik.

### Alur Interaksi

1. Pengguna memperlihatkan objek ke kamera USB.
2. Sistem menangkap gambar menggunakan HPS.
3. Gambar diproses melalui tahap preprocessing.
4. CNN melakukan klasifikasi citra.
5. Hasil klasifikasi digunakan untuk menentukan elemen.
6. Monster menerima elemen dan mengalami perubahan atribut.
7. Sistem menentukan respons dan perkembangan karakter.
8. Karakter ditampilkan melalui VGA Display.

## 5. Fitur Utama

### A. CNN Object Classification
Sistem mengenali lima kelas elemen berdasarkan gambar yang ditangkap kamera.

### B. Elemental Interaction
Setiap elemen memberikan pengaruh berbeda terhadap atribut dan kemampuan monster.

### C. Dynamic Character Evolution
Karakter dapat mengalami perubahan berdasarkan akumulasi elemen yang diberikan.

### D. Character Status
Sistem direncanakan memiliki beberapa parameter karakter:
- Health
- Energy
- Happiness
- Elemental Affinity
- Evolution Level

### E. Visual Display
Monster ditampilkan melalui VGA dengan informasi status, animasi, dan perubahan karakter.

### F. Camera-Based Interaction
Pengguna dapat memberikan input melalui objek nyata maupun gambar yang ditampilkan pada layar perangkat lain.

## 6. Arsitektur Sistem

MONSTER.AI dirancang menggunakan pembagian pemrosesan antara HPS dan FPGA pada DE10-Standard.

```text
              USB WEBCAM
                   |
                   v
             HPS (ARM)
          Linux + OpenCV
                   |
                   v
          IMAGE PREPROCESSING
             Resize 32x32
                   |
                   v
             HPS-FPGA BRIDGE
                   |
                   v
          FPGA CNN ACCELERATOR
                (Verilog)
                   |
                   v
           CLASSIFICATION
                   |
                   v
             MONSTER ENGINE
                   |
          +--------+--------+
          |                 |
          v                 v
      CHARACTER          EVOLUTION
       STATUS              SYSTEM
          |                 |
          +--------+--------+
                   |
                   v
              VGA DISPLAY
```

## 7. Teknologi yang Digunakan

| Teknologi | Fungsi |
|---|---|
| Python | Training, preprocessing, dan evaluasi CNN |
| Verilog | Implementasi CNN accelerator dan game logic |
| Quartus Prime | Sintesis dan implementasi desain FPGA |
| ModelSim | Simulasi dan verifikasi rangkaian Verilog |
| OpenCV | Pengambilan dan pengolahan gambar kamera |
| USB Webcam | Input objek visual |
| DE10-Standard | Platform implementasi hardware |
| VGA | Tampilan visual karakter virtual |

## 8. Dataset

Dataset dirancang menggunakan lima kelas utama:

- Fire
- Water
- Electric
- Plant
- Rock

### Struktur Dataset

```text
dataset/
├── training/
│   ├── fire/
│   ├── water/
│   ├── electric/
│   ├── plant/
│   └── rock/
│
└── test/
    ├── fire/
    ├── water/
    ├── electric/
    ├── plant/
    └── rock/
```

Ketentuan dataset:
- Resolusi gambar minimal 32 × 32 piksel.
- Format gambar JPG, JPEG, atau PNG.
- Data training dan testing tidak menggunakan gambar duplikat.
- Setiap kelas memiliki variasi gambar yang memadai.
- Preprocessing dilakukan sebelum gambar digunakan dalam CNN.

## 9. Implementasi Algoritma

### Python
Python digunakan untuk:
- Membaca dataset.
- Preprocessing citra.
- Membangun arsitektur CNN.
- Melatih model.
- Mengevaluasi akurasi.
- Quantization bobot CNN.
- Mengekspor bobot untuk implementasi hardware.

### Verilog
Verilog digunakan untuk:
- Implementasi convolution.
- Implementasi activation function (ReLU).
- Implementasi pooling.
- Implementasi classifier.
- Pengolahan hasil klasifikasi.
- Pengendalian status dan evolusi karakter.
- Integrasi dengan VGA.

## 10. Struktur Repository

```text
MONSTER.AI/
│
├── dataset/
│   ├── training/
│   └── test/
│
├── verilog/
│   └── fpga/
│       ├── rtl/
│       ├── testbench/
│       ├── quartus/
│       └── modelsim/
│
├── algoritma/
│   ├── python/
│   ├── c/
│   └── matlab/
│
├── output/
│   ├── training_results/
│   ├── accuracy/
│   ├── confusion_matrix/
│   ├── fpga_synthesis/
│   └── demo/
│
├── publikasi/
│   ├── paper/
│   └── presentasi/
│
└── laporan/
    ├── progres.md
    ├── logbook.md
    └── hasil_pengujian.md
```

## 11. Evaluasi dan Pengujian

Evaluasi proyek direncanakan mencakup dua aspek.

### Evaluasi Model CNN
- Training accuracy.
- Validation accuracy.
- Testing accuracy.
- Confusion matrix.
- Performa klasifikasi setiap kelas.

### Evaluasi Hardware FPGA
- Resource utilization.
- Logic elements / ALM.
- Register.
- DSP utilization.
- Memory utilization.
- Clock frequency.
- Inference latency.

Hasil pengujian Python dan FPGA akan dibandingkan untuk mengevaluasi konsistensi hasil klasifikasi.

## 12. Rencana Pengembangan

| Tahapan | Aktivitas | Status |
|---|---|---|
| 1 | Penentuan ide dan konsep | Selesai |
| 2 | Pembuatan repository GitHub | Selesai |
| 3 | Persiapan struktur dataset | Selesai |
| 4 | Pengumpulan dataset | Proses |
| 5 | Preprocessing gambar | Belum dimulai |
| 6 | Training CNN menggunakan Python | Belum dimulai |
| 7 | Evaluasi dan quantization CNN | Belum dimulai |
| 8 | Implementasi CNN menggunakan Verilog | Belum dimulai |
| 9 | Simulasi ModelSim | Belum dimulai |
| 10 | Implementasi Quartus pada DE10-Standard | Belum dimulai |
| 11 | Integrasi kamera USB | Belum dimulai |
| 12 | Pengembangan monster evolution | Belum dimulai |
| 13 | Pengujian sistem keseluruhan | Belum dimulai |

## 13. Target Akhir Proyek

Target akhir MONSTER.AI adalah menghasilkan sistem makhluk virtual interaktif yang mampu mengenali objek melalui kamera, melakukan klasifikasi menggunakan CNN berbasis FPGA, dan memberikan respons berupa perubahan atribut serta evolusi karakter secara dinamis.

Proyek ini diharapkan menjadi demonstrasi integrasi antara Artificial Intelligence, digital hardware design, dan interactive computing menggunakan board DE10-Standard.

---

**MONSTER.AI — Recognize the Element, Evolve Your Monster!**
