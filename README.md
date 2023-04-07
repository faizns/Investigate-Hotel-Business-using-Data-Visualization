# 🏬 **Investigate Hotel Business using Data Visualization**
<br>

**Tool** : Jupyter Notebook <br>
**Programming Language** : Python <br>
**Libraries** : Pandas, NumPy <br>
**Visualization** : Matplotlib, Seaborn <br>
**Dataset** : Disediakan oleh Rakamin Academy - [Hotel Booking Data]() <br>
<br>

----

## 📂 **STAGE 0: Problem Statement**

### Introduction
Analisis kinerja bisnis merupakan kunci penting bagi perusahaan untuk mencapai keberhasilan dalam bisnisnya. Perusahaan dapat melakukan analisis untuk mengidentifikasi permasalahan, kelemahan, dan kekuatan yang dimilikinya. Dalam bisnis perhotelan, penting untuk memahami perilaku pelanggan. Dengan memahami perilaku pelanggan, perusahaan dapat mengetahui faktor apa saja yang mempengaruhi pelanggan dalam melakukan pemesanan hotel.
Selain itu, perusahaan juga dapat mengidentifikasi produk atau layanan apa yang kurang laku di pasar. Hal ini dilakukan untuk menyesuaikan strategi bisnis yang tepat guna sehingga perusahaan dapat meningkatkan pengalaman pelanggan dan dapat mencapai tujuan bisnis jangka panjang. 

### Business Questions
- Jenis hotel apa yang paling sering dikunjungi oleh pelanggan?
- Apakah durasi menginap mempengaruhi tingkat pembatalan pemesanan hotel?
- Apakah jarak waktu antara pemesanan hotel dan hari kedatangan tamu mempengaruhi tingkat pembatalan pemesanan hotel?

### Objective
Membuat visualisasi berbasis data sebagai insight bagi bisnis hotel
<br>
<br>
<br>

---

## 📂 STAGE 1: Data Preprocessing

### Data Overview
Dataset terdiri dari 29 kolom dan 119390 baris dengan periode tahun 2017 - 2019.

### Data Assessment
Asesment data dilakukan untuk memastikan bahwa data yang digunakan untuk analisis selanjutnya sudah siap dan sesuai dengan kebutuhan analisis. Hal yang dilakukan:
- Mengecek nilai null atau missing value pada data
- Mengecek duplikasi data
- Melakukan tipe data dan konsistensi nilai
- Memeriksa outlier atau data yang tidak biasa

Tabel 1 - Hasil Data Assessmen
 **Data Assessment** | **Finding**  | **Handling** 
--------------------|--------------|--------------
Missing values     | Terdapat nilai null pada `company`, `city`, `children`, dan `agent` | - `company` : d**diisi dengan 0**, mengindikasikan tamu tidak bersal dari company <br> - `agent` : **diisi dengan 0**, mengindikasikan tamu melakukan reservasi mandiri atau tidak melalui agen <br> - `children` : **diisi dengan 0**, mengindikasikan tamu tidak membawa anak-anak <br> - `city` : **diisi dengan 'Undefined'**, karena kota tidak diketahui secara pasti
Nilai yang tidak sesuai atau tidak konsisten | Makna 'Undefined' pada kolom `meal` | Nilai kolom `meal` dapat dikategorikan menjadi 2 yaitu **'With Meal'** (Breakfast, Full Board, Dinner) dan **'No Meal' (No Meal, Undefined)**
Data anomali atau data yang tidak diperlukan | - Terdapat nilai negatif dan outlier yang sangat jauh dari distribusi data pada kolom `adr` <br> - Terdapat 180 data booking tidak memiliki tamu | Menghapus atau **drop baris data tersebut**           

<br>
<br>

---

## 📂 STAGE 2: Data Analysis
### 1. Monthly Hotel Booking Analysis Based on Hotel Type
Analisis ini akan dilakukan untuk mengatahui tren pemesanan pada setiap jenis hotel. Analisis ini dapat membantu perusahaan **untuk lebih memahami pasar dan kebutuhan pelanggan mereka, serta memungkinkan mereka untuk dapat meningkatkan efisiensi operasional dan mengoptimalkan revenue**.

<p align="center">
    <kbd><img width="600" alt="tipe hotel rasio" src="https://user-images.githubusercontent.com/115857221/230533333-0f148859-0edf-4baf-bfb6-18fcbe71d699.png"></kbd><br>
    Gambar 1 — Grafik Presentase Rasio City Hotel dan Resort Hotel
</p>
<br>

Dari plot diatas terlihat bahwa **City Hotel lebih diminati oleh pelanggan**, dengan presentase pemesanannya mencapai **66.41%**. Hotel ini biasanya terletak di pusat kota atau daerah perkotaan, dekat dengan tempat-tempat wisata dan bisnis, sehingga pelanggan yang memesan hotel ini mungkin memiliki aktivitas utama di sekitar tempat mereka menginap. Di sisi lain, **Resort Hotel hanya dipesan oleh 33.59% pelanggan**. Hotel ini biasanya terletak di tempat yang indah seperti tepi pantai, pegunungan, atau daerah pedesaan yang tenang dan terdapat fasilitas yang lengkap. Pelanggan yang memesan hotel ini diduga memiliki tujuan untuk berlibur dan bersantai di tempat tersebut. 
<br>
<br>

<p align="center">
    <kbd> <img width="1000" alt="tipe hotel perbulan" src="https://user-images.githubusercontent.com/115857221/229820633-3b06eb81-5d85-4bba-bab6-733d5a846394.png">
 </kbd> <br>
    Gambar 2 — Grafik Angka Pemesanan City Hotel dan Resort Hotel Bedasarkan Bulan
</p>
<br>

Pemesanan hotel cenderung mengalami **peningkatan pada musim liburan**, khususnya pada periode **Mei - Agustus**. Kedua tipe hotel yaitu City Hotel dan Resort Hotel, memiliki nilai pemesanan tertinggi pada periode tersebut, dengan **peningkatan yang signifikan pada City Hotel**. Hal ini kemungkinan terjadi karena banyaknya hari libur nasional pada tahun 2017-2019, seperti cuti bersama dan even keagamaan (Ramadhan) yang memungkinkan masyarakat untuk berlibur. Selain itu dengan mayoritas penduduk Indonesia adalah Muslim dan adanya budaya mudik dan silaturahmi pada saat Idul Fitri memungkinkan masyarakat bepergian jauh dan membutuhkan tempat menginap ditengah perjalanan, sehingga melakukan pemesanan hotel. 

Sedangkan pada musim liburan periode **Oktober - Desember** pemesanan hotel juga mengalami peningkatan, namun cenderung lebih rendah daripada Mei - Agustus, kemungkinan banyak orang lebih memilih untuk merayakan hari besar seperti Natal dan Tahun Baru di rumah.

Pada periode **Januari - Maret**, tingkat pemesanan hotel **paling rendah**. Hal tersebut terjadi kemungkinan karena sedikitnya hari libur nasional, serta periode tersebut merupakan awal tahun ajaran baru bagi pelajar dan bukan periode aktivitas perjalanan bisnis yang sibuk karena masih awal tahun. <br>
<br>


### 2. Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates
Analisis ini memfokuskan pada hubungan antara durasi menginap dan tingkat pembatalan pemesanan hotel. Berdasarkan data, sekitar 19% pesanan hotel yang dilakukan secara online dibatalkan sebelum pelanggan tiba [[sumber](https://www.phocuswire.com/One-in-five-hotel-bookings-on-the-web-are-cancelled)]. Pembatalan ini dapat menyebabkan ketersediaan kamar berkurang dan berdampak pada pendapatan hotel karena setiap kamar yang kosong dapat menjadi beban finansial pada hari tersebut. Selain itu, jika hotel menggunakan Online Travel Agency (OTA), tingkat pembatalan ini dapat mempengaruhi peringkat hotel di pencarian [[sumber](https://www.hotelminder.com/everything-you-need-to-know-about-hotel-cancellations)].

<p align="center">
    <kbd> <img width="600" alt="pembatalan city" src="https://user-images.githubusercontent.com/115857221/229821918-ae476922-2470-40fd-8dda-0a0a7f584b23.png"></kbd> <br>
    Gambar 3 — Grafik Presentase Pembatalan Hotel City
</p>
<br>

<p align="center">
    <kbd><img width="600" alt="hotel resort" src="https://user-images.githubusercontent.com/115857221/229821958-a2153c90-9069-4685-a5d7-b0020763dbb2.png"></kbd> <br>
    Gambar 4 — Grafik Presentase Pembatalan Hotel Resort
</p>
<br>

City Hotel juga memiliki presentase *cancellation rate* yang lebih tinggi dibandingkan dengan Resort Hotel. Hal ini menunjukkan bahwa **banyak pelanggan yang memesan City Hotel cenderung lebih sering membatalkan pesanannya**. City Hotel memiliki lokasi yang lebih terpusat di kota atau daerah perkotaan dan dekat dengan tempat-tempat wisata dan bisnis, dapat diduga banyaknya kegiatan yang harus diatur dan mungkin juga pengaruh faktor lain, banyak pelanggan yang membatalkan pesanan mereka.<br>
<br>

<p align="center">
    <kbd><img width="1000" alt="tren pembatalan" src="https://user-images.githubusercontent.com/115857221/229822263-6a6b771a-245f-4447-8c64-e1d44ad75e02.png">
</kbd> <br>
    Gambar 5 — Tren Pembatalan Pemesanan Hotel Berdasarkan Durasi Menginap
</p>
<br>

Bedasarkan durasi menginap terlihat bahwa **tingkat pembatalan pesanan hotel akan cenderung semakin tinggi seiring dengan semakin lama durasi menginapnya**, baik di City Hotel maupun Resort Hotel. Pada City Hotel *cancellation rate* meningkat secara lebih signifikan dengan presentase nilai dibawah 50% pada durasi satu minggu. Pada durasi menginap lebih dari empat minggi Resort Hotel ini juga memiliki *cancellation rate* yang lebih rendah. Pada intinya kedua Jenis hotel memiliki **tren positif, dimana semakin lama durasi menginap, semakin tinggi kemungkinan pemesanan tersebut dibatalkan**.

Mengapa semakin lama durasi menginap mengakibatkan tingkat pembatalan bertambah ini, perusahaan dapat melakukan evaluasi serta analisis lebih lanjut. Beberapa faktor yang dapat memungkinkan diantaranya ketidakpuasan pelanggan. Pelanggan yang menginap di hotel selama jangka waktu yang lama mungkin memiliki harapan yang lebih tinggi dan menuntut pelayanan yang lebih baik. Jika pelanggan tidak puas dengan pelayanan hotel, mereka mungkin akan memutuskan untuk membatalkan reservasi mereka dan mencari hotel yang lebih baik. Selain itu biaya yang lebih tinggi juga dapat menjadi faktor. Biaya mungkin dapat menjadi lebih besar dari yang diharapkan atau dianggarkan pelanggan sebelumnya, sehingga mereka mencari alternatif yang lebih terjangkau.<br>
<br>



### 3. Impact Analysis of Lead Time on Hotel Bookings Cancellation Rates



<p align="center">
    <kbd><img width="1000" alt="tren lead" src="https://user-images.githubusercontent.com/115857221/230551207-aa417f83-5979-4bc6-a615-e2f10e835b26.png"></kbd> <br>
    Gambar 6 — Tren Pembatalan Pemesanan Hotel Berdasarkan Lead Time
</p>
<br>

<br>
<br>

---

## 📂 STAGE 3: Summary and Recommendation
