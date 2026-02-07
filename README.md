# 2026-siperu-docs

Repositori dokumentasi untuk proyek SIPERU (Sistem Peminjaman Ruangan). Isinya bukan kode aplikasi, melainkan dokumen arsitektur, manual pengguna, serta laporan teknis (SRS/SDD) untuk backend, frontend, dan infrastruktur.

![Docs](https://img.shields.io/badge/docs-siperu-blue)
![CI Backend](https://github.com/Ahnafprojects/2026-siperu-backend/actions/workflows/ci.yml/badge.svg?branch=develop)
![CI Frontend](https://github.com/Ahnafprojects/2026-siperu-frontend/actions/workflows/ci.yml/badge.svg?branch=develop)
![CI Infra](https://github.com/Ahnafprojects/2026-siperu-infrastructure/actions/workflows/ci.yml/badge.svg)

## Struktur Folder
- `architecture`: dokumen arsitektur dan diagram alur.
- `manuals`: manual pengguna dan alur penggunaan aplikasi.
- `planning`: laporan teknis per domain.

## Isi Utama
- Arsitektur sistem: `architecture/README.md`
- Manual pengguna: `manuals/USER_GUIDE.md`
- Backend SRS: `planning/backend/SRS.md`
- Backend SDD: `planning/backend/SDD.md`
- Frontend SRS: `planning/frontend/SRS.md`
- Frontend SDD: `planning/frontend/SDD.md`
- Infrastruktur SRS: `planning/infra/SRS.md`
- Infrastruktur SDD: `planning/infra/SDD.md`

## Repo Terkait
- Backend: `../2026-siperu-backend` (repo sibling).
- Frontend: `../2026-siperu-frontend` (repo sibling).
- Infrastruktur: `../2026-siperu-infrastructure` (repo sibling).

## Cara Pakai
1. Mulai dari arsitektur untuk gambaran umum.
2. Baca manual pengguna untuk memahami alur UI.
3. Lanjut ke SRS/SDD sesuai kebutuhan (backend, frontend, infra).

## Ringkasan Endpoint (Backend)
- Rooms: `GET /api/rooms`, `GET /api/rooms/{id}`, `POST /api/rooms`, `PUT /api/rooms/{id}`, `DELETE /api/rooms/{id}`.
- Bookings: `GET /api/bookings`, `GET /api/bookings/{id}`, `POST /api/bookings`, `PUT /api/bookings/{id}/status`, `DELETE /api/bookings/{id}`.

## Ringkasan Flow
- Admin: memantau dashboard, menyetujui/menolak booking, dan mengelola jadwal ruangan.
- User: mengajukan booking dan menunggu persetujuan.

## Catatan
Dokumen mengikuti implementasi SIPERU terbaru (frontend React + Vite, backend ASP.NET, dan infrastruktur Docker Compose).

## Scope Versi Dokumen
- Frontend: React + Vite, fokus dashboard admin peminjaman ruangan.
- Backend: ASP.NET Core Web API + EF Core + SQLite, endpoint Rooms dan Bookings.
- Infrastruktur: Docker Compose untuk orkestrasi lokal dengan repo sibling.

## Kontribusi
- Buat perubahan dokumentasi yang fokus dan jelas.
- Jika perlu, sertakan catatan perubahan di bagian Changelog.

## Lisensi
- UNLICENSED (belum ditentukan).

## Changelog
- 2026-02-07: Penambahan struktur docs dan ringkasan dokumen utama.
- 2026-02-07: Sinkronisasi konten backend, frontend, dan infra sesuai implementasi.
