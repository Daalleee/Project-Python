UJIAN AKHIR SEMESTER (UAS) – TAKE HOME PROJECT
Pemrosesan Bahasa Alami (NLP)
I. Deskripsi Proyek
Buatlah sebuah pipeline NLP sederhana untuk menganalisis data teks (ulasan aplikasi,
komentar media sosial, atau berita). Dataset:
Gunakan dataset Ulasan Hotel berikut :
https://github.com/IndoNLP/indonlu/tree/master/dataset/hoasa_absa-airy. Anda boleh
menggunakan semua data, atau minimal 100 kalimat ulasan.
Bagian 1: Pra-pemrosesan Teks (Bobot: 20%)
Sebelum data diolah, data harus dibersihkan agar model dapat bekerja maksimal. Pilih
teknik preprocessing berikut sesuai sifat data dan tujuan anda:
1. Case Folding: Mengubah huruf menjadi kecil semua.
2. Tokenisasi: Memecah kalimat menjadi kata-kata.
3. Stopword Removal: Menghapus kata umum yang tidak bermakna (contoh: "yang",
"dan", "di").
4. Cleaning: Menghapus tanda baca, angka, atau karakter aneh menggunakan Regex.
5. Pilih Salah Satu: Stemming (Kata dasar) ATAU Lemmatization.
Tugas Laporan: Tampilkan 5 baris data sebelum dan sesudah diproses. Jelaskan mengapa
tahap preprocessing tersebut penting dilakukan sebelum masuk ke tahap machine learning.
Bagian 2: Analisis Teks (Pilih Topik A atau Topik B) (Bobot: 30%)
Pilihlah salah satu topik di bawah ini sesuai dengan pemahaman terbaik Anda.
Pilihan A: Klasifikasi Teks (Text Classification)
Buatlah model untuk memprediksi kategori atau sentimen (Positif/Negatif) dari teks.
1. Gunakan algoritma Naive Bayes atau Support Vector Machine (SVM).
2. Ubah teks menjadi angka menggunakan TF-IDF.
3. Lakukan pembagian data (split data) menjadi data latih (80%) dan data uji (20%).
4. Analisis: Hitung dan jelaskan berapa Akurasi model Anda pada data uji.
Pilihan B: Pemodelan Topik (Topic Modeling)
Buatlah sistem untuk menemukan topik tersembunyi dari kumpulan dokumen.
1. Gunakan algoritma Latent Dirichlet Allocation (LDA) atau Non-Negative Matrix
Factorization (NMF).
2. Tentukan jumlah topik (K), misalnya K=3 atau K=5.
3. Analisis: Tampilkan 5-10 kata kunci teratas (top words) untuk setiap topik yang
ditemukan. Berikan label/nama topik menurut interpretasi Anda sendiri berdasarkan
kata-kata tersebut (misal: Topik 1 tentang "Politik", Topik 2 tentang "Olahraga").
Bagian 3: Aplikasi NLP (Bobot: 50%)
C: Peringkasan Teks (Text Summarization)
Buatlah sistem untuk meringkas artikel panjang menjadi singkat.
1. Gunakan dataset dari materi kuliah.
2. Implementasikan metode ekstraktif menggunakan TF-IDF Scoring.
○ Petunjuk: Hitung skor setiap kalimat berdasarkan bobot kata-katanya, lalu
ambil kalimat dengan skor tertinggi.
3. Analisis: Bandingkan hasil ringkasan mesin dengan ringkasan referensi. Apakah
mesin berhasil menangkap inti kalimat? Jelaskan kelebihan metode ekstraktif
dibanding abstraktif secara teori.
D: Chatbot Sederhana
Buatlah Chatbot berbasis aturan (Rule-Based) sederhana untuk layanan pelanggan
(misalnya: Chatbot Info Kampus atau Chatbot Toko Online).
1. Tentukan minimal 3 Intent (Maksud), misalnya: salam, tanya_jadwal, tanya_biaya.
2. Gunakan logika Pencocokan Kata Kunci (keyword matching) sederhana atau Regex.
3. Sediakan respons Fallback jika bot tidak mengerti pertanyaan pengguna.
4. Analisis: Jelaskan keterbatasan utama dari chatbot berbasis aturan yang Anda buat
dibandingkan dengan chatbot berbasis Generative AI (seperti ChatGPT/DialoGPT).
Ketentuan Pengumpulan:
1. Format: Kumpulkan dalam bentuk Laporan PDF (berisi kode, hasil screenshot, dan
analisis) dan Google Colab Notebook (.ipynb) yang sudah diberi penjelasan teks.
2. Keaslian: Mahasiswa diperbolehkan melihat materi kuliah dan internet, namun
dilarang menyalin penuh (copy-paste) kode teman. Kode yang sama persis akan
mendapat nilai 0.