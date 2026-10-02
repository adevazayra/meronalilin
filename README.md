# Jelantah / Cahaya

Website statis satu halaman: edukasi limbah minyak jelantah + produk lilin aromaterapi,
lengkap dengan pemutar ambient "Ruang Tenang".

## Menjalankan

Buka `index.html` langsung di browser. Tidak ada build step, tidak ada dependency.
Untuk deploy: unggah `index.html` ke Netlify / Vercel / GitHub Pages apa adanya.

Kalau ingin menjalankan lewat server lokal (disarankan supaya path `/audio/` bekerja):

```
python3 -m http.server 8000
```

## Mengganti data statistik

Semua angka ada di objek `STATISTICS` di dalam `<script>`. Tiap titik data punya field
`year`, `value`, dan `isProjection`, sedangkan tiap indikator punya `label`, `unit`,
`source`, dan `sourceUrl`.

**Angka saat ini masih placeholder.** Verifikasi ke BPS, Kementerian ESDM, GIMNI, atau
laporan asosiasi UCO sebelum dipublikasikan. Chart, tooltip, catatan sumber di bawah
grafik, dan daftar sumber di footer semuanya membaca dari objek yang sama — cukup ganti
angkanya, sisanya ikut.

## Menambahkan file audio

Pemutar mencoba memuat berkas dari field `src` di `PLAYLIST` (`/audio/track-01.mp3` dst).
Kalau berkas tidak ditemukan, pemutar otomatis memakai **generator ambient Web Audio API** —
nada dan derau dibangkitkan di browser, jadi demo tetap bersuara tanpa berkas apa pun.

Untuk memakai audio asli:

1. Buat folder `audio/` di sebelah `index.html`.
2. Isi dengan berkas **royalty-free atau Creative Commons**. Sumber yang bisa dipakai:
   Pixabay Music, Free Music Archive, ccMixter, Uppbeat.
3. Perbarui `title`, `artist`, `duration`, `license`, dan `sourceUrl` tiap trek di `PLAYLIST`.

> Jangan pernah memasukkan lagu komersial ke folder ini. Catat lisensi setiap berkas di
> tabel bawah sebelum website dipublikasikan.

| Trek | Judul | Sumber | Lisensi |
|------|-------|--------|---------|
| 01   | —     | —      | —       |

## Konten lain yang bisa diedit

| Objek | Isi |
|-------|-----|
| `SUPPLY` | 6 tahap alur supply + checklist terima/tolak |
| `PROSES` | 7 langkah pengolahan |
| `BAHAN` | tabel komposisi bahan |
| `PRODUK` | varian aroma, harga, durasi bakar |
| `FAQ` | pertanyaan penutup |
| `PLAYLIST` | 20 trek Ruang Tenang |

Kalkulator dampak memakai konstanta `OIL_PER_CANDLE`, `WATER_PER_L`, `BURN_HOURS` —
asumsinya ditampilkan terbuka di halaman, jangan ubah angkanya tanpa mengubah teks asumsi.

## Catatan

- Form supplier hanya validasi client-side; submit tercetak ke `console.log`. Sambungkan
  ke backend atau layanan form (Formspree, Google Form, dsb) sebelum dipakai betulan.
- Klaim "anti-nyamuk" ditulis dengan tanda bintang dan dijelaskan di FAQ — jangan
  dinaikkan jadi klaim kesehatan.
- `prefers-reduced-motion` dihormati: animasi nyala lilin, reveal, dan visualizer berhenti.
