# Pemasangan

[English](Installation.md) | [Bahasa Indonesia](Installation.id.md)

Tema GRUB tidak selalu dipasang dengan cara yang sama pada setiap distribusi. Baca petunjuk dari proyek tema aslinya terlebih dahulu dan pastikan tema tersebut mendukung versi GRUB, mode boot, serta resolusi layar yang digunakan.

## 1. Dapatkan berkas tema

Buka halaman proyek asli tema melalui katalog. Clone repositorinya atau unduh arsip sumber dari layanan hosting proyek tersebut. Jika tema berada di dalam subdirektori, unduh repositori lalu gunakan folder tema tersebut.

Utamakan pemasangan manual jika belum yakin dengan perubahan yang dilakukan skrip instalasi. Periksa skrip sebelum menjalankannya dengan hak administrator.

## 2. Salin tema

Buat direktori untuk tema lalu salin berkas-berkasnya. Contoh berikut menggunakan jalur bergaya Debian/Ubuntu; distribusi lain mungkin menggunakan direktori GRUB yang berbeda.

```sh
sudo install -d /boot/grub/themes/my-theme
sudo cp -a ./my-theme/. /boot/grub/themes/my-theme/
```

Direktori tema harus berisi berkas `theme.txt` beserta aset yang dirujuk olehnya, seperti gambar, font, dan ikon.

## 3. Konfigurasikan GRUB

Edit `/etc/default/grub` dengan hak administrator dan atur jalur tema:

```sh
GRUB_THEME="/boot/grub/themes/my-theme/theme.txt"
```

Atur `GRUB_GFXMODE` hanya jika diperlukan dan pilih resolusi yang didukung layar serta GRUB. Simpan salinan konfigurasi yang masih berfungsi sebelum melakukan perubahan.

## 4. Buat ulang konfigurasi GRUB

Gunakan perintah yang sesuai dengan distribusi:

- Debian dan Ubuntu: `sudo update-grub`
- Fedora dan openSUSE: `sudo grub2-mkconfig -o /boot/grub2/grub.cfg`
- Arch Linux dan banyak distribusi lainnya: `sudo grub-mkconfig -o /boot/grub/grub.cfg`

Sebagian distribusi menggunakan jalur keluaran yang berbeda. Ikuti dokumentasi distribusi masing-masing dan jangan menyalin perintah secara membabi buta.

## Catatan

- Jangan menganggap semua tema mendukung setiap resolusi, mode firmware, atau versi GRUB.
- Kebijakan Secure Boot dapat mencegah font atau aset lain yang belum ditandatangani untuk dimuat. Ikuti proses penandatanganan yang didokumentasikan distribusi; jangan menonaktifkan fitur keamanan tanpa memahami konsekuensinya.
- Siapkan metode pemulihan dan salinan konfigurasi GRUB yang diketahui berfungsi sebelum mengubah pengaturan bootloader.
- GRUB Customizer dan skrip instalasi pihak ketiga dapat mengubah lebih banyak hal daripada tema itu sendiri. Periksa perilakunya sebelum digunakan.
