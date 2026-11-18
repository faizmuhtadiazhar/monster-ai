# MONSTER.AI

**Judul:** MONSTER.AI: Pengembangan Makhluk Virtual Interaktif dengan Klasifikasi Elemen Berbasis CNN dan Evolusi Karakter Dinamis

## Deskripsi
MONSTER.AI adalah proyek makhluk virtual interaktif. CNN dirancang untuk mengklasifikasikan citra elemen (Fire, Water, Electric, Plant, dan Rock). Hasil klasifikasi digunakan oleh game logic untuk mengubah atribut dan evolusi karakter.

## Platform dan teknologi
- Board: Terasic DE10-Standard
- Bahasa: Python dan Verilog
- Input gambar: kamera USB (kompatibilitas kamera dan Linux HPS perlu diuji)
- Keluaran: VGA

## Struktur repository
- `dataset/`: data training dan testing
- `verilog/fpga/`: RTL, testbench, dan berkas proyek Quartus/ModelSim
- `algoritma/`: kode Python, C, dan MATLAB (sesuai kebutuhan)
- `output/`: hasil eksperimen dan pengujian
- `publikasi/`: referensi dan bahan presentasi
- `laporan/`: progres, logbook, dan hasil pengujian

## Catatan dataset
- Simpan gambar sesuai kelas pada folder `training/` dan `test/`.
- Setiap gambar harus berukuran minimal 32 x 32 piksel.
- Pastikan gambar pada data test tidak digunakan pada data training.
- Folder saat ini hanya berisi placeholder `.gitkeep`; gambar dataset belum disertakan.
- Lakukan preprocessing ke ukuran input CNN yang disepakati sebelum training/inference.

## Status
Kerangka repository awal. Kode CNN, desain Verilog, dataset, dan hasil pengujian akan ditambahkan bertahap.
