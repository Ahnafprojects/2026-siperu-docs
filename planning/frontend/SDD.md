# SDD Frontend SIPERU

## Ringkasan Desain
Frontend dashboard admin untuk peminjaman ruangan, dibangun dengan React + Vite dan Tailwind CSS.

## Struktur Halaman
- Dashboard.
- Daftar Peminjaman.
- Detail Peminjaman.
- Jadwal Ruangan.

## Komponen Inti
- Navbar.
- Tabel Peminjaman.
- Status Badge.
- Modal (Tambah, Detail, Ubah Status, Hapus).

## State dan Data Fetching
- Data diambil dari Backend API.
- Cache ringan untuk daftar peminjaman.

## Validasi
- Validasi client-side sebelum submit.
- Tampilkan pesan error yang jelas.

## UX dan Aksesibilitas
- Gunakan kontras warna yang cukup.
- Fokus keyboard terlihat.
- Loading indicator konsisten.

## Catatan Implementasi
- React 19 + TypeScript.
- Vite 7, Tailwind CSS 4, Framer Motion, Lucide React.
- Env: `VITE_API_BASE_URL`.
