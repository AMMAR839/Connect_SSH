
### Tahap 1: Konfigurasi di Laptop Ubuntu 

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


