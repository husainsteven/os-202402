# Laporan Praktikum Sistem Operasi - Modul 1

**Nama**  : Husain Stefano  
**NIM**   : 240202836  
**Kelas** : 2IKRA  
**Modul** : Modul 1 – System Call dan Instrumentasi Kernel

---

## Tujuan Praktikum

1. Mengimplementasikan syscall `getpinfo(struct pinfo *ptable)` untuk mendapatkan informasi proses aktif.
2. Mengimplementasikan syscall `getreadcount()` untuk menghitung total pemanggilan `read()` sejak sistem boot.

---

## Hasil Implementasi

### a. File yang Dimodifikasi

- `proc.h`
- `sysproc.c`
- `sysfile.c`
- `syscall.c`
- `syscall.h`
- `user.h`
- `usys.S`
- `Makefile`

---

### b. Deskripsi Syscall

#### `getpinfo(struct pinfo *ptable)`
- Mengisi array `pid`, `mem`, dan `name` dari proses aktif.
- Informasi disalin ke user melalui pointer `ptable`.

#### `getreadcount()`
- Mengembalikan nilai integer jumlah pemanggilan `read()`.

---

### c. Langkah Implementasi

1. Tambahkan struct `pinfo` ke `proc.h`
2. Tambah counter global `readcount` di `sysproc.c`
3. Modifikasi `sys_read()` untuk menaikkan `readcount`
4. Implementasi `sys_getpinfo` dan `sys_getreadcount` di `sysproc.c`
5. Daftarkan syscall di `syscall.c`, `syscall.h`, `user.h`, `usys.S`
6. Buat program pengujian `ptest.c` dan `rtest.c`
7. Tambah ke Makefile

---

### d. Hasil Pengujian

#### `ptest`

```bash
$ ptest
PID	MEM	NAME
1	4096	init
2	2048	sh
3	2048	ptest
```

#### `rtest`

```bash
$ rtest
Read Count Sebelum: 3
hello
Read Count Setelah: 4
```

---

## Kesimpulan

Modul ini memberikan pemahaman tentang bagaimana menambahkan dan menggunakan system call baru dalam kernel xv6. Diperlukan pemahaman pointer, manajemen proses, serta koneksi antara user space dan kernel space.

**Tanggal Praktikum**: 26 Juli 2025