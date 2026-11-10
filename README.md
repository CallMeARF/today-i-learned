# Today I Learned (TIL)

> Catatan harian ringkas berisi fakta atau trivia programming.

---

## 📚 Daftar Isi

- [Git & GitHub](#git--github)
  - [2026-11-09: Asal Usul Nama "Git"](#2026-11-09-asal-usul-nama-git)

---

## Git & GitHub

### 2026-11-09: Asal Usul Nama "Git"

Linus Torvalds menamai _software_ buatan ini secara humoris dan ironis. Dalam bahasa gaul Inggris (_British slang_), kata **"git"** adalah sebutan kasar yang berarti "orang yang tidak menyenangkan, bodoh, atau menyebalkan". Linus berseloroh, _"Saya orang yang egois, jadi saya menamai semua proyek saya sesuai nama saya sendiri: pertama Linux, dan sekarang Git."_

Secara teknis, Linus menyebut Git sebagai singkatan fleksibel tergantung _mood_ pengembangnya: jika kinerjanya bagus maka berarti _Global Information Tracker_, namun jika terjadi _error_ atau masalah pada sistem, maka Git berarti _Global Information Trash_.

---

### 2026-11-10: Efisiensi Forking Workflow & Cross-Repository PR

Pull Request (PR) pada repositori hasil _fork_ dapat dilakukan secara langsung lintas repositori (_cross-repository_) dari branch fitur milik kita ke branch utama (_main_) repositori pemilik asli (_upstream_).

Kita tidak perlu memindahkan atau me-merge perubahan tersebut ke branch _main_ di akun kita sendiri terlebih dahulu. Setelah PR diterima oleh pemilik repositori asli, kita cukup mengeksekusi fitur **Sync Fork** di GitHub untuk menyelaraskan branch _main_ kita secara instan.

---
