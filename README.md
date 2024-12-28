# **EKSPLORASI PENGARUH GENRE MUSIK TERHADAP POPULARITAS LAGU PADA PLATFORM SPOTIFY**

![Spotify](assets/Spotify.jpg)

Genre musik memainkan peran penting dalam menentukan daya tarik dan popularitas sebuah lagu. Berbagai genre seperti pop, R&B, hip-hop, hingga K-Pop memiliki karakteristik unik yang memengaruhi respons pendengar. Tujuan utama penelitian ini adalah untuk memahami pola popularitas ini agar dapat memberikan wawasan berharga bagi musisi dalam menciptakan karya yang lebih resonan dengan audiens mereka.

Industri musik digital saat ini terus berkembang pesat dengan pola konsumsi musik yang berubah ke arah digital. Namun, bagaimana genre dan karakteristik lagu memengaruhi popularitasnya masih menjadi pertanyaan yang belum sepenuhnya terjawab. Oleh karena itu, penelitian ini bertujuan untuk mengeksplorasi data lagu dari Spotify dan menjawab pertanyaan kunci mengenai pola genre dan penyanyi tertentu dalam meningkatkan popularitas lagu.

Dataset yang digunakan berisi informasi tentang lebih dari 32.000 lagu yang dikumpulkan dari API Spotify, mencakup atribut seperti genre, popularitas, danceability, energi, valence, dan tempo. Data ini bersumber dari repositori [GitHub](https://github.com/rfordatascience/tidytuesday/blob/master/data/2020/2020-01-21/readme.md) yang mencatat lagu-lagu dirilis antara tahun 1921 hingga 2020. Analisis diawali dengan identifikasi genre musik yang dominan, mengatasi nilai yang hilang melalui imputasi rata-rata, serta mengecek tren waktu untuk memetakan evolusi popularitas genre tertentu.

## **Langkah-Langkah Analisis Data**
### **Instalasi yang Diperlukan**
1. **Instalasi Java Development Kit (JDK)**
    ```bash
    !apt-get install openjdk-8-jdk-headless -qq > /dev/null
    ```
2. **Unduh Apache Spark versi 3.5.1 dengan dukungan Hadoop 3**
    ```bash
    !wget -q http://archive.apache.org/dist/spark/spark-3.5.1/spark-3.5.1-bin-hadoop3.tgz
    ```
3. **Ekstrak File Spark**
    ```bash
    !tar xf spark-3.5.1-bin-hadoop3.tgz
    ```
4. **Instal Pustaka findspark**
    ```bash
    !pip install -q findspark
    ```
5. **Langkah Opsional: Verifikasi Ekstraksi Spark**
   ```bash
   !tar xf spark-3.5.1-bin-hadoop3.tgz
    ```
### **Pembersihan Data**
- Mengatasi nilai yang hilang dengan pengisian (imputasi) rata-rata.
- Konversi tipe data yang diperlukan untuk analisis, misalnya dari string ke float.
- Normalisasi atribut numerik tertentu agar lebih mudah dianalisis.

## **Eksplorasi dan Analisis Data**
### **Analisis Tren Waktu**
![Tren Waktu](assets/Tren@20Waktu.png)

Popularitas lagu mencapai puncaknya pada tahun 1960 dengan skor lebih dari 70, sebelum mengalami penurunan tajam pada awal 1960-an. Selama 1960-an hingga 1980-an, terjadi fluktuasi signifikan dengan rata-rata skor di kisaran 40-50. Tren penurunan berlanjut pada 1990-an hingga awal 2010-an, dengan popularitas stabil pada skor 30-40, kemungkinan dipengaruhi oleh perubahan preferensi musik. Setelah 2010, popularitas rata-rata meningkat kembali, mencapai lebih dari 50 pada akhir dekade 2010-an hingga 2020.

### **Korelasi Antar Fitur Numerik**
![Fitur Numerik](assets/Korelasi@20Antar@20Fitur@20Numerik.png)

Nilai korelasi berkisar dari -1 hingga 1, di mana:
- 1 menunjukkan hubungan positif sempurna: ketika satu fitur meningkat, fitur lain juga meningkat secara proporsional.
- -1 menunjukkan hubungan negatif sempurna: ketika satu fitur meningkat, fitur lain menurun secara proporsional.
- 0 menunjukkan tidak ada hubungan linear antara kedua fitur.

**Beberapa poin penting:**
- Track Popularity memiliki korelasi rendah dengan fitur lain, tertinggi dengan acousticness (0.09) dan negatif dengan duration_ms (-0.14) serta instrumentalness (-0.15).
- Energy dan Loudness sangat berkorelasi (0.68), menunjukkan lagu energik cenderung lebih keras.
- Danceability berkorelasi dengan Valence (0.33), menandakan lagu positif lebih mudah untuk menari.
- Acousticness negatif dengan Energy (-0.54), menunjukkan lagu akustik cenderung kurang energik.

### **Popularitas Berdasarkan Genre**
![Popularitas Berdasarkan Genre](assets/Popularitas@20Berdasarkan@20Genre.png)

Visualisasi ini dapat membantu untuk mengidentifikasi genre mana yang memiliki rata-rata popularitas tertinggi dan mana yang lebih rendah. Ada beberapa genre dengan label yang kurang deskriptif atau menggunakan ID unik.
Jadi genre latin adalah yang memiliki popularitas tertinggi. Kemudian genre dengaan popularitas rendah mungkin memiliki lagu-lagu yang kurang dikenal atau segmentasi pasar yang lebih kecil.

### **Popularitas Berdasarkan Mode (Mayor/Minor)**
![Popularitas Berdasarkan Mode](assets/Popularitas@20Berdasarkan@20Mode.png)

Visualisasi ini menunjukkan bagaimana mode atau fitur musik tertentu berkorelasi dengan tingkat popularitasnya. Misalnya: Lagu dalam mode tertentu, seperti "1", cenderung lebih populer daripada lagu dalam mode lainnya. Lagu dalam kategori tertentu, seperti "progressive electro house", juga cukup populer.

### **Tren Berdasarkan Fitur Audio (Energy dan Danceability)**
![Fitur Audio](assets/Tren@20Berdasarkan@20Fitur@20Audio.png)

Danceability dan energy berkontribusi pada karakteristik lagu, tetapi popularitas tidak hanya dipengaruhi oleh kedua faktor tersebut. Visualisasi ini memberikan gambaran menyeluruh tentang distribusi lagu dalam hal danceability, energy, dan bagaimana popularitas tersebar di antara kombinasi ini.

### **Visualisasi PCA: Popularitas Lagu**
![Visualisasi PCA](assets/Visualisasi@20PCA.png)

Visualisasi ini menunjukkan bagaimana lagu-lagu dengan berbagai tingkatan popularitas tersebar dalam ruang dimensi yang dihasilkan PCA (Principal Component Analysis). Lagu dengan popularitas tertinggi ditunjukkan oleh warna merah, menunjukkan bahwa fitur numerik tertentu memiliki hubungan yang kuat dengan popularitas. Sebaliknya, jika warna tersebar merata, berarti fitur yang digunakan tidak cukup untuk memprediksi popularitas dengan baik.

## **Clustering**
### **Berdasarkan Danceability, Energy, dan Track Popularity**
![Clustering1](assets/Clustering@20Berdasarkan@20danceability,@20energy,@20dan@20popularitas.png)

Visualisasi ini menunjukkan bagaimana lagu-lagu dapat dikelompokkan berdasarkan danceability, energy, dan popularitas.

### **Berdasarkan Danceability dan Energy**
![Clustering2](assets/Clustering@20Berdasarkan@20Danceability@20dan@20Energy.png)

Setiap klaster memiliki karakteristik berikut:
- Klaster kuning (Danceability tinggi, Energy tinggi): Lagu-lagu yang cenderung energik dan sangat cocok untuk aktivitas menari.
- Klaster ungu (Danceability rendah, Energy tinggi): Lagu-lagu dengan energi tinggi tetapi kurang danceable, mungkin cocok untuk genre tertentu seperti lagu keras atau intens tetapi tidak untuk menari.
- Klaster hijau toska (Danceability rendah, Energy tinggi): Lagu-lagu dengan energi tinggi tetapi kurang danceable, mungkin cocok untuk suasana santai atau introspektif.

### **Hubungan antara Tempo dan Popularity**
![Hubungan Tempo dan Popularitas](assets/Hubungan@20antara@20Tempo@20dan@20Popularitas.png)
Visualisasi ini menunjukkan hubungan antara tempo, atau kecepatan sebuah lagu, dan popularitasnya. Jadi popularitas sebuah lagu tidak dipengaruhi secara langsung oleh tempo. Sebaliknya, lagu dengan kecepatan yang berbeda memiliki peluang yang sama untuk menjadi populer.

## Author
[Nazilullaily Nur Aisyah]
[Valencia Sefiana Putri]
