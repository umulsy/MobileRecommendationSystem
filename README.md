# Mobile Recommendation System
## Project Overview
Di zaman sekarang, komunikasi yang biasa dilakukan dengan cara tatap muka, sekarang bahkan kita dapat melakukan pertemuan jarak jauh hanya dengan menggunakan fitur yang ada pada ponsel kita. Selain itu, hal ini juga dapat menimbulkan hilangnya hubungan antar manusia. Karena kita biasa melakukan interaksi atau bersosialisasi langsung dengan orang lain, tapi sekarang lebih ke interaksi terhadap diri sendiri, hal ini terjadi karena kita lebih sering fokus kepada ponsel daripada berinteraksi dengan orang lain di kehidupan nyata. Seperti apa yang telah kita ketahui, ponsel di era saat ini telah menjadi suatu kebutuhan karena kegunaanya yang sangat memudahkan kita untuk beraktivitas. Ditambah dengan banyaknya fitur-fitur canggih yang ada untuk makin mempermudah aktivitas, fitur yang bermacam-macam ditawarkan, seperti voice call, mengirim pesan, ditambah lagi dengan adanya aplikasi yang ditawarkan, seperti WhatsApp, dan yang lainnya (Sinapoy, 2021). Fenomena ini membuat para pengusaha ponsel berlomba-lomba untuk meluncurkan ponsel dengan spesifikasi yang beragam. Hal ini membuat konsumen bingung untuk menentukan pilihan untuk membeli ponsel dengan spesifikasi yang sesuai dengan kebutuhan mereka.

Berdasarkan permasalahan tersebut, pada proyek ini akan dibuat suatu model sistem rekomendasi menggunkaan _content-based filtering_ untuk merekomendasikan jenis merek ponsel yang mungkin ingin mereka beli. _Content-based filtering_ merupakan metode yang digunakan untuk merekomendasikan item berdasarkan "fitur" dari item berdasarkan dari aksi atau _explicit feedback_ sebelumnya. Contohnya yaitu merekomendasikan suatu film berdasarkan genrenya. Dengan adanya sistem rekomendasi ini diharapkan dapat membantu pembaca untuk menentukan ponsel yang akan mereka beli dan ponsel-ponsel yang mirip.
## Bussiness Understanding
### Problem Statement
Berdasarkan project overview, rumusan permasalahan yang akan diselesaikan pada proyek ini adalah :
1. Sistem rekomendasi apa yang paling sesuai untuk diterapkan pada permasalahan ini?
2. Bagaimana cara membuat sistem rekomendasi ponsel yang akan merekomendasikan ponsel berdasarkan spesifikasi ponsel?
### Goals
Tujuan dibuatnya proyek ini adalah sebagai berikut:
1. Membuat sistem rekomendasi ponsel dengan spesifikasi sebagai fitur.
2. Memberikan rekomendasi ponsel yang mirip dengan ponsel yang dinginkan pengguna.
### Solutions
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya:
1. Membuat sebuah model sistem rekomendasi
2. Mengevaluasi hasil rekomendasi yang diberikan
## Data Understanding
Dataset yang digunakan diambil dari situs [kaggle](https://www.kaggle.com/datasets/gyanprakashkushwaha/mobile-recommendation-system-dataset/code) dengan lisensi berikut Apache 2.0.
Berdasarkan deskripsi pada sumber dataset, dataset ini memiliki lima kolom yaitu kolom  Names, Ratings, Prices, link gambar and Corpus (spesifikasi) yang didalamnya berisi penjelasan storage_ram, camera, oS_Processor, display, network, battery. Dataset juga ini memiliki 2546 baris.
Berikut adalah list column dan penjelasannya :
- `name` : Nama berbagai model ponsel pintar, yang menunjukkan keragaman dan variasi penawaran.
- `ratings` : Peringkat dan ulasan pengguna yang terkait dengan setiap model, yang mencerminkan kepuasan dan umpan balik pelanggan.
- `price` : Harga ponsel, membantu pengguna memahami keterjangkauan dan proposisi nilai setiap perangkat.
- `corpus` : yang berisi informasi lengkap tentang storage_ram, camera, oS_Processor, display, network, dan battery.
- `img_URL` : Berisi link gambar ponsel
## Data Exploration
## Data Preparation
## Modeling
## Evaluation
## References
