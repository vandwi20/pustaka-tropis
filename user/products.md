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
- `tags` (string, opsional) - Filter berdasarkan tags
- `price_type` (string, opsional) - Filter berdasarkan tipe bayar (`fixed`,`range`,`free`)
- `orderby` (string, opsional) - Urutan data (`buyer` untuk jumlah pembeli, default `created_at` DESC)

**Response:**
```json
{
    "pagination": {
        "prev": null,
        "next": null,
        "list_prev": [],
        "list_next": []
    },
    "current_page": 1,
    "total_pages": 1,
    "item_found": 3,
    "curent_item": 3,
    "limit": 10,
    "data": [
        {
            "id": 1,
            "name": "product example 1",
            "tags": [
                "pohon",
                "dahan",
                "tanah"
            ],
            "categories": [
                "aesthetic",
                "city"
            ],
            "buyer_count": "0",
            "price_type": "fixed",
            "price_start": 1000,
            "price_end": 0,
            "price_fix": 0,
            "image_preview": "https://testing.pustakatropis.com/image_preview%20example%201",
            "created_at": "2025-03-24 17:23:34",
            "rating": 0
        },
        {
            "id": 2,
            "name": "product example 2",
            "tags": [
                "pohon",
                "dahan",
                "tanah"
            ],
            "categories": [
                "aesthetic",
                "city"
            ],
            "buyer_count": "0",
            "price_type": "range",
            "price_start": 1000,
            "price_end": 0,
            "price_fix": 0,
            "image_preview": "https://testing.pustakatropis.com/image_preview%20example%201",
            "created_at": "2025-03-24 17:23:34",
            "rating": 0
        },
        {
            "id": 3,
            "name": "product example 3",
            "tags": [
                "pohon",
                "dahan",
                "ranting"
            ],
            "categories": [
                "aesthetic",
                "nature"
            ],
            "buyer_count": "0",
            "price_type": "free",
            "price_start": 1000,
            "price_end": 0,
            "price_fix": 0,
            "image_preview": "https://testing.pustakatropis.com/image_preview%20example%201",
            "created_at": "2025-03-24 17:23:34",
            "rating": 0
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

