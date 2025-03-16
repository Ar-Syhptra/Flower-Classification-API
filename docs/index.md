# Flower Classification API

## Deskripsi
Dokumentasi API untuk mengelola user dan data bunga dalam sistem.

## BASE URL
```
http://localhost:3000/api
```

## Autentikasi
API ini menggunakan autentikasi berbasis JWT ( Web Token). Setiap request yang memerlukan autentikasi harus menyertakan token di header `Authorization` dengan format:
```
Authorization: Bearer <token>
```

---

## Endpoints

### 1. Register User
**Method:** `POST`

**Endpoint:** `/auth/register`

#### Request Body:
```
{
  "username": "user123",
  "password": "password123"
}
```

#### Response:
- **201 Created**
  ```
  {
    "status": "success",
    "message": "User berhasil didaftarkan!",
    "data": {
      "id": 1,
      "username": "user123"
    }
  }
  ```
- **400 Bad Request**
  ```
  {
    "status": "error",
    "message": "Username sudah terdaftar, gunakan username yang lain!!"
  }
  ```
  ```
  {
    "status": "error",
    "message": "Username dan password wajib diisi!!"
  }
  ```
- **500 Internal Server Error**
  ```
  {
    "status": "error",
    "message": "Terjadi kesalahan pada server!!",
    "error": "err.message"
  }
  ```

---

### 2. Login User
**Method:** `POST`

**Endpoint:** `/auth/login`

#### Request Body:
```
{
  "username": "user123",
  "password": "password123"
}
```

#### Response:
- **200 OK**
  ```
  {
    "status": "success",
    "message": "Login berhasil!",
    "token": "jwt-token"
  }
  ```
- **400 Bad Request**
  ```
  {
    "status": "error",
    "message": "Username dan Password wajib diisi!!"
  }
  ```
- **401 Unauthorized**
  ```
  {
    "status": "error",
    "message": "Username atau password salah!!"
  }
  ```
- **500 Internal Server Error**
  ```
  {
    "status": "error",
    "message": "Terjadi kesalahan pada server!!",
    "error": "err.message"
  }
  ```

---

### 3. Mendapatkan Semua Data Bunga
**Method:** `GET`

**Endpoint:** `/flowers`

#### Headers:
```
Authorization: Bearer <token>
```

#### Response:
- **200 OK**
  ```
  {
    "status": "success",
    "message": "Data bunga berhasil diambil!",
    "data": [
      {
        "id": 1,
        "name": "Rose",
        "scientific_name": "Rosa",
        "description": "Bunga berwarna merah yang melambangkan cinta.",
        "health_uses": "Digunakan untuk minyak esensial",
        "culture_uses": "Sering digunakan dalam pernikahan",
        "sunlight_tips": "Membutuhkan sinar matahari penuh",
        "water_tips": "Disiram setiap hari",
        "soil_tips": "Tanah yang subur dan gembur",
        "habitat": "Taman dan kebun",
        "status": "Tumbuh dengan baik",
        "wikipedia": "https://en.wikipedia.org/wiki/Rose"
      }
    ]
  }
  ```
- **401 Unauthorized**
  ```
  {
    "status": "error",
    "message": "Akses ditolak. Token tidak ditemukan!!"
  }
  ```
- **500 Internal Server Error**
  ```
  {
    "status": "error",
    "message": "Terjadi kesalahan pada server!!",
    "error": "err.message"
  }
  ```

---

### 4. Menambahkan Data Bunga
**Method:** `POST`

**Endpoint:** `/flowers`

#### Headers:
```
Authorization: Bearer <token>
```

#### Request Body:
```
{
  "name": "string",
  "scientific_name": "string",
  "description": "string",
  "health_uses": "string",
  "culture_uses": "string",
  "sunlight_tips": "string",
  "water_tips": "string",
  "soil_tips": "string",
  "habitat": "string",
  "status": "string",
  "wikipedia": "string"
}
```

#### Response:
- **201 Created**
  ```
  {
    "status": "success",
    "message": "Data bunga berhasil ditambahkan!",
    "data": {
      "id": 1,
      "name": "string",
      "scientific_name": "string",
      "description": "string",
      "health_uses": "string",
      "culture_uses": "string",
      "sunlight_tips": "string",
      "water_tips": "string",
      "soil_tips": "string",
      "habitat": "string",
      "status": "string",
      "wikipedia": "string"
    }
  }
  ```
- **401 Unauthorized**
  ```
  {
    "status": "error",
    "message": "Akses ditolak. Token tidak ditemukan!!"
  }
  ```
- **500 Internal Server Error**
  ```
  {
    "status": "error",
    "message": "Terjadi kesalahan pada server!!",
    "error": "err.message"
  }
  ```

---

### 5. Mendapatkan Data Bunga Berdasarkan ID
**Method:** `GET`

**Endpoint:** `/flowers/{id}`

#### Headers:
```
Authorization: Bearer <token>
```

#### Response:
- **200 OK**
  ```
  {
    "status": "success",
    "message": "Data bunga berhasil diambil!",
    "data": {
      "id": 2,
      "name": "Sunflower",
      "scientific_name": "Helianthus annuus",
      "description": "Bunga besar yang mengikuti arah matahari.",
      "health_uses": "Minyak bijinya digunakan untuk kesehatan.",
      "culture_uses": "Melambangkan kebahagiaan dan kesetiaan.",
      "sunlight_tips": "Butuh sinar matahari penuh.",
      "water_tips": "Disiram secukupnya.",
      "soil_tips": "Tanah berpasir dengan drainase baik.",
      "habitat": "Padang rumput dan lahan pertanian.",
      "status": "Tumbuh subur",
      "wikipedia": "https://en.wikipedia.org/wiki/Sunflower"
    }
  }
  ```
- **404 Not Found**
  ```
  {
    "status": "error",
    "message": "Data bunga tidak ditemukan!!"
  }
  ```

- **500 Internal Server Error**
  ```
  {
    "status": "error",
    "message": "Terjadi kesalahan pada server!!",
    "error": "err.message"
  }
  ```

---
## Schema Table Data

### Table `Flower`
| Field            | Tipe Data | Deskripsi |
|-----------------|-----------|-----------|
| `id`           | integer   | ID unik bunga |
| `name`         | string    | Nama bunga |
| `scientific_name` | string    | Nama ilmiah bunga |
| `description`  | string    | Deskripsi bunga |
| `health_uses`  | string    | Manfaat kesehatan |
| `culture_uses` | string    | Kegunaan budaya |
| `sunlight_tips` | string    | Tips pencahayaan |
| `water_tips`   | string    | Tips penyiraman |
| `soil_tips`    | string    | Jenis tanah yang cocok |
| `habitat`      | string    | Habitat alami bunga |
| `status`       | string    | Status pertumbuhan |
| `wikipedia`    | string    | Link Wikipedia |

---

## Status Response
| Kode | Deskripsi |
|------|------------|
| 200  | OK |
| 201  | Created |
| 400  | Bad Request |
| 401  | Unauthorized |
| 404  | Not Found |
| 500  | Internal Server Error |

