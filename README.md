# 📊 End-to-End YouTube Comments Sentiment Analysis & Indonesian NLP Pipeline

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1H2cyYVkeH3tRTUXjHypsI-PYQoJedkf3)
![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=Python&logoColor=white)
![YouTube API](https://img.shields.io/badge/YouTube%20Data-API%20v3-FF0000?style=for-the-badge&logo=YouTube&logoColor=white)
![NLP](https://img.shields.io/badge/Natural%20Language-Processing-00A67E?style=for-the-badge)
![Visuals](https://img.shields.io/badge/Seaborn%20%26-WordCloud-orange?style=for-the-badge)

---

## 📌 Project Overview

Proyek ini adalah pipeline **Natural Language Processing (NLP) & Analisis Sentimen Bahasa Indonesia** berbasis end-to-end yang mengambil data opini publik secara langsung (*real-time scraping*) dari **YouTube Data API v3**, menjalankan pembersihan teks mendalam (*Indonesian Slang Normalization*), serta menerapkan mesin klasifikasi sentimen berbasis aturan cerdas (*Negation-Aware Sentiment Engine*).

### 🎯 Tujuan Utama:
1. **Automated Scraping:** Mengambil 500 komentar publik YouTube secara dinamis melalui integrasi resmi YouTube Data API v3 dengan mekanisme *pagination token*.
2. **Text Preprocessing & Slang Normalization:** Mengeliminasi derau (*noise* seperti mention, URL, hashtag, simbol asing) serta memetakan singkatan dan bahasa gaul lokal Indonesia (`yg` $\rightarrow$ `yang`, `mantul` $\rightarrow$ `mantap`, `ga/gak` $\rightarrow$ `tidak`).
3. **Negation-Aware Sentiment Engine:** Mengatasi kelemahan algoritma sentimen konvensional dengan membalikkan polaritas kata saat didahului oleh penyangkal (contoh: *"tidak bagus"* secara akurat diklasifikasikan sebagai **Negatif**, bukan Positif).
4. **Visual Analytics & WordCloud:** Menyajikan visualisasi distribusi sentimen dan awan kata kunci emosional setelah penyaringan kata henti (*stopwords*).

---

## 🚀 Coba Langsung di Google Colab

Notebook ini dapat dijalankan langsung di cloud tanpa instalasi lokal:

👉 **[Jalankan di Google Colab (Klik di Sini)](https://colab.research.google.com/drive/1H2cyYVkeH3tRTUXjHypsI-PYQoJedkf3)**

---

## 🛠️ Alur Arsitektur & Metodologi Pipeline

```
[YouTube Video Target (ID: TVvc8K8VwNI)]
                   │
                   ▼ (YouTube Data API v3 + Pagination)
[Raw Comment Corpus (500 Komentar)]
                   │
                   ▼
[Text Preprocessing & Slang Normalizer]
  ├── Regex URL & Mention Stripping
  └── Kamus Normalisasi Slang Indonesia (SLANG_MAP)
                   │
                   ▼
[Negation-Aware Lexicon Scoring Engine]
  ├── Token-Level Word Matching (Anti-Substr Bug)
  └── Multi-step Negation Detection ("tidak", "bukan", "kurang")
                   │
                   ▼
[Analytics & Visualization Output]
  ├── Sentiment Distribution Barplot (Seaborn)
  └── High-Resolution Emotional WordCloud
```

---

## 📈 Hasil Analisis Data (Studi Kasus 500 Komentar Publik)

Berdasarkan ekstraksi 500 komentar nyata pada video publik (fokus opini kepemimpinan & sosial):

```
+---------------------------------------------------------------------------------+
|                       DISTRIBUSI SENTIMEN OPINI PUBLIK                         |
+--------------------------+-----------------------------+------------------------+
| ⚪ Netral : 285 (57.0%)  | 🟢 Positif : 193 (38.6%)    | 🔴 Negatif : 22 (4.4%) |
+--------------------------+-----------------------------+------------------------+
```

### 💡 Temuan Analitis:
1. **Sentimen Positif Mendominasi Opini Emosional (38.6% vs 4.4%):**  
   Dukungan masyarakat terhadap program video sangat tinggi, dengan kata kunci emosional teratas mencakup *hebat, mantap, amanah, inspirasi, peduli, berkah, sukses*.
2. **Kategori Netral yang Seimbang (57.0%):**  
   Mayoritas komentar netral berupa salam kedaerahan (*"Ciamis hadir"*, *"Bandung menyimak"*) dan pertanyaan prosedural.
3. **Efektivitas Penanganan Negasi:**  
   Kalimat seperti *"Program ini tidak bagus dan kurang mantap"* berhasil dibalik skornya menjadi polaritas negatif secara konsisten, membuktikan akurasi penalaran mesin klasifikasi.

---

## 🔒 Praktik Terbaik Keamanan (Security Best Practices)

Proyek ini tidak menyimpan (*no hardcoded keys*) API Key di dalam kode sumber repositori:
* Mendukung pengambilan aman melalui **Google Colab Secrets (`userdata.get('YOUTUBE_API_KEY')`)**.
* Menyediakan input terproteksi berbasis **`getpass`** di terminal interaktif.

---

## 📂 Struktur Berkas Repositori

```
├── README.md                                      # Dokumentasi teknis & ringkasan bisnis
├── YouTube_Sentiment_Analysis_Indonesian.ipynb    # Jupyter Notebook lengkap siap eksekusi
└── .gitignore                                     # Proteksi file kredensial & environment
```

---

## 👤 Author & Profil Analis

* **Nama:** Rifasa Hadiarto (UNIKOM)
* **Sertifikasi:** Certified Data Analyst — Badan Nasional Sertifikasi Profesi (BNSP)
* **Spesialisasi:** Natural Language Processing (NLP), Data Scraping & API Integration, Exploratory Data Analysis, BI Dashboards (Tableau & Looker Studio).
