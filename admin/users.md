# Dokumentasi API: Manajemen Pengguna (Users)

## Autentikasi
Semua endpoint dalam kategori pengguna dilindungi oleh autentikasi. Jika pengguna tidak terautentikasi, maka akan menerima respons berikut:

**Status Code: 401**
```json
{
    "status": 401,
    "error": true,
    "message": "Unauthorized. Silakan login terlebih dahulu."
}
```

---

# Endpoint: Menambahkan Pengguna

## Endpoint
**POST** `/api/admin/users`

## Deskripsi
Endpoint ini digunakan untuk menambahkan pengguna baru.

## Parameter
| Parameter | Tipe   | Wajib | Deskripsi                |
|-----------|--------|------|--------------------------|
| name      | string | Ya   | Nama pengguna            |
| email     | string | Ya   | Email pengguna (unik)    |
| password  | string | Ya   | Kata sandi pengguna      |

## Contoh Request

### HTTP Request
```http
POST /api/admin/users HTTP/1.1
Host: your-api-domain.com
Content-Type: application/json
```

## Response

### Berhasil
**Status Code: 201**
```json
{
    "status": 201,
    "message": "User berhasil dibuat"
}
```

## Catatan
- Email harus unik dan belum pernah terdaftar sebelumnya.
- Kata sandi akan disimpan dalam bentuk hash.

---

# Endpoint: Mendapatkan Daftar Pengguna

## Endpoint
**GET** `/api/admin/users`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan daftar pengguna dengan opsi pencarian dan pagination.

## Parameter
| Parameter | Tipe   | Wajib | Deskripsi                                |
|-----------|--------|------|------------------------------------------|
| name      | string | Tidak | Nama pengguna yang ingin dicari          |
| limit     | int    | Tidak | Jumlah item yang ditampilkan per halaman |
| page      | int    | Tidak | Nomor halaman data yang ingin diakses    |

## Contoh Request

### HTTP Request
```http
GET /api/admin/users?name=example&page=1&limit=10 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "pagination": {
        "prev": null,
        "next": 2,
        "list_prev": [],
        "list_next": [2]
    },
    "current_page": 1,
    "total_pages": 2,
    "item_found": 3,
    "curent_item": 2,
    "limit": 10,
    "data": [
        {
            "id": 1,
            "name": "User Example 1",
            "email": "user1@example.com",
            "created_at": "2025-03-21 10:32:56"
        },
        {
            "id": 2,
            "name": "User Example 2",
            "email": "user2@example.com",
            "created_at": "2025-03-21 10:35:00"
        }
    ]
}
```

---

# Endpoint: Mendapatkan Detail Pengguna

## Endpoint
**GET** `/api/admin/users/{id}`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan detail sebuah pengguna berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi            |
|----------|------|------|--------------------|
| id       | int  | Ya   | ID pengguna yang dicari |

## Contoh Request

### HTTP Request
```http
GET /api/admin/users/1 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "id": 1,
    "name": "User Example 1",
    "email": "user1@example.com",
    "created_at": "2025-03-21 10:32:56"
}
```

---

# Endpoint: Memperbarui Pengguna

## Endpoint
**PUT** `/api/admin/users/{id}`

## Deskripsi
Endpoint ini digunakan untuk memperbarui informasi pengguna.

## Parameter
| Parameter | Tipe   | Wajib | Deskripsi                         |
|-----------|--------|------|---------------------------------|
| name      | string | Tidak | Nama pengguna                   |
| email     | string | Tidak | Email pengguna (harus unik)     |
| password  | string | Tidak | Kata sandi baru pengguna        |

## Contoh Request

### HTTP Request
```http
PUT /api/admin/users/1 HTTP/1.1
Host: your-api-domain.com
Content-Type: application/json
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Data berhasil diperbarui"
}
```

---

# Endpoint: Menghapus Pengguna

## Endpoint
**DELETE** `/api/admin/users/{id}`

## Deskripsi
Endpoint ini digunakan untuk menghapus pengguna berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi            |
|----------|------|------|--------------------|
| id       | int  | Ya   | ID pengguna yang akan dihapus |

## Contoh Request

### HTTP Request
```http
DELETE /api/admin/users/1 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Data berhasil dihapus"
}
```

### Gagal (Pengguna Tidak Ditemukan)
**Status Code: 404**
```json
{
    "status": 404,
    "error": true,
    "message": "Data tidak ditemukan"
}
```

---

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika pengguna dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

