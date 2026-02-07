# SRS Backend SIPERU

## Tujuan
Mendefinisikan kebutuhan fungsional dan non-fungsional untuk layanan backend SIPERU.

## Ruang Lingkup
Backend menyediakan API untuk data ruangan dan booking, termasuk validasi bentrok jadwal dan perubahan status booking.

## Pemangku Kepentingan
- Pengguna.
- Admin/Petugas.
- Tim Operasional.

## Kebutuhan Fungsional
- CRUD Rooms.
- CRUD Bookings.
- Update status booking (Approved/Rejected/Pending).
- Validasi bentrok jadwal untuk booking status Approved.
- Dokumentasi API via Swagger.

## Kebutuhan Non-Fungsional
- Kinerja. Respon API utama kurang dari 2 detik pada beban normal.
- Keamanan. Konfigurasi environment dan string koneksi aman.
- Ketersediaan. Target uptime 99%.
- Observabilitas. Logging dan Swagger UI.

## Data dan Integrasi
- SQLite sebagai database utama.
- Swagger/OpenAPI untuk dokumentasi.

## Batasan
- Perubahan skema harus lewat migrasi.
- Default database menggunakan file `siperu.db`.
