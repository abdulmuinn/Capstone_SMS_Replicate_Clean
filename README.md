# Capstone: AI-Assisted Public Data Analytics (SMS Spam via Replicate API)

## Project Overview
Analisis end-to-end pada dataset publik **SMS Spam Collection (5000 baris)** untuk mengidentifikasi pola **spam vs ham** pada pesan teks.  
Pipeline mencakup **EDA**, **preprocessing teks**, **zero-shot classification** menggunakan **LLM (Replicate API)**, model **baseline supervised** (TF‑IDF + Logistic Regression), serta pembuatan **insight & rekomendasi** otomatis.

## Files
- **Notebook Colab**: `Capstone_SMS_Replicate_Clean.ipynb` — jalankan dari atas ke bawah.  
- **Raw Dataset**: `sms_spam_full.csv` — upload ke Colab Files sebelum menjalankan notebook.

> Catatan: Untuk menjalankan bagian LLM, set environment variable `REPLICATE_API_TOKEN` terlebih dahulu.

## Raw Dataset Link
- Local/Repo: `./sms_spam_full.csv`  
 - Sumber: dataset contoh dibuat dari sampel SMS spam/ham dan direplikasi menjadi 5000 baris untuk keperluan analitik.

## Analysis Steps (ringkas)
1. **EDA**: cek info dataset, missing values, distribusi label, sampel data.  
2. **Preprocessing**: normalisasi teks (`lowercase`, hapus URL/simbol, normalisasi spasi).  
3. **Zero-shot classification (LLM)**: klasifikasi teks ke `["spam","ham"]` menggunakan model di Replicate dengan prompt berformat **JSON-only** agar hasil mudah di-parse.  
4. **Baseline supervised**: TF‑IDF (1–2 gram) + Logistic Regression; evaluasi `precision/recall/F1` dan confusion matrix.  
5. **Insights & recommendations**: LLM menghasilkan laporan **Analytical Result, Insights & Findings, Recommendations** dalam **Bahasa Indonesia**.

## Insight & Findings (contoh ringkasan)
- Pesan dengan kata kunci **promo/menang/hadiah/klik** cenderung terklasifikasi **spam**.  
- Struktur kalimat imperatif dan urgensi (*URGENT, reply YES, call now*) menjadi indikator kuat spam.  
- **Ham** didominasi pesan percakapan sehari‑hari (janji temu, ucapan, koordinasi).  

## Recommendations (contoh)
- Terapkan **filter berbasis kata kunci** & **scoring TF‑IDF + LR** sebagai baseline produksi.  
- Tuning threshold untuk menekan **false positive** pada notifikasi penting.  
- Tambah contoh berlabel untuk memperkuat model supervised (khusus domain lokal/ID).  
- Monitoring berkala pada distribusi kata baru (adaptasi terhadap pola spam terkini).

## AI Support Explanation
Proyek ini memanfaatkan **Replicate API** untuk:
- **Zero‑Shot Labeling**: tanpa data latih tambahan, model LLM mengklasifikasikan pesan ke label yang diinginkan.  
- **Narrative Analytics**: LLM menghasilkan ringkasan *analytical result*, *insights*, dan *recommendations* dalam format Markdown.  

