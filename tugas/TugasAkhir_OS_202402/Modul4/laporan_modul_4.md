# Laporan Praktikum Sistem Operasi - Modul 4

**Nama**  : Husain Stefano  
**NIM**   : 240202836  
**Kelas** : 2IKRA  
**Modul** : Modul 4 – Subsistem Kernel Alternatif (xv6-public)

---

## Tujuan Praktikum

1. Mengimplementasikan syscall `chmod(path, mode)` untuk mengatur mode file menjadi **read-only** atau **read-write**.
2. Menambahkan driver device `/dev/random` sebagai pseudo-device yang menghasilkan data acak.

---

## Hasil Implementasi

### a. File yang Dimodifikasi / Ditambahkan

- `fs.h`
- `file.c`
- `fs.c`
- `syscall.h`
- `user.h`
- `usys.S`
- `syscall.c`
- `sysfile.c`
- `random.c`
- `init.c`
- `Makefile`

---

### b. Penjelasan Fitur yang Diimplementasikan

#### 1. `chmod(path, mode)`
- Mengatur inode file ke mode 0 (read-write) atau 1 (read-only).
- Mencegah `write()` jika inode dalam mode read-only.

#### 2. `/dev/random`
- Device pseudo yang mengembalikan byte acak.
- Implementasi dengan LCG sederhana.
- Diakses seperti file biasa melalui `read()`.

---

### c. Hasil Pengujian

#### `chmodtest`

```
Write blocked as expected
```

#### `randomtest`

```
187 53 99 241 0 34 199 8
```

---

## Kesimpulan

Modul ini mengajarkan tentang perluasan syscall dan penambahan driver baru di kernel. Fitur `chmod()` menunjukkan pengendalian akses file, sedangkan `/dev/random` memperkenalkan konsep pseudo-device.

**Tanggal Praktikum**: 29 Juli 2025