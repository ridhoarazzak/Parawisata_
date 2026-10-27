# Pojok Solsel: tambahan untuk nextjs-boilerplate

Struktur ini cocok dengan repo kamu (App Router, `app/` di root, alias `@/*` = root).

## Pasang
1. Salin `app/`, `components/`, `lib/`, `data/`, `scripts/` ke root repo. `app/layout.tsx`, `app/page.tsx`, dan `app/globals.css` akan menimpa bawaan create-next-app.
2. Tambahkan di `package.json` bagian `scripts`:
   ```json
   "data": "node scripts/build-data.mjs",
   "prebuild": "node scripts/build-data.mjs"
   ```
3. `npm run dev`, buka http://localhost:3000.

`globals.css` tidak memuat `@import "tailwindcss"` karena tampilan ini memakai CSS sendiri dan reset Tailwind akan mengubah tampilannya. Kalau nanti butuh Tailwind di halaman lain, tambahkan lagi barisnya dan cek tampilan.

## Cara memperbarui data
1. Ganti/tambah CSV di `data/raw/` (nama kolom harus sama).
2. Isi manual (deskripsi, jam, rating, tempat tambahan) di `data/overrides.json`, bukan di CSV.
3. `npm run data` memeriksa kolom, koordinat, rating, skor, nama ganda, titik di luar Solok Selatan, dan kunci overrides yang salah ketik, lalu menulis `data/places.json`. Jika ada ERROR, file tidak ditulis.
4. Karena ada `prebuild`, `next build` (dan deploy Vercel) gagal bila data bermasalah.
