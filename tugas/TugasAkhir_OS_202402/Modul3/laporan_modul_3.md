# Laporan Praktikum Sistem Operasi - Modul 3

**Nama**  : Husain Stefano  
**NIM**   : 240202836  
**Kelas** : 2IKRA  
**Modul** : Modul 3 – Manajemen Memori Lanjutan (CoW & Shared Memory)

---

## Tujuan Praktikum

1. Mengimplementasikan **Copy-on-Write (CoW)** pada `fork()`
2. Menambahkan fitur **Shared Memory** ala System V

---

## Hasil Implementasi

### a. File yang Dimodifikasi

- `vm.c`
- `trap.c`
- `proc.c`
- `sysproc.c`
- `defs.h`, `mmu.h`
- `syscall.c`, `syscall.h`, `user.h`, `usys.S`
- `Makefile`

---

### b. Fitur Copy-on-Write

- Mengganti `copyuvm()` dengan `cowuvm()`
- Tambahkan flag `PTE_COW`
- Tangani `T_PGFLT` untuk salin halaman saat `write`
- Gunakan `ref_count[]` untuk melacak pemakaian halaman

#### Uji `cowtest`

```bash
Child sees: Y
Parent sees: X
```

---

### c. Fitur Shared Memory

- Tambah `shmtab[]` berisi key, frame, refcount
- Implementasi syscall `shmget(int)` dan `shmrelease(int)`
- Memungkinkan proses berbagi satu halaman memori di `USERTOP`

#### Uji `shmtest`

```bash
Child reads: A
Parent reads: B
```

---

## Kesimpulan

Modul ini mengajarkan teknik manajemen memori tingkat lanjut, terutama efisiensi `fork()` dengan CoW dan komunikasi antar proses via shared memory. Pemahaman ini penting dalam membangun kernel modern yang efisien dan aman.

**Tanggal Praktikum**: 28 Juli 2025