# Assignment Semantic Search

## 1. Problem Statement
Membangun prototype asisten customer service
e-commerce yang mencari FAQ relevan menggunakan
semantic search dan menghasilkan jawaban dengan LLM.

## 2. Knowledge Base
Dataset FAQ e-commerce yang diberikan mentor.

Dataset asli disimpan di folder data/.

## 3. Technology Stack
- Python
- Pandas dan NumPy
- Gemini Embeddings API
- FAISS
- Gemini API untuk text generation

## 4. System Workflow
1. Ingest: membaca dataset FAQ.
2. Embed: membuat embedding dari pertanyaan dan jawaban.
3. Store: menyimpan embedding ke FAISS.
4. Retrieve: mencari FAQ relevan berdasarkan query.
5. Generate: menghasilkan jawaban menggunakan LLM.

## 5. How to Run
1. Buat virtual environment.
2. Install requirements.txt.
3. Siapkan GEMINI_API_KEY dalam file .env.
4. Jalankan notebook dari awal hingga akhir.

## 6. Evaluation
Pengujian dilakukan menggunakan minimal 5 query:
pertanyaan langsung, parafrase, sinonim, dan pertanyaan
yang tidak memiliki jawaban dalam knowledge base.

Hasil dan analisis:
lihat documentation/retrieval_test_results.md.

## 7. Limitations
- Jawaban bergantung pada kualitas FAQ.
- Retrieval dapat mengambil informasi yang kurang relevan.
- LLM masih mungkin menghasilkan jawaban yang keliru.
- Sistem tidak menjamin jawaban untuk informasi
  yang tidak tersedia dalam knowledge base.