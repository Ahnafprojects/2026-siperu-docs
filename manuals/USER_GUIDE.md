# Manual Pengguna SIPERU

Dokumen ini menjelaskan alur penggunaan aplikasi SIPERU berdasarkan implementasi UI frontend saat ini.

## Gambaran Umum
- Ringkasan statistik peminjaman dan ketersediaan ruangan.
- Manajemen daftar peminjaman: lihat detail, setujui/tolak, batalkan, hapus.
- Jadwal penggunaan per ruangan.
- Form pengajuan peminjaman.

## Status Peminjaman
- `Pending` (menunggu persetujuan).
- `Approved` (disetujui).
- `Rejected` (ditolak).
- `Cancelled` (dibatalkan).

## Transisi Status di UI
- `Pending` -> `Approved`.
- `Pending` -> `Rejected`.
- `Pending` -> `Cancelled`.
- Selain `Pending` hanya bisa dihapus dari riwayat.

## Alur Admin (Dashboard)
1. Masuk Dashboard.
2. Sistem memuat data `rooms` dan `bookings`.
3. Ringkasan menampilkan total peminjaman dan jumlah ruangan aktif.
4. Grid ruangan menampilkan status `Available` atau `In Use`.
5. Klik kartu ruangan untuk melihat jadwal detail.
6. Tabel peminjaman bisa dicari dan difilter.
7. Status `Pending` bisa `Approve` atau `Reject`.
8. Modal detail menampilkan aksi sesuai status.
9. Klik `New Booking` untuk membuat peminjaman baru.

## Alur User (Mahasiswa)
1. Mengajukan peminjaman via form.
2. Status awal selalu `Pending`.
3. Jika masih `Pending`, user dapat `Cancel Booking`.
4. Jika `Approved` atau `Rejected`, tidak ada aksi lanjutan.

## Perilaku UI (Teknis)
- Data diambil dari API: `GET /rooms`, `GET /bookings`, `POST /bookings`, `PUT /bookings/{id}/status`, `DELETE /bookings/{id}`.
- Penyaringan tanggal di tabel berdasarkan `startTime`.
- Jadwal ruangan menampilkan semua peminjaman kecuali status `Rejected`.

## Batasan Saat Ini
- Belum ada autentikasi/role management.
- UI menganggap admin sebagai pengguna utama dashboard.
- Validasi bentrok jadwal dilakukan di backend.

## Tips
- Pastikan jadwal tidak bentrok dengan peminjaman lain.
- Gunakan data yang valid agar proses cepat.

## Bantuan
Hubungi petugas melalui kanal bantuan resmi proyek.
