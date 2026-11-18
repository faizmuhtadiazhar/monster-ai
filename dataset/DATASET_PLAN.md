# Rencana Dataset MONSTER.AI

## 1. Definisi kelas

| Label CNN | Contoh gambar |
|---|---|
| FIRE | nyala lilin/kompor yang difoto dengan aman, api unggun dari jarak aman, atau gambar api di layar |
| WATER | gelas berisi air, tetesan, percikan, aliran air, atau gambar air di layar |
| ELECTRIC | baterai/perangkat elektronik dan gambar petir/percikan listrik |
| PLANT | daun, tanaman pot, rumput, bunga |
| ROCK | batu, kerikil, bebatuan |

**Kelas ELECTRIC:** rancangan awal menggabungkan dua subjenis visual yang berbeda: `battery_device` dan `lightning_spark`. Catat subjenis di manifest dan jaga jumlahnya seimbang. Jika model sulit mempelajari satu kelas gabungan, buat dua label CNN terpisah lalu petakan kedua hasilnya ke elemen game `ELECTRIC`.

## 2. Dua mode input webcam

Kumpulkan data dari:
- `physical`: webcam melihat objek nyata.
- `screen`: webcam melihat gambar objek yang ditampilkan di layar HP/laptop.

Usahakan kedua mode muncul pada training dan test untuk setiap kelas yang memungkinkan. Untuk petir, gunakan gambar pada layar; jangan mencoba membuat petir sungguhan. Untuk api, utamakan gambar di layar atau foto api yang sudah ada; jangan membuat api demi pengambilan dataset.

Ambil variasi jarak, sudut, pencahayaan, latar, perangkat layar, dan ukuran objek. Sisakan variasi sesi/objek untuk test. Jangan membagi frame berurutan dari video yang sama ke training dan test karena itu dapat membuat hasil evaluasi terlalu optimistis.

## 3. Target jumlah awal

Mulai kecil untuk memastikan pipeline berjalan:

| Split | Per kelas | Total 5 kelas |
|---|---:|---:|
| Training | 50 | 250 |
| Test | 10 | 50 |
| **Total** | **60** | **300** |

Target pengembangan setelah pipeline benar: 100 training + 20 test per kelas (600 gambar). Tambahkan validation terpisah sebelum training; jangan memakai test untuk memilih model.

## 4. Rekomendasi komposisi

Untuk kelas umum, targetkan campuran `physical` dan `screen` dalam kedua split. Contoh awal per kelas: 25 training physical + 25 training screen; 5 test physical + 5 test screen.

Khusus ELECTRIC:
- Pastikan battery/device dan lightning/spark sama-sama terwakili.
- Catat dua hal pada manifest: `subtype` dan `capture_mode`.
- Jangan biarkan semua battery hanya physical dan semua lightning hanya screen tanpa mencatatnya; model bisa belajar mode capture alih-alih elemen.

## 5. Sumber data publik

- D-Fire: dataset api/asap. Gunakan hanya gambar yang benar-benar memuat api untuk label FIRE; jangan memasukkan kelas smoke-only sebagai FIRE. Periksa sumber asli dan syarat atribusi gambar sebelum redistribusi.
- Google Open Images: sumber untuk mencari gambar objek seperti plant, rock, water, battery/electronic devices, dan objek relevan lain. Pilih gambar satu per satu sesuai label visual dan cek lisensi tiap gambar.
- Foto sendiri melalui webcam: sangat dianjurkan agar data menyerupai kondisi demo akhir.

Jangan mengambil gambar acak dari Google Images tanpa memeriksa hak penggunaan. Simpan URL sumber, nama dataset, lisensi/izin, dan tanggal unduh pada manifest.

## 6. Checklist kualitas

1. Label gambar benar.
2. Resolusi asli minimal 32 x 32 piksel.
3. Tidak ada file rusak atau duplikat.
4. Training dan test terpisah berdasarkan foto/sesi, bukan salinan frame.
5. Kedua mode input (physical/screen) terwakili.
6. Kelas ELECTRIC memiliki kedua subjenis.
7. Semua gambar punya catatan sumber dan izin.
8. Setelah itu baru lakukan resize ke 32 x 32 RGB untuk input CNN.
