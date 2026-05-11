### Jawaban Pertanyaan Refleksi

**Nama :** Jibran Dwi Andra

**NIM :** 231011401730

**Kelas :** 06TPLE003

---

### 1. Mengapa `power()` harus dipanggil di dalam `term()`, bukan sebaliknya?

Ini adalah prinsip **Operator Precedence** (Prioritas Operator). Dalam struktur *Recursive Descent Parser*, fungsi yang dipanggil di level yang lebih rendah justru dieksekusi lebih dulu.

**Urutan Prioritasnya:**

```
* `expr()` → Penjumlahan & Pengurangan (Paling luar)
* `term()` → Perkalian & Pembagian
* `power()` → Pangkat (Paling dalam/awal)
* `factor()` → Nilai dasar (Angka/Variabel)
```
Dengan memanggil `power()` di dalam `term()`, kita memastikan operasi pangkat diselesaikan sebelum hasilnya dikalikan atau dibagi. 

Contoh: 
```
2 * 3^2 akan dihitung sebagai 2 * 9 = 18, bukan (2 * 3)^2 = 36.
```

### 2. Apa yang terjadi pada Analisis Semantik jika variabel `z` tidak ada di `symbol_table`?

Fase Analisis Semantik akan mendeteksi **Semantic Error** berupa variabel yang tidak terdefinisi (*Undefined Variable*). Meskipun secara penulisan (sintaks) kode `z` mungkin benar, namun karena kompiler tidak menemukan referensi nilai untuk `z` di dalam `symbol_table`, sistem akan menghentikan proses dan mengeluarkan pesan kesalahan:

```
`ParserError: Semantic Error: Undefined variable 'z'`
```

### 3. Mengapa instruksi untuk `a ^ 2` harus muncul sebelum `+` dalam TAC?

Karena **Three Address Code (TAC)** mengikuti prinsip ketergantungan data (*data dependency*). Sebuah operasi baru bisa dijalankan jika nilai-nilai pengisinya (*operand*) sudah siap.

Dalam ekspresi $a^2 + b$, nilai dari $a^2$ harus dihitung dan disimpan terlebih dahulu dalam variabel sementara (misalnya `t1`), agar nantinya instruksi penjumlahan memiliki nilai konkret untuk dijumlahkan. TAC mencerminkan urutan kerja prosesor yang logis dan sekuensial.

**Contoh alur yang benar:**
```
`t1 = a ^ 2`  (Hitung pangkat dulu)
`t2 = t1 + b` (Gunakan hasil t1 untuk penjumlahan)
```
