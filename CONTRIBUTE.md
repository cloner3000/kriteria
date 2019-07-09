# How To Contribute

PENTING!!! HARAP KODING DI BRANCH MASING-MASING!!!

Dokumen ini adalah panduan untuk kontribusi dalam pengembangan aplikasi. Mengingat aplikasi dikembangkan oleh sekelompok
orang sehingga diperlukan standarisasi penulisan kode dan penamaan file dan variabel.


## Aturan Penamaan Model
Untuk model harus mengikuti aturan penamaan Yii2 sebagai berikut:
1. Nama diawali dengan huruf kapital. Jika memiliki 2 atau lebih suku kata, setiap awal suku kata adalah huruf kapital.
   Misalnya `MataKuliah`.
2. Untuk nama model dari tabel di database (ActiveRecord), gunakan nama tabelnya yang tertulis di komentar setiap tabel 
   tanpa prefix/suffix `t_` atau `d_`.
   Misalnya, nama tabel di database adalah `t_psrt`, maka nama model adalah `Peserta`.
3. Untuk nama model Form gunakan prefix `Form`. Misalnya form masuk, gunakan nama model `FormMasuk`.


## Aturan Penamaan Controller
Controller Utama adalah `BerandaController` atau `MainController`.

Untuk penamaan Controller diatur sedemikian rupa menggunakan bahasa Indonesia atau bahasa Inggris dan diakhiri dengan suffix `Controller`.

Begitu pula dengan penamaan Method/Function di dalam Controller. 
Penamaan ini tujuannya untuk menghasilkan URL yang lebih baik.

Berikut contoh URL yang baik
```
http://id.uin-suska.ac.id/masuk             untuk masuk aplikasi
http://id.uin-suska.ac.id/beranda           untuk beranda utama
http://id.uin-suska.ac.id/kata-sandi/lupa   untuk lupa kata sandi
http://id.uin-suska.ac.id/akun/baru         untuk buat akun baru
```

## Aturan Penamaan View
Aturan penamaan view disesuaikan dengan aturan Yii2 dengan tambahan sebagai berikut:
1. Nama view default mengikuti nama function di controller.
2. Jika 1 function membutuhkan lebih dari 1 file view, gunakan nama ektra setelah nama view.

Berikut contoh penamaan default View
```
Nama Controller                 Nama View
====================================================
MainController/actionIndex      main/index
MainController/actionMasuk      main/masuk
MainController/actionKeluar     main/keluar
DaftarController/actionBaru     daftar/baru
```

Berikut contoh nama view untuk masing-masing function:
```
class DaftarController {
    public function actionBaru($tipe) {
        if($tipe == 'Satu') {
            return $this->render('baru-satu');
        } elseif($tipe == 'Dua') {
            return $this->render('baru-dua');
        } elseif($tipe == 'Tiga') {
            return $this->render('baru-tiga');
        } else {
            return $this->render('baru');
        }
    }
}
```

## Aturan Penamaan Asset dan File Asset (JS CSS)
Untuk membuat asset, silahkan gunakan aturan sebagai nerikut:
1. Asset Utama adalah `AppAsset`, asset ini untuk load asset umum (jQuery, Bootstrap, AdminLTE, Font Awesome).
2. Nama asset ikut nama Controller dan nama Function diakhiri dengan kata `Asset`. 

Berikut contoh penamaan Asset
```
Nama Controller                 Nama Asset
====================================================
MainController/actionMasuk      MainMasukAsset
MainController/actionKeluar     MainKeluarAsset
DaftarController/actionBaru     DaftarBaruAsset
```

Untuk nama file JS dan CSS untuk asset, gunakan aturan berikut:
1. File JS dan CSS custom dibuat di folder `/web/customs`. File CSS diletakkan di folder `css` dan file JS di folder `js`.
2. Setiap file JS dan CSS dibuat folder khusus berdasarkan nama controller, kecuali `AppAsset`.
3. Nama file JS dan CSS dibuat berdasarkan views
4. File JS dan CSS yang sudah di-minify gunakan suffix `.min` sebelum
   ekstensi file.

Berikut contoh penamaan file JS dan CSS berdasarkan nama Controller + View
```
Nama Controller                 Nama View           Nama File JS CSS
===================================================================================
DaftarController/actionBaru     daftar/baru-satu    custom/css/daftar/baru.satu.css
DaftarController/actionBaru     daftar/baru-satu    custom/js/daftar/baru.satu.min.js
DaftarController/actionBaru     daftar/baru         custom/css/daftar/baru.min.css
DaftarController/actionBaru     daftar/baru         custom/js/daftar/baru.js
```
