# Today I Learned (TIL)

> Catatan harian ringkas berisi fakta atau trivia programming.

---

## 📚 Daftar Isi

- [2026-11-09: Asal Usul Nama "Git"](#2026-11-09-asal-usul-nama-git)
- [2026-11-10: Efisiensi Forking Workflow & Cross-Repository PR](#2026-11-10-efisiensi-forking-workflow--cross-repository-pr)
- [2026-11-11: Perbedaan `isset()` dan `empty()` dalam PHP](#2026-11-11-perbedaan-isset-dan-empty-dalam-php)
- [2026-11-12: Perbedaan `include` dan `require` dalam PHP](#2026-11-12-perbedaan-include-dan-require-dalam-php)

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

2026-11-11: Perbedaan isset() dan empty() dalam PHP

Dalam PHP, isset() dan empty() sama-sama digunakan untuk memeriksa suatu variabel, tetapi memiliki fungsi yang berbeda. isset() memeriksa apakah variabel sudah didefinisikan dan nilainya bukan null, sedangkan empty() memeriksa apakah variabel tidak memiliki nilai atau dianggap kosong. Nilai seperti 0, "0", false, null, dan string kosong ("") dianggap kosong oleh empty(). Hal yang perlu diperhatikan adalah variabel yang belum didefinisikan akan menghasilkan false ketika diperiksa menggunakan kedua fungsi tersebut. Oleh karena itu, gunakan isset() ketika ingin memastikan variabel tersedia dan tidak bernilai null, sedangkan empty() ketika ingin memastikan variabel memiliki nilai yang tidak kosong.

---

2026-11-12: Perbedaan include dan require dalam PHP

PHP menyediakan include dan require untuk menyisipkan isi file PHP lain ke dalam file yang sedang dijalankan. Keduanya berguna untuk menghindari penulisan kode berulang, misalnya ketika memisahkan bagian header, footer, atau konfigurasi database ke dalam file tersendiri. Perbedaan utamanya terletak pada penanganan kesalahan ketika file yang dipanggil tidak ditemukan. include akan menghasilkan peringatan (warning), tetapi eksekusi program tetap dilanjutkan. Sebaliknya, require akan menghasilkan kesalahan fatal (Error) sehingga eksekusi program dihentikan. Oleh karena itu, require lebih tepat digunakan untuk file yang wajib tersedia agar aplikasi dapat berjalan, seperti konfigurasi database, sedangkan include dapat digunakan untuk bagian tambahan yang tidak selalu wajib ditampilkan.

---
