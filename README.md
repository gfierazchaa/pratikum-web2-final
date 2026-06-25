# praktikum-web2-final

**Nama :** Ghefira Azka Fardani

**NIM :** 312410521

**Kelas :** I241E

**Mata Kuliah :** Pemrograman Web

---

# 📌 Deskripsi Praktikum

Laporan akhir praktikum ini merupakan gabungan dari beberapa materi yang telah dipelajari selama perkuliahan Pemrograman Web, yaitu implementasi Frontend menggunakan VueJS, Backend menggunakan CodeIgniter 4, serta pengelolaan database MySQL.

Pada praktikum ini dikembangkan aplikasi pengelolaan artikel yang dapat melakukan operasi Create, Read, Update, dan Delete (CRUD) melalui REST API serta menampilkan data secara dinamis menggunakan VueJS.

---

# 🎯 Tujuan Praktikum

* Memahami konsep Single Page Application (SPA).
* Memahami penggunaan VueJS pada sisi frontend.
* Memahami pembuatan REST API menggunakan CodeIgniter 4.
* Memahami komunikasi data menggunakan Axios.
* Memahami pengelolaan database MySQL.
* Mengimplementasikan CRUD berbasis API.

---

# 🛠️ Teknologi yang Digunakan

## Frontend

* HTML5
* CSS3
* JavaScript
* VueJS
* Vue Router
* Axios

## Backend

* PHP
* CodeIgniter 4
* REST API

## Database

* MySQL
* phpMyAdmin

---

# 📂 Struktur Project

```text
Laporan-Akhir-Praktikum/
│
├── lab8_vuejs/
│   ├── assets/
│   │   ├── css/
│   │   └── js/
│   │       └── components/
│   └── index.html
│
├── lab11_ci4/
│   └── ci4/
│       ├── app/
│       │   ├── Controllers/
│       │   ├── Models/
│       │   ├── Views/
│       │   └── Config/
│       └── public/
│
└── lab_ci4.sql
```

---

# 📖 Praktikum 1 : Frontend Menggunakan VueJS

## Pengertian VueJS

VueJS merupakan framework JavaScript yang digunakan untuk membangun antarmuka pengguna secara interaktif dan responsif.

Pada praktikum ini VueJS digunakan untuk menampilkan halaman aplikasi secara dinamis tanpa perlu melakukan reload halaman.

---

## Struktur Komponen VueJS

Contoh komponen:

```javascript
const Home = {
    template: `
        <div>
            <h2>Home</h2>
            <p>Selamat datang di aplikasi VueJS</p>
        </div>
    `
}
```

### Penjelasan

* `template` digunakan untuk menampilkan tampilan HTML.
* Komponen dapat digunakan kembali pada halaman lain.
* VueJS akan merender tampilan secara otomatis.

---

## Vue Router

Contoh penggunaan routing:

```javascript
const routes = [
    { path: '/', component: Home },
    { path: '/artikel', component: Artikel },
    { path: '/about', component: About }
];
```

### Penjelasan

* Route digunakan untuk menghubungkan URL dengan komponen.
* Saat URL berubah, VueJS akan menampilkan komponen yang sesuai.
* Membentuk konsep Single Page Application (SPA).

---

## Axios

Contoh mengambil data dari API:

```javascript
axios.get(apiUrl)
    .then(response => {
        this.artikel = response.data.artikel;
    });
```

### Penjelasan

* Axios digunakan untuk mengakses REST API.
* Data dari server diterima dalam format JSON.
* Data kemudian ditampilkan ke halaman VueJS.

---

# 📖 Praktikum 2 : Backend Menggunakan CodeIgniter 4

## Pengertian CodeIgniter 4

CodeIgniter 4 merupakan framework PHP yang menerapkan konsep MVC (Model View Controller) untuk mempermudah pengembangan aplikasi web.

---

## Controller

Contoh controller:

```php
class Artikel extends BaseController
{
    public function index()
    {
        return view('artikel/index');
    }
}
```

### Penjelasan

* Controller berfungsi mengatur logika aplikasi.
* Menghubungkan Model dan View.
* Menentukan proses yang dijalankan saat URL diakses.

---

## Model

Contoh model:

```php
class ArtikelModel extends Model
{
    protected $table = 'artikel';
}
```

### Penjelasan

* Model digunakan untuk mengakses database.
* Menyimpan query dan pengolahan data.
* Mempermudah proses CRUD.

---

## View

Contoh view:

```php
<h2>Daftar Artikel</h2>
```

### Penjelasan

* View digunakan untuk menampilkan data kepada pengguna.
* Berisi kode HTML dan tampilan aplikasi.

---

# 📖 Praktikum 3 : REST API

## Pengertian REST API

REST API merupakan layanan yang memungkinkan pertukaran data antara frontend dan backend menggunakan format JSON.

---

## Method GET

Digunakan untuk mengambil data.

```php
public function index()
{
    return $this->respond($this->model->findAll());
}
```

### Penjelasan

* Mengambil seluruh data artikel.
* Mengirimkan data dalam format JSON.

---

## Method POST

Digunakan untuk menambah data.

```php
$data = [
    'judul' => $this->request->getVar('judul'),
    'isi' => $this->request->getVar('isi')
];
```

### Penjelasan

* Data dikirim dari frontend atau Postman.
* Data disimpan ke database.

---

## Method PUT

Digunakan untuk mengubah data.

```php
$this->model->update($id, $data);
```

### Penjelasan

* Memperbarui data berdasarkan ID.
* Data lama diganti dengan data baru.

---

## Method DELETE

Digunakan untuk menghapus data.

```php
$this->model->delete($id);
```

### Penjelasan

* Menghapus data dari database.
* Data tidak lagi tersedia pada sistem.

---

# 🗄️ Database

Database yang digunakan bernama:

```sql
lab_ci4
```

Tabel utama yang digunakan:

## Tabel Artikel

```sql
CREATE TABLE artikel (
    id INT PRIMARY KEY,
    judul VARCHAR(200),
    isi TEXT,
    gambar VARCHAR(200)
);
```

### Fungsi

* Menyimpan data artikel.
* Menyimpan judul artikel.
* Menyimpan isi artikel.
* Menyimpan gambar artikel.

---

## Tabel Kategori

```sql
CREATE TABLE kategori (
    id_kategori INT PRIMARY KEY,
    nama_kategori VARCHAR(100)
);
```

### Fungsi

* Mengelompokkan artikel berdasarkan kategori.
* Mempermudah pencarian data.

---

# 🔄 Alur Sistem

```text
Database MySQL
       ▲
       │
       ▼
CodeIgniter 4 REST API
       ▲
       │
       ▼
Axios
       ▲
       │
       ▼
VueJS Frontend
       ▲
       │
       ▼
User
```

### Penjelasan

1. User mengakses aplikasi.
2. VueJS mengirim request ke API menggunakan Axios.
3. REST API memproses request.
4. Data diambil dari database.
5. Data dikembalikan dalam format JSON.
6. VueJS menampilkan data ke pengguna.

---

# 🚀 Cara Menjalankan Project

## Menjalankan Database

1. Buka phpMyAdmin.
2. Buat database baru dengan nama:

```sql
lab_ci4
```

3. Import file:

```text
lab_ci4.sql
```

---

## Menjalankan Backend

Masuk ke folder:

```bash
cd lab11_ci4/ci4
```

Jalankan:

```bash
php spark serve
```

Server berjalan pada:

```text
http://localhost:8080
```

---

## Menjalankan Frontend

Buka folder:

```text
lab8_vuejs
```

Kemudian jalankan menggunakan Live Server atau web server lokal.

---

# 📝 Kesimpulan

Praktikum ini berhasil mengimplementasikan konsep Frontend dan Backend modern menggunakan VueJS dan CodeIgniter 4. VueJS digunakan untuk membangun antarmuka yang interaktif, sedangkan CodeIgniter 4 digunakan untuk membangun REST API yang terhubung dengan database MySQL. Melalui praktikum ini diperoleh pemahaman mengenai konsep MVC, REST API, CRUD, serta komunikasi data antara frontend dan backend menggunakan Axios.
