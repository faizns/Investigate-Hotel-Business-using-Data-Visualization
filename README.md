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
Analisis kinerja bisnis sangat penting bagi perusahaan, termasuk dalam bisnis perhotelan karena dapat membantu dalam mengidentifikasi permasalahan, kelemahan, dan kekuatan perusahaan. Dengan menganalisis performa bisnis, perusahaan juga dapat mengambil tindakan yang tepat untuk mengatasi masalah, memperbaiki kelemahan, dan mempertahankan kekuatan. Hasil dari analisis kinerja ini dapat digunakan sebagai dasar untuk merumuskan strategi bisnis yang lebih baik di masa depan.

Dalam bisnis perhotelan, memahami perilaku pelanggan sangat penting untuk meningkatkan kinerja bisnis. Analisis perilaku pelanggan membantu dalam memahami faktor-faktor yang mempengaruhi keputusan konsumen dalam melakukan pemesanan hotel, termasuk faktor-faktor yang dapat memicu pembatalan pemesanan hotel. Selain itu, analisis perilaku pelanggan dapat membantu dalam mengisi kesenjangan pasar dan mengidentifikasi produk atau layanan yang kurang laku di pasar. Dengan memahami perilaku pelanggan, perusahaan dapat menyesuaikan strategi bisnis dan meningkatkan pengalaman pelanggan untuk mencapai tujuan bisnis jangka panjang.

### Business Questions
- Jenis hotel apa yang paling sering dikunjungi oleh tamu?
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
Analisis ini akan dilakukan untuk mengatahui trend pemesanan untuk setiap jenis hotel. Analisis tren pemesanan dapat membantu perusahaan **untuk lebih memahami pasar dan kebutuhan pelanggan mereka, serta memungkinkan mereka untuk dapat meningkatkan efisiensi operasional dan revenue**.

<p align="center">
    <kbd><img width="600" alt="hotel resort" src="https://user-images.githubusercontent.com/115857221/229820148-6d3da36d-df80-4908-8786-5f24cc267a8b.png"></kbd> <br>
    Gambar 1 — Grafik Presentase Rasio City Hotel dan Resort Hotel
</p>
<br>

Dari analisis keseluruhan, dapat disimpulkan bahwa **City Hotel lebih diminati oleh pelanggan** dengan persentase pemesanan mencapai 66.41%. Hotel ini biasanya terletak di pusat kota atau daerah perkotaan, dekat dengan tempat-tempat wisata dan bisnis, sehingga pelanggan yang memesan hotel ini mungkin memiliki aktivitas utama di sekitar tempat mereka menginap. Di sisi lain, Resort Hotel hanya dipesan oleh 33.59% pelanggan. Hotel ini biasanya terletak di tempat yang indah seperti tepi pantai, pegunungan, atau daerah pedesaan yang tenang dan terdapat fasilitas yang lengkap. Pelanggan yang memesan hotel ini diduga memiliki tujuan untuk berlibur dan bersantai di tempat tersebut. 
<br>
<br>

<p align="center">
    <kbd> <img width="1000" alt="tipe hotel perbulan" src="https://user-images.githubusercontent.com/115857221/229820633-3b06eb81-5d85-4bba-bab6-733d5a846394.png">
 </kbd> <br>
    Gambar 2 — Grafik Angka Pemesanan City Hotel dan Resort Hotel Bedasarkan Bulan
</p>
<br>

Pemesanan hotel cenderung mengalami peningkatan pada musim liburan, khususnya pada periode Mei - Agustus. Kedua tipe hotel yaitu City Hotel dan Resort Hotel, memiliki nilai pemesanan tertinggi pada periode tersebut, dengan peningkatan yang signifikan pada City Hotel. Hal ini kemungkinan terjadi karena banyaknya hari libur nasional pada tahun 2017-2019, seperti cuti bersama dan even keagamaan (Ramadhan) yang memungkinkan masyarakat untuk berlibur. Selain itu dengan mayoritas penduduk Indonesia adalah Muslim dan  adanya budaya mudik dan silaturahmi pada saat Idul Fitri memungkinkan masyarakat bepergian jauh dan membutuhkan tempat menginap ditengah perjalanan, sehingga melakukan pemesanan hotel. 

Sedangkan pada musim liburan periode Oktober - Desember, pemesanan hotel juga mengalami peningkatan namun cenderung lebih rendah daripada Mei - Agustus, kemungkinan banyak orang lebih memilih untuk merayakan hari besar seperti Natal dan Tahun Baru di rumah.

Pada periode Januari - Maret, tingkat pemesanan hotel paling rendah karena sedikitnya hari libur nasional dan periode tersebut merupakan awal tahun ajaran baru bagi pelajar yang membatasi waktu untuk berlibur dan memiliki bukan aktivitas perjalanan bisnis yang sibuk karena masih awal tahun. <br>
<br>


### 2. Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates
Analisis ini memfokuskan pada hubungan antara durasi menginap dan tingkat pembatalan pemesanan hotel. Berdasarkan data, sekitar 19% pesanan hotel yang dilakukan secara online dibatalkan sebelum tamu tiba di hotel [sumber]. Pembatalan ini dapat menyebabkan ketersediaan kamar berkurang dan berdampak pada pendapatan hotel. Setiap kamar yang kosong dapat menjadi beban finansial pada hari tersebut. Selain itu, jika hotel menggunakan Online Travel Agency (OTA), tingkat pembatalan dapat mempengaruhi peringkat hotel dalam hasil pencarian [sumber].

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

Selain jumlah pelanggan yang lebih tinggi, City Hotel juga memiliki presentase Cancellation Rate yang lebih tinggi yaitu 41.79% dibandingkan dengan Resort Hotel yaitu 27.77%. Hal ini menunjukkan bahwa banyak pelanggan yang memesan City Hotel cenderung lebih sering membatalkan pesanan mereka dibandingkan dengan Resort Hotel. City Hotel memiliki lokasi yang lebih terpusat di kota atau daerah perkotaan dan dekat dengan tempat-tempat wisata dan bisnis, dapat diduga banyaknya kegiatan yang harus diatur dan mungkin juga pengaruh faktor lain, banyak pelanggan yang membatalkan pesanan mereka.

Mengapa angke presentase Cancellation Rate pada kedua tipe hotel ini sangat tinggi? Berdasarkan sumber, pemesanan melalui online travel agency (OTA) memiliki kontribusi yang tinggi terhadap tingkat pembatalan (Cancellation Rate) dibandingkan dengan pemesanan langsung (offline). Banyak hotel yang cenderung menetapkan kebijakan pembatalan yang fleksibel pada OTA, tanpa mempertimbangkan tanggal atau tarif khusus yang dipesan. Selain itu, terkadang pelanggan memesan beberapa hotel jauh hari dan kemudian membatalkan semuanya kecuali satu. Untuk mencegah hal ini, perusahaan perlu mengambil tindakan preventif. Selain itu, pemesanan palsu (fraud) juga dapat menyebabkan tingkat pembatalan yang tinggi. Perlu adanya data tambahan apakah pemesanan melalui online platform atau tidk untuk menganalisi lebih lanjut
<br>

<p align="center">
    <kbd><img width="1000" alt="tren pembatalan" src="https://user-images.githubusercontent.com/115857221/229822263-6a6b771a-245f-4447-8c64-e1d44ad75e02.png">
</kbd> <br>
    Gambar 5 — Tren Pembatalan Pemesanan Hotel Berdasarkan Durasi Menginap
</p>
<br>

Tingkat pembatalan pesanan hotel akan cenderung semakin tinggi seiring dengan semakin lama durasi menginap yang dipesan, baik di City Hotel maupun Resort Hotel. Namun, terdapat perbedaan yang cukup signifikan pada City Hotel, di mana untuk durasi menginap lebih dari 2 minggu memiliki Cancellation Rate lebih dari 50%, bahkan untuk durasi menginap lebih dari sebulan, hanya 1 dari 10 orang yang tidak membatalkan pesanannya. Kondisi ini tentunya memerlukan tindakan strategis yang tepat dari perusahaan untuk dapat memperkecil tingkat pembatalan yang terjadi dan meningkatkan keuntungan bisnis.


### 3. Impact Analysis of Lead Time on Hotel Bookings Cancellation Rates

<br>
<br>

---

## 📂 STAGE 3: Summary and Recommendation
