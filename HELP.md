# Go-Lang Moodules
- Sebelum ada GoModules, untuk menggunakan library atau dependecy external, harus copy dependecy project lain ke project saat ini.
- GoModules digunakan untuk melakukan manajemen dependency atau library di GoLang.
- GoModules mulai ada sejak GoLang versi 1.11 dan 1.12.

## Membuat Module Baru (atau project baru)
- Menggunakan perintah `go mod init nama-module`. Nama module biasanya disamakan dengan nama folder.
- Akan berisi informasi nama module dan versi GoLang yg digunakan.

## Rilis Module
- Membuat project dengan nama module sesuai repo github, contoh `go mod init github.com/dirasanjayawardana/golang_dasar_contoh_module`
- Untuk merilis module, hanya perlu membuat Tag Git dengan `git tag v1.0.0` (contoh untuk merilis module versi 1.0.0)
- Kemudian push module ke github, contoh `git push origin v1.0.0`

## Menambah Dependecy
- Dengan peritah `go get nama-module`, contoh `go get github.com/dirasanjayawardana/golang_dasar_contoh_module`
- Ketika sudah berhasil, pada file go.mod akan berisi dependecy yang sudah di tambahkan

## Clone Project GoLang
- ``go mod tidy` -> Menghapus dependency yang tidak terpakai dan menambahkan dependency yang dibutuhkan berdasarkan kode saat ini.
- ``go mod download` -> Mengunduh semua dependency yang terdaftar dalam file go.mod tanpa perlu menjalankan kode.
- Dependency yg didownload akan disimpan di dalam cache modul Go di direktori `$GOPATH/pkg/mod` (linux) dan `%GOPATH%\pkg\mod` (windows)
- Secara default, jika GOPATH tidak diatur, Go akan menggunakan direktori `~/go/pkg/mod` (linux) dan `%USERPROFILE%\go\pkg\mod`

## Upgrade Module
- Untuk upgrade module, cukup commit perubahan dan membuat tag baru di Git, contoh `git tag v2.0.0`
- Kemudian push `git push origin v2.0.0`

## Upgrade Dependency
### Minor update (1.x.x)
- Untuk upgrade versi dependency terbaru, dengan mengubah isi go.mod dengan tag terbaru
- Contohnya `require github.com/dirasanjayawardana/golang_dasar_contoh_module v1.5.0`
- Kemudian jalankan `go get`

### Major Update (x.0.0)
- Major update biasanya terjadi karena ada perubahan pada isi kode program module
- Sehingga tidak backward compatible (tidak compatible dengan versi sebelumnya)
- Untuk melakukan upgrade major, strategi terbaiknya adalah merubah nama module pada project library nya
- contoh `module github.com/dirasanjayawardana/golang_dasar_contoh_module` menjadi `module github.com/dirasanjayawardana/golang_dasar_contoh_module/v2`
- Kemudian commit dan buat tag dengan versi `vx.0.0` contohnya `v2.0.0`
- Kemudian untuk menggunakannya, hapus module sebelumnya pada go.mod, kemudian `go get github.com/dirasanjayawardana/golang_dasar_contoh_module/v2`