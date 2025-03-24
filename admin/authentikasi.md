# Dokumentasi API: Login Admin

## Endpoint
**POST** `/api/admin/auth/login`

## Deskripsi
Endpoint ini digunakan untuk login ke sistem admin dengan username dan password.

## Parameter

| Parameter   | Tipe    | Wajib | Deskripsi               |
|------------|--------|------|------------------------|
| username   | string | Ya   | Username admin         |
| password   | string | Ya   | Password admin         |

## Contoh Request

### HTTP Request
```http
POST /api/admin/auth/login HTTP/1.1
Host: your-api-domain.com
Content-Type: application/x-www-form-urlencoded

username=admin&password=password123
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Login berhasil"
}
```

### Gagal
Jika login gagal (misalnya username atau password salah), maka response akan seperti berikut:

**Status Code: 401**
```json
{
    "status": 401,
    "message": "Username atau password salah"
}
```

## Catatan
- Pastikan username dan password yang dikirimkan sesuai dengan yang terdaftar di sistem.
- Gunakan HTTPS untuk keamanan data.

---

# Dokumentasi API: Logout Admin

## Endpoint
**DELETE** `/api/admin/auth/logout`

## Deskripsi
Endpoint ini digunakan untuk logout dari sistem admin tanpa memerlukan token.

## Contoh Request

### HTTP Request
```http
DELETE /api/admin/auth/logout HTTP/1.1
Host: your-api-domain.com
```

## Response

### Berhasil
**Status Code: 200**
```json
{
    "status": 200,
    "message": "Logout berhasil"
}
```

## Catatan
- Logout tidak memerlukan token, cukup dengan memanggil endpoint yang tersedia.

---

# Dokumentasi API: Cek Login Admin

## Endpoint
**GET** `/api/admin/auth/check`

## Deskripsi
Endpoint ini digunakan untuk mengecek apakah admin sudah login atau belum.

## Contoh Request

### HTTP Request
```http
GET /api/admin/auth/check HTTP/1.1
Host: your-api-domain.com
```

## Response

### Sudah Login
**Status Code: 200**
```json
{
    "status": 200,
    "message": "User sedang login"
}
```

### Belum Login
**Status Code: 401**
```json
{
    "status": 401,
    "message": "User belum login"
}
```

## Catatan
- Endpoint `/api/admin/auth/check` digunakan untuk mengecek status login admin.
