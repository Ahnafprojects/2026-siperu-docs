# SDD Backend SIPERU

## Ringkasan
Backend menyediakan API untuk manajemen `Room` (ruangan) dan `Booking` (peminjaman ruangan).
Teknologi: ASP.NET Core Web API + Entity Framework Core.

## Base URL
- Default routing: `/{host}/api/{controller}`
- Endpoint utama: `api/rooms`
- Endpoint utama: `api/bookings`

## Autentikasi
- Tidak ada autentikasi/otorisasi di kode saat ini.

## Endpoints

## Rooms
- GET `api/rooms`: Ambil seluruh data ruangan. Response `200 OK` + array `Room`.
- GET `api/rooms/{id}`: Ambil detail 1 ruangan. Response `200 OK` + `Room` atau `404 Not Found`.
- POST `api/rooms`: Tambah ruangan baru. Response `201 Created` + `Room` atau `400 Bad Request`.
- PUT `api/rooms/{id}`: Update data ruangan. Response `204 No Content`, `400 Bad Request`, atau `404 Not Found`.
- DELETE `api/rooms/{id}`: Hapus ruangan. Response `204 No Content` atau `404 Not Found`.

## Bookings
- GET `api/bookings`: Ambil seluruh data booking (termasuk `Room`). Query params opsional: `status`, `search`. Sorting: `StartTime` desc. Response `200 OK` + array `Booking`.
- GET `api/bookings/{id}`: Ambil detail 1 booking (termasuk `Room`). Response `200 OK` + `Booking` atau `404 Not Found`.
- POST `api/bookings`: Buat booking baru. Status dipaksa `Pending`. Validasi: `EndTime` > `StartTime`, `RoomId` ada, tidak bentrok dengan booking `Approved`. Response `201 Created` + `Booking` atau `400 Bad Request`.
- PUT `api/bookings/{id}/status`: Update status booking. Body JSON string, contoh `"Approved"`. Status valid: `Pending`, `Approved`, `Rejected`. Jika `Approved`, cek bentrok booking `Approved` lain. Response `204 No Content`, `400 Bad Request`, atau `404 Not Found`.
- DELETE `api/bookings/{id}`: Hapus booking (hard delete). Response `204 No Content` atau `404 Not Found`.

## Contoh Request/Response

## GET `api/rooms`
```json
[
  {
    "id": 1,
    "name": "C-101",
    "capacity": 30,
    "description": "Ruang Kelas Lantai 1",
    "isAvailable": true,
    "createdAt": "2026-02-08T00:00:00Z"
  }
]
```

## POST `api/rooms`
```json
{
  "name": "Lab Bahasa",
  "capacity": 20,
  "description": "Lab audio",
  "isAvailable": true
}
```

## GET `api/bookings?status=approved&search=rapat`
```json
[
  {
    "id": 1,
    "studentName": "Ahmad Fauzi",
    "purpose": "Rapat Himpunan",
    "startTime": "2026-02-09T10:00:00",
    "endTime": "2026-02-09T12:00:00",
    "roomId": 1,
    "status": "Approved",
    "room": {
      "id": 1,
      "name": "C-101",
      "capacity": 30,
      "description": "Ruang Kelas Lantai 1",
      "isAvailable": true,
      "createdAt": "2026-02-08T00:00:00Z"
    }
  }
]
```

## POST `api/bookings`
```json
{
  "studentName": "Dina",
  "purpose": "Diskusi proyek",
  "startTime": "2026-02-12T09:00:00",
  "endTime": "2026-02-12T11:00:00",
  "roomId": 2
}
```

## PUT `api/bookings/{id}/status`
```json
"Approved"
```

## Skema Data

## Tabel: Rooms
- Field `Id`: int, PK, auto.
- Field `Name`: string (max 100), required.
- Field `Capacity`: int, required.
- Field `Description`: string, nullable.
- Field `IsAvailable`: bool, default `true`.
- Field `CreatedAt`: datetime, default `DateTime.UtcNow`.

## Tabel: Bookings
- Field `Id`: int, PK, auto.
- Field `StudentName`: string, required.
- Field `Purpose`: string, required.
- Field `StartTime`: datetime, required.
- Field `EndTime`: datetime, required.
- Field `RoomId`: int, FK -> `Rooms.Id`, required.
- Field `Status`: string, default `Pending`.
- Field `Room`: object, nullable, navigation.

## Validasi dan Error Handling
- Validasi input di setiap endpoint.
- Error response konsisten dengan kode dan pesan.

## Aturan Bisnis
- Booking bentrok jika `start < existing.EndTime` dan `end > existing.StartTime`.
- Bentrok hanya dihitung terhadap booking berstatus `Approved`.
- Saat create booking, status selalu dipaksa `Pending`.

## Catatan Implementasi
- Swagger tersedia di `/swagger`.
- Env utama: `ConnectionStrings__DefaultConnection`.

## Catatan Implementasi
- .NET 10, EF Core 10, SQLite.
- Swagger tersedia di `/swagger`.
