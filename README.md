# **EKSPLORASI PENGARUH GENRE MUSIK TERHADAP POPULARITAS LAGU PADA PLATFORM SPOTIFY**

![Spotify](assets/Spotify.jpg)
Genre musik memainkan peran penting dalam menentukan daya tarik dan popularitas sebuah lagu. Berbagai genre seperti pop, R&B, hip-hop, hingga K-Pop memiliki karakteristik unik yang memengaruhi respons pendengar. Tujuan utama penelitian ini adalah untuk memahami pola popularitas ini agar dapat memberikan wawasan berharga bagi musisi dalam menciptakan karya yang lebih resonan dengan audiens mereka.

Industri musik digital saat ini terus berkembang pesat dengan pola konsumsi musik yang berubah ke arah digital. Namun, bagaimana genre dan karakteristik lagu memengaruhi popularitasnya masih menjadi pertanyaan yang belum sepenuhnya terjawab. Oleh karena itu, penelitian ini bertujuan untuk mengeksplorasi data lagu dari Spotify dan menjawab pertanyaan kunci mengenai pola genre dan penyanyi tertentu dalam meningkatkan popularitas lagu.

Dataset yang digunakan berisi informasi tentang lebih dari 32.000 lagu yang dikumpulkan dari API Spotify, mencakup atribut seperti genre, popularitas, danceability, energi, valence, dan tempo. Data ini bersumber dari repositori [GitHub](https://github.com/rfordatascience/tidytuesday/blob/master/data/2020/2020-01-21/readme.md)yang mencatat lagu-lagu dirilis antara tahun 1921 hingga 2020. Analisis diawali dengan identifikasi genre musik yang dominan, mengatasi nilai yang hilang melalui imputasi rata-rata, serta mengecek tren waktu untuk memetakan evolusi popularitas genre tertentu.

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
### **Korelasi Antar Fitur Numerik**
![Fitur Numerik](assets/Korelasi@20Antar@20Fitur@20Numerik.png)
### **Popularitas Berdasarkan Genre**
![Popularitas Berdasarkan Genre](assets/Popularitas@20Berdasarkan@20Genre.png)
### **Tren Berdasarkan Fitur Audio (Energy dan Danceability)**
![Fitur Audio](assets/Tren@20Berdasarkan@20Fitur@20Audio.png)
### **Visualisasi PCA: Popularitas Lagu**
![Visualisasi PCA](assets/Visualisasi@20PCA.png)

## 

## Author
[Nazilullaily Nur Aisyah]
[Valencia Sefiana Putri]
