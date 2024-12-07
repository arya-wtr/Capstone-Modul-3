<a id="readme-top"></a>


<h3 align="center">Customer Lifetime Value</h3>

  <p align="center">
    Capstone Modul 3
    by N.B. Arya Widiantara
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#business-problem-understanding">Business Problem Understanding</a>
      <ul>
        <li><a href="#context">Context</a></li>
        <li><a href="#problem-statement">Problem Statement</a></li>
        <li><a href="#goals">Goals</a></li>
        <li><a href="#analytic-approach">Analytic Approach</a></li>
        <li><a href="#metric-evaluation">Metric Evaluation</a></li>
      </ul>
    </li>
    <li>
      <a href="#data-understanding">Data Understanding</a>
      <ul>
        <li><a href="#features">Features</a></li>
        <li><a href="#data-preprocessing">Data Preprocessing</a></li>
      </ul>
    </li>
    <li>
      <a href="#modeling-and-tuning">Modeling & Tuning</a>
      <ul>
        <li><a href="#modeling">Modeling</a></li>
        <li><a href="#tuning">Tuning</a></li>
        <li><a href="#actual-vs-prediction-clv">Actual vs Prediction CLV</a></li>
        <li><a href="#feature-importances">Feature Importances</a></li>
      </ul>
    </li>
    <li><a href="#conclusion-and-recommendation">Conclusion & Recommendation</a></li>
  </ol>
</details>



<!-- Business Problem Understanding -->
## Business Problem Understanding

### Context

Pelanggan selalu menjadi teka-teki bagi sebuah bisnis. Banyak sekali buku-buku mengenai cara sukses sebuah bisnis, jika deep dive kedalamnya semua akan kembali lagi ke pelanggan, karena merekalah yang membawa masuk keuntungan. Akan tetapi tidak semua pelanggan sesuai dengan bisnis, beberapa pelanggan mungkin membawa nilai lebih bagi bisnis dan beberapa mungkin tidak.

Customer Lifetime Value, atau CLV, adalah ukuran seberapa berharganya seorang pelanggan bagi sebuah perusahaan. CLV hadir sebagai tools yang membantu untuk mengidentifikasi pelanggan yang valuable bagi bisnis. CLV dapat dimanfaatkan secara efektif dengan mengidentifikasi pelanggan yang bernilai tinggi dengan memahami perilaku, preferensi, dan kebutuhan mereka.

"CLV" The Only Metric That Matters - "Forbes"

Dengan menggunakan CLV (Customer Lifetime Value), perusahaan memiliki dasar untuk merumuskan dan menerapkan strategi yang spesifik untuk pelanggan, guna memaksimalkan keuntungan "lifetime" dari setiap pelanggan serta bisa memperpanjang durasi hubungan dengan pelanggan tersebut.

### Problem Statement

Perusahaan AUTOLIFE Insurance sebagai salah satu perusahaan asuransi automotif asal US, memiliki kesulitan dalam mengidentifikasi seluruh pelanggan. Dengan resource yang ada, perusahaan kesulitan dalam mengidentifikasi pelanggan mana yang menjanjikan potensi tertinggi untuk profitabilitas jangka panjang. Hal yang menjadi tantangan utama adalah cara memprediksi CLV pelanggan secara akurat. Ini akan memungkinkan perusahaan untuk lebih efektif menargetkan pelanggan yang paling berharga dan merencanakan pertumbuhan jangka panjang dengan lebih baik.

Tim marketing dari AUTOLIFE Insurance berperan melakukan kampanye pemasaran yang menargetkan pelanggan yang ada, seperti promosi, komunikasi rutin, dan penawaran khusus. Maka dari itu, mereka sangat membutuhkan cara bagaimana dengan lebih efektif menentukan pelanggan yang berharga ini.

### Goals

Berdasarkan permasalahan yang ada, perusahaan AUTOLIFE Insurance tentunya ingin memiliki sebuah tools yang dapat memilih pelanggan mana yang valuable bagi bisnis mereka. Bagi tim marketing, adanya tools tersebut akan sangat membantu dalam menentukan dasaran yang dapat diukur dalam menentukan pelanggan-pelanggan yang memiliki potensi keuntungan jangka panjang, dan berkelanjutan.

Harapannya tim marketing dapat memperkirakan nilai CLV untuk setiap pelanggan secara akurat sehingga membantu dalam membuat keputusan strategi marketing untuk memaksimalisasi keuntungan dalam jangka panjang. Serta dapat mengidentifikasi faktor-faktor utama yang mempengaruhi CLV sehingga dapat mengambil keputusan berbasis data dalam mengelola hubungan dengan pelanggan.

### Analytic Approach

Kita akan menyiapkan dasaran untuk menganalisis data sehingga dapat menemukan pola dari fitur-fitur yang ada dari data existing klien. Semua itu akan berdasarkan CLV yang sudah terkalkulasi dan beberapa variabel-variabel pendukung.

Dengan hal itu, kita dapat membangun suatu model regresi yang akan membantu perusahaan sebagai 'tools' prediksi nilai Customer Lifetime Value, yang mana akan berguna untuk dalam menentukan pelanggan yang menjadi target nantinya.

### Metric Evaluation

Evaluasi metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana RMSE adalah nilai rataan akar kuadrat dari error, MAE adalah rataan nilai absolut dari error, sedangkan MAPE adalah rataan persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai RMSE, MAE, dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi nilai Customer Lifetime Value sesuai dengan limitasi fitur yang digunakan.


<!-- DATA UNDERSTANDING -->
## DATA UNDERSTANDING

### Features

| No. | **Attribute**    | **Description**                                          |
|-----| ---------------- | -------------------------------------------------------- |
| 1.  | **Vehicle Class**       | Tipe kendaraan yang diasuransikan.                |
| 2.  | **Coverage**     | Tipe perlindungan pada polis asuransi.                      |
| 3.  | **Renew Offer Type**   | Tipe perpanjangan polis asuransi.                      |
| 4.  | **EmploymentStatus**     | Status pekerjaan pelanggan. |
| 5.  | **Marital Status** | Status pernikahan pelanggan.             |
| 6.  | **Education**      | Tingkat pendidikan terakhir pelanggan.                  |
| 7.  | **Number of Policies**         | Jumlah polis asuransi.                     |
| 8.  | **Monthly Premium Auto**       | Premi yang dibayar setiap bulan.                   |
| 9.  | **Total Claim Amount**    | Total klaim yang diajukan.                |
| 10.  | **Income**     | Nilai pendapatan pelanggan.           |
| 11.  | **Customer Lifetime Value**  | Customer lifetime value.                   |

### Data Preprocessing

Dengan Data Understanding, Data Cleaning, Encoding sehingga mendapat data yang ready untuk modeling

<!-- Modeling and Tuning -->
## Modeling and Tuning

### Modeling

menentukan kandidat model : 

lr = LinearRegression()

knn = KNeighborsRegressor()

dt = DecisionTreeRegressor(random_state= 0)

rf = RandomForestRegressor(random_state= 0)

xgb = XGBRegressor(random_state= 0)

gbr = GradientBoostingRegressor(random_state= 0)


dan mendapatkan hasil terbaik pada model **GradientBoostingRegressor**

### Tuning

Setelah di hyperparameter tuning dengan **GRIDSEARCHCV** didapatkan improvement pada semua eva metriks yang dipakai.

### Actual vs Prediction CLV

Terdapat hubungan antara nilai prediksi dengan nilai aktualnya, ada kecocokan atau tidak.

### Feature Importances

Terdapat fitur fitur penting yang mempengaruhi nilai Target (Customer Lifetime Value).

<!-- Conclusion and recommendation -->
## Conclusion and recommendation

Terdapat Konklusi dan Rekomendasi Model dari hasil analisis, terdapat juga rekomendasi bisnis kepada tim marketing.



<!-- ABOUT PROJECT -->
## ABOUT PROJECT

Project ini sebagai syarat requirement dari Purwadhika Digital Technology School.


<!-- CONTACT -->
## Contact

Arya Widiantara - arya.wtr@gmail.com

Project Link: [https://github.com/arya-wtr](https://github.com/arya-wtr)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
