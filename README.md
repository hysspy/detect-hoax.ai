# Deteksi Berita Hoaks Indonesia dengan AI (IBM Granite)

## Project Overview

Proyek ini bertujuan untuk menganalisis dan mengklasifikasikan berita berbahasa Indonesia sebagai "HOAX" atau "VALID" menggunakan model AI Large Language Model (LLM) dari IBM, yaitu Granite | ibm-granite/granite-3.3-8b-instruct. Latar belakang proyek ini adalah maraknya misinformasi dan disinformasi di ruang digital Indonesia, yang memerlukan solusi teknologi untuk membantu proses verifikasi. Pendekatan yang digunakan adalah *zero-shot learning* melalui *prompt engineering*, di mana kemampuan model diuji tanpa melalui proses *fine-tuning* khusus, untuk mensimulasikan penggunaan AI secara praktis dan cepat dalam mendeteksi hoaks.

## Raw Dataset Link

Dataset yang digunakan dalam proyek ini digabungkan dari beberapa sumber berita kredibel dan portal klarifikasi hoaks. Anda dapat menemukan semua file data mentah di repositori ini:
- [turnbackhoax_2020_2025.csv](./turnbackhoax_2020_2025.csv)
- [cnnindonesia_news_RAW.csv](./cnnindonesia_news_RAW.csv)
- [detikcom_news_RAW.csv](./detikcom_news_RAW.csv)
- [kompas_news_RAW.csv](./kompas_news_RAW.csv)

Sumber : 
Deteksi Berita Hoaks Indo - Dataset | RAW

https://www.kaggle.com/datasets/mochamadabdulazis/deteksi-berita-hoaks-indo-dataset/data

<img width="717" height="553" alt="1" src="https://github.com/user-attachments/assets/7a3afdb8-d114-4af8-a6f4-7024b38d2bb3" />

## Insight & Findings

Analisis pada sampel data menunjukkan bahwa model IBM Granite memiliki karakteristik yang unik sebagai detektor hoaks:

1.  **Akurasi Cukup Baik:** Model mencapai akurasi keseluruhan **71.88%**, menunjukkan kemampuan dasar yang solid untuk membedakan berita tanpa pelatihan khusus.

<img width="640" height="547" alt="4" src="https://github.com/user-attachments/assets/2301c691-60d5-4b46-9c9b-d07dca64e0c9" />


2.  **Sangat Agresif Menemukan Hoaks:** Temuan paling signifikan adalah model ini memiliki **Recall 1.00 untuk kategori HOAX**. Artinya, model berhasil mengidentifikasi **SEMUA** berita hoaks dalam sampel uji tanpa ada yang terlewat.
<img width="944" height="506" alt="2" src="https://github.com/user-attachments/assets/698618af-0f2f-477a-9f31-ee025808f721" />

3.  **Cenderung "Terlalu Curiga":** Konsekuensinya, model menjadi sangat skeptis dan salah mengklasifikasikan sebagian besar berita valid sebagai hoaks (Recall untuk kategori VALID hanya 0.34).

4.  **Prediksi "VALID" Sangat Terpercaya:** Ketika model sudah yakin dan memprediksi sebuah berita sebagai **VALID**, prediksinya **100% akurat** (Precision 1.00).

Secara keseluruhan, model ini berperilaku seperti "penjaga gerbang" yang sangat waspada, memprioritaskan penangkapan semua potensi hoaks.

## AI Support Explanation

Dukungan AI dalam proyek ini sepenuhnya bergantung pada model **IBM Granite (`ibm-granite/granite-3.3-8b-instruct`)** yang diakses melalui platform Replicate. Teknik utamanya adalah **Prompt Engineering**, di mana instruksi spesifik dalam bahasa alami diberikan kepada model untuk melakukan dua tugas:

1.  **Klasifikasi Teks:** Model diberi prompt untuk menganalisis konten berita dan mengklasifikasikannya sebagai "HOAX" atau "VALID".
2.  **Peringkasan Teks:** Model juga diinstruksikan untuk membaca artikel panjang dan membuat ringkasan singkat dalam format poin-poin untuk demonstrasi kapabilitas tambahan.

Seluruh proses ini dilakukan dengan pendekatan **Zero-Shot Learning**, yang menguji kemampuan generalisasi model pada tugas spesifik tanpa data pelatihan tambahan.
