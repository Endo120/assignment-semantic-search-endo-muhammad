
# Retrieval Test Results

## 1. Tujuan Pengujian

Pengujian dilakukan untuk mengevaluasi relevansi hasil semantic search dan kualitas jawaban LLM berdasarkan FAQ yang ditemukan. Pengujian mencakup pertanyaan langsung, parafrase, serta pertanyaan yang informasinya belum tersedia dalam knowledge base.

## 2. Hasil Pengujian

### Test Case 1 — Pertanyaan Langsung tentang Pengiriman

**Query:**  
Bagaimana cara melacak paket yang sedang dikirim?

**Sumber FAQ Teratas:**  
Bagaimana cara melacak paket yang sedang dikirim?

**Hasil Retrieval:**  
Relevan. FAQ yang ditemukan sesuai dengan pertanyaan pengguna.

**Evaluasi Jawaban AI:**  
Jawaban menjelaskan bahwa nomor resi tersedia di halaman "Pesanan Saya" setelah barang dikirim. Pengguna juga diarahkan untuk menggunakan nomor resi pada website kurir terkait.

**Kesimpulan:**  
Berhasil. Semantic search menemukan FAQ yang tepat dan LLM menghasilkan jawaban yang sesuai dengan informasi yang ditemukan.

---

### Test Case 2 — Pertanyaan Langsung tentang Refund

**Query:**  
Berapa lama proses refund setelah pengembalian disetujui?

**Sumber FAQ Teratas:**  
Berapa lama proses refund setelah pengembalian disetujui?

**Hasil Retrieval:**  
Relevan. FAQ yang ditemukan sesuai dengan topik dan maksud pertanyaan.

**Evaluasi Jawaban AI:**  
Jawaban menyebutkan bahwa refund biasanya diproses dalam waktu 3–7 hari kerja setelah barang diterima dan diverifikasi oleh penjual.

**Kesimpulan:**  
Berhasil. Sistem mengambil FAQ yang sesuai dan menyampaikan informasi durasi refund dengan jelas.

---

### Test Case 3 — Parafrase Pertanyaan Pembatalan Pesanan

**Query:**  
Saya berubah pikiran setelah checkout, masih bisakah pesanan dibatalkan?

**Sumber FAQ Teratas:**  
Bagaimana cara membatalkan pesanan yang sudah dibuat?

**Hasil Retrieval:**  
Relevan. Meskipun kalimat query berbeda dari pertanyaan FAQ, sistem menemukan informasi mengenai pembatalan pesanan.

**Evaluasi Jawaban AI:**  
Jawaban menjelaskan bahwa pembatalan dapat dilakukan melalui halaman "Pesanan Saya" selama status pesanan masih "Diproses". Jika status sudah "Dikirim", pembatalan tidak dapat dilakukan.

**Kesimpulan:**  
Berhasil. Hasil ini menunjukkan bahwa semantic search dapat menemukan FAQ berdasarkan kesamaan makna, bukan hanya kesamaan kata secara persis.

---

### Test Case 4 — Parafrase Pertanyaan Barang Rusak

**Query:**  
Paket baru datang, tetapi barang di dalamnya pecah. Bagaimana solusinya?

**Sumber FAQ Teratas:**  
Apa yang harus dilakukan jika paket diterima dalam kondisi rusak?

**Hasil Retrieval:**  
Relevan. FAQ yang ditemukan sesuai dengan masalah barang rusak atau pecah setelah pengiriman.

**Evaluasi Jawaban AI:**  
Jawaban meminta pengguna mengambil foto atau video kondisi paket dan melaporkan kendala melalui menu komplain dalam waktu 2 × 24 jam sejak barang diterima.

**Kesimpulan:**  
Berhasil. Sistem memahami bahwa kata "pecah" dalam query berkaitan dengan kondisi barang "rusak" pada FAQ. Jawaban juga memberikan langkah penanganan yang spesifik.

---

### Test Case 5 — Pertanyaan di Luar Knowledge Base

**Query:**  
Apakah tersedia layanan pembayaran menggunakan cryptocurrency?

**Sumber FAQ Teratas:**  
Metode pembayaran apa saja yang tersedia?

**Hasil Retrieval:**  
Sebagian relevan. FAQ membahas metode pembayaran, tetapi belum tentu secara khusus menjawab ketersediaan cryptocurrency.

**Evaluasi Jawaban AI:**  
Jawaban menyatakan bahwa informasi mengenai cryptocurrency belum tersedia. AI kemudian menyebutkan metode pembayaran yang tercantum dalam FAQ, yaitu transfer bank, kartu kredit/debit, e-wallet, dan minimarket rekanan.

**Kesimpulan:**  
Cukup baik. LLM mengakui keterbatasan informasi dan menggunakan FAQ yang ditemukan sebagai konteks. Namun, pengujian ini juga menunjukkan bahwa retrieval masih dapat mengembalikan FAQ yang hanya berkaitan secara umum dengan query.

## 3. Ringkasan Hasil Pengujian

| No. | Jenis Pengujian | Relevansi Retrieval | Kualitas Jawaban |
|---|---|---|---|
| 1 | Pertanyaan langsung: pelacakan paket | Relevan | Sesuai |
| 2 | Pertanyaan langsung: refund | Relevan | Sesuai |
| 3 | Parafrase: pembatalan pesanan | Relevan | Sesuai |
| 4 | Parafrase: barang pecah | Relevan | Sesuai |
| 5 | Informasi di luar knowledge base | Sebagian relevan | Cukup baik |

## 4. Analisis Keseluruhan

Berdasarkan lima query yang diuji, sistem menunjukkan kemampuan menemukan FAQ yang sesuai untuk pertanyaan langsung maupun pertanyaan yang menggunakan kalimat berbeda dari FAQ asli.

Hasil pada query pembatalan pesanan dan barang rusak menunjukkan manfaat semantic search dalam mengenali kesamaan makna. Sistem tidak harus menemukan kata-kata yang identik untuk memperoleh FAQ yang relevan.

Pada pertanyaan cryptocurrency, retrieval menemukan FAQ mengenai metode pembayaran. FAQ tersebut masih berhubungan dengan topik pembayaran, tetapi tidak secara khusus menjawab ketersediaan cryptocurrency. Jawaban AI cukup baik karena menyatakan keterbatasan informasi yang tersedia.

Secara keseluruhan, hasil pengujian awal menunjukkan bahwa pipeline semantic search dan LLM dapat berfungsi sesuai tujuan prototype. Namun, pengujian ini masih terbatas pada lima query dan belum cukup untuk menyimpulkan performa sistem pada seluruh knowledge base.

## 5. Keterbatasan dan Rekomendasi

1. **Jumlah pengujian terbatas.**  
   Tambahkan lebih banyak query dengan variasi bahasa dan tingkat kesulitan berbeda.

2. **Retrieval dapat menemukan konteks yang hanya berkaitan secara umum.**  
   Evaluasi similarity score dan pertimbangkan mekanisme untuk menolak hasil retrieval yang tidak cukup relevan.

3. **Jawaban LLM perlu diverifikasi.**  
   Pastikan setiap informasi dalam jawaban dapat ditelusuri kembali ke FAQ yang digunakan sebagai context.

4. **Pengujian di luar knowledge base perlu diperluas.**  
   Gunakan pertanyaan yang benar-benar tidak tercakup dalam FAQ untuk mengevaluasi kemampuan sistem mengakui keterbatasannya.

## 6. Kesimpulan

Prototype berhasil menunjukkan alur end-to-end dari query pengguna, retrieval FAQ menggunakan semantic search, hingga pembuatan jawaban oleh LLM.

Empat query pertama menghasilkan retrieval yang relevan berdasarkan FAQ teratas yang diamati, sedangkan query kelima menunjukkan bahwa sistem masih perlu dievaluasi dalam membedakan konteks yang relevan secara umum dengan informasi yang benar-benar menjawab pertanyaan.

Hasil ini menjadi dasar untuk pengembangan dan evaluasi lebih lanjut sebelum sistem digunakan dalam lingkungan produksi.
