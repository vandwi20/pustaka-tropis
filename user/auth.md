# Dokumentasi API Autentikasi

## Endpoint: `/api/user/auth`

### 1. Login
**Endpoint:** `POST /api/user/auth/login`

**Deskripsi:**
Digunakan untuk melakukan login pengguna.

**Request Body:**
```json
{
    "email": "user@example.com",
    "password": "password123"
}
```

**Response Sukses:**
```json
{
    "status": 200,
    "message": "Login berhasil"
}
```

**Response Gagal:**
- Jika email atau password salah:
```json
{
    "status": 400,
    "message": "Password salah"
}
```
- Jika email tidak ditemukan:
```json
{
    "status": 400,
    "message": "User tidak ditemukan"
}
```
- Jika sudah login sebelumnya:
```json
{
    "status": 200,
    "message": "Anda sudah login"
}
```

---

### 2. Cek Status Login
**Endpoint:** `GET /api/user/auth/check`

**Deskripsi:**
Digunakan untuk mengecek apakah pengguna sudah login atau belum.

**Response Jika Sudah Login:**
```json
{
    "status": 200,
    "message": "Anda sudah login"
}
```

**Response Jika Belum Login:**
```json
{
    "status": 400,
    "message": "Anda belum login"
}
```

---

### 3. Logout
**Endpoint:** `DELETE /api/user/auth/logout`

**Deskripsi:**
Digunakan untuk melakukan logout pengguna.

**Response Sukses:**
```json
{
    "status": 200,
    "message": "Berhasil logout"
}
```

**Response Jika Tidak Login:**
```json
{
    "status": 400,
    "message": "Anda tidak login"
}
```

---

### 4. Registrasi
**Endpoint:** `POST /api/user/auth/register`

**Deskripsi:**
Digunakan untuk mendaftarkan pengguna baru.

**Request Body:**
```json
{
    "name": "John Doe",
    "email": "johndoe@example.com",
    "password": "password123"
}
```

**Response Sukses:**
```json
{
    "status": 201,
    "message": "Berhasil registrasi"
}
```

**Response Gagal:**
- Jika data tidak lengkap atau tidak valid:
```json
{
    "status": 400,
    "message": "Validation errors",
    "errors": {
        "email": "Email sudah terdaftar"
    }
}
```

---

### 5. Detail Pengguna
**Endpoint:** `GET /api/user/auth/detail`

**Deskripsi:**
Digunakan untuk mendapatkan informasi pengguna yang sedang login.

**Response Jika Berhasil:**
```json
{
    "id": 1,
    "name": "John Doe",
    "email": "johndoe@example.com",
    "created_at": "2024-03-22 12:00:00",
    "updated_at": "2024-03-22 12:30:00"
}
```

**Response Jika Belum Login:**
```json
{
    "status": 400,
    "message": "Anda belum login"
}
```


