<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/27/PHP-logo.svg" width="100" alt="PHP Logo">
  <img src="https://www.svgrepo.com/show/353579/codeigniter.svg" width="100" alt="CodeIgniter 4 Logo">
</div>

# 📌 Laporan Lengkap Praktikum 1-3 & 7

Dokumen ini adalah laporan komprehensif untuk praktikum 1, 2, 3, dan 7 dalam mata kuliah Pemrograman Website 2. Setiap sesi praktikum mengupas tuntas konsep-konsep fundamental hingga implementasi praktis menggunakan framework CodeIgniter 4.

Dalam seri praktikum ini, mahasiswa dibimbing untuk memahami konsep dasar framework, arsitektur MVC (Model-View-Controller), dan diharapkan mampu merancang aplikasi web fungsional dengan CodeIgniter 4. Semua tahapan, mulai dari instalasi, konfigurasi awal, pengembangan fitur CRUD, routing, hingga pemanfaatan View Layout dan View Cell, dibahas secara mendetail.

Laporan ini dilengkapi dengan screenshot dari hasil implementasi untuk mempermudah pemahaman dan sebagai bukti penyelesaian setiap tugas. Setelah menyelesaikan seluruh praktikum, mahasiswa diharapkan memiliki kompetensi untuk membangun aplikasi web yang terstruktur, efisien, dan modular.

## 🔗 Daftar Isi

| No  | Praktikum                                  | Link                                                     |
| --- | ------------------------------------------ | -------------------------------------------------------- |
| 1   | Praktikum 1: Pengenalan PHP Framework (CodeIgniter 4) | [Klik di sini](#praktikum-1-php-framework-codeigniter-4) |
| 2   | Praktikum 2: Framework Lanjutan (CRUD)     | [Klik di sini](#praktikum-2-framework-lanjutan-crud)     |
| 3   | Praktikum 3: View Layout dan View Cell     | [Klik di sini](#praktikum-3-view-layout-dan-view-cell)   |
| 4   | Praktikum 7: Relasi Tabel dan Query Builder| [Klik di sini](#praktikum-7-Relasi-Tabel-dan-Query-Builder) |

## 👤 Profil Mahasiswa

| Atribut         | Keterangan            |
| --------------- | --------------------- |
| **Nama**        | Ihsan Rangga          |
| **NIM**         | 312310494             |
| **Kelas**       | TI.23.A.5             |
| **Mata Kuliah** | Pemrograman Website 2 |

---

# Praktikum 1: PHP Framework (CodeIgniter 4)

## 🎯 Tujuan Praktikum

- Mengerti konsep dasar dari sebuah Framework.
- Mengenal arsitektur Model-View-Controller (MVC).
- Membangun aplikasi sederhana menggunakan CodeIgniter 4.
- Mengimplementasikan sistem routing dan controller.
- Mendesain tampilan antarmuka dengan View dan Layout CSS.

---

## ⚙️ Langkah-Langkah Praktikum

### 📌 1. Persiapan Awal

🔹 Mengaktifkan ekstensi PHP yang dibutuhkan di file `php.ini`.
🔹 Melakukan restart pada layanan Apache melalui XAMPP Control Panel.

📷 **Screenshot Konfigurasi PHP.ini:**

![alt text](<gambar/image.png>)

---

### 📌 2. Instalasi CodeIgniter 4

🔹 Unduh CodeIgniter 4 dari [website resminya](https://codeigniter.com/download).
🔹 Ekstrak file ke dalam direktori `htdocs/lab11_ci/`.
🔹 Ubah nama folder menjadi `ci4` untuk kemudahan akses.
🔹 Buka `http://localhost/lab11_ci/ci4/public/` untuk memverifikasi instalasi.

📷 **Screenshot Tampilan Awal CodeIgniter 4:**

![alt text](<gambar/image-1.png>)

---

### 📌 3. Menjalankan CLI (Command Line Interface)

```bash
cd xampp/htdocs/lab11_ci/ci4/
php spark
```

📷 **Screenshot Hasil Perintah CLI:**

![alt text](<gambar/image-2.png>)
---

### 📌 4. Mengaktifkan Mode Debugging

```bash
# Buka file .env dan modifikasi baris berikut:
CI_ENVIRONMENT = development
```

📷 **Screenshot Konfigurasi Debugging:**

![alt text](<gambar/image-3.png>)

---

### 📌 5. Membuat Route Baru

Tambahkan kode berikut pada file `app/config/Routes.php`:

```php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```

```bash
php spark routes
```

📷 **Screenshot Halaman Error:**

![alt text](<gambar/image-4.png>)
---

### 📌 6. Membuat Controller Page

Buat file `Page.php` di direktori `app/Controllers/`:

```php
<?php
namespace App\Controllers;
class Page extends BaseController {
    public function about() { echo "Ini adalah halaman About"; }
    public function contact() { echo "Ini adalah halaman Contact"; }
    public function faqs() { echo "Ini adalah halaman FAQ"; }
}
```

📷 **Screenshot Tampilan Halaman About:**

![alt text](<gambar/image-5.png>)

---

### 📌 7. Membuat View

Buat file `app/Views/about.php`:

```php
<!DOCTYPE html>
<html>
<head>
    <title><?= $title; ?></title>
</head>
<body>
    <h1><?= $title; ?></h1>
    <p><?= $content; ?></p>
</body>
</html>
```

📷 **Screenshot Tampilan View About:**

![alt text](<gambar/image-6.png>)
---

### 📌 8. Membuat Layout Web dengan CSS

- Simpan file `style.css` di dalam folder `public/`
- Buat `header.php` dan `footer.php` di `app/Views/template/`
- Modifikasi `about.php` untuk menggunakan `include`:

```php
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```

📷 **Screenshot :**

![alt text](<gambar/image-7.png>)

### 📌 9. 🚀 Menambahkan Halaman Baru (Services & Artikel)

Untuk menyempurnakan website, halaman `Services` dan `Artikel` ditambahkan untuk menyajikan informasi yang relevan.

🛠 **Langkah 1: Menambahkan Route**
Tambahkan route baru di `app/Config/Routes.php`:

```php
$routes->get('/services', 'Page::services');
$routes->get('/artikel', 'Page::artikel');
```

📝 **Langkah 2: Membuat Method di Controller**
Tambahkan method `services()` dan `artikel()` di `app/Controllers/Page.php`:

```php
public function services() {
    return view('services', [
        'title' => '💼 Halaman Layanan Kami',
        'content' => 'Kami menyediakan berbagai layanan, mulai dari konsultasi IT hingga pengembangan software.'
    ]);
}

public function artikel() {
    return view('artikel', [
        'title' => '📰 Halaman Artikel Terbaru',
        'content' => 'Selamat datang di halaman artikel. Di sini Anda dapat membaca berbagai tulisan menarik.'
    ]);
}
```

🎨 **Langkah 3: Membuat View**
Buat file `app/Views/services.php` dan `app/Views/artikel.php`:

```php
// services.php
<?= $this->include('template/header'); ?>
<h1>🛠 <?= $title; ?></h1>
<p>📌 <?= $content; ?></p>
<?= $this->include('template/footer'); ?>

// artikel.php
<?= $this->include('template/header'); ?>
<h1>📰 <?= $title; ?></h1>
<p>📖 <?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```

🌐 **Langkah 4: Mengakses Halaman**
Buka browser dan akses URL berikut:
`http://localhost:8080/services`
`http://localhost:8080/artikel`

📷 **Screenshot Halaman Services & Artikel:**

![alt text](<gambar/image-8.png>)
![alt text](<gambar/image-9.png>)

✅ **Kesimpulan Praktikum 1**

Dari praktikum ini, telah dipelajari dasar-dasar penggunaan framework CodeIgniter 4, mencakup:
-   Struktur direktori dan konfigurasi awal.
-   Menjalankan aplikasi melalui Command Line Interface (CLI).
-   Pembuatan dan pengelolaan routing untuk halaman web.
-   Penggunaan Controller dan View untuk menyajikan konten dinamis.
-   Implementasi layout terstruktur dengan header dan footer.
-   Penambahan halaman baru (Services dan Artikel) untuk melengkapi fungsionalitas website.

Praktikum ini memberikan wawasan mendalam tentang bagaimana CodeIgniter 4 menyederhanakan proses pengembangan aplikasi web. Framework ini menyediakan struktur yang rapi, efisien, dan fleksibel, yang sangat berguna untuk membangun aplikasi web secara lebih profesional. 🚀🔥

---

# Praktikum 2: Framework Lanjutan (CRUD)

## Tujuan

1. Mahasiswa dapat memahami konsep dasar dari Model.
2. Mahasiswa dapat memahami konsep dasar dari operasi CRUD.
3. Mahasiswa dapat membuat aplikasi sederhana menggunakan Framework Codeigniter4.

## Langkah-langkah Praktikum

### 1. Membuat Database & Tabel

```sql
CREATE DATABASE lab_ci4;

CREATE TABLE artikel (
    id INT(11) auto_increment,
    judul VARCHAR(200) NOT NULL,
    isi TEXT,
    gambar VARCHAR(200),
    status TINYINT(1) DEFAULT 0,
    slug VARCHAR(200),
    PRIMARY KEY(id)
);
```

![alt text](<gambar/image-10.png>)

### 2. Konfigurasi Koneksi Database

Konfigurasi koneksi dilakukan pada file `.env`.

![alt text](<gambar/image-11.png>)

### 3. Membuat Model

Buat file `ArtikelModel.php` pada direktori `app/Models`.

```php
<?php
namespace App\Models;
use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}
```

![alt text](<gambar/image-12.png>)

### 4. Membuat Controller

Buat Controller `Artikel.php` pada direktori `app/Controllers`.

```php
<?php
namespace App\Controllers;
use App\Models\ArtikelModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/index', compact('artikel', 'title'));
    }
}
```

![alt text](<gambar/image-13.png>)

### 5. Membuat View

Buat file `index.php` di dalam `app/views/artikel`.

```php
<?= $this->include('template/header'); ?>

<?php if($artikel): foreach($artikel as $row): ?>
<article class="entry">
    <h2><a href="<?= base_url('/artikel/' . $row['slug']);?>"><?= $row['judul']; ?></a></h2>
    <img src="<?= base_url('/gambar/' . $row['gambar']);?>" alt="<?= $row['judul']; ?>">
    <p><?= substr($row['isi'], 0, 200); ?></p>
</article>
<hr class="divider" />
<?php endforeach; else: ?>
<article class="entry">
    <h2>Belum ada data tersedia.</h2>
</article>
<?php endif; ?>

<?= $this->include('template/footer'); ?>
```

![alt text](<gambar/image-14.png>)

### 6. Menambahkan Data & Menampilkan Detail

Data ditambahkan ke dalam database dan fungsi `view($slug)` dibuat di controller untuk menampilkan detail dari setiap artikel.

![alt text](<gambar/image-15.png>)
![alt text](<gambar/image-16.png>)

### 7. Membuat Menu Admin (CRUD)

- Buat method `admin_index()`, `add()`, `edit()`, dan `delete()` pada Controller `Artikel`.
- Buat view untuk `admin_index`, `form_add`, dan `form_edit`.
- Tambahkan routing untuk semua fungsi admin.

![alt text](<gambar/image-17.png>)
![alt text](<gambar/image-18.png>)
![alt text](<gambar/image-19.png>)

---

# Praktikum 3: View Layout dan View Cell

## Tujuan

1. Mengerti konsep View Layout di CodeIgniter 4.
2. Menggunakan View Layout untuk membuat template yang konsisten.
3. Mengimplementasikan View Cell untuk komponen yang modular.

## Langkah-langkah Praktikum

### 1. Membuat Layout Utama

Buat file `main.php` di dalam `app/Views/layout/`.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title ?? 'Website Saya' ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
        <header>
            <h1>Layout Utama Website</h1>
        </header>
        <nav>
            <a href="<?= base_url('/');?>" class="active">Home</a>
            <a href="<?= base_url('/artikel');?>">Artikel</a>
            <a href="<?= base_url('/about');?>">About</a>
            <a href="<?= base_url('/contact');?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main">
                <?= $this->renderSection('content') ?>
            </section>
            <aside id="sidebar">
                <?= view_cell('App\\Cells\\ArtikelTerkini::render') ?>
            </aside>
        </section>
        <footer>
            <p>&copy; 2024 - Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```


### 2. Modifikasi View

Ubah file view seperti `home.php` agar dapat menggunakan layout yang baru dibuat.

```php
<?= $this->extend('layout/main') ?>
<?= $this->section('content') ?>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
<?= $this->endSection() ?>
```


### 3. Membuat View Cell

Buat class `ArtikelTerkini.php` di `app/Cells/` dan view `artikel_terkini.php` di `app/Views/components/`.


### 4. Modifikasi Database & Model

Tambahkan kolom `created_at` pada tabel `artikel` dan perbarui `allowedFields` di `ArtikelModel`.

```sql
ALTER TABLE artikel ADD COLUMN created_at DATETIME DEFAULT CURRENT_TIMESTAMP;
UPDATE artikel SET created_at = CURRENT_TIMESTAMP;
```


### 5. Hasil Akhir

Akses halaman utama untuk melihat tampilan dengan layout dan view cell yang baru diimplementasikan.

![alt text](<gambar/image-20.png>)

---

## Pertanyaan dan Jawaban

### 1. Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi?

Manfaat utamanya adalah **Reusability** (kode dapat digunakan kembali) dan **Konsistensi Tampilan**. Dengan layout, kita hanya perlu mendefinisikan struktur utama (seperti header, footer, sidebar) satu kali dan menerapkannya di banyak halaman. Ini membuat kode lebih rapi dan pemeliharaan menjadi lebih mudah.

### 2. Jelaskan perbedaan antara View Cell dan View biasa.

| Fitur       | View Cell                                       | View Biasa                               |
|-------------|-------------------------------------------------|------------------------------------------|
| **Tujuan**  | Komponen UI kecil yang dapat digunakan kembali   | Menampilkan halaman penuh atau bagian besar dari halaman |
| **Logika**  | Memiliki class tersendiri untuk mengambil data     | Menerima data langsung dari Controller            |
| **Contoh**  | Sidebar artikel terkini, widget, keranjang belanja | Halaman home, detail produk, halaman kontak |

### 3. Ubah View Cell agar hanya menampilkan post dengan kategori tertentu.

Untuk melakukan ini, kita bisa memodifikasi method `render` di class Cell untuk menerima parameter kategori, lalu menggunakannya untuk memfilter data dari model.

```php
// Panggilan di view
<?= view_cell('App\\Cells\\ArtikelTerkini::render', ['kategori' => 'tutorial']) ?>

// Modifikasi di class ArtikelTerkini
public function render(string $kategori = null)
{
    $model = new ArtikelModel();
    if ($kategori) {
        $model->where('kategori', $kategori);
    }
    $artikel = $model->orderBy('created_at', 'DESC')->limit(5)->findAll();
    return view('components/artikel_terkini', ['artikel' => $artikel]);
}
```

## Kesimpulan

Dalam rangkaian praktikum ini, saya telah berhasil mengimplementasikan konsep-konsep kunci dalam CodeIgniter 4, mulai dari dasar-dasar MVC, routing, hingga fitur-fitur lanjutan seperti CRUD, View Layout, dan View Cell. Penggunaan View Layout sangat membantu dalam menciptakan tampilan yang konsisten, sementara View Cell menyediakan cara yang efisien untuk mengelola komponen UI yang dapat digunakan kembali. Melalui praktikum ini, saya mendapatkan pemahaman yang lebih baik tentang cara membangun aplikasi web yang terstruktur, modular, dan mudah dikelola.


# Praktikum 7: Relasi Tabel dan Query Builder

## Deskripsi

Praktikum ini adalah kelanjutan dari praktikum sebelumnya yang berfokus pada implementasi relasi antar tabel dalam database menggunakan CodeIgniter 4. Pada praktikum ini, saya mempelajari cara membuat relasi One-to-Many antara tabel kategori dan artikel, serta menggunakan Query Builder untuk melakukan join tabel.

## Tujuan Praktikum

1. Memahami konsep relasi antar tabel dalam sebuah database.
2. Mengimplementasikan relasi One-to-Many.
3. Melakukan query dengan join tabel menggunakan Query Builder.
4. Menampilkan data dari tabel yang saling berelasi.

## Langkah-langkah Praktikum

### 1. Persiapan Database

Memastikan server MySQL berjalan dan membuka database `lab_ci4`.

### 2. Membuat Tabel Kategori

Membuat tabel baru bernama `kategori` dengan struktur sebagai berikut:

- `id_kategori` (INT, PRIMARY KEY, AUTO_INCREMENT)
- `nama_kategori` (VARCHAR 100)
- `slug_kategori` (VARCHAR 100)

**Query SQL:**

```sql
CREATE TABLE kategori (
    id_kategori INT(11) AUTO_INCREMENT,
    nama_kategori VARCHAR(100) NOT NULL,
    slug_kategori VARCHAR(100),
    PRIMARY KEY (id_kategori)
);
```

**Screenshot:**
![alt text](<gambar/image-24.png>)

### 3. Modifikasi Tabel Artikel

Menambahkan foreign key `id_kategori` pada tabel `artikel` untuk menciptakan relasi dengan tabel `kategori`.

**Query SQL:**

```sql
ALTER TABLE artikel
ADD COLUMN id_kategori INT(11),
ADD CONSTRAINT fk_kategori_artikel
FOREIGN KEY (id_kategori) REFERENCES kategori(id_kategori);
```


### 4. Membuat Model Kategori

Membuat file `KategoriModel.php` di folder `app/Models/` untuk mengelola data dari tabel kategori.

**Kode KategoriModel.php:**

```php
<?php
namespace App\Models;
use CodeIgniter\Model;

class KategoriModel extends Model
{
    protected $table = 'kategori';
    protected $primaryKey = 'id_kategori';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['nama_kategori', 'slug_kategori'];
}
```


### 5. Modifikasi Model Artikel

Memodifikasi `ArtikelModel.php` dengan menambahkan method `getArtikelDenganKategori()` untuk melakukan join dengan tabel `kategori`.

**Kode ArtikelModel.php:**

```php
<?php
namespace App\Models;
use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar', 'id_kategori'];

    public function getArtikelDenganKategori()
    {
        return $this->db->table('artikel')
            ->select('artikel.*, kategori.nama_kategori')
            ->join('kategori', 'kategori.id_kategori = artikel.id_kategori')
            ->get()
            ->getResultArray();
    }
}
```


### 6. Modifikasi Controller Artikel

Memperbarui controller `Artikel.php` untuk:

- Menggunakan method join dari model yang telah dibuat.
- Menambahkan fungsionalitas filter berdasarkan kategori.
- Menangani data kategori pada form tambah dan edit artikel.

**Kode Controller Artikel.php:**

```php
<?php
namespace App\Controllers;
use App\Models\ArtikelModel;
use App\Models\KategoriModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->getArtikelDenganKategori(); // Menggunakan method baru
        return view('artikel/index', compact('artikel', 'title'));
    }

    public function admin_index()
    {
        $title = 'Daftar Artikel (Admin)';
        $model = new ArtikelModel();

        // Ambil keyword pencarian
        $q = $this->request->getVar('q') ?? '';

        // Ambil filter kategori
        $kategori_id = $this->request->getVar('kategori_id') ?? '';

        $data = [
            'title' => $title,
            'q' => $q,
            'kategori_id' => $kategori_id,
        ];

        // Membangun query
        $builder = $model->table('artikel')
            ->select('artikel.*, kategori.nama_kategori')
            ->join('kategori', 'kategori.id_kategori = artikel.id_kategori');

        // Terapkan filter pencarian jika ada keyword
        if ($q != '') {
            $builder->like('artikel.judul', $q);
        }

        // Terapkan filter kategori jika kategori_id dipilih
        if ($kategori_id != '') {
            $builder->where('artikel.id_kategori', $kategori_id);
        }

        // Terapkan pagination
        $data['artikel'] = $builder->paginate(10);
        $data['pager'] = $model->pager;

        // Ambil semua kategori untuk dropdown filter
        $kategoriModel = new KategoriModel();
        $data['kategori'] = $kategoriModel->findAll();

        return view('artikel/admin_index', $data);
    }

    public function add()
    {
        // Validasi...
        if ($this->request->getMethod() == 'post' && $this->validate([
            'judul' => 'required',
            'id_kategori' => 'required|integer' // Pastikan id_kategori wajib diisi dan berupa integer
        ])) {
            $model = new ArtikelModel();
            $model->insert([
                'judul' => $this->request->getPost('judul'),
                'isi' => $this->request->getPost('isi'),
                'slug' => url_title($this->request->getPost('judul')),
                'id_kategori' => $this->request->getPost('id_kategori')
            ]);
            return redirect()->to('/admin/artikel');
        } else {
            $kategoriModel = new KategoriModel();
            $data['kategori'] = $kategoriModel->findAll(); // Ambil kategori untuk form
            $data['title'] = "Tambah Artikel";
            return view('artikel/form_add', $data);
        }
    }

    public function edit($id)
    {
        $model = new ArtikelModel();
        if ($this->request->getMethod() == 'post' && $this->validate([
            'judul' => 'required',
            'id_kategori' => 'required|integer'
        ])) {
            $model->update($id, [
                'judul' => $this->request->getPost('judul'),
                'isi' => $this->request->getPost('isi'),
                'id_kategori' => $this->request->getPost('id_kategori')
            ]);
            return redirect()->to('/admin/artikel');
        } else {
            $data['artikel'] = $model->find($id);
            $kategoriModel = new KategoriModel();
            $data['kategori'] = $kategoriModel->findAll(); // Ambil kategori untuk form
            $data['title'] = "Edit Artikel";
            return view('artikel/form_edit', $data);
        }
    }

    public function delete($id)
    {
        $model = new ArtikelModel();
        $model->delete($id);
        return redirect()->to('/admin/artikel');
    }

    public function view($slug)
    {
        $model = new ArtikelModel();
        $data['artikel'] = $model->where('slug', $slug)->first();
        if (empty($data['artikel'])) {
            throw new \CodeIgniter\Exceptions\PageNotFoundException('Artikel tidak dapat ditemukan.');
        }
        $data['title'] = $data['artikel']['judul'];
        return view('artikel/detail', $data);
    }
}
```


### 7. Modifikasi View

#### a. index.php (Halaman Depan)

Menampilkan daftar artikel beserta nama kategorinya.

**Kode index.php:**

```php
<?= $this->include('template/header'); ?>
<?php if ($artikel): foreach ($artikel as $row): ?>
<article class="entry">
    <h2><a href="<?= base_url('/artikel/' . $row['slug']); ?>"><?= $row['judul']; ?></a></h2>
    <p>Kategori: <?= $row['nama_kategori'] ?></p>
    <img src="<?= base_url('/gambar/' . $row['gambar']); ?>" alt="<?= $row['judul']; ?>">
    <p><?= substr($row['isi'], 0, 200); ?></p>
</article>
<hr class="divider" />
<?php endforeach; else: ?>
<article class="entry">
    <h2>Belum ada data yang tersedia.</h2>
</article>
<?php endif; ?>
<?= $this->include('template/footer'); ?>
```

#### b. admin_index.php (Halaman Admin)

Menambahkan:

- Filter berdasarkan kategori.
- Kolom kategori pada tabel.
- Dropdown untuk memfilter artikel.

**Kode admin_index.php:**

```php
<?= $this->include('template/admin_header'); ?>
<h2><?= $title; ?></h2>
<div class="row mb-3">
    <div class="col-md-6">
        <form method="get" class="form-inline">
            <input type="text" name="q" value="<?= $q; ?>" placeholder="Cari judul artikel" class="form-control mr-2">
            <select name="kategori_id" class="form-control mr-2">
                <option value="">Semua Kategori</option>
                <?php foreach ($kategori as $k): ?>
                <option value="<?= $k['id_kategori']; ?>" <?= ($kategori_id == $k['id_kategori']) ? 'selected' : ''; ?>><?= $k['nama_kategori']; ?></option>
                <?php endforeach; ?>
            </select>
            <input type="submit" value="Cari" class="btn btn-primary">
        </form>
    </div>
</div>
<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Kategori</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
        <?php if (count($artikel) > 0): ?>
        <?php foreach ($artikel as $row): ?>
        <tr>
            <td><?= $row->id; ?></td>
            <td>
                <b><?= $row->judul; ?></b>
                <p><small><?= substr($row->isi, 0, 50); ?></small></p>
            </td>
            <td><?= $row->nama_kategori; ?></td>
            <td><?= $row->status; ?></td>
            <td>
                <a class="btn btn-sm btn-info" href="<?= base_url('/admin/artikel/edit/' . $row->id); ?>">Ubah</a>
                <a class="btn btn-sm btn-danger" onclick="return confirm('Anda yakin ingin menghapus data ini?');" href="<?= base_url('/admin/artikel/delete/' . $row->id); ?>">Hapus</a>
            </td>
        </tr>
        <?php endforeach; ?>
        <?php else: ?>
        <tr>
            <td colspan="5">Tidak ada data ditemukan.</td>
        </tr>
        <?php endif; ?>
    </tbody>
</table>
<?= $pager->only(['q', 'kategori_id'])->links(); ?>
<?= $this->include('template/admin_footer'); ?>
```

**Screenshot:**
![alt text](<gambar/image-21.png>)

#### c. form_add.php (Form Tambah Artikel)

Menambahkan dropdown untuk memilih kategori saat membuat artikel baru.

**Kode form_add.php:**

```php
<?= $this->include('template/admin_header'); ?>
<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <label for="judul">Judul</label>
        <input type="text" name="judul" id="judul" required>
    </p>
    <p>
        <label for="isi">Isi</label>
        <textarea name="isi" id="isi" cols="50" rows="10"></textarea>
    </p>
    <p>
        <label for="id_kategori">Kategori</label>
        <select name="id_kategori" id="id_kategori" required>
            <?php foreach($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>"><?= $k['nama_kategori']; ?></option>
            <?php endforeach; ?>
        </select>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>
<?= $this->include('template/admin_footer'); ?>
```

**Screenshot:**
![alt text](<gambar/image-22.png>)

#### d. form_edit.php (Form Edit Artikel)

Menambahkan dropdown kategori dengan nilai yang sudah terpilih sesuai dengan data artikel yang sedang diedit.

**Kode form_edit.php:**

```php
<?= $this->include('template/admin_header'); ?>
<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <label for="judul">Judul</label>
        <input type="text" name="judul" value="<?= $artikel['judul']; ?>" id="judul" required>
    </p>
    <p>
        <label for="isi">Isi</label>
        <textarea name="isi" id="isi" cols="50" rows="10"><?= $artikel['isi']; ?></textarea>
    </p>
    <p>
        <label for="id_kategori">Kategori</label>
        <select name="id_kategori" id="id_kategori" required>
            <?php foreach($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>" <?= ($artikel['id_kategori'] == $k['id_kategori']) ? 'selected' : ''; ?>><?= $k['nama_kategori']; ?></option>
            <?php endforeach; ?>
        </select>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>
<?= $this->include('template/admin_footer'); ?>
```

**Screenshot:**
![alt text](<gambar/image-23.png>)

## Konsep yang Dipelajari

### 1. Relasi Database

- **Relasi One-to-Many**: Satu kategori dapat memiliki banyak artikel.
- **Foreign Key**: Menghubungkan tabel artikel dengan tabel kategori.
- **Join Query**: Menggabungkan data dari dua tabel atau lebih untuk analisis.

### 2. Query Builder CodeIgniter 4

- **Select dengan Join**: Mengambil data dari beberapa tabel sekaligus.
- **Where Clause**: Memfilter data berdasarkan kondisi yang spesifik.
- **Like Query**: Pencarian berdasarkan pola teks.
- **Pagination**: Memecah data menjadi beberapa halaman untuk tampilan yang lebih baik.

### 3. Pola Desain MVC

- **Model**: Mengelola semua interaksi dengan database.
- **View**: Bertanggung jawab untuk menampilkan data kepada pengguna.
- **Controller**: Mengatur alur logika aplikasi dan menjadi perantara antara Model dan View.

## Struktur File

```
app/
├── Controllers/
│   └── Artikel.php
├── Models/
│   ├── ArtikelModel.php
│   └── KategoriModel.php
└── Views/
    └── artikel/
        ├── index.php
        ├── admin_index.php
        ├── form_add.php
        ├── form_edit.php
        └── detail.php
```

## KESIMPULAN

Pada Praktikum ini berhasil mengimplementasikan relasi One-to-Many antara tabel kategori dan artikel. Dengan menggunakan Query Builder dari CodeIgniter 4, saya dapat melakukan join tabel dengan mudah dan aman. Fitur-fitur yang berhasil diimplementasikan meliputi dibawah ini:

1. ✅ Relasi antar tabel menggunakan foreign key.
2. ✅ Join query untuk menampilkan data dari beberapa tabel.
3. ✅ Filter dan pencarian artikel berdasarkan kategori.
4. ✅ Form input yang terintegrasi dengan data dari tabel kategori.
5. ✅ Pagination yang berfungsi dengan baik meskipun ada filter.

Pada Praktikum ini memberikan pemahaman yang lebih Praktis tentang cara kerja database relasional dan pemanfaatan Query Builder dalam framework CodeIgniter 4.

## SEKIAN TERIMA KASIH :)
