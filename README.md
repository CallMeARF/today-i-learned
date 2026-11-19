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
- [2026-11-16: Mengapa `HttpOnly` Cookie Penting untuk Mencegah Pencurian Sesi XSS](#2026-11-16-mengapa-httponly-cookie-penting-untuk-mencegah-pencurian-sesi-xss)
- [2026-11-17: Jebakan `z-index` dan Stacking Context dalam CSS](#2026-11-17-jebakan-z-index-dan-stacking-context-dalam-css)
- [2026-11-18: Mengapa `chmod 777` Berbahaya dan Cara Membaca Izin File Linux](#2026-11-18-mengapa-chmod-777-berbahaya-dan-cara-membaca-izin-file-linux)
- [2026-11-19: Mengenal N+1 Query Problem dan Cara Menghindarinya](#2026-11-19-mengenal-n1-query-problem-dan-cara-menghindarinya)

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

### 2026-11-16: Mengapa `HttpOnly` Cookie Penting untuk Mencegah Pencurian Sesi XSS

Secara _default_, _cookie_ yang disimpan di _browser_ dapat dibaca dan dimodifikasi oleh JavaScript melalui properti `document.cookie`. Jika aplikasi web memiliki celah _Cross-Site Scripting_ (XSS), skrip berbahaya dari pihak ketiga bisa mencuri _session ID_ atau token autentikasi pengguna hanya dengan mengakses `document.cookie` lalu mengirimkannya ke server penyerang.

Dengan menambahkan atribut **`HttpOnly`** pada header `Set-Cookie` dari sisi _server_, _browser_ akan melarang akses JavaScript terhadap _cookie_ tersebut dan hanya mengirimkannya secara otomatis melalui permintaan HTTP/HTTPS. Meskipun tidak mencegah serangan XSS itu sendiri, `HttpOnly` membatasi dampak serangan sehingga _session hijacking_ jauh lebih sulit dilakukan.

---

### 2026-11-17: Jebakan `z-index` dan Stacking Context dalam CSS

Memberikan nilai `z-index: 9999` tidak selalu menjamin sebuah elemen akan tampil di lapisan paling depan. Dalam CSS, urutan tumpukan elemen (*layering*) tidak dihitung secara global, melainkan dibatasi oleh **`stacking context`** milik elemen induknya (*parent*).

Sebuah elemen induk akan menciptakan *stacking context* baru apabila memiliki properti tertentu seperti `position` (selain `static`) dengan nilai `z-index` spesifik, `opacity` kurang dari `1`, `transform`, atau `filter`. Jika induk A memiliki `z-index: 1` dan induk B memiliki `z-index: 2`, maka elemen anak di dalam induk A tidak akan pernah bisa menutupi induk B meskipun diberi `z-index: 99999`. Memahami struktur *stacking context* mencegah penumpukan angka `z-index` yang tidak perlu saat menata komponen seperti *navbar*, *dropdown*, dan *modal*.

---

### 2026-11-18: Mengapa `chmod 777` Berbahaya dan Cara Membaca Izin File Linux

Saat mengalami kendala *permission denied* di Linux, menjalankan `chmod 777` sering dijadikan jalan pintas agar aplikasi langsung berjalan. Padahal, perintah ini memberikan hak akses penuh untuk membaca (`read` = 4), menulis (`write` = 2), dan mengeksekusi (`execute` = 1) file kepada tiga pihak sekaligus: pemilik file (*owner*), grup (*group*), dan semua pengguna lain di sistem (*others*).

Jika sebuah direktori publik web diberi izin `777`, siapa pun atau skrip berbahaya yang berhasil masuk ke *server* dapat mengubah kode sumber maupun menyisipkan *malware* dengan bebas. Sebagai standar keamanan produksi, gunakan **`755`** untuk direktori (pemilik memiliki akses penuh, sementara yang lain hanya bisa membaca dan masuk ke direktori) dan **`644`** untuk file biasa agar hanya pemilik yang dapat memodifikasi isinya.

---

### 2026-11-19: Mengenal N+1 Query Problem dan Cara Menghindarinya

*N+1 Query Problem* terjadi ketika sebuah aplikasi mengeksekusi **1 *query*** utama untuk mengambil daftar data induk (misalnya 20 artikel blog), lalu menjalankan **N *query*** tambahan secara berulang di dalam *loop* untuk mengambil data relasinya (misalnya nama penulis untuk masing-masing dari 20 artikel tersebut). Akibatnya, sistem melakukan 21 kali *round-trip* ke *database* hanya untuk memuat satu halaman.

Masalah performa ini sering tersembunyi di balik fitur *lazy loading* bawaan ORM (seperti Eloquent di Laravel) saat data sampel masih sedikit, namun akan melambatkan aplikasi secara drastis ketika jumlah baris membengkak. Solusinya adalah menggunakan teknik ***eager loading*** (seperti `Article::with('author')->get()`), sehingga seluruh data relasi diambil sekaligus hanya dalam **2 *query*** terlepas dari berapa banyak baris data yang dimuat.

---