setup
-----

### **README Proyek N8N Lokal Anda**

Ini adalah panduan singkat untuk menjalankan **N8N** (platform otomatisasi *workflow*) secara lokal di komputer Anda menggunakan **Docker**.

-----

### **Apa Itu N8N?**

**N8N** adalah alat otomatisasi alur kerja sumber terbuka yang kuat. Ini memungkinkan Anda menghubungkan berbagai aplikasi dan API untuk mengotomatiskan tugas dan proses yang berulang. Dengan N8N, Anda dapat membuat *workflow* yang kompleks dengan mudah, mengintegrasikan lebih dari 500 layanan, dan bahkan memanfaatkan fitur AI bawaan untuk membuat agen cerdas.

-----

### **Fitur Utama N8N:**

  * **Otomatisasi Fleksibel:** Buat alur kerja otomatis dari yang sederhana hingga kompleks.
  * **Integrasi Luas:** Terhubung dengan lebih dari 500 aplikasi dan layanan.
  * **Editor Visual:** Bangun *workflow* dengan antarmuka *drag-and-drop* yang intuitif.
  * **Kustomisasi Kode:** Tambahkan kode JavaScript atau Python untuk fungsi kustom.
  * **Fitur AI:** Bangun agen AI menggunakan model seperti ChatGPT atau Claude.
  * **Self-Hosted:** Kendalikan data Anda sepenuhnya dengan menjalankan N8N di server atau komputer Anda sendiri.

-----

### **Persyaratan Sistem:**

  * **Docker Desktop:** Pastikan Anda sudah menginstal Docker Desktop di sistem operasi Anda (Windows, macOS, Linux). Anda bisa mengunduhnya dari [situs web resmi Docker](https://www.docker.com/products/docker-desktop/).

-----

### **Langkah-langkah Instalasi Lokal (Menggunakan Docker):**

Ikuti langkah-langkah di bawah ini untuk menjalankan N8N di komputer Anda:

1.  **Buka Docker Desktop:** Pastikan aplikasi Docker Desktop sedang berjalan di *background*.

2.  **Buka Terminal/Command Prompt:** Buka terminal (untuk macOS/Linux) atau Command Prompt/PowerShell (untuk Windows).

3.  **Buat Volume Docker (Opsional, tapi Disarankan):**
    Volume Docker digunakan untuk menyimpan data *workflow* N8N Anda agar tidak hilang saat kontainer N8N dihentikan atau dihapus.

    ```bash
    docker volume create n8n_data
    ```

4.  **Unduh dan Jalankan Image N8N:**
    Jalankan perintah berikut untuk mengunduh *image* N8N resmi dan menjalankannya sebagai kontainer Docker. Pastikan port `5678` tersedia di sistem Anda.

    ```bash
    docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n n8n
    ```

      * `-it`: Memungkinkan interaksi interaktif dengan kontainer.
      * `--rm`: Secara otomatis menghapus kontainer saat keluar (jika tidak ingin menyimpan kontainer setelah berhenti).
      * `--name n8n`: Memberi nama kontainer "n8n" agar mudah diidentifikasi.
      * `-p 5678:5678`: Memetakan port 5678 di host Anda ke port 5678 di dalam kontainer.
      * `-v n8n_data:/home/node/.n8n`: Memasang volume `n8n_data` ke direktori data N8N di dalam kontainer.
      * `n8n`: Nama *image* Docker yang akan dijalankan.

5.  **Akses N8N di Browser Anda:**
    Setelah kontainer N8N berhasil berjalan, buka *web browser* Anda dan navigasikan ke alamat berikut:

    ```
    http://localhost:5678
    ```

6.  **Daftar dan Aktifkan Lisensi (Gratis):**

      * Anda akan diminta untuk mendaftar akun N8N gratis. Ikuti langkah-langkah pendaftarannya.
      * Setelah mendaftar, Anda bisa memilih untuk mengaktifkan lisensi gratis untuk membuka beberapa fitur tambahan. Kunci lisensi akan dikirimkan ke email yang Anda daftarkan. Salin kunci tersebut dan tempelkan di pengaturan N8N Anda.

-----

### **Mencoba Workflow AI Sederhana:**

N8N mendukung integrasi AI. Untuk mencoba agen AI sederhana:

1.  Di *dashboard* N8N, cari dan klik tombol "**Test simple AI agent**".
2.  Anda memerlukan **kunci API OpenAI** (atau penyedia AI lainnya) untuk fitur ini. Dapatkan kunci API Anda dari platform OpenAI.
3.  Buat kredensial baru di N8N menggunakan kunci API Anda.
4.  Mulai uji *chatbot* AI Anda. Untuk membuat *chatbot* lebih cerdas dengan memori percakapan, Anda mungkin perlu menambahkan *memory node* di *workflow* Anda.

-----

### **Memperbarui N8N:**

Untuk memastikan Anda selalu menggunakan versi N8N terbaru:

1.  **Buka Docker Desktop.**
2.  Cari *image* N8N di daftar *image* Anda.
3.  Klik tombol "**Pull**" (atau opsi serupa) untuk mengunduh versi terbaru dari *image* N8N.
4.  **Hentikan kontainer N8N yang sedang berjalan** (jika ada).
5.  Jalankan kembali kontainer N8N menggunakan perintah `docker run` yang sama seperti pada langkah instalasi di atas. Ini akan menggunakan *image* terbaru yang telah Anda unduh.

-----

### **Memecahkan Masalah Umum:**

  * **`Port 5678 already in use`:** Pastikan tidak ada aplikasi lain yang menggunakan port 5678. Anda bisa mengganti port `5678:5678` di perintah `docker run` menjadi `8000:5678` (atau port lain yang tersedia) untuk mengakses N8N di `localhost:8000`.
  * **Kontainer tidak berjalan:** Periksa *log* di Docker Desktop untuk melihat pesan kesalahan yang mungkin muncul.
  * **Data hilang setelah kontainer dihapus:** Pastikan Anda menggunakan volume Docker (`-v n8n_data:/home/node/.n8n`) untuk menyimpan data Anda secara persisten.

-----

N8N adalah alat yang luar biasa untuk mengotomatisasi tugas Anda. Selamat mencoba\!

-----

Apakah Anda ingin menambahkan bagian lain atau mengubah sesuatu di README ini?
