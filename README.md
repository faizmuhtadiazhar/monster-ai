# MONSTER.AI

**Judul:** MONSTER.AI: Pengembangan Makhluk Virtual Interaktif dengan Klasifikasi Elemen Berbasis CNN dan Evolusi Karakter Dinamis

## Deskripsi
MONSTER.AI adalah proyek makhluk virtual interaktif. CNN dirancang untuk mengklasifikasikan citra elemen (Fire, Water, Electric, Plant, dan Rock). Hasil klasifikasi digunakan oleh game logic untuk mengubah atribut dan evolusi karakter.

## Platform dan teknologi
- Board: Terasic DE10-Standard
- Bahasa: Python dan Verilog
- Input yang direncanakan: kamera USB melalui HPS (kompatibilitas perangkat tetap perlu diuji)
- Keluaran: VGA

## Struktur repository
- `dataset/`: data training dan testing
- `verilog/fpga/`: RTL, testbench, dan berkas proyek Quartus/ModelSim
- `algoritma/`: kode Python, C, dan MATLAB sesuai kebutuhan
- `output/`: hasil eksperimen dan pengujian
- `publikasi/`: referensi dan bahan presentasi
- `laporan/`: progres, logbook, dan hasil pengujian

## Catatan
Folder kelas dataset saat ini hanya berisi README petunjuk. Gambar dataset belum disertakan. Setiap gambar harus berukuran minimal 32 x 32 piksel dan data test tidak boleh duplikat dengan data training.
