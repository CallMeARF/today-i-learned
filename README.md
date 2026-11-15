# Today I Learned (TIL)

> Catatan harian ringkas berisi fakta atau trivia programming.

---

## 📚 Daftar Isi

- [2026-11-09: Asal Usul Nama "Git"](#2026-11-09-asal-usul-nama-git)
- [2026-11-10: Efisiensi Forking Workflow & Cross-Repository PR](#2026-11-10-efisiensi-forking-workflow--cross-repository-pr)
- [2026-11-11: Perbedaan `isset()` dan `empty()` dalam PHP](#2026-11-11-perbedaan-isset-dan-empty-dalam-php)
- [2026-11-12: Perbedaan `include` dan `require` dalam PHP](#2026-11-12-perbedaan-include-dan-require-dalam-php)
- [2026-11-13: Perbedaan Operator `==` dan `===` dalam PHP](#2026-11-13-perbedaan-operator--dan--dalam-php)
- [2026-11-14: Mengapa `NULL = NULL` Menghasilkan `UNKNOWN` di SQL](#2026-11-14-mengapa-null--null-menghasilkan-unknown-di-sql)
- [2026-11-15: Jebakan Perilaku `typeof null === "object"` di JavaScript](#2026-11-15-jebakan-perilaku-typeof-null--object-di-javascript)

---

### 2026-11-09: Asal Usul Nama "Git"

Linus Torvalds menamai _software_ buatan ini secara humoris dan ironis. Dalam bahasa gaul Inggris (_British slang_), kata **"git"** adalah sebutan kasar yang berarti "orang yang tidak menyenangkan, bodoh, atau menyebalkan". Linus berseloroh, _"Saya orang yang egois, jadi saya menamai semua proyek saya sesuai nama saya sendiri: pertama Linux, dan sekarang Git."_

Secara teknis, Linus menyebut Git sebagai singkatan fleksibel tergantung _mood_ pengembangnya: jika kinerjanya bagus maka berarti _Global Information Tracker_, namun jika terjadi _error_ atau masalah pada sistem, maka Git berarti _Global Information Trash_.

---

### 2026-11-10: Efisiensi Forking Workflow & Cross-Repository PR

Pull Request (PR) pada repositori hasil _fork_ dapat dilakukan secara langsung lintas repositori (_cross-repository_) dari branch fitur milik kita ke branch utama (_main_) repositori pemilik asli (_upstream_).

Kita tidak perlu memindahkan atau me-merge perubahan tersebut ke branch _main_ di akun kita sendiri terlebih dahulu. Setelah PR diterima oleh pemilik repositori asli, kita cukup mengeksekusi fitur **Sync Fork** di GitHub untuk menyelaraskan branch _main_ kita secara instan.

---

### 2026-11-11: Perbedaan isset() dan empty() dalam PHP

Dalam PHP, isset() dan empty() sama-sama digunakan untuk memeriksa suatu variabel, tetapi memiliki fungsi yang berbeda. isset() memeriksa apakah variabel sudah didefinisikan dan nilainya bukan null, sedangkan empty() memeriksa apakah variabel tidak memiliki nilai atau dianggap kosong. Nilai seperti 0, "0", false, null, dan string kosong ("") dianggap kosong oleh empty(). Hal yang perlu diperhatikan adalah variabel yang belum didefinisikan akan menghasilkan false ketika diperiksa menggunakan kedua fungsi tersebut. Oleh karena itu, gunakan isset() ketika ingin memastikan variabel tersedia dan tidak bernilai null, sedangkan empty() ketika ingin memastikan variabel memiliki nilai yang tidak kosong.

---

### 2026-11-12: Perbedaan include dan require dalam PHP

PHP menyediakan include dan require untuk menyisipkan isi file PHP lain ke dalam file yang sedang dijalankan. Keduanya berguna untuk menghindari penulisan kode berulang, misalnya ketika memisahkan bagian header, footer, atau konfigurasi database ke dalam file tersendiri. Perbedaan utamanya terletak pada penanganan kesalahan ketika file yang dipanggil tidak ditemukan. include akan menghasilkan peringatan (warning), tetapi eksekusi program tetap dilanjutkan. Sebaliknya, require akan menghasilkan kesalahan fatal (Error) sehingga eksekusi program dihentikan. Oleh karena itu, require lebih tepat digunakan untuk file yang wajib tersedia agar aplikasi dapat berjalan, seperti konfigurasi database, sedangkan include dapat digunakan untuk bagian tambahan yang tidak selalu wajib ditampilkan.

---

### 2026-11-13: Perbedaan Operator == dan === dalam PHP

Dalam PHP, operator == dan === sama-sama digunakan untuk membandingkan dua nilai, tetapi memiliki aturan perbandingan yang berbeda. Operator == (loose comparison) hanya membandingkan nilai tanpa mengharuskan tipe datanya sama, sehingga PHP dapat melakukan konversi tipe data secara otomatis (type juggling). Sebaliknya, operator === (strict comparison) membandingkan nilai sekaligus tipe datanya. Sebagai contoh, 5 == "5" menghasilkan true karena nilainya dianggap sama setelah konversi tipe data, sedangkan 5 === "5" menghasilkan false karena satu nilai bertipe integer dan yang lainnya string. Oleh karena itu, operator === lebih disarankan ketika ingin memastikan nilai dan tipe data benar-benar sama sehingga menghindari hasil perbandingan yang tidak terduga.

---

### 2026-11-14: Mengapa `NULL = NULL` Menghasilkan `UNKNOWN` di SQL

Dalam SQL, `NULL` bukanlah sebuah nilai kosong atau nol, melainkan penanda bahwa suatu data **tidak diketahui** (_unknown_) atau belum ada. Karena sifatnya yang tidak diketahui, membandingkan dua nilai `NULL` menggunakan operator `=` (seperti `WHERE deleted_at = NULL`) tidak akan menghasilkan `TRUE`, melainkan `UNKNOWN`—yang pada klausa `WHERE` diperlakukan sama seperti `FALSE`.

Itulah sebabnya _query_ `SELECT * FROM users WHERE deleted_at = NULL` selalu mengembalikan nol baris meskipun kolom tersebut banyak yang kosong. Untuk memeriksa keberadaan `NULL` secara akurat di SQL, wajib gunakan operator khusus **`IS NULL`** atau **`IS NOT NULL`**.

---

### 2026-11-15: Jebakan Perilaku `typeof null === "object"` di JavaScript

Jika kamu menjalankan `typeof null` di JavaScript, hasilnya adalah `"object"`, bukan `"null"`. Perilaku ini sebenarnya adalah _bug_ historis sejak versi pertama JavaScript pada tahun 1995 yang tidak pernah diperbaiki demi menjaga kompatibilitas dengan jutaan situs web lama (_backward compatibility_).

Pada implementasi awal mesin JavaScript, tipe data direpresentasikan menggunakan _type tag_ 32-bit, di mana tag `000` menandakan sebuah objek. Sementara itu, nilai `null` direpresentasikan sebagai _NULL pointer_ (`0x00` yang seluruh bitnya nol), sehingga mesin keliru membacanya sebagai `"object"`. Oleh karena itu, jangan pernah mengandalkan `typeof x === "object"` saja untuk mengecek objek; pastikan juga menambahkan kondisi `x !== null`.

---
