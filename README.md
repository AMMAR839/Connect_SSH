Langkah yang sangat tepat! Menggunakan SSH (Secure Shell) adalah cara standar dan paling efisien untuk mengontrol komputer *companion* (seperti Ubuntu di kapalmu) dari jarak jauh (misalnya dari laptop Windows GCS di darat).

Dengan SSH, kamu tidak perlu lagi menyambungkan monitor atau keyboard ke laptop Ubuntu saat pengujian; cukup akses terminalnya lewat jaringan Wi-Fi/LAN.

Berikut adalah langkah-langkah untuk membuat laptop Ubuntu kamu bisa diakses lewat SSH:

### Tahap 1: Konfigurasi di Laptop Ubuntu (Hanya dilakukan sekali)

**1. Install OpenSSH Server**
Secara default, Ubuntu memiliki SSH *client*, tetapi belum menginstal SSH *server* untuk menerima koneksi. Buka terminal di Ubuntu dan jalankan:

```bash
sudo apt update
sudo apt install openssh-server -y

```

**2. Pastikan Layanan SSH Berjalan**
Setelah instalasi selesai, cek status layanannya:

```bash
sudo systemctl status ssh

```

*(Jika statusnya `active (running)`, tekan tombol `q` untuk keluar dari log).*

**3. Izinkan SSH Lewat Firewall (Opsional tapi Penting)**
Jika laptop Ubuntu kamu mengaktifkan *Uncomplicated Firewall* (UFW), kamu harus membuka port untuk SSH agar koneksi tidak diblokir:

```bash
sudo ufw allow ssh

```

**4. Cari Tahu Username dan IP Address Ubuntu**
Kamu butuh dua informasi ini untuk login nanti.

* Untuk melihat **username**, ketik: `whoami`
* Untuk melihat **IP Address**, ketik: `hostname -I` atau `ip a` (Catat IP yang terhubung ke Wi-Fi/LAN yang sama dengan Windows, biasanya berawalan `192.168.x.x`).

---

### Tahap 2: Cara Mengakses dari Laptop Windows

**Syarat Wajib:** Pastikan Laptop Windows dan Laptop Ubuntu **terhubung ke jaringan yang sama** (misalnya konek ke router Wi-Fi yang sama, atau terhubung langsung menggunakan kabel LAN).

1. Buka **Command Prompt (cmd)** atau **PowerShell** di Windows. (Windows 10 dan 11 sudah punya fitur SSH bawaan, jadi tidak perlu aplikasi tambahan seperti PuTTY).
2. Ketik perintah koneksi dengan format `ssh username@ip_address`. Misalnya, jika username Ubuntu kamu adalah `ammar` dan IP-nya `192.168.1.15`, ketik:
```cmd
ssh ammar@192.168.1.15

```


3. Saat pertama kali terkoneksi, akan muncul pesan peringatan *authenticity of host*. Ketik `yes` lalu tekan Enter.
4. Masukkan **password laptop Ubuntu** kamu (saat mengetik password di terminal, karakternya memang tidak akan muncul di layar. Ketik saja lalu tekan Enter).

Jika berhasil, tampilan Command Prompt Windows kamu akan berubah menjadi *command line* Ubuntu. Kamu sudah bisa menjalankan skrip `jalankan_rtk.sh`, menjalankan node ROS, atau mengecek koneksi MAVProxy langsung dari Windows!

### Tips Tambahan untuk Proyek Kapal:

Karena IP Address Wi-Fi bisa berubah-ubah setiap kali laptop direstart (DHCP), apakah kamu ingin saya pandu cara membuat koneksi **Static IP** antara Ubuntu dan Windows menggunakan kabel LAN agar koneksinya selalu tetap dan stabil saat dibawa ke lapangan?
