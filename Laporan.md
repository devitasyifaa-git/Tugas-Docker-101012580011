# Laporan Praktikum Docker Dasar

## Identitas
**NAMA: Devita Syifa Azzahraa<br>
**NIM:** 101012580011**

## 1. Instalasi dan Pengujian Docker

Docker Desktop berhasil diinstal dan Docker Engine dapat digunakan untuk menjalankan container.

Pengujian dilakukan menggunakan container Ubuntu 22.04 dengan perintah:

`docker run -it --name tes-ubuntu-101012580011 ubuntu:22.04 bash`

Kemudian dilakukan pengecekan informasi sistem menggunakan:

`cat /etc/os-release`

Setelah selesai, container dihentikan dan dihapus menggunakan:

`exit`

`docker rm tes-ubuntu-101012580011`

## 2. Pembuatan Aplikasi Web
Aplikasi web sederhana dibuat menggunakan Python dengan modul `http.server`.

Aplikasi menggunakan environment variable `STUDENT_NIM` untuk menampilkan NIM pada halaman web.

File utama aplikasi adalah `app.py`.

## 3. Pembuatan Docker Image
Docker image dibuat menggunakan `Dockerfile` dengan base image Python 3.11 slim.

Image dibuat menggunakan perintah:

`docker build -t web-tugas-101012580011:1.0 .`

## 4. Menjalankan Container
Container aplikasi dijalankan dengan port forwarding dari port 8080 pada host ke port 8000 pada container:

`docker run -d -p 8080:8000 --name web-container-101012580011 web-tugas-101012580011:1.0`

Pengujian aplikasi dilakukan menggunakan:

`curl http://localhost:8080`

Hasil pengujian menampilkan pesan:

**Praktikum Docker Dasar Berhasil!**

serta NIM mahasiswa.

## 5. Docker Compose

Aplikasi kemudian dijalankan menggunakan Docker Compose dengan dua service, yaitu:

- **web** sebagai aplikasi web Python.
- **cache** menggunakan Redis.

Docker Compose dijalankan menggunakan:

`docker compose up -d`

Status container diperiksa menggunakan:

`docker compose ps`

Kedua service berhasil berjalan dengan status **Up**.
## 6. Hasil Pengujian

Pengujian menggunakan:

`curl http://localhost:8080`

menghasilkan halaman dengan pesan:

**Praktikum Docker Dasar Berhasil!**

**Dikembangkan oleh NIM: 101012580011**

## 7. Kesimpulan
Praktikum Docker Dasar berhasil dilakukan mulai dari menjalankan container Ubuntu, membuat Docker image, menjalankan aplikasi web dalam container, hingga menggunakan Docker Compose untuk menjalankan service web dan cache secara bersamaan.
