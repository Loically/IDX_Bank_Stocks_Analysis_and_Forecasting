# IDX Bank Stock's Analysis and Forecasting - Fajar Zulkautsari Muhammad

## Domain Proyek
Dalam beberapa tahun terakhir, Indonesia telah mencatat pertumbuhan ekonomi yang stabil, yang memberikan dukungan fundamental bagi sektor bisnis dan perusahaan yang terdaftar di bursa saham. Tren investasi juga mengalami perubahan[[1]](https://journal3.uin-alauddin.ac.id/index.php/Iqtisaduna/article/view/20214). Peran regulasi dalam meningkatkan transparansi dan keamanan pasar saham juga menjadi faktor penting. Selain itu, dampak pandemi COVID-19 tidak dapat diabaikan[[2]](https://journal.ipb.ac.id/index.php/jmo/article/view/32657), menghadirkan volatilitas dan liquiditas yang tinggi[[3]](https://ejournal.unisnu.ac.id/JDEB/article/view/20) dan memaksa pasar untuk beradaptasi dengan perubahan kondisi ekonomi yang cepat. Akhirnya, meningkatnya perhatian investor global terhadap saham-saham Indonesia telah menciptakan dinamika tambahan dalam pasar saham domestik. Pemahaman yang mendalam tentang semua faktor ini adalah kunci dalam mengambil keputusan investasi yang cerdas dan berinformasi.

Dalam era digital ini, peramalan harga saham memiliki peran yang sangat penting dalam pengambilan keputusan investasi[[4]](https://ieeexplore.ieee.org/abstract/document/9350582). Para investor, pedagang saham, dan institusi keuangan bergantung pada analisis yang cermat dan peramalan yang akurat untuk mengidentifikasi peluang investasi dan mengelola risiko. Dalam proyek ini akan memanfaatkan kecerdasan buatan, khususnya _Long Short-Term Memory_ (LSTM), untuk mengembangkan model peramalan harga saham yang kuat dan andal.

Proyek ini bertujuan untuk merinci dan menganalisis proses peramalan harga saham berdasarkan data historis, faktor-faktor pasar, dan tren yang relevan. Dalam latar belakang yang berfokus pada sektor perbankan, kita akan menggali peran bank dalam ekonomi dan pentingnya memahami perilaku harga saham bank. Lalu, dengan pemahaman yang mendalam tentang masalah bisnis, kita akan merumuskan tujuan proyek dan menciptakan kerangka kerja untuk mengatasi tantangan peramalan harga saham.

## Business Understanding
### Problem Statements
Masalah yang menjadi latar belakang proyek ini antara lain:
- Bagaimana analisis terhadap harga saham sektor perbankan?
- Bagaimana strategi investasi yang tepat pada saham sektor perbankan?

### Goals
Tujuan dari proyek ini antara lain:
- Mengimplementasikan Exploratory Data Analysis (EDA) untuk mengetahui performa saham di sektor perbankan.
- Melakukan prediksi harga saham yang dapat digunakan sebagai acuan dalam membuat keputusan strategi investasi.

### Solution Statements:
Masalah dan tujuan yang telah diuraikan diatas dapat diselesaikan dengan pendekatan Machine Learning untuk melakukan _forecasting_ pergerakan harga saham. Salah satu model yang bisa melakukan hal tersebut adalah model LSTM _(Long-Short Term Memory)_ sebagai baseline model.

## Data Understanding
Dataset yang digunakan adalah data pergerakan harga saham dari TOP 5 saham Bank yang termasuk dalam Bursa Efek Indonesia (IDX). Dataset tersebut didapatkan dari situs [Yahoo! Finance](https://finance.yahoo.com/) dengan menggunakan [Yahoo! Finance API](https://pypi.org/project/yfinance/). Dalam Analisis, data yang digunakan yaitu data dalam 3 tahun terakhir dengan jumlah data 729 data per emiten bank. Dengan total 5 emiten bank yang dianalisis sehingga jumlah data untuk analisis adalah sebanyak 3645 data. Sedangkan untuk _forecasting_, data yang digunakan adalah data emiten saham BBCA dengan total data maksimal yang bisa didapatkan dari dari situs Yahoo! Finance yaitu sejak 08 Juni 2004 hingga kini (10 September 2023) dengan jumlah data sebanyak 4773 data.

### Variabel-variabel pada dataset adalah sebagai berikut:
- **Open**       : Harga saham saat market dibuka di pagi hari
- **High**       : Titik harga saham tertinggi yang dicapai pada hari yang sama
- **Low**        : Titik harga saham terendah yang dicapai pada hari yang sama
- **Close**      : Harga saham saat market ditutup di sore hari
- **Adj Close**  : Harga saham saat market ditutup yang telah disesuaikan (misal ada _stock split_, dsb)
- **Volume**     : Jumlah volume transaksi saham yang terjadi pada hari yang sama

_Exploratory Data Analysis_ (EDA) dan visualisasi dilakukan untuk mendapatkan informasi yang mendalam tentang perbandingan harga saham di sektor bank. EDA dan visualisasi dilakukan untuk mendapatkan informasi mengenai pergerakan harga saham dan volume transaksi harian dan juga dilihat dari _daily return_ dan tingkat resiko dari masing-masing bank.
![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/007b9f10-0b16-4dde-92b2-cb124bd21284)

Jika dilihat dari pola pergerakan harga saham di atas, BBCA, BBNI dan BBRI memiliki pola _uptrend_ yang cukup baik. Sebenarnya, BMRI juga memiliki pola _uptrend_ tapi terdapat lonjakan di tahun 2023 yang bisa dikatan terjadi pergerakan harga yang anomali. di sisi lain, BRIS mengalami _uptrend_ sampai 2021 dan kemudian _downtrend_ dan _sideways_.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/79984cfb-64b3-4911-b68d-0d6f463bbb29)

Selain itu, Korelasi antar harga emiten ditinjau untuk mendapatkan emiten yang memiliki pengaruh terhadap emiten bank lainnya. Jika ditinjau dari _heatmap_ di atas, dapat dikatakan bahwa tidak ada korelasi yang sangat signifikan dalam hal _return_ saham harian. Namun, pada harga saham, 4 dari 5 bank memiliki korelasi yang sangat signifikan, hanya BRIS yang tidak memiliki korelasi dengan semua bank.

Salah satu cara untuk mengetahui potensi risiko adalah dengan membandingkan rata-rata return harian dengan standar deviasi. Rata-rata _return_ harian merupakan representasi dari nilai ekspektasi keuntungan yang diperoleh dan standar deviasi merupakan sebaran dari keuntungan yang mungkin diperoleh. Semakin besar standar deviasi, maka semakin besar pula potensi risikonya.
![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/8958489b-6079-46db-a897-087f90ffb927)

Terlihat bahwa BBCA memiliki potensi risiko paling rendah yaitu sekitar 1%. Diikuti oleh BBRI dan BBNI yang juga memiliki potensi risiko yang cukup rendah yaitu sekitar 1,7%. Kemudian, ada BRIS dengan 3,5% dan yang paling berisiko adalah BMRI dengan potensi risiko 4,5%.
Berdasarkan hasil analisis, emiten bank yang memiliki performa yg cukup stabil dan potensi resiko yg paling rendah adalah **BBCA**.

## Data Preparation 
_Data preparation_ (persiapan data) adalah tahap kritis dalam proyek analisis dan peramalan saham seperti pada proyek ini. Dalam tahap ini, data mentah dikumpulkan, dimuat, dibersihkan, dan diubah menjadi bentuk yang dapat digunakan untuk analisis dan pemodelan. Berikut penjelasan lebih lanjut tentang data preparation dalam proyek ini:
- **Pengumpulan Data**: Tahap pertama adalah mengumpulkan data yang diperlukan untuk analisis. Data bersumber dari situs [Yahoo! Finance](https://finance.yahoo.com/) dengan menggunakan Yahoo! Finance API.
- **Transformasi Data**: Beberapa teknik transformasi data dilakukan untuk mendapatkan informasi yang tidak disediakan oleh dataset secara langsung. Seperti untuk mendapatkan nilai _'Daily Return'_ yang menjelaskan tentang persen untung/rugi emiten tersebut dalam sehari. _'Daily Return'_ didapatkan dengan cara mencari selisih (dalam bentuk persentase) dari harga _'close'_ pada hari ini dengan harga _'close'_ pada hari sebelumnya. Nilai ini bisa didapatkan dengan menggunakan fungsi dari _library_ Pandas, yaitu [pct_change()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.pct_change.html)
- **Pemisahan Data**: Data biasanya dibagi menjadi dua bagian, yaitu data pelatihan _(training data)_ dan data pengujian _(testing data)_. Data pelatihan digunakan untuk melatih model peramalan, sedangkan data pengujian digunakan untuk menguji kinerja model. Karena data yang digunakan merupakan _Time Series_ yang sangat bergantung para urutan tanggal, data ini dipisah dengan cara dipotong dengan proposi 80% data awal sebagai data latih dan 20% data terakhir sebagai data latih.
- **Normalisasi dan Standarisasi**: Karena data yang digunakan mungkin memiliki rentang nilai yang berbeda, normalisasi atau standarisasi diperlukan. Normalisasi yang digunakan adalah [_MinMaxScaler()_](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html). _MinMaxScaler_ akan mengubah interval data menjadi range antara 0 sampai dengan 1. Hal ini bertujuan untuk memastikan bahwa atribut data memiliki skala yang beragam. _MinMaxScaler_ digunakan karena cocok untuk melakukan normalisasi terhadap data harga yang tidak mungkin ada nilai negatif. Range harga saham yang berkisar antara 729 - 9400 akan dinormalisasi menjadi range 0 - 1.

$$
X_{\text{scaled}} = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}
$$

- **_Windowing_ Data**: Tujuan utama _windowing_ data adalah untuk membagi data deret waktu menjadi segmen yang lebih kecil, sehingga memungkinkan analisis dan pemodelan yang lebih efektif. Dengan membagi data menjadi jendela waktu, data akan dipisah untuk dijadikan atribut dan label. Window size yang dipakai pada data adalah 50 data (50 hari) dengan lag 1 data (1 hari).
- **Validasi Data**: Validasi data melibatkan pemeriksaan akhir untuk memastikan bahwa data sudah siap digunakan. Ini termasuk memastikan tidak ada masalah yang belum teratasi dan bahwa data memiliki format yang sesuai seperti data shape, dsb.

## Modeling
_Base Model Machine Learning_ yang digunakan pada proyek ini adalah LSTM _(Long-Short Term Memory)_. LSTM cocok untuk proyek analisis dan peramalan saham karena mampu menangani data deret waktu harga saham dengan kemampuan memahami pola dan tren jangka panjang, mengingat informasi penting dari masa lalu, dan memproses data besar dengan fleksibilitas. LSTM juga dapat memodelkan pola kompleks, volatilitas harga saham, dan dapat berintegrasi dengan data tambahan seperti berita keuangan untuk meningkatkan kemampuan _forecasting_. 

Infrastruktur dari model ini menggunakan 2 lapisan LSTM, 2 _Hidden layer_ dan sebuah _output layer_ dengan rincian sebagai berikut : 
**1. Lapisan LSTM Pertama (LSTM):**
Output Shape: (None, 50, 128)
Jumlah Parameter: 66,560
Lapisan LSTM pertama memiliki 128 unit neuron. Ini adalah lapisan sekuensial yang mengambil input dalam bentuk sekuens data dengan panjang 50 (sesuai dengan windowed_data) dan menghasilkan output sekuensial. Output ini akan menjadi input untuk lapisan LSTM berikutnya.

**2. Lapisan LSTM Kedua (LSTM_1):**
Output Shape: (None, 64)
Jumlah Parameter: 49,408
Lapisan LSTM kedua memiliki 64 unit neuron. Ini adalah lapisan LSTM yang mengambil output sekuensial dari lapisan sebelumnya dan menghasilkan keluaran yang tidak sekuensial, tetapi berdimensi 64.

**3. Lapisan Dense Pertama (Dense):**
Output Shape: (None, 10)
Jumlah Parameter: 650
Fungsi Aktivasi: ReLU
Lapisan ini adalah lapisan tersembunyi pertama dengan 10 unit neuron dan fungsi aktivasi ReLU. Lapisan ini bertanggung jawab untuk menggabungkan dan mengolah informasi dari lapisan LSTM sebelumnya.

**4. Lapisan Dense Kedua (Dense_1):**
Output Shape: (None, 5)
Jumlah Parameter: 55
Fungsi Aktivasi: ReLU
Lapisan ini adalah lapisan tersembunyi kedua dengan 5 unit neuron dan fungsi aktivasi ReLU. Lapisan ini membantu model dalam memahami pola yang lebih kompleks dalam data.

**5. Lapisan Output (Dense_2):**
Output Shape: (None, 1)
Jumlah Parameter: 6
Lapisan ini adalah lapisan output dengan 1 unit neuron tanpa fungsi aktivasi tertentu. Lapisan ini menghasilkan prediksi harga saham.
Total parameter dalam model ini adalah 116,679, dan semua parameter ini dapat disesuaikan selama proses pelatihan. Model ini dirancang untuk memahami pola sekuensial dalam data harga saham dan menghasilkan prediksi yang akurat.

Pada model ini menggunakan optimizers [**Adam**](https://keras.io/api/optimizers/adam/) dan loss function [**Huber**](https://www.tensorflow.org/api_docs/python/tf/keras/losses/Huber). Optimizer Adam dipilih karena memiliki kemampuan untuk mengadaptasi _Learning Rate_. _Learning rate_ adalah pengatur kecepatan pembelajaran model selama pelatihan. Ini menentukan seberapa besar langkah yang diambil dalam arah yang mengurangi nilai _loss function_. _Learning rate_ yang lebih besar akan menghasilkan langkah yang lebih besar, sementara _learning rate_ yang lebih kecil akan menghasilkan langkah yang lebih kecil. Harga saham dapat mengalami fluktuasi yang signifikan dari waktu ke waktu. Optimizer Adam dengan kemampuannya untuk mengadaptasi learning rate secara dinamis membantu model beradaptasi dengan fluktuasi ini. selain itu juga Adam cukup efisien dalam hal konvergensi. Ini adalah hal yang positif karena model perlu cepat menyesuaikan diri dengan perubahan dalam data harga saham yang dapat terjadi dalam jangka waktu yang singkat.

Sedangkan _loss function_ Huber dipilih karena data harga saham seringkali rentan terhadap peristiwa eksternal atau berita yang dapat menghasilkan outlier. Fungsi kerugian Huber, yang merupakan kombinasi antara _Mean Absolute Error_ (MAE) dan _Mean Squared Error_ (MSE), lebih toleran terhadap outlier daripada MSE. Ini memungkinkan model untuk tidak terlalu dipengaruhi oleh peristiwa yang tidak biasa atau anomali dalam data harga saham. 

Proses pelatihan model ini menggunakan metode GSD _(Graduate Student Descent)_ untuk mencari secara manual _Hyperparameter_ yang mendapatkan hasil terbaik. Sehingga didapatkan _Learning Rate_ 1e-3, berlangsung selama 15 _epochs_, dan _batch size_ sebesar 5. Di mana satu _epoch_ adalah satu kali proses pelatihan menggunakan seluruh dataset. _Batch size_ sebesar 5 berarti model akan diperbarui setiap 5 kali sampel data diberikan. 

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/4d384d4b-802b-4561-b449-56d85c35db39)

Dilihat dari grafik histori pelatihan, MAE yang didapatkan cenderung mengalami penurunan yang artinya model semakin baik. Hasil pelatihan model dengan _hyperparameter_ tersebut mendapatkan hasil yang cukup baik dengan MAE 0.0043 atau hanya sebesar 0.43% dan _train loss_ sebesar 1.7753e-05.

## Evaluation
Proses evaluasi yang dilakukan adalah dengan menggunakan metriks MAE dan melakukan visualisasi terhadap hasil prediksi yang dihasilkan oleh model terhadap data test. MAE adalah metrik evaluasi yang mengukur rata-rata kesalahan absolut antara prediksi model dan nilai sebenarnya dalam data. MAE menghasilkan skor kesalahan non-negatif, dan semakin kecil nilai MAE, semakin baik model dalam memprediksi nilai target. Formula MAE dapat diilustrasikan sebagai berikut :

$$
MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|
$$

Dimana:
- $MAE$ adalah Mean Absolute Error.
- $n$ adalah jumlah sampel.
- $y_i$ adalah nilai sebenarnya dari sampel ke-i.
- $hat{y}_i$ adalah nilai perkiraan dari sampel ke-i.

![image](https://github.com/Loically/IDX_Bank_Stocks_Analysis_and_Forecasting/assets/114181235/640399e1-ebc1-4e70-8fcb-df40b26303f8)

Hasil prediksi model divisualisasikan seperti pada gambar di atas. Terlihat bahwa pada data test, prediksi yang dihasilkan model (garis hijau) cukup berhimpit dengan nilai sebenarnya (garis kuning). Sehingga model dikatakan cukup baik dalam memprediksikan harga saham dengan MAE pada prediksi sebesar 86.902 dari nilai maksimum 9400 (0.9244%). 

Dengan hasil ini, diharapkan model bisa membantu investor untuk membuat keputusan strategi investasi yang lebih baik. Seperti contohnya trader bisa melakukan trading jangka pendek/menengah dengan cara pembelian saat prediksi model berada dibawah atau harga saham sedang mengalami koreksi dan saat sedang berada dipuncak (sebelum koreksi kembali). Dan juga untuk investor yg bisa membeli pada saat harga sedang koreksi atau turun. 


