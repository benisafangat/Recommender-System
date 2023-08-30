# Laporan Proyek Machine Learning: Recommender System

## Project Overview
Dalam era digital saat ini, jumlah informasi dan konten yang tersedia secara online terus berkembang pesat. Hal ini telah memunculkan tantangan baru dalam membantu pengguna menavigasi dan menemukan informasi yang paling relevan dan bermanfaat bagi mereka. Sistem rekomendasi adalah solusi yang digunakan oleh banyak platform untuk memberikan pengalaman yang lebih personal dan efisien kepada pengguna. Dua pendekatan yang dominan dalam pengembangan sistem rekomendasi adalah content-based filtering dan collaborative filtering.

1. Content-Based Filtering:

Content-based filtering adalah metode yang didasarkan pada analisis atribut konten dari produk atau konten yang ada. Konsep dasar di balik pendekatan ini adalah bahwa pengguna cenderung tertarik pada item yang memiliki atribut yang serupa dengan item yang telah mereka sukai sebelumnya. Misalnya, dalam rekomendasi film, sistem content-based akan menganalisis atribut seperti genre, pemeran, sutradara, dan ulasan untuk merekomendasikan film dengan atribut serupa dengan film yang telah disukai pengguna.

2. Collaborative Filtering:

Collaborative filtering berfokus pada pola interaksi dan perilaku pengguna. Pendekatan ini berasumsi bahwa jika dua pengguna memiliki sejarah preferensi yang mirip atau jika mereka berinteraksi dengan item yang sama, mereka cenderung memiliki preferensi yang serupa untuk item yang belum pernah mereka lihat sebelumnya. Misalnya, jika dua pengguna yang memiliki sejarah pembelian yang mirip menyukai produk A, sistem collaborative filtering dapat merekomendasikan produk A kepada pengguna lain yang memiliki sejarah pembelian yang mirip.

Kelebihan Kombinasi Kedua Pendekatan:

Kedua pendekatan ini memiliki kelebihan dan kelemahan masing-masing. Content-based filtering memiliki kelebihan dalam memberikan rekomendasi yang sesuai dengan preferensi yang spesifik dan dapat memitigasi masalah cold start, yaitu ketika informasi perilaku pengguna terbatas. Di sisi lain, collaborative filtering mengatasi masalah ketidakmampuan sistem untuk memahami atribut kompleks dari suatu item. Namun, collaborative filtering cenderung mengalami masalah dengan pengguna baru yang tidak memiliki sejarah interaksi.

Kombinasi content-based filtering dan collaborative filtering dapat mengatasi kelemahan masing-masing metode. Dengan menggabungkan kedua pendekatan ini, sistem rekomendasi dapat menghasilkan rekomendasi yang lebih akurat dan personal. Dalam hal ini, content-based filtering memberikan wawasan tentang atribut dan preferensi pengguna, sementara collaborative filtering memungkinkan sistem untuk mengidentifikasi pola perilaku yang mendasari preferensi pengguna.

Dengan pertumbuhan data yang semakin besar dan kompleksitas preferensi pengguna yang semakin tinggi, pendekatan yang menggabungkan content-based filtering dan collaborative filtering menjadi semakin relevan dalam mengembangkan sistem rekomendasi yang efektif dan berdaya guna dalam berbagai konteks, seperti e-commerce, platform media sosial, dan layanan hiburan.

## Business Understanding

### Problem Statements
Bagaimana cara merekomendasikan film yang disukai oleh satu pengguna agar dapat direkomendasikan kepada pengguna lainnya?

### Goals
Membuat sistem rekomendasi yang akurat berdasarkan ratings dan history pengguna pada masa lalu.

### Solution
Solusi yang dapat diterapkan yaitu menggunakan pendekatan *machine learning* dengan teknik sistem rekomendasi:

* Content-Based Filtering: Algoritma yang merekomendasikan item serupa dengan preferensi pengguna, berdasarkan aktivitas atau umpan balik yang diberikan sebelumnya.

![content base](https://github.com/benisafangat/recommender-system/assets/70525105/65d4c765-45f2-4656-9c25-92ff238d196d)


* Collaborative Filtering: Algoritma yang mengandalkan pendapat dari komunitas pengguna. Metode ini tidak memerlukan atribut khusus untuk setiap item.


![cola](https://github.com/benisafangat/recommender-system/assets/70525105/55b60160-2133-41a9-83a5-eb7870d8a6d4)


Sistem rekomendasi yang akurat memiliki potensi untuk memberikan sejumlah manfaat signifikan bagi bisnis. Berikut beberapa contoh konkret mengenai manfaat tersebut:
* Peningkatan Retensi Pelanggan
* Peningkatan Penjualan Silang (Cross-Selling) dan Penjualan Naik (Upselling)
* Personalisasi Pengalaman Pelanggan
* Optimasi Persediaan dan Manajemen Stok

## Data Understanding
Dataset yang digunakan dalam proyek *machine learning* ini berasal dari Movie Recommendation Data yang diperoleh dari situs Kaggle. Dalam kasus ini, data memiliki 4 file terpisah mengenai links, movie, ratings dan tags. Datasets yang digunakan mempunyai total data sebanyak 124003 data dengan sebaran data sebanyak 9742 data links, 9742 data movies, 100836 data ratings, dan 3683 data tags. Link datasets dapat ditemukan pada tautan berikut: https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data.

### Univariate Exploratory Data Analysis
Variabel-variabel pada Movie Recommendation Data dataset adalah sebagai berikut:
* Links : Data link movie
* Movies : Data movie yang tersedia
* Ratings : Data penilaian untuk movie
* Tags : Data kata kunci untuk movie

## Data Preparation
* Mengatasi Missing Value: Menghapus data yang terdapat missing value. Hal ini dilakukan karena apabila terdapat data yang kosong dapat mempengaruhi performa model dalam melakukan rekomendasi.
* Menggabungkan Variabe: Variabel dapat digabungkan berdasarkan ID yang bersifat unik dari yang lain. Tujuan dari menggabungkan variabel adalah untuk meningkatkan kualitas rekomendasi yang diberikan kepada pengguna, dengan memanfaatkan informasi yang lebih lengkap dan mendalam tentang preferensi, perilaku, atau karakteristik pengguna dan item.
* Mengurutan Data: Data diurutkan berdasarkan movieId secara berurutan (ascending). Hal ini dilakukan untuk mempermudah keterbacaan data dalam mengatasi duplikasi data.
* Mengatasi Duplikasi Data: Data yang memiliki nilai atau konten yang identik diatasi dengan cara dihapus menggunakan fungsi drop_duplicates(), karena data yang digunakan hanya data unik untuk dimasukkan ke dalam proses pemodelan
* Konversi Data Menjadi List: Data diubah menjadi bentuk daftar (list). Tujuan utama dari mengkonversi data menjadi list adalah untuk memudahkan pemrosesan, manipulasi, dan analisis lebih lanjut.
* Membuat Dictionary: Menentukan pasangan key-value pada data id, movie_id, dan genre yang telah disiapkan sebelumnya. Sama seperti konversi data menjadi list berfungsi untuk memberikan struktur data yang terorganisir, efisien dalam akses dan manipulasi, serta memudahkan analisis dan pengolahan data.
* Membagi Data: Dataset yang akan digunakan pada tahap *modeling* dibagi menjadi data latih dan data validasi. Data yang digunakan harus dipisah agar memudahkan model dalam melakukan pelatihan. Rasio pembagian datasets yaitu 70% untuk data latih dan 30% untuk data validasi.

## Modeling and Result

### Content-Based Filtering
* TF-IDF Vectorizer: Melakukan pembobotan teks.
* Cosine Similarity: Menghitung derajat kesamaan (similarity degree) antar movie dengan teknik cosine similarity.
* Mendapatkan Rekomendasi: Hasil modeling dari model ini adalah sebagai berikut:

Berikut ini adalah film-film yang disukai oleh pengguna pada masa lalu:

**No**|**Id**|**Movie Name**|**Genre**
:-----:|:-----:|:-----:|:-----:
4|	7|	Sabrina (1995)|	Comedy/Romance

Dari hasil di atas, terlihat bahwa pengguna menyukai film berjudul "Sabrina" (1995) dengan genre comedy dan romance. Oleh karena itu, berikut adalah hasil rekomendasi lima teratas berdasarkan algoritma Content-Based Filtering:

**No**|**Movie Name**|**Genre**
:-----:|:-----:|:-----:
0|	Coming to America (1988)|	Comedy/Romance
1|	Woman of the Year (1942)|	Comedy/Romance
2|	Crossing Delancey (1988)|	Comedy/Romance
3|	Desk Set (1957)|	Comedy/Romance
4|	Legally Blonde (2001)|	Comedy/Romance

Dari hasil di atas, terlihat bahwa film dengan genre comedy dan romance menjadi rekomendasi utama dari sistem. Rekomendasi ini didasarkan pada preferensi penonton atau pengguna di masa lalu. Berdasarkan evaluasi metrics yaitu: dari 5 item yang direkomendasikan, semuanya merekomendasikan genre yang relevan yaitu comedy dan romance. Artinya, model menghasilkan precision sebesar 5/5 atau 100% dan recall sebesar 5/5 atau 100% juga.

### Collaborative Filtering
Algoritma ini mengukur kesamaan antara movie-movie berdasarkan seberapa sering pengguna satu dengan yang lainnya menilai atau menyukai movie yang sama terhadap movie tersebut.
* Training: Proses training pada model ini menggunakan Optimizer Adam dengan Learning Rate: 0.0001, Loss: BinaryCrossentropy(), Metrics: RootMeanSquaredError().
Penggunaan Optimizer Adam pada model ini yaitu optimizer Adam stabil dalam berbagai macam data dan mampu menghasilkan performa yang baik. Serta penggunaan Learning Rate (0.0001) yaitu karena dengan nilai tersebut dapat memberikan performa hasil yang baik pada model ini.
* Rekomendasi Movie: hasil dari proses training yaitu model dicoba untuk membuat rekomendasi. berikut adalah hasilnya.

Showing Recommendations for users: 7

Movie with High Ratings from user

**No**|**Movie Name**|**Genre**
:-----:|:-----:|:-----:
0| Silence of the Lambs, The (1991)| Crime/Horror/Thriller
1| Psycho (1960)| Crime/Horror
2| Terminator, The (1984)| Action/Sci-Fi/Thriller
3| Seven Samurai (Shichinin no samurai) (1954)| Action/Adventure/Drama

Top 10 Movie Recommendation

**No**|**Movie Name**|**Genre**
:-----:|:-----:|:-----:
0| Shawshank Redemption, The (1994)| Crime/Drama
1| Godfather, The (1972)| Crime/Drama
2| Rear Window (1954)| Mystery/Thriller
3| Paths of Glory (1957)| Drama/War
4| One Flew Over the Cuckoo's Nest (1975)| Drama
5| Princess Bride, The (1987)| Action/Adventure/Comedy/Fantasy/Romance
6| Lawrence of Arabia (1962)| Adventure/Drama/War
7| Goodfellas (1990)| Crime/Drama
8| Ran (1985)| Drama/War
9| Dark Knight, The (2008)| Action/Crime/Drama/IMAX

Dari hasil di atas, terlihat bahwa film dengan genre crime, horror, dan thriller memiliki peringkat tertinggi. Selanjutnya, sistem merekomendasikan sepuluh film teratas dengan genre crime dan drama.

## Evaluation

### Content-Based Filtering
Cosine Similarity adalah metode yang sering digunakan dalam content-based filtering untuk mengukur sejauh mana kesamaan antara dua item berdasarkan atribut atau fitur yang dimilikinya. Metode ini mengukur sudut kosinus antara dua vektor yang mewakili item-item tersebut dalam ruang atribut. Semakin kecil sudut kosinus antara vektor-vektor ini, semakin mirip atau serupa item-item tersebut dalam hal atribut atau fitur yang dianalisis.

Proses penggunaan Cosine Similarity dalam content-based filtering adalah sebagai berikut:

* Representasi Vektor: Setiap item diwakili oleh sebuah vektor yang mencerminkan atribut-atributnya. Misalnya, dalam konteks rekomendasi film, setiap film dapat direpresentasikan sebagai vektor yang berisi informasi seperti genre, sutradara, aktor, dll.
* Penghitungan Cosine Similarity: Untuk setiap pasangan item, Cosine Similarity dihitung dengan mengukur sudut kosinus antara vektor-vektor representasi item tersebut. Nilai Cosine Similarity berkisar antara -1 (sangat berlawanan) hingga 1 (sangat serupa).

Penentuan Rekomendasi: Item-item yang memiliki Cosine Similarity tinggi dengan item yang disukai pengguna atau item yang sedang dilihat dianggap lebih relevan dan kemungkinan direkomendasikan.


**Movie Name**|**Prime of Miss Jean Brodie, The (1969)**|**Coraline (2009)**|**Men in Black II (a.k.a. MIIB) (a.k.a. MIB 2) (2002)**|**Fly Away Home (1996)**|**Doors, The (1991)**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
Independence Day (a.k.a. ID4) (1996)|	0.000000|	0.178324|	0.752571|	0.270412|	0.000000
Match Factory Girl, The (Tulitikkutehtaan tyttö) (1990)|	0.600342|	0.000000|	0.287774|	0.000000|	0.600342
Penny Serenade (1941)|	0.531842|	0.000000|	0.000000|	0.000000|	0.531842
Batman v Superman: Dawn of Justice (2016)|	0.000000|	0.299805|	0.710506|	0.255297|	0.000000
Lion King, The (1994)|	0.175928|	0.286090|	0.000000|	0.538419|	0.175928
Once Bitten (1985)|	0.000000|	0.000000|	0.172784|	0.000000|	0.000000
Philadelphia Story, The (1940)|	0.433964|	0.000000|	0.208021|	0.000000|	0.433964
Country Girl, The (1954)|	1.000.000|	0.000000|	0.000000|	0.000000|	1.000.000
Rare Exports: A Christmas Tale (Rare Exports) (2010)|	0.000000|	0.000000|	0.611265|	0.000000|	0.000000
Solo: A Star Wars Story (2018)|	0.000000|	0.000000|	0.698339|	0.663164|	0.000000

Dengan cosine similarity, model berhasil mengidentifikasi kesamaan antara satu movie dengan restoran lainnya. Shape (1554, 1554) merupakan ukuran matriks similarity dari data yang dimiliki. Berdasarkan data yang ada, matriks di atas sebenarnya berukuran 1554 movie x 1554 movie (masing-masing dalam sumbu X dan Y). Artinya, model mengidentifikasi tingkat kesamaan pada 1554 nama movie.  

Berdasarkan hasil cosine similarity diatas data movie pada sumbu x memiliki kesamaan dengan data movie pada sumbu y, dapat dilihat movie Country Girl, The (1954) teridentifikasi sama *(similar)* dengan movie Prime of Miss Jean Brodie, The (1969) dan Doors, The (1991). 

### Collaborative Filtering
Proses evaluasi pada model machine learning ini, metrik yang digunakan adalah mean squared error (MSE). Metriks ini mengukur seberapa dekat hasil prediksi dari model dengan nilai sesungguhnya (titik data aktual) pada data pengujian. MSE menghitung selisih kuadrat antara nilai prediksi (Yi_pred) dan nilai sesungguhnya (Yi) dari setiap titik data, kemudian mengambil rata-rata dari selisih kuadrat tersebut untuk mendapatkan MSE. Berikut adalah rumusnya:

![Group 16](https://github.com/benisafangat/predictive-analytics/assets/70525105/d32cfd4e-97cb-4f36-8b89-1e8beaf985c0)

Keterangan:

* N = jumlah dataset
* Yi = nilai sebenarnya
* Yi_pred = nilai prediksi

Kelebihan dan Kekurangan dari metrik ini adalah:

Kelebihan: Metrik ini memberikan penalti yang lebih tinggi pada kesalahan besar, sehingga bisa lebih tepat dalam beberapa situasi.

Kekurangan: Metrik ini memberikan bobot yang relatif lebih tinggi pada kesalahan besar. Ini berarti RMSE menjadi lebih bermanfaat saat kesalahan besar sangat tidak diinginkan.

Dengan menggunakan MSE sebagai metrik evaluasi, dapat menilai seberapa baik performa model dalam melakukan rekomendasi movie. Semakin kecil nilai MSE, semakin dekat garis regresi model dengan titik data aktual, dan semakin akurat prediksi model.
Berikut adalah hasil model evaluasi metriks:

![metrics evaluasi](https://github.com/benisafangat/recommender-system/assets/70525105/d69bf724-f218-44c3-a7f4-f4b220b7967c)

Pada grafik diatas, hasil performa model menggunakan metrics evaluasi MSE didapatkan bahwa nilai pada MSE pada data latih dan data validasi hampir mendekati, ini artinya model dapat memberikan performa yang baik atau goodfit pada kasus ini.


## Kesimpulan
* Berdasarkan teknik pemodelan yang telah diterapkan, didapatkan bahwa kedua model dapat menghasilkan performa yang baik terhadap rekomendasi movie yang dihasilkan.
* Pada teknik collaborative filtering, nilai performa MSE yang didapatkan cukup baik dengan nilai rmse untuk data latih sebesar 0.1776 dan data validasi sebesar 0.1970. Serta nilai loss untuk data latih sebesar 0.5858 dan data validasi sebesar 0.6022.
* Untuk saran perbaikan dimasa yang akan datang yaitu gunakan datasets yang lebih besar dan melakukan tuning hyperparameter untuk mencapai performa yang maksimal.

## Referensi
* Lops, P., De Gemmis, M., & Semeraro, G. (2011). Content-based recommender systems: State of the art and trends. Recommender systems handbook, 73-105.
* Shakirova, E. (2017, February). Collaborative filtering for music recommender system. In 2017 IEEE Conference of Russian Young Researchers in Electrical and Electronic Engineering (EIConRus) (pp. 548-550). IEEE.
* Lubis, Y. I., Napitupulu, D. J., & Dharma, A. S. (2020). Implementasi Metode Hybrid Filtering (Collaborative dan Content-based) untuk Sistem Rekomendasi Pariwisata. In 12th Conference on Information Technology and Electrical Engineering (pp. 28-35).
* https://medium.com/@ahmadsholihin1705/rekomendasi-menggunakan-content-based-filtering-dan-collaborative-filtering-2aab2aec8ebe
