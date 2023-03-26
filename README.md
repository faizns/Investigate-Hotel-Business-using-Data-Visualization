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

### Background Story
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

### 2. Impact Analysis of Stay Duration on Hotel Bookings Cancellation Rates

### 3. Impact Analysis of Lead Time on Hotel Bookings Cancellation Rates

<br>
<br>

---

## 📂 STAGE 3: Summary and Recommendation
