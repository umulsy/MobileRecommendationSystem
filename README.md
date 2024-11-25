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
- `name` : Nama berbagai model ponsel pintar, yang menunjukkan keragaman dan variasi penawaran. (bertipe string)
- `ratings` : Peringkat dan ulasan pengguna yang terkait dengan setiap model, yang mencerminkan kepuasan dan umpan balik pelanggan. (bertipe desimal)
- `price` : Harga ponsel, membantu pengguna memahami keterjangkauan dan proposisi nilai setiap perangkat. (bertipe string)
- `corpus` : yang berisi informasi lengkap tentang storage_ram, camera, oS_Processor, display, network, dan battery. (bertipe string)
- `img_URL` : Berisi link gambar ponsel (URL)
## Data Exploration
### Melihat nilai unique dan menghitung jumlah pada kolom rating
Rating yang terdapat pada kolom ini adalah sebagai berikut : [2.9, 3.0, 3.1, 3.3, 3.5, 3.6, 3.7, 3.8, 3.9, 4.0, 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7, 4.8, 5.0]. Terlihat bahwa rating dimulai dari rentang 2.9 - 5.0.
### Menampilkan deskripsi statistik kolom rating
Hasil dari deskripsi statistik rating adalah sebagai berikut
| Desc| Rating      |
| --- | ----------- |
|count| 2546.000000 |
|mean |  4.295797   |
|std  |	 0.214691   |
|min	|  2.900000   |
|25%	|  4.200000   |
|50%	|  4.300000   |
|75%	|  4.400000   |
|max	|  5.000000   |

Rata-rata rating yang didapat adalah 4.3
### Visualisai distribusi rating
![image](https://github.com/user-attachments/assets/1ffef16d-3b75-4bfa-b23d-52b40f2b7674)

Grafik di atas adalah distribusi rating dan jumlah per rating
### Melihat banyaknya jumlah corpus pada data
Untuk mengecek kolom corpus digunakan syntax berikut `len(data.corpus.unique()))`

Didapatkan kolom corpus berjumlah 1604 berarti terdapat missing value pada kolom corpus
### Mengecek Missing value
Setelah dilakukan pengecekan dengan syntax `isna.sum()` ternyata benar terdapat missing value pada kolom corpus sejumlah 12
### Membuat sample gambar ponsel
![image](https://github.com/user-attachments/assets/d1bffbbb-ec4a-4e34-8099-618493635c56)

Berikut adalah sample gambar ponsel baris kedua pada tabel


## Data Preparation
Pada data preparation, langkah langkah yang dilakukan adalah sebagai berikut :
### Menghapus missing value 
Dilakukan penghapusan kolom yang berisi null pada tabel dengan syntax `dropna()`. Pada tabel ini hanya terdapat pada kolom corpus
### Membuat rata-rata rating dan jumlahnya
Pada tahap ini dilakukan untuk analisa lebih lanjut, rata-rata rating akan ditampilkan pada gambar ponsel di akhir
### Mengubah bentuk data price menjadi data numerik
Pada kolom data price tidak bertipe numerik. Terdapat simbol mata uang rupee (India) koma (,) , dan titik (.). Agar mempermudah proses analisis maka kolom price diubah ke data bertipe float dengan menhapus seluruh simbol pada data
### Mengkonversi nilai mata uang
Berdasarkan dataset, mata uang yang digunakan pada dataset tersebut adalah rupee karena dataset berasal dari India. Untuk menyesuaikan harga ponsel dengan harga pasar Indonesia, dalam proyek ini dikalikan dengan Rp188,71 karena `1 rupe = Rp188,71`
### Menambahkan kolom brand dan kategori harga (opsional)
Pada proyek ini ditambahkan kolom brand dan kategori harga untuk pengembangan proyek analisis lebih lanjut. Tidak digunakan dalam proyek submission ini.
## Modeling
### TF-IDF Vektorisasi
Pada tahap ini, akan dibangun sistem rekomendasi berdasarkan spesifika yang dimiliki ponsel. Teknik ini digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap spesifikasi ponsel. TF-IDF merupakan teknik pembobotan kata yang berbasis pada statistik kemunculan kata dan tingkat kepentingan dokumen yang mengandungnya. Pembobotan kata ini merupakan hasil dari perkalian term frequency dan inverse document frequency yang tiap nilainya didapatkan dari (1) dimana wi adalah kata ke-I, d adalah dokumen, TF(wi, d) adalah jumlah kemunculan kata wi pada dokumen d dan IDF(wi) adalah nilai inverse document frequency dari wi.

$TF∗IDF=TF(Wi,d )∗IDF(Wi)$

### Cosine Similiarity
Cosine similarity mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama. Ia menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity. Metrik ini sering digunakan untuk mengukur kesamaan dokumen dalam analisis teks. Sebagai contoh, dalam studi kasus ini, cosine similarity digunakan untuk mengukur kesamaan nama restoran dan nama masakan. Pada proyek ini, akan dicari tingkat kemiripan spesifikasi hp dengan nama hp.

Untuk mengetahui seberapa baik model dalam memberikan sebuah rekomendasi dapat dibuah sebuah fungsi yang akan menerima nama_hp, similarity_data, items, k dengan definisi masing-masing parameter sebagai berikut:

`nama_hp`: Nama hp
`similarity_data`: DataFrame mengenai similarity yang telah dibuat di tahap sebelumnya.
`items` : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah name dan corpus
`k` : Banyak rekomendasi yang ingin diberikan. Pada proyek ini 5

Sample Hasil Rekomendasi dari Ponsel `OPPO Find X (Glacier Blue, 256 GB)` adalah sebagai berikut :

<img width="437" alt="image" src="https://github.com/user-attachments/assets/173cd2d4-4b4b-409c-b304-bb1c8aafe77d">



### Membuat Visualisasi Gambar Hasil Rekomendasi
Pada tahap ini dibuat fungsi `visualisasi_mobile` untuk membuat gambar hasil rekomendasi. Fungsi ini menggunakan kolom `img_URL , rating, dan price`. Hasil visualisasi akan menampilkan gambar ponsel, rating, dan harga ponsel dari rekomendasi ponsel yang diinginkan
Gambar hasil rekomendasi `OPPO Find X (Glacier Blue, 256 GB)`

![image](https://github.com/user-attachments/assets/00f1c1a0-4b7e-4cbd-ac93-83672ff19467)

## Evaluation

## References
