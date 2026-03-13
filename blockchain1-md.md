## Penjelasan Kode

Kode ini adalah **implementasi blockchain sederhana** menggunakan Python, terdiri dari 3 class utama:

---

### 1. Class `Transaction`
Merepresentasikan sebuah transaksi keuangan antar pengguna.

- **`__init__`** – Menyimpan data pengirim (`sender`), penerima (`receiver`), dan jumlah (`amount`).
- **`to_dict()`** – Mengubah data transaksi menjadi format dictionary, agar mudah diubah ke JSON.
- **`print()`** – Mencetak isi transaksi ke konsol.

---

### 2. Class `Block`
Merepresentasikan satu blok di dalam rantai blockchain.

- **`__init__`** – Menyimpan index blok, timestamp waktu pembuatan, daftar transaksi, nonce (angka untuk mining), hash blok sebelumnya, dan hash blok itu sendiri.
- **`calculate_hash()`** – Menghitung hash SHA-256 dari seluruh data blok. Hash ini bersifat unik dan berubah jika ada data yang dimodifikasi.
- **`print_hash()`** – Mencetak hash blok.
- **`mine_block(difficulty)`** – Proses **Proof of Work**: terus menambah nilai `nonce` dan menghitung ulang hash sampai hash diawali dengan sejumlah angka `"0"` sesuai tingkat kesulitan (`difficulty`). Inilah inti dari mekanisme mining.

---

### 3. Class `Blockchain`
Merepresentasikan keseluruhan rantai blok.

- **`__init__`** – Membuat chain yang diawali dengan **genesis block** (blok pertama), menetapkan difficulty = 5, dan menyiapkan daftar transaksi tertunda.
- **`init_genesis_block()`** – Membuat blok pertama (genesis block) dengan index 0, tanpa transaksi, dan previous hash `"0"`.
- **`add_transactions()`** – Menambahkan transaksi baru ke daftar pending.
- **`get_latest_chain()`** – Mengambil blok terakhir dalam chain.
- **`mine_pending_transactions()`** – Mengumpulkan semua transaksi pending, membuat blok baru, menjalankan proses mining, lalu mengosongkan daftar transaksi pending.

---

### Alur Kerja Program (Bagian `main`)
1. Membuat transaksi dari **Alice** ke **Bob** sebesar **10**.
2. Mencetak transaksi tersebut.
3. Membuat blok secara langsung dan mencetak hashnya.
4. Membuat objek blockchain `myBlockchain`.
5. Menambahkan transaksi ke daftar pending.
6. Menjalankan `mine_pending_transactions()` untuk mem-mining blok baru dan menambahkannya ke chain.
