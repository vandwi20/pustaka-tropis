# Dokumentasi API: Produk Admin

## Autentikasi
Semua endpoint dalam kategori produk dilindungi oleh autentikasi. Jika pengguna tidak terautentikasi, maka akan menerima respons berikut:

**Status Code: 401**
```json
{
    "status": 401,
    "error": true,
    "message": "Unauthorized. Silakan login terlebih dahulu."
}
```

---

# Endpoint: Menambahkan Produk

## Endpoint
**POST** `/api/admin/products`

## Deskripsi
Endpoint ini digunakan untuk menambahkan produk baru.

## Parameter
| Parameter    | Tipe   | Wajib | Deskripsi                                      |
|-------------|--------|------|------------------------------------------------|
| name        | string | Ya   | Nama produk                                    |
| description | string | Ya   | Deskripsi produk                              |
| price_type  | string | Ya   | Jenis harga (`range`, `fixed`, `free`)        |
| price_start | int    | Tidak | Harga awal (jika `price_type` adalah `range`) |
| price_end   | int    | Tidak | Harga akhir (jika `price_type` adalah `range`) |
| price_fix   | int    | Tidak | Harga tetap (jika `price_type` adalah `fixed`) |
| tags   | array    | Ya | List Category dengan array|
| tags   | array    | Ya | List Category dengan array|
| gambar      | file   | Ya   | Gambar produk dalam format JPG, JPEG, PNG, GIF |

## Contoh Request

### HTTP Request
```http
POST /api/admin/products HTTP/1.1
Host: your-api-domain.com
Content-Type: multipart/form-data
```

## Response

### Berhasil
**Status Code: 201**
```json
{
    "status": 201,
    "message": "Produk berhasil ditambahkan"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Pastikan file gambar memenuhi aturan validasi yang ditetapkan.

---

# Endpoint: Mendapatkan Daftar Produk

## Endpoint
**GET** `/api/admin/products`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan daftar produk dengan opsi pencarian dan penyortiran.

## Parameter
| Parameter  | Tipe   | Wajib | Deskripsi                                        |
|-----------|-------|------|------------------------------------------------|
| name      | string | Tidak | Nama produk yang ingin dicari                  |
| limit     | int    | Tidak | Jumlah item yang ditampilkan per halaman       |
| orderby   | string | Tidak | Urutan data berdasarkan jumlah pembeli (`buyer`) |
| page      | int    | Tidak | Nomor halaman data yang ingin diakses         |

## Contoh Request

### HTTP Request
```http
GET /api/admin/products?name=example&limit=2&orderby=buyer&page=1 HTTP/1.1
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
        "list_next": [
            2
        ]
    },
    "current_page": 1,
    "total_pages": 2,
    "item_found": 3,
    "curent_item": 2,
    "limit": 2,
    "data": [
        {
            "id": 1,
            "name": "product example 1",
            "buyer_count": "0",
            "categories": "admin,user",
            "image_preview": "https://testing.pustakatropis.com/image_preview%20example%201",
            "created_at": "2025-03-21 10:32:56"
        },
        {
            "id": 2,
            "name": "product example 2",
            "buyer_count": "0",
            "categories": "jagung,pohon",
            "image_preview": "https://testing.pustakatropis.com/image_preview%20example%202",
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

# Endpoint: Mendapatkan Detail Produk

## Endpoint
**GET** `/api/admin/products/{id}`

## Deskripsi
Endpoint ini digunakan untuk mendapatkan detail sebuah produk berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi            |
|----------|------|------|--------------------|
| id       | int  | Ya   | ID produk yang dicari |

## Contoh Request

### HTTP Request
```http
GET /api/admin/products/1 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "id": 1,
    "name": "product example 1",
    "description": "description example 1",
    "categories": "admin,user",
    "buyer_count": "0",
    "image_preview": "https://testing.pustakatropis.com/image_preview%20example%201",
    "image_raw": "https://testing.pustakatropis.com/image_raw%20example%201",
    "price_type": "fixed",
    "price_start": 1000,
    "price_end": 0,
    "price_fix": 0,
    "created_at": "2025-03-21 10:32:56",
    "updated_at": null
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika produk dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

---

# Endpoint: Menghapus Produk

## Endpoint
**DELETE** `/api/admin/products/{id}`

## Deskripsi
Endpoint ini digunakan untuk menghapus sebuah produk berdasarkan ID.

## Parameter
| Parameter | Tipe  | Wajib | Deskripsi            |
|----------|------|------|--------------------|
| id       | int  | Ya   | ID produk yang akan dihapus |

## Contoh Request

### HTTP Request
```http
DELETE /api/admin/products/1 HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Produk berhasil dihapus"
}
```

### Gagal (Produk Tidak Ditemukan)
**Status Code: 404**
```json
{
    "status": 404,
    "error": true,
    "message": "Produk tidak ditemukan"
}
```

## Catatan
- Pastikan pengguna telah login sebelum mengakses endpoint ini.
- Jika produk dengan ID yang diberikan tidak ditemukan, sistem akan mengembalikan respons dengan status `404 Not Found`.

