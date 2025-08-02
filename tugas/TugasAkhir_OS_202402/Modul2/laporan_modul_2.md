# Laporan Praktikum Sistem Operasi - Modul 2

**Nama**  : Husain Stefano  
**NIM**   : 240202836  
**Kelas** : 2IKRA  
**Modul** : Modul 2 – Penjadwalan CPU (Non-Preemptive Priority)

---

## Tujuan Praktikum

Mengubah algoritma penjadwalan default xv6 menjadi non-preemptive priority scheduling, dan menambahkan syscall untuk mengatur prioritas proses.

---

## Hasil Implementasi

### a. File yang Dimodifikasi

- `proc.h`
- `proc.c`
- `sysproc.c`
- `syscall.c`
- `syscall.h`
- `user.h`
- `usys.S`
- `Makefile`

---

### b. Perubahan Utama

1. Tambah field `priority` pada `struct proc`
2. Tambahkan syscall `set_priority(int)` untuk ubah prioritas proses
3. Modifikasi fungsi `scheduler()` agar memilih proses RUNNABLE dengan prioritas tertinggi (angka kecil)

---

### c. Program Uji

`ptest.c` berisi dua `fork()` anak dengan prioritas berbeda.

---

### d. Hasil Pengujian

```bash
$ ptest
Child 2 selesai
Child 1 selesai
Parent selesai
```

> Anak ke-2 memiliki prioritas lebih tinggi, sehingga selesai lebih dahulu.

---

## Kesimpulan

Modul ini memberikan wawasan tentang bagaimana kernel menjadwalkan proses, serta pengaruh nilai prioritas terhadap eksekusi program. Dengan pendekatan non-preemptive, kontrol eksekusi lebih deterministik tetapi mengorbankan fairness.

**Tanggal Praktikum**: 27 Juli 2025