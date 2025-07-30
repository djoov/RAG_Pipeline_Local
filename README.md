# RAG Pipeline Lokal dengan Ollama 🚀

*(Modifikasi dari Proyek Asli pixegami)*

Repositori ini adalah versi yang telah dimodifikasi dan disederhanakan secara signifikan dari proyek `simple-rag-pipeline` oleh pixegami. Modifikasi ini bertujuan untuk membuat sistem RAG (Retrieval-Augmented Generation) yang berjalan **100% lokal** menggunakan Ollama, dengan fokus pada kemudahan penggunaan, stabilitas, dan fleksibilitas.

Seluruh proses, mulai dari memproses dokumen hingga menghasilkan jawaban, terjadi sepenuhnya di komputer Anda. Ini memastikan privasi data terjaga dan tidak memerlukan koneksi internet setelah penyiapan awal.

---

## ✨ Fitur Utama & Modifikasi

Proyek ini mengambil konsep inti dari repositori asli dan memperbaikinya dengan beberapa modifikasi kunci:

* **100% Lokal & Offline**
  Menggunakan Ollama untuk menjalankan model embedding dan LLM secara lokal. Tidak ada data yang dikirim ke API eksternal.

* **Pemrosesan Dokumen yang Andal**
  Mengganti metode pemecahan teks asli dengan LangChain (`PyPDFLoader` dan `RecursiveCharacterTextSplitter`) untuk memastikan PDF dibaca dan dipecah menjadi potongan teks dengan ukuran konsisten, menghilangkan error fundamental.

* **Skrip Tunggal yang Disederhanakan**
  Struktur proyek yang kompleks disatukan menjadi satu skrip utama, `run_local.py`, yang menangani seluruh alur kerja dari awal hingga akhir.

* **Mode Chat Interaktif**
  Setelah dokumen diproses, Anda dapat langsung bertanya jawab dengan dokumen melalui terminal.

* **Dukungan Model yang Fleksibel**
  Mudah mengganti model embedding atau LLM hanya dengan mengubah nama model di dalam skrip—selama model tersedia di Ollama.

---

## ⚙️ Cara Kerja

1. **Load & Chunk**
   Skrip membaca semua file PDF di `sample_data/source/` dan memecahnya menjadi potongan teks kecil dengan LangChain.

2. **Embedding**
   Setiap potongan teks diubah menjadi vektor embedding menggunakan model embedding lokal (contoh: `nomic-embed-text`).

3. **Retrieval**
   Pertanyaan Anda juga diubah menjadi embedding. Sistem mencari potongan teks dengan vektor paling mirip secara matematis.

4. **Generation**
   Potongan teks relevan digabungkan dengan pertanyaan, lalu diberikan ke LLM (contoh: `phi3:mini` atau `llama3:8b`) untuk menghasilkan jawaban dalam bahasa alami.

---

## 🚀 Prasyarat

* **Python 3.10+**
* **Ollama**
  Unduh dan instal dari situs resmi Ollama. Pastikan layanan Ollama berjalan di latar belakang.

---

## 🛠️ Penyiapan & Instalasi

1. **Clone Repositori**

   ```bash
   git clone # RAG Pipeline Lokal dengan Ollama 🚀

*(Modifikasi dari Proyek Asli pixegami)*

Repositori ini adalah versi yang telah dimodifikasi dan disederhanakan secara signifikan dari proyek `simple-rag-pipeline` oleh pixegami. Modifikasi ini bertujuan untuk membuat sistem RAG (Retrieval-Augmented Generation) yang berjalan **100% lokal** menggunakan Ollama, dengan fokus pada kemudahan penggunaan, stabilitas, dan fleksibilitas.

Seluruh proses, mulai dari memproses dokumen hingga menghasilkan jawaban, terjadi sepenuhnya di komputer Anda. Ini memastikan privasi data terjaga dan tidak memerlukan koneksi internet setelah penyiapan awal.

---

## ✨ Fitur Utama & Modifikasi

Proyek ini mengambil konsep inti dari repositori asli dan memperbaikinya dengan beberapa modifikasi kunci:

* **100% Lokal & Offline**
  Menggunakan Ollama untuk menjalankan model embedding dan LLM secara lokal. Tidak ada data yang dikirim ke API eksternal.

* **Pemrosesan Dokumen yang Andal**
  Mengganti metode pemecahan teks asli dengan LangChain (`PyPDFLoader` dan `RecursiveCharacterTextSplitter`) untuk memastikan PDF dibaca dan dipecah menjadi potongan teks dengan ukuran konsisten, menghilangkan error fundamental.

* **Skrip Tunggal yang Disederhanakan**
  Struktur proyek yang kompleks disatukan menjadi satu skrip utama, `run_local.py`, yang menangani seluruh alur kerja dari awal hingga akhir.

* **Mode Chat Interaktif**
  Setelah dokumen diproses, Anda dapat langsung bertanya jawab dengan dokumen melalui terminal.

* **Dukungan Model yang Fleksibel**
  Mudah mengganti model embedding atau LLM hanya dengan mengubah nama model di dalam skrip—selama model tersedia di Ollama.

---

## ⚙️ Cara Kerja

1. **Load & Chunk**
   Skrip membaca semua file PDF di `sample_data/source/` dan memecahnya menjadi potongan teks kecil dengan LangChain.

2. **Embedding**
   Setiap potongan teks diubah menjadi vektor embedding menggunakan model embedding lokal (contoh: `nomic-embed-text`).

3. **Retrieval**
   Pertanyaan Anda juga diubah menjadi embedding. Sistem mencari potongan teks dengan vektor paling mirip secara matematis.

4. **Generation**
   Potongan teks relevan digabungkan dengan pertanyaan, lalu diberikan ke LLM (contoh: `phi3:mini` atau `llama3:8b`) untuk menghasilkan jawaban dalam bahasa alami.

---

## 🚀 Prasyarat

* **Python 3.10+**
* **Ollama**
  Unduh dan instal dari situs resmi Ollama. Pastikan layanan Ollama berjalan di latar belakang.

---

## 🛠️ Penyiapan & Instalasi

1. **Clone Repositori**

   ```bash
   git clone https://github.com/djoov/RAG_Pipeline_Local
   cd RAG_Pipeline_Local
   ```

2. **Buat Virtual Environment**

   ```bash
   # Windows
   python -m venv venv
   .\venv\Scripts\activate

   # macOS / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Instal Dependensi**

   ```bash
   pip install -r requirements.txt
   ```

4. **Unduh Model Ollama**

   * Model Embedding (Wajib):

     ```bash
     ollama pull nomic-embed-text
     ```

   * Model LLM Penjawab (Pilih Salah Satu):

     ```bash
     # Untuk VRAM < 6GB
     ollama pull phi3:mini

     # Untuk VRAM > 6GB
     ollama pull llama3:8b
     ```

---

## ▶️ Cara Menjalankan

1. **Tambahkan Dokumen**
   Letakkan file PDF yang ingin diolah di `sample_data/source/`.

2. **Jalankan Skrip**

   ```bash
   python run_local.py
   ```

3. **Tanya Jawab**
   Setelah proses selesai, Anda akan melihat prompt:

   ```txt
   Masukkan pertanyaan Anda (atau ketik 'keluar' untuk berhenti):
   ```

   Ketik pertanyaan, tekan Enter, dan tunggu jawaban.

---

## 🔧 Kustomisasi & Eksperimen

* **Mengganti Model LLM**
  Ubah `LLM_MODEL` di `run_local.py` ke model yang sudah diunduh.

* **Mengganti Model Embedding**
  Unduh dan ubah `EMBEDDING_MODEL` di skrip jika diperlukan.

* **Menyesuaikan Ukuran Chunk**
  Atur `chunk_size` dan `chunk_overlap` di `RecursiveCharacterTextSplitter` sesuai kebutuhan.

---

## 🙏 Ucapan Terima Kasih

Proyek ini tidak akan ada tanpa kerja keras dan sumber terbuka dari pixegami.

Kunjungi repositori aslinya di: [https://github.com/pixegami/simple-rag-pipeline](https://github.com/pixegami/simple-rag-pipeline)

   cd [NAMA_FOLDER_REPOSITORI]
   ```

2. **Buat Virtual Environment**

   ```bash
   # Windows
   python -m venv venv
   .\venv\Scripts\activate

   # macOS / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Instal Dependensi**

   ```bash
   pip install -r requirements.txt
   ```

4. **Unduh Model Ollama**

   * Model Embedding (Wajib):

     ```bash
     ollama pull nomic-embed-text
     ```

   * Model LLM Penjawab (Pilih Salah Satu):

     ```bash
     # Untuk VRAM < 6GB
     ollama pull phi3:mini

     # Untuk VRAM > 6GB
     ollama pull llama3:8b
     ```

---

## ▶️ Cara Menjalankan

1. **Tambahkan Dokumen**
   Letakkan file PDF yang ingin diolah di `sample_data/source/`.

2. **Jalankan Skrip**

   ```bash
   python run_local.py
   ```

3. **Tanya Jawab**
   Setelah proses selesai, Anda akan melihat prompt:

   ```txt
   Masukkan pertanyaan Anda (atau ketik 'keluar' untuk berhenti):
   ```

   Ketik pertanyaan, tekan Enter, dan tunggu jawaban.

---

## 🔧 Kustomisasi & Eksperimen

* **Mengganti Model LLM**
  Ubah `LLM_MODEL` di `run_local.py` ke model yang sudah diunduh.

* **Mengganti Model Embedding**
  Unduh dan ubah `EMBEDDING_MODEL` di skrip jika diperlukan.

* **Menyesuaikan Ukuran Chunk**
  Atur `chunk_size` dan `chunk_overlap` di `RecursiveCharacterTextSplitter` sesuai kebutuhan.

---

## 🙏 Ucapan Terima Kasih

Proyek ini tidak akan ada tanpa kerja keras dan sumber terbuka dari pixegami.

Kunjungi repositori aslinya di: [https://github.com/pixegami/simple-rag-pipeline](https://github.com/pixegami/simple-rag-pipeline)

