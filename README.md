# Today I Learned (TIL)

Kumpulan catatan singkat harian mengenai konsep programming, Git, backend, dan *best practices*.

---

## 📚 Daftar Isi

- [Git & GitHub](#git--github)
  - [2026-11-09: Navigasi Commit (`HEAD~` vs `HEAD^`)](#2026-11-09-navigasi-commit-head-vs-head)
    - [Simbol Caret (`^`)](#1-simbol-caret-)
    - [Simbol Tilde (`~`)](#2-simbol-tilde-)
    - [Aturan Cepat (Cheatsheet)](#3-aturan-cepat-cheatsheet)
- [PHP & Backend](#php--backend)

---

## Git & GitHub

### 2026-11-09: Navigasi Commit (`HEAD~` vs `HEAD^`)

Saat ingin berpindah atau melihat commit sebelum `HEAD` (commit saat ini), Git menyediakan dua simbol khusus: **Caret (`^`)** dan **Tilde (`~`)**. Sekilas fungsinya sama, tapi ada perbedaan mendasar:

#### 1. Simbol Caret (`^`)
- **Fungsi:** Bergerak **secara horizontal** melintasi *parent* (orang tua) dari commit hasil *merge*.
- `HEAD^` (atau `HEAD^1`) = Parent pertama dari commit saat ini.
- `HEAD^2` = Parent kedua (cabang lain yang di-*merge* ke cabang ini).

#### 2. Simbol Tilde (`~`)
- **Fungsi:** Bergerak **secara vertikal** lurus ke belakang sesuai urutan riwayat commit.
- `HEAD~1` = 1 commit di belakang HEAD.
- `HEAD~2` = 2 commit di belakang HEAD (sama dengan `HEAD^^`).
- `HEAD~5` = 5 commit di belakang HEAD.

#### 3. Aturan Cepat (Cheatsheet)
- Gunakan **`~N`** jika cuma ingin mundur **N langkah** ke belakang pada garis riwayat yang sama.
- Gunakan **`^N`** khusus saat menelusuri **parent cabang lain** pada titik commit hasil *merge*.

---

## PHP & Backend
