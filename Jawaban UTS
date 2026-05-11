# UTS Teknik Kompilasi

**Nama :** Jibran Dwi Andra    

**NIM :** 231011401730

**Kelas :** 06TPLE003

**Mata Kuliah :** Teknik Kompilasi

---

---

### ✅ TUGAS 1 — Penambahan Token Eksponen

Saya menambahkan simbol `\^` ke dalam kumpulan karakter operator pada fungsi `re.findall`. Ini memungkinkan *Lexer* mengenali operator pangkat sebagai token yang valid.

**Perubahan Kode:**

```python
# Menambahkan ^ ke dalam regex
self.tokens = iter(re.findall(r'[a-zA-Z_]\w*|\d+(?:\.\d+)?|[\+\-\*/\(\)\^]', source))

```

---

### ✅ TUGAS 2 — Definisi Precedence Pangkat

Membuat fungsi baru `power()` yang menangani operasi eksponensial. Fungsi ini memanggil `factor()` untuk mendapatkan angka atau variabel, lalu memproses simbol `^`.

**Implementasi Fungsi:**

```python
def power(self):
    node = self.factor()
    while self.self_current == '^':
        op = self.self_current
        self.advance()
        # Menggunakan rekursi agar pangkat bersifat right-associative (2^3^2)
        node = BinOp(left=node, op=op, right=self.power()) 
    return node

```

---

### ✅ TUGAS 3 — Rekonstruksi Hirarki Precedence

Mengubah alur pemanggilan pada fungsi `term()`. Agar operator perkalian (`*`) dan pembagian (`/`) menghormati prioritas pangkat yang lebih tinggi, mereka sekarang memanggil `power()` alih-alih langsung ke `factor()`.

**Perubahan pada `term()`:**

```python
def term(self):
    node = self.power() # Prioritas ditingkatkan ke power
    while self.self_current in ('*', '/'):
        op = self.self_current
        self.advance()
        node = BinOp(left=node, op=op, right=self.power())
    return node

```

---
