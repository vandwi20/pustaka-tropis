# Dokumentasi API: Kategori Admin

## Autentikasi
Semua endpoint dalam kategori ini dilindungi oleh autentikasi. Jika pengguna tidak terautentikasi, maka akan menerima respons berikut:

**Status Code: 401**
```json
{
    "status": 401,
    "error": true,
    "message": "Unauthorized. Silakan login terlebih dahulu."
}
```

---

# Endpoint: Mendapatkan Daftar Kategori

## Endpoint
**GET** `/api/admin/categories`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan daftar kategori dengan opsi pencarian dan penyortiran.

## Parameter
| Parameter  | Tipe   | Wajib | Deskripsi                                  |
|-----------|-------|------|------------------------------------------|
| name      | string | Tidak | Nama kategori yang ingin dicari        |
| limit     | int    | Tidak | Jumlah item yang ditampilkan per halaman |
| page      | int    | Tidak | Nomor halaman data yang ingin diakses  |

## Contoh Request

### HTTP Request
```http
GET /api/admin/categories?name=example&limit=10&page=1 HTTP/1.1
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
            "name": "category example 1",
            "created_at": "2025-03-21 10:32:56"
        },
        {
            "id": 2,
            "name": "category example 2",
            "created_at": "2025-03-21 10:32:56"
        }
    ]
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Parameter pencarian bersifat opsional dan dapat digunakan untuk menyaring hasil.
- Gunakan parameter `page` untuk berpindah halaman dalam hasil pencarian.

---

# Endpoint: Mendapatkan Detail Kategori

## Endpoint
**GET** `/api/admin/categories/{id}`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan detail sebuah kategori berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi            |
|----------|------|------|--------------------|
| id       | int  | Ya   | ID kategori yang dicari |

## Contoh Request

### HTTP Request
```http
GET /api/admin/categories/1 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "id": 1,
    "name": "category example 1",
    "created_at": "2025-03-21 10:32:56"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika kategori dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

---

# Endpoint: Menambahkan Kategori

## Endpoint
**POST** `/api/admin/categories`

## Deskripsi
Endpoint ini digunakan untuk menambahkan kategori baru.

## Parameter
| Parameter | Tipe   | Wajib | Deskripsi       |
|----------|--------|------|---------------|
| name     | string | Ya   | Nama kategori  |

## Contoh Request

### HTTP Request
```http
POST /api/admin/categories HTTP/1.1
Host: your-api-domain.com
Content-Type: application/json

{
    "name": "New Category"
}
```

## Response

### Berhasil
**Status Code: 201**
```json
{
    "status": 201,
    "message": "Data berhasil disimpan"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika kategori dengan nama yang sama sudah ada, maka akan mengembalikan respons `400 Bad Request`.

---

# Endpoint: Mengupdate Kategori

## Endpoint
**PUT** `/api/admin/categories/{id}`

## Deskripsi
Endpoint ini digunakan untuk memperbarui kategori berdasarkan ID.

## Parameter
| Parameter | Tipe   | Wajib | Deskripsi       |
|----------|--------|------|---------------|
| id       | int    | Ya   | ID kategori   |
| name     | string | Ya   | Nama kategori |

## Contoh Request

### HTTP Request
```http
PUT /api/admin/categories/1 HTTP/1.1
Host: your-api-domain.com
Content-Type: application/json

{
    "name": "Updated Category"
}
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Data berhasil diupdate"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika kategori dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

---

# Endpoint: Menghapus Kategori

## Endpoint
**DELETE** `/api/admin/categories/{id}`

## Deskripsi
Endpoint ini digunakan untuk menghapus kategori berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi           |
|----------|------|------|------------------|
| id       | int  | Ya   | ID kategori yang akan dihapus |

## Contoh Request

### HTTP Request
```http
DELETE /api/admin/categories/1 HTTP/1.1
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

### Gagal (Kategori Tidak Ditemukan)
**Status Code: 404**
```json
{
    "status": 404,
    "error": true,
    "message": "Data tidak ditemukan"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika kategori dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

---

