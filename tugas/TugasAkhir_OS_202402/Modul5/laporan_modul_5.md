# Laporan Praktikum Sistem Operasi - Modul 5

**Nama**  : Husain Stefano  
**NIM**   : 240202836  
**Kelas** : 2IKRA  
**Modul** : Modul 5 – Audit dan Keamanan Sistem (xv6-public)

---

## Tujuan Praktikum

1. Merekam setiap system call yang dipanggil ke dalam audit log.
2. Mengimplementasikan syscall `get_audit_log(char *buf, int max)` untuk membaca log.
3. Membatasi akses log hanya pada proses dengan PID 1.

---

## Hasil Implementasi

### a. File yang Dimodifikasi

- `syscall.c`
- `sysproc.c`
- `defs.h`
- `user.h`
- `usys.S`
- `syscall.h`
- `Makefile`

---

### b. Penjelasan Fitur Audit

- Audit log menyimpan PID, nomor syscall, dan waktu (tick).
- Maksimal 128 entri disimpan.
- Proses dengan PID ≠ 1 akan ditolak aksesnya ke audit log.

---

### c. Program Pengujian

#### Jika dijalankan oleh proses biasa:

```
$ audit
Access denied or error.
```

#### Jika dijalankan sebagai PID 1:

```
=== Audit Log ===
[0] PID=1 SYSCALL=5 TICK=12
[1] PID=1 SYSCALL=6 TICK=13
...
```

---

## Kesimpulan

Modul ini menekankan aspek keamanan dengan mencatat semua aktivitas sistem call serta mengamankan akses terhadap data tersebut. Teknik ini umum diterapkan dalam sistem audit modern.

**Tanggal Praktikum**: 30 Juli 2025