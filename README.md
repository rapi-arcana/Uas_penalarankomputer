# CBR\_Perdagangan\_Orang

Proyek ini adalah implementasi sistem **Case-Based Reasoning (CBR)** untuk menganalisis dan memprediksi putusan perkara Pidana Perdagangan Orang berdasarkan dokumen hukum dari situs Direktori Mahkamah Agung Indonesia (`https://putusan3.mahkamahagung.go.id/`). Sistem ini mencakup pipeline lengkap mulai dari pengambilan data (scraping), ekstraksi metadata, representasi data, retrieval, prediksi, hingga evaluasi performa model.

## Deskripsi

Proyek ini terdiri dari lima bagian utama:

1. **Part 1 - Scraping Dokumen**: Mengambil dokumen PDF putusan pidana perdagangan orang dari situs Direktori Mahkamah Agung dan mengonversinya ke file teks.
2. **Part 2 - Representasi dan Ekstraksi Metadata**: Mengekstrak informasi seperti nomor perkara, klasifikasi, tanggal, dan ringkasan dari file teks dan menyimpannya dalam format CSV.
3. **Part 3 - Retrieval Kasus Serupa**: Melakukan pencarian kasus yang serupa menggunakan model seperti BM25, Logistic Regression, dan IndoBERT.
4. **Part 4 - Prediksi Putusan**: Memprediksi amar putusan menggunakan pendekatan supervised learning dengan model seperti SVM, Logistic Regression, dan IndoBERT.
5. **Part 5 - Evaluasi dan Analisis**: Mengevaluasi performa retrieval dan prediksi, serta menganalisis kesalahan model menggunakan visualisasi dan LIME.

## Prasyarat

* Python 3.11
* Jupyter Notebook / VSCode / Google Colab
* Koneksi internet untuk scraping data
* Dependensi Python (lihat `requirements.txt`)

## Instalasi

1. **Clone Repositori**

   ```bash
   git clone https://github.com/username/CBR_Perdagangan_Orang.git
   cd CBR_Perdagangan_Orang
   cd CBR/notebooks
   ```

2. **Virtual Environment (Opsional)**

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate     # Windows
   ```

3. **Instal Dependensi**

   ```bash
   pip install -r requirements.txt
   ```

4. **Unduh NLTK**

   ```python
   import nltk
   nltk.download('punkt')
   ```

## Struktur Direktori

```plaintext
CBR_Perdagangan_Orang/
├── CBR/
│   ├── data/
│   │   ├── eval/
│   │   ├── processed/
│   │   ├── raw/
│   │   ├── results/
│   │   ├── Perdagangan_Orang/
│   ├── notebooks/
│   │   ├── Part_1_Scraper.ipynb
│   │   ├── Part_2_Representation.ipynb
│   │   ├── Part_3_Retrieval.ipynb
│   │   ├── Part_4_Predict.ipynb
│   │   ├── Part_5_Evaluation.ipynb
│   │   
├── README.md
```

## Cara Menjalankan Pipeline

1. **Part 1: Scraping**

   * Unduh dokumen PDF perkara perdagangan orang dan ubah menjadi teks.
   * Output: `data/raw/` dan log di `logs/`.

2. **Part 2: Representasi**

   * Ekstraksi metadata dari teks, simpan di `data/processed/cases.csv`.

3. **Part 3: Retrieval**

   * Temukan kasus relevan berdasarkan input menggunakan model NLP dan ML.

4. **Part 4: Prediksi**

   * Prediksi amar putusan (misal: pidana penjara, denda) berdasarkan fitur metadata dan isi dokumen.

5. **Part 5: Evaluasi**

   * Evaluasi performa prediksi dan retrieval.
   * Visualisasi hasil evaluasi disimpan di `data/eval/`.

## Catatan Penting

* Disarankan tidak memproses lebih dari 60 file untuk menghindari masalah path terlalu panjang (terutama di Windows).
* Model IndoBERT dan `sentence-transformers` diunduh otomatis.
* Analisis LIME dapat berjalan lambat jika teks sangat panjang.
* Semua log aktivitas ada di folder `logs/`.

## Contoh Output

* File teks: `data/raw/case_001.txt`
* Metadata: `data/processed/cases.csv`
* Hasil prediksi: `data/results/*.csv`
* Evaluasi: `data/eval/*.csv` dan `*.png`

## Troubleshooting

* **Scraping gagal**: Cek koneksi internet dan pastikan URL situs Mahkamah Agung aktif.
* **IndoBERT error**: Coba instal ulang `torch` dan pastikan mendukung CUDA jika ingin pakai GPU.
* **LIME terlalu lama**: Gunakan input yang lebih pendek.

## Kontribusi

1. Fork repositori ini
2. Buat branch (`git checkout -b fitur/nama-fitur`)
3. Commit dan push
4. Ajukan Pull Request


