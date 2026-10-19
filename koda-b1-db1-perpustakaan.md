# Database

## Sistem Perpustakaan

Entitas : User

- id_user = id (PK)
- nama = string
- asal = string

Entitas : Buku

- id_buku = id (PK)
- judul = string
- id_kategori = (FK)
- id_rak = (FK)

Entitas : Kategori

- id_kategori = id (PK)
- nama = string

Entitas : rak_buku

- id_rak = id (PK)
- nama_rak = string

Entitas : Petugas

- id_petugas = id (PK)
- nama = string

Entitas : Peminjaman

- id_user = (FK)
- id_buku = (FK)
- id_petugas = (FK)

## diagram

```mermaid
erDiagram
    USER ||--o{ PEMINJAMAN : meminjam
    PETUGAS || --o{ PEMINJAMAN : mengurus
    KATEGORI || --o{ BUKU : includes
    RAK_BUKU || --o{ BUKU : includes
    BUKU || --o{ PEMINJAMAN : dipinjam

    USER {
        int(PK) id_user
        string nama
        string asal
        string contact
    }
    BUKU {
        int(PK) id_buku
        string judul
        int id_kategori
        int(FK) id_rak
    }
    KATEGORI{
        int(PK) id_kategori
        string nama
    }
    RAK_BUKU{
        int(PK) id_rak
        string nama_rak
    }
    PETUGAS{
        int(PK) id_petugas
        string nama
        string contact
    }
    PEMINJAMAN{
        int(PK) id_peminjaman
        int(FK) id_user
        int(FK) id_petugas
        int(FK) id_buku
        date tanggal_peminjaman
        date tanggal_pengembalian
    }
```
