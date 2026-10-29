# Gambar portfolio — panduan singkat

Semua gambar disimpan di folder ini (`public/images/`) dan dibaca otomatis
oleh aplikasi. Tidak perlu mengubah kode dan tidak perlu `npm run build`.

## 1. Foto profil

Taruh satu file di sini, nama **harus** `profile`:

```
public/images/profile.webp
```

Ekstensi yang didukung: `jpg`, `jpeg`, `png`, `webp`, `avif`
(pilih salah satu saja, jangan sekaligus).

- Rasio tampilan di website: 640 x 760 px (portrait).
- Saran: minimal 800 x 950 px, ukuran file di bawah 500 KB.
- Kalau file belum ada, website menampilkan placeholder monogram "AH".

## 2. Foto project

Satu folder per project. Isinya cover + screenshot galeri (jumlahnya bebas):

```
public/images/projects/{slug}/cover.webp   -> gambar kartu project (16:10, 1600x1000)
public/images/projects/{slug}/1.webp       -> screenshot galeri 1
public/images/projects/{slug}/2.webp       -> screenshot galeri 2
public/images/projects/{slug}/3.webp       -> screenshot galeri 3
```

`{slug}` yang tersedia (folder sudah dibuat, jangan di-rename):

| No | Folder               | Project                                   |
|----|----------------------|-------------------------------------------|
| 01 | `skin-ai`            | Skin AI — Facial Skin Care DSS            |
| 02 | `tickdesk`           | TickDesk — IT Service Dispatch System     |
| 03 | `vmush`              | VMush — Smart Mushroom House              |
| 04 | `puzzle-adventure`   | Puzzle Picture Adventure                  |
| 05 | `smart-agri`         | Smart Agri — Precision Farming            |
| 06 | `sip-coffee`         | SIP Coffee — Traceability Ecosystem       |
| 07 | `lawvegas`           | LawVegas — Law Firm Portal                |
| 08 | `deskcash`           | Deskcash — Cafe POS & Inventory System    |
| 09 | `medicare`           | MediCare+ — Pharmacy Commerce & Stock     |

Catatan:

- Format yang dipakai sekarang: **`.webp`** (paling kecil, teks tetap tajam).
  `jpg` / `jpeg` / `png` / `avif` juga terbaca, tapi kalau ada dua format
  dengan nama sama, urutan prioritasnya: `jpg` → `jpeg` → `png` → `webp` → `avif`.
  Jadi hapus file lama kalau mengganti format.
- Nama file `1`, `2`, `3` dst. = urutan screenshot di dalam modal project.
  Keterangan (caption) tiap screenshot diatur di `config/portfolio.php`.
- Cover otomatis ikut tampil sebagai slide **pertama** di gallery modal
  (caption "Project cover"), jadi gallery memuat semua gambar project.
- Jumlah screenshot per project tidak harus 3. Tambah/kurangi baris pada array
  `images` project tersebut di `config/portfolio.php`, contoh:

  ```php
  ['file' => 'images/projects/skin-ai/5', 'caption' => 'Judul screenshot kelima'],
  ```

- Cover dibuat 1600 x 1000 px (16:10) dan tampil dengan `object-fit: cover`,
  jadi bagian tepi gambar bisa terpotong sedikit. Screenshot landscape
  (16:9) paling aman; screenshot HP portrait tetap muat di galeri.
- File yang belum ada akan diganti placeholder desain, jadi website tetap rapi
  walau baru sebagian gambar yang diisi.

## Checklist

- [x] `profile.png` (foto profil sudah ada)
- [x] `projects/skin-ai/` — cover + 4 screenshot
- [x] `projects/tickdesk/` — cover + 5 screenshot
- [x] `projects/vmush/` — cover + 6 screenshot (mobile)
- [ ] `projects/puzzle-adventure/` — belum ada gambar
- [ ] `projects/smart-agri/` — belum ada gambar
- [x] `projects/sip-coffee/` — cover + 5 screenshot
- [x] `projects/lawvegas/` — cover + 2 screenshot
- [x] `projects/deskcash/` — cover + 2 screenshot
- [x] `projects/medicare/` — cover + 4 screenshot (admin & apoteker)

## Setelah menambah gambar

Refresh browser. Kalau yang diganti adalah file dengan nama sama, tekan
`Ctrl + Shift + R` supaya cache browser tidak memakai gambar lama.

Kalau website di-deploy sebagai HTML statis, jalankan `.\build-static.ps1`
ulang supaya folder `dist/` ikut memuat gambar baru.
