# Arsitektur Sistem SIPERU

Dokumen ini menjelaskan arsitektur sistem SIPERU untuk peminjaman/booking ruangan kampus.

## Ringkasan
SIPERU adalah sistem peminjaman ruangan. Pengguna mengajukan booking, admin memverifikasi, dan sistem menjaga ketersediaan jadwal agar tidak bentrok.

## Tujuan Arsitektur
- Skalabel untuk beban permohonan yang fluktuatif.
- Mudah dirawat dengan pemisahan tanggung jawab antar layanan.
- Aman dengan autentikasi, otorisasi, dan audit trail.
- Terukur dengan logging terpusat dan monitoring.

## Batasan
- Dokumen ini berfokus pada arsitektur logis dan alur data.
- Detail teknis implementasi ada di dokumen SDD.

## Diagram Konteks
```mermaid
flowchart LR
  User[Pengguna] -->|Ajukan booking| Web[Frontend React + Vite]
  Admin[Admin] -->|Verifikasi/Proses| Web
  Web -->|API| BE[Backend ASP.NET]
  BE -->|Query/Write| DB[(SQLite)]
  BE -->|Swagger UI| Docs[API Docs]
```

## Komponen Utama
- Frontend (React + Vite). Dashboard admin dan UI pengguna.
- Backend API (ASP.NET Core). Logika bisnis booking dan validasi bentrok jadwal.
- Database (SQLite). Penyimpanan data ruang dan booking.
- Swagger UI. Dokumentasi API.

## Alur Utama Booking
```mermaid
sequenceDiagram
  actor U as Pengguna
  participant W as Frontend
  participant B as Backend API
  participant D as Database

  U->>W: Ajukan booking ruangan
  W->>B: Kirim data booking
  B->>B: Validasi bentrok jadwal
  B->>D: Simpan booking
  B-->>W: Respon sukses
  W-->>U: Status booking
```

## Arsitektur Logis
- Layer Presentasi. Frontend React + Vite.
- Layer Layanan. Backend API ASP.NET Core.
- Layer Data. SQLite untuk data ruangan dan booking.

## Observabilitas
- Logging di Backend API.
- Swagger UI untuk eksplorasi endpoint.

## Risiko dan Mitigasi
- Lonjakan trafik. Gunakan cache dan autoscaling.
- Kualitas data. Validasi berlapis di frontend dan backend.
- Ketersediaan. Backup terjadwal dan strategi recovery.

## Catatan
Silakan lengkapi nama layanan, teknologi, dan detail integrasi sesuai implementasi aktual.
