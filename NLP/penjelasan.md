# Penjelasan Proyek UAS NLP - Pipeline Analisis Teks Ulasan Hotel

## Bagian 1: Pra-pemrosesan Teks (Bobot: 20%)

### 1.1 Deskripsi dan Tujuan Preprocessing
Preprocessing adalah langkah awal yang sangat penting dalam pipeline NLP. Tujuan utama preprocessing adalah membersihkan dan menyiapkan data teks mentah agar siap diproses oleh algoritma machine learning. Dalam konteks dataset ulasan hotel, preprocessing membantu memperbaiki kualitas data sehingga model dapat belajar dengan lebih efektif.

### 1.2 Teknik Preprocessing yang Diterapkan

#### 1.2.1 Case Folding
Case folding adalah proses mengubah semua huruf dalam teks menjadi bentuk lowercase (huruf kecil). Dalam implementasi ini, semua teks diubah menjadi huruf kecil untuk menghindari perbedaan antara kata yang sebenarnya sama tetapi berbeda penulisan kapitalnya, misalnya "Hotel" dan "hotel".

Contoh:
- Sebelum: "Hotel Ini Sangat Bagus!"
- Setelah: "hotel ini sangat bagus!"

#### 1.2.2 Tokenisasi
Tokenisasi adalah proses memecah teks menjadi unit-unit kecil yang disebut token, biasanya berupa kata-kata. Dalam Python menggunakan library NLTK, fungsi `word_tokenize()` digunakan untuk memisahkan kalimat menjadi kata-kata individual.

Contoh:
- Teks: "hotel ini sangat bagus"
- Token: ["hotel", "ini", "sangat", "bagus"]

#### 1.2.3 Stopword Removal
Stopword adalah kata-kata umum yang tidak membawa informasi signifikan dan biasanya dihapus dari teks untuk mengurangi noise. Contoh stopword dalam bahasa Indonesia adalah "yang", "dan", "di", "ada", "akan", dll. Dalam implementasi, kita menggunakan daftar stopword dari NLTK untuk bahasa Indonesia.

#### 1.2.4 Cleaning
Proses cleaning menghilangkan karakter-karakter yang tidak relevan seperti tanda baca, angka, atau simbol-simbol khusus. Dalam implementasi ini, kita menggunakan ekspresi reguler (regex) untuk menghapus semua karakter selain huruf dan spasi:
`re.sub(r'[^a-zA-Z\s]', ' ', text)`

#### 1.2.5 Stemming
Stemming adalah proses mengubah kata-kata ke bentuk kata dasarnya. Dalam implementasi ini, kita menggunakan library Sastrawi yang memiliki stemmer untuk bahasa Indonesia. Contoh:
- "membangun" → "bangun"
- "berlari" → "lari"
- "berkata" → "kata"

#### 1.2.6 Perbandingan Data Sebelum dan Sesudah Preprocessing

**Data Sebelum Preprocessing:**
| No | Teks Asli |
|----|-----------|
| 1  | Hotel Ini Sangat Bagus Dan Bersih! |
| 2  | Pelayanan Buruk Dan Kamar Kotor. |
| 3  | Harga Terjangkau Dan Fasilitas Lengkap. |
| 4  | Makanan Enak Dan Staf Ramah! |
| 5  | Kamar Sempit Dan Tidak Nyaman. |

**Data Setelah Preprocessing:**
| No | Teks Setelah Preprocessing |
|----|-----------------------------|
| 1  | hotel bagus bersih |
| 2  | layan buruk kamar kotor |
| 3  | harga terjangkau fasilitas lengkap |
| 4  | makan enak staf ramah |
| 5  | kamar sempit nyaman |

### 1.3 Pentingnya Preprocessing Sebelum Machine Learning
Preprocessing sangat penting dilakukan sebelum masuk ke tahap machine learning karena:

1. **Konsistensi Data**: Menghasilkan representasi konsisten dari kata yang sama meskipun ditulis dengan cara berbeda
2. **Reduksi Noise**: Menghilangkan informasi yang tidak relevan sehingga fokus pada fitur penting
3. **Efisiensi Model**: Mengurangi dimensi data dan kompleksitas sehingga model lebih cepat belajar
4. **Kualitas Fitur**: Meningkatkan kualitas fitur yang digunakan untuk training model
5. **Keakuratan Model**: Dengan data bersih, model dapat belajar pola yang lebih relevan

## Bagian 2: Klasifikasi Teks (Bobot: 30%)

### 2.1 Deskripsi dan Tujuan Klasifikasi Teks
Tujuan dari klasifikasi teks adalah membangun model yang dapat secara otomatis menentukan kategori atau sentimen dari teks ulasan hotel. Dalam proyek ini, kita berfokus pada klasifikasi sentimen binary, yaitu menentukan apakah ulasan bersifat positif atau negatif.

### 2.2 Algoritma yang Digunakan

#### 2.2.1 Naive Bayes
Naive Bayes adalah algoritma klasifikasi probabilistik berdasarkan Teorema Bayes dengan asumsi independensi antar fitur. Algoritma ini sangat efektif untuk tugas klasifikasi teks karena:

- Cepat dan efisien dalam pelatihan
- Baik dalam menangani data dengan banyak fitur
- Performa yang bagus untuk tugas klasifikasi teks

#### 2.2.2 Support Vector Machine (SVM)
SVM adalah algoritma yang mencari hyperplane optimal untuk memisahkan data dalam ruang fitur berdimensi tinggi. SVM cocok untuk klasifikasi teks karena:

- Efektif dalam ruang berdimensi tinggi
- Tahan terhadap overfitting
- Bagus untuk tugas binary classification

### 2.3 TF-IDF (Term Frequency-Inverse Document Frequency)
TF-IDF adalah metode untuk menghitung bobot pentingnya sebuah kata dalam sebuah dokumen terhadap kumpulan dokumen. Metode ini mengubah teks menjadi representasi numerik yang dapat diproses oleh algoritma machine learning.

Rumus TF-IDF:
- TF = (Jumlah kemunculan kata dalam dokumen) / (Jumlah total kata dalam dokumen)
- IDF = log(Total dokumen / Jumlah dokumen yang mengandung kata tersebut)
- TF-IDF = TF * IDF

### 2.4 Pembagian Data (Train-Test Split)
Data dibagi menjadi dua bagian:
- Data latih (80%): Digunakan untuk melatih model
- Data uji (20%): Digunakan untuk mengevaluasi kinerja model

Pembagian dilakukan secara acak dengan proporsi tetap untuk menjaga distribusi kelas tetap seimbang di antara data latih dan uji.

### 2.5 Hasil Evaluasi Model

#### 2.5.1 Model Naive Bayes
- Akurasi: [Nilai akurasi akan diisi saat eksekusi]
- Classification Report: [Akan ditampilkan metriks presisi, recall, dan F1-score]

#### 2.5.2 Model SVM
- Akurasi: [Nilai akurasi akan diisi saat eksekusi]
- Classification Report: [Akan ditampilkan metriks presisi, recall, dan F1-score]

### 2.6 Analisis Hasil
Berdasarkan hasil akurasi dari kedua model, kita dapat menganalisis:
- Algoritma mana yang lebih efektif untuk tugas klasifikasi sentimen ini
- Kekuatan dan kelemahan masing-masing model
- Faktor-faktor yang mempengaruhi kinerja model

## Bagian 3D: Chatbot Sederhana (Bobot: 50%)

### 3.1 Deskripsi dan Tujuan Chatbot
Chatbot sederhana untuk layanan pelanggan hotel bertujuan untuk menyediakan jawaban otomatis terhadap pertanyaan-pertanyaan umum dari pelanggan. Ini merupakan implementasi dasar dari sistem dialog berbasis aturan (rule-based).

### 3.2 Intent yang Diimplementasikan
Dalam chatbot ini, kita mendefinisikan minimal 3 intent utama:

#### 3.2.1 Intent "Salam"
- Tujuan: Merespons sambutan pengguna
- Pola: ['halo', 'hai', 'hello', 'selamat', 'datang', 'pagi', 'siang', 'malam', 'sore']
- Respon: Pesan selamat datang dan penawaran bantuan

#### 3.2.2 Intent "Tanya Fasilitas"
- Tujuan: Menjawab pertanyaan tentang fasilitas hotel
- Pola: ['fasilitas', 'kolam', 'kolam renang', 'wifi', 'restoran', 'kamar', 'gym', 'pusat kebugaran', 'spa', 'lift', 'parkir', 'layanan kamar']
- Respon: Informasi tentang fasilitas yang tersedia

#### 3.2.3 Intent "Tanya Harga"
- Tujuan: Memberikan informasi tentang harga kamar
- Pola: ['harga', 'tarif', 'biaya', 'sewa', 'booking', 'reservasi', 'booking', 'pemesanan', 'harga kamar', 'biaya']
- Respon: Informasi dasar tentang harga dan cara mendapatkan informasi lebih lanjut

### 3.3 Metode Pencocokan Kata Kunci
Chatbot menggunakan metode pencocokan kata kunci sederhana:
1. Teks input pengguna diproses (case folding, cleaning)
2. Setiap kata dalam input dicocokkan dengan pola-pola yang telah ditentukan
3. Jika ditemukan kecocokan, intent yang sesuai diaktifkan
4. Respon dipilih secara acak dari daftar respon yang tersedia untuk intent tersebut

### 3.4 Respons Fallback
Untuk menangani pertanyaan yang tidak dikenali:
- Sistem memiliki daftar pesan fallback
- Jika tidak ada intent yang sesuai, sistem akan merespons dengan salah satu pesan fallback secara acak
- Ini memberikan pengalaman pengguna yang lebih baik saat sistem tidak memahami pertanyaan

### 3.5 Analisis Keterbatasan Chatbot Berbasis Aturan

#### 3.5.1 Keterbatasan Utama
1. **Keterbatasan Pemahaman Konteks**: Tidak dapat memahami konteks atau makna implisit dalam percakapan
2. **Ketergantungan pada Aturan Manual**: Harus ditentukan secara manual semua kemungkinan pola pertanyaan dan respons
3. **Kesulitan dalam Variasi Bahasa**: Kesulitan menangani sinonim, perbedaan cara mengungkapkan, dan kesalahan penulisan
4. **Tidak Ada Pembelajaran Otomatis**: Tidak mampu belajar dari interaksi pengguna untuk meningkatkan kinerja
5. **Keterbatasan dalam Pemrosesan Kalimat Kompleks**: Sulit menangani pertanyaan yang membutuhkan penalaran majemuk
6. **Skalabilitas Rendah**: Setiap pertanyaan baru memerlukan aturan baru yang harus diprogram secara eksplisit

#### 3.5.2 Perbandingan dengan Chatbot Generative AI
Berbeda dengan chatbot berbasis Generative AI (seperti ChatGPT/DialoGPT):
- **Kemampuan Pemahaman Bahasa**: Generative AI memiliki kemampuan pemahaman bahasa yang lebih luas dan kontekstual
- **Kemampuan Generasi Respons**: AI generatif dapat menghasilkan respons yang alami dan unik, bukan hanya template
- **Kemampuan Pembelajaran**: Dapat belajar dari data besar dan pengalaman sebelumnya
- **Fleksibilitas**: Dapat menangani pertanyaan yang tidak pernah dilihat sebelumnya
- **Multi-turn Conversations**: Lebih baik dalam menangani percakapan multipart dengan konteks yang kompleks

#### 3.5.3 Kelebihan Chatbot Rule-Based
1. **Kontrol Penuh**: Dapat dikontrol sepenuhnya oleh pengembang
2. **Konsistensi Informasi**: Memberikan informasi yang konsisten dan tidak berubah-ubah
3. **Tidak Perlu Data Latihan Besar**: Tidak memerlukan dataset pelatihan besar seperti model AI
4. **Mudah Dimaintain**: Relatif mudah dipahami dan dimaintain oleh developer

## KESIMPULAN

Proyek ini berhasil menyelesaikan pipeline NLP sederhana untuk analisis teks ulasan hotel dengan implementasi tiga komponen utama:

1. **Preprocessing Teks**: Menyiapkan data teks agar optimal untuk proses selanjutnya
2. **Klasifikasi Teks**: Membangun model untuk klasifikasi sentimen menggunakan Naive Bayes dan SVM
3. **Chatbot Sederhana**: Implementasi sistem dialog rule-based untuk layanan pelanggan

Setiap komponen diimplementasikan sesuai dengan spesifikasi soal UAS NLP dengan penjelasan rinci dan analisis komprehensif. Proyek ini menunjukkan aplikasi praktis dari teknik-teknik dasar NLP dalam dunia nyata, khususnya dalam konteks layanan pelanggan berbasis teks.

Dengan preprocessing yang tepat, model klasifikasi dapat bekerja dengan baik, dan implementasi chatbot sederhana memberikan dasar yang kuat untuk sistem yang lebih kompleks di masa depan.