# Dokumentasi API Products

## Endpoint: `/api/user/products`

### 1. Mendapatkan Daftar Produk
**Method:** `GET`

**URL:** `/api/user/products`

**Query Parameters:**
- `page` (integer, opsional) - Nomor halaman (default: 1)
- `limit` (integer, opsional) - Jumlah item per halaman (default: 10)
- `name` (string, opsional) - Filter berdasarkan nama produk
- `categories` (string, opsional) - Filter berdasarkan kategori
- `price_type` (string, opsional) - Filter berdasarkan tipe bayar (`fixed`,`range`,`free`)
- `orderby` (string, opsional) - Urutan data (`buyer` untuk jumlah pembeli, default `created_at` DESC)

**Response:**
```json
{
    "pagination": {
        "prev": null,
        "next": 2,
        "list_prev": [],
        "list_next": [2, 3]
    },
    "current_page": 1,
    "total_pages": 5,
    "item_found": 50,
    "curent_item": 10,
    "limit": 10,
    "data": [
        {
            "id": 1,
            "name": "Produk A",
            "buyer_count": 100,
            "categories": "Elektronik",
            "image_preview": "https://example.com/images/product_a.jpg",
            "created_at": "2024-01-01 12:00:00"
        }
    ]
}
```

### 2. Mendapatkan Detail Produk
**Method:** `GET`

**URL:** `/api/user/products/{id}`

**Path Parameters:**
- `id` (integer, wajib) - ID produk yang dicari

**Response:**
```json
{
    "id": 1,
    "name": "Produk A",
    "description": "Deskripsi Produk A",
    "categories": "Elektronik",
    "buyer_count": 100,
    "image_preview": "https://example.com/images/product_a.jpg",
    "price_type": "fixed",
    "price_start": null,
    "price_end": null,
    "price_fix": 100000,
    "created_at": "2024-01-01 12:00:00",
    "updated_at": "2024-01-05 15:00:00"
}
```

**Error Response:**
```json
{
    "status": 404,
    "message": "Data tidak ditemukan"
}
```

