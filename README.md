# IDX Bank Stock's Analysis and Forecasting - Fajar Zulkautsari Muhammad

## Domain Proyek
Proyek ini merupakan sebuah analisis dan proyeksi terkait dengan saham bank yang terdaftar di Bursa Efek Indonesia (IDX). Bursa Efek Indonesia adalah salah satu bursa saham terkemuka di Asia Tenggara, dan sektor perbankan merupakan salah satu sektor yang signifikan dalam pasar saham Indonesia. Oleh karena itu, proyek ini memiliki latar belakang yang relevan dan penting dalam konteks ekonomi dan investasi di Indonesia. Berikut adalah beberapa alasan mengapa proyek ini dapat dijustifikasi:
- **Pentingnya Sektor Perbankan**: Sektor perbankan adalah tulang punggung ekonomi Indonesia. Bank-bank terdaftar di IDX memiliki dampak signifikan pada stabilitas dan pertumbuhan ekonomi nasional. Oleh karena itu, analisis dan proyeksi kinerja saham bank sangat penting untuk pemegang saham, investor, dan pengambil kebijakan.
- **Dampak Global**: Perbankan adalah industri yang terkait dengan pasar global, dan perubahan di pasar global dapat berdampak besar pada saham bank Indonesia. Faktor seperti suku bunga global, perubahan kebijakan moneter, dan peristiwa ekonomi global dapat memengaruhi kinerja saham bank di IDX.
- **Data Tersedia**: Data historis tentang kinerja saham bank yang terdaftar di IDX tersedia secara luas. Ini termasuk data harga saham harian, laporan keuangan, dan berbagai metrik kinerja lainnya. Data ini menjadi dasar penting untuk analisis dan proyeksi.
- **Minat Investor**: Saat ini, banyak investor, baik individu maupun institusi, yang tertarik untuk berinvestasi di pasar saham Indonesia. Analisis yang kuat tentang saham bank dapat memberikan wawasan berharga kepada investor tentang potensi peluang dan risiko dalam berinvestasi di sektor ini.
- **Pentingnya Peramalan**: Investor dan pemegang saham seringkali mencari informasi yang dapat membantu mereka merencanakan investasi mereka ke depan. Peramalan kinerja saham bank dapat memberikan panduan tentang bagaimana saham-saham ini dapat berkinerja dalam jangka waktu tertentu.

Dengan latar belakang tersebut, proyek ini akan bertujuan untuk menyediakan analisis tentang saham bank di IDX dan mungkin juga pendekatan kecerdasan buatan (AI) untuk meramalkan kinerja masa depan saham-saham tersebut. Proyek ini akan memberikan nilai tambah dalam pengambilan keputusan investasi dan pemahaman yang lebih baik tentang pasar saham Indonesia.

## Business Understanding
Proyek ini dapat diarahkan dengan lebih baik untuk memenuhi kebutuhan investor serta memberikan nilai tambah yang signifikan dalam pengambilan keputusan investasi di pasar saham Indonesia.

### Problem Statements
Masalah yang menjadi latar belakang proyek ini antara lain:
- **Volatilitas Pasar Saham**: Pasar saham Indonesia, seperti kebanyakan pasar saham di seluruh dunia, seringkali mengalami volatilitas tinggi. Fluktuasi harga saham dapat dipengaruhi oleh berbagai faktor seperti perubahan suku bunga, kondisi ekonomi, peristiwa geopolitik, dan berita perusahaan. Pemegang saham dan investor memerlukan pemahaman yang lebih baik tentang dinamika ini untuk mengelola risiko dan peluang investasi mereka.
- **Ketergantungan pada Sektor Perbankan**: Sektor perbankan Indonesia memiliki pengaruh besar dalam indeks saham utama, seperti IHSG (Indonesia Stock Exchange Composite Index). Oleh karena itu, kinerja saham bank-bank yang terdaftar di IDX sangat penting bagi kesehatan keseluruhan pasar saham.
- **Kebutuhan Investasi yang Diversifikasi**: Pemegang saham dan investor sering mencari peluang untuk diversifikasi portofolio mereka. Analisis yang kuat tentang saham bank dapat membantu mereka menentukan apakah sektor ini adalah pilihan investasi yang menarik dalam upaya diversifikasi.

### Goals

Tujuan dari proyek ini antara lain:
- **Menganalisis Kinerja Historis**: Salah satu tujuan proyek ini adalah untuk melakukan analisis menyeluruh terhadap kinerja historis saham bank yang terdaftar di IDX. Ini termasuk menganalisis data harga saham, volume perdagangan, dan indikator kinerja lainnya selama beberapa periode waktu.
- **Mengidentifikasi Tren dan Pola**: Proyek ini akan bertujuan untuk mengidentifikasi tren dan pola dalam kinerja saham bank. Ini termasuk pengenalan tren jangka pendek dan jangka panjang, serta pola pergerakan harga yang mungkin ada.
- **Meramalkan Kinerja Masa Depan**: Salah satu tujuan utama adalah meramalkan kinerja masa depan saham bank. Ini melibatkan penggunaan metode analisis yang tepat, seperti analisis fundamental dan/atau teknikal, serta potensi penerapan kecerdasan buatan (AI) untuk memprediksi harga saham.
- **Memberikan Rekomendasi Investasi**: Proyek ini akan memberikan rekomendasi investasi berdasarkan analisis dan proyeksi yang telah dilakukan. Rekomendasi ini akan membantu pemegang saham dan investor dalam pengambilan keputusan investasi yang lebih baik.
- **Memberikan Pemahaman tentang Risiko**: Selain rekomendasi investasi, proyek ini juga akan memberikan pemahaman yang lebih baik tentang risiko yang terkait dengan investasi di sektor perbankan. Ini termasuk risiko ekonomi, regulasi, dan risiko bisnis yang mungkin dihadapi oleh bank-bank tersebut.
- **Menginformasikan Keputusan Investasi**: Tujuan akhir dari proyek ini adalah memberikan informasi yang berharga kepada pemegang saham dan investor sehingga mereka dapat membuat keputusan investasi yang lebih terinformasi dan dapat mengelola portofolio mereka dengan lebih efektif.
Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

## Data Understanding
Dataset yang digunakan adalah data pergerakan harga saham dari TOP 5 saham Bank yang termasuk dalam Bursa Efek Indonesia (IDX). Dataset tersebut didapatkan dari situs [Yahoo! Finance](https://finance.yahoo.com/) dengan menggunakan [Yahoo! Finance API](https://pypi.org/project/yfinance/).

### Variabel-variabel pada dataset adalah sebagai berikut:
- **Open**       : Harga saham saat market dibuka di pagi hari
- **High**       : Titik harga saham tertinggi yang dicapai pada hari yang sama
- **Low**        : Titik harga saham terendah yang dicapai pada hari yang sama
- **Close**      : Harga saham saat market ditutup di sore hari
- **Adj Close**  : Harga saham saat market ditutup yang telah disesuaikan (misal ada stock split, dsb)
- **Volume**     : Jumlah volume transaksi saham yang terjadi pada hari yang sama

Dilakukan juga Exploratory Data Analysis (EDA) dan visualisasi terhadap data ini untuk mendapatkan informasi yang mendalam tentang perbandingan harga saham di sektor bank. EDA dan visualisasi dilakukan untuk mendapatkan informasi mengenai pergerakan harga saham dan volume transaksi harian dan juga dilihat dari daily return dan tingkat resiko dari masing-masing bank. Selain itu, Korelasi antar harga emiten ditinjau untuk mendapatkan emiten yang memiliki pengaruh terhadap emiten bank lainnya. Prediksi dengan model akan dilakukan pad emiten bank yang memiliki performa yang baik dengan potensi risiko yang rendah. 

Berdasarkan hasil analisis, emiten bank yang memiliki performa yg cukup stabil dan potensi resiko yg paling rendah adalah **BBCA**.

## Data Preparation 
Data preparation (persiapan data) adalah tahap kritis dalam proyek analisis dan peramalan saham seperti pada proyek ini. Dalam tahap ini, data mentah dikumpulkan, dimuat, dibersihkan, dan diubah menjadi bentuk yang dapat digunakan untuk analisis dan pemodelan. Berikut penjelasan lebih lanjut tentang data preparation dalam proyek ini:
- **Pengumpulan Data**: Tahap pertama adalah mengumpulkan data yang diperlukan untuk analisis. Data bersumber dari situs [Yahoo! Finance](https://finance.yahoo.com/) dengan menggunakan Yahoo! Finance API.
- **Transformasi Data**: Beberapa teknik transformasi data dilakukan untuk mendapatkan informasi yang tidak disediakan oleh dataset secara langsung. Seperti untuk mendapatkan nilai 'Daily Return' yang menjelaskan tentang persen untung/rugi emiten tersebut dalam sehari. 'Daily Return' didapatkan dengan cara mencari selisih (dalam bentuk persentase) dari harga 'close' pada hari ini dengan harga 'close' pada hari sebelumnya. nilai ini bisa didapatkan dengan menggunakan fungsi dari library Pandas, yaitu [pct_change()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.pct_change.html)
- **Pemisahan Data**: Data biasanya dibagi menjadi dua bagian, yaitu data pelatihan (training data) dan data pengujian (testing data). Data pelatihan digunakan untuk melatih model peramalan, sedangkan data pengujian digunakan untuk menguji kinerja model. Karena data yang digunakan merupakan Time Series yang sangat bergantung para urutan tanggal, data ini dipisah dengan cara dipotong dengan proposi 80% data awal sebagai data latih dan 20% data terakhir sebagai data latih.
- **Normalisasi dan Standarisasi**: Karena data yang digunakan mungkin memiliki rentang nilai yang berbeda, normalisasi atau standarisasi mungkin diperlukan. Normalisasi yang digunakan adalah [MinMaxScaler()](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html). MinMaxScaler akan mengubah interval data menjadi range antara 0 sampai dengan 1. Hal ini bertujuan untuk memastikan bahwa atribut data memiliki skala yang beragam.
- **Windowing Data**: Tujuan utama windowing data adalah untuk membagi data deret waktu menjadi segmen yang lebih kecil, sehingga memungkinkan analisis dan pemodelan yang lebih efektif. Dengan membagi data menjadi jendela waktu, Anda dapat mengidentifikasi pola, tren, atau perilaku dalam interval waktu tertentu yang mungkin tidak terlihat dalam data secara keseluruhan. Window size yang dipakai pada data adalah 60 data (60 hari) dengan lag 1 data (1 hari).
- **Validasi Data**: Validasi data melibatkan pemeriksaan akhir untuk memastikan bahwa data sudah siap digunakan. Ini termasuk memastikan tidak ada masalah yang belum teratasi dan bahwa data memiliki format yang sesuai seperti data shape, dsb.

## Modeling
Base Model Machine Learning yang digunakan pada proyek ini adalah LSTM (Long-Short Term Memory). LSTM cocok untuk proyek analisis dan peramalan saham karena mampu menangani data deret waktu harga saham dengan kemampuan memahami pola dan tren jangka panjang, mengingat informasi penting dari masa lalu, dan memproses data besar dengan fleksibilitas. LSTM juga dapat memodelkan pola kompleks, volatilitas harga saham, dan dapat berintegrasi dengan data tambahan seperti berita keuangan untuk meningkatkan kemampuan _forecasting_.

pada model ini menggunakan optimizers [**Adam**](https://keras.io/api/optimizers/adam/) dan loss function [**Huber**](https://www.tensorflow.org/api_docs/python/tf/keras/losses/Huber). Proses pelatihan model ini berlangsung selama 15 epochs, di mana satu epoch adalah satu kali proses pelatihan menggunakan seluruh dataset. Batch size sebesar 1 berarti model akan diperbarui setiap kali satu sampel data diberikan, yang sering disebut sebagai stochastic gradient descent (SGD) mini-batch dengan ukuran batch sebesar 1.

## Evaluation
Proses evaluasi yang dilakukan adalah dengan menggunakan metriks MAE (Mean Absolute Error) dan melakukan visualisasi terhadap hasil prediksi yang dihasilakn oleh model terhadap data test. Mean Absolute Error (MAE) adalah metrik evaluasi yang mengukur rata-rata kesalahan absolut antara prediksi model dan nilai sebenarnya dalam data. MAE menghasilkan skor kesalahan non-negatif, dan semakin kecil nilai MAE, semakin baik model dalam memprediksi nilai target. MAE sederhana, tahan terhadap outliers, dan mudah diinterpretasikan. Formula untuk menghitung nilai MAE adalah sebagai berikut:

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/9c351c9d-4fa2-4f33-ae60-8effd5620d50)
