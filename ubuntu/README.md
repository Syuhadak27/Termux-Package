# 🖥️ Instalasi Ubuntu di Termux & Wrangler (Cloudflare Workers CLI)

Panduan ini menjelaskan cara menginstal **Ubuntu di Termux** menggunakan **proot**, serta **Wrangler (Cloudflare Workers CLI)** untuk Cloudflare Workers.

---

## 📌 1. Instal Termux
Unduh Termux dari sumber berikut:  
- 📥 **[F-Droid](https://f-droid.org/en/packages/com.termux/)** *(Direkomendasikan)*
- 📥 **[GitHub Termux](https://github.com/termux/termux-app/releases)*
- ❌ **Jangan gunakan dari Play Store** (versi tidak diperbarui).

---

## ⚡ 2. Update & Install Proot
```sh
pkg update && pkg upgrade -y
pkg install proot-distro -y
```

---

## 🏗️ 3. Install Ubuntu
Untuk **Ubuntu 24.04**:
```sh
proot-distro install ubuntu
```
Untuk **Ubuntu 22.04**:
```sh
proot-distro install ubuntu-22.04
```

---

## 🚀 4. Menjalankan Ubuntu
```sh
proot-distro login ubuntu
```
Atau, jika menggunakan versi lain:
```sh
proot-distro login ubuntu-22.04
```

---

## 🔗 5. Membuat Skrip `ubuntu.sh`
Agar bisa menjalankan Ubuntu dengan mudah:
```sh
echo 'proot-distro login ubuntu' > ubuntu.sh
chmod +x ubuntu.sh
```
Sekarang bisa dijalankan dengan:
```sh
./ubuntu.sh
```
Agar bisa dipanggil dari mana saja:
```sh
mv ubuntu.sh $PREFIX/bin/ubuntu
```
Sekarang cukup ketik:
```sh
ubuntu
```

---

## 🔄 6. Update Sistem Ubuntu
```sh
apt update && apt upgrade -y
```

---

## ⚙️ 7. Install Wrangler (Cloudflare Workers CLI)

### 🔹 a) Install Dependensi
```sh
apt install curl npm -y
```
Cek versi:
```sh
node -v
npm -v
```

### 🔹 b) Bersihkan Cache npm (Jika Perlu)
```sh
npm cache clean --force
```

### 🔹 c) Install Wrangler
```sh
npm install -g wrangler --unsafe-perm=true
```
Cek apakah sudah terpasang:
```sh
wrangler --version
```

Jika ada error, coba instal langsung via skrip resmi Cloudflare:
```sh
curl -fsSL https://workers.cloudflare.com/get-npm-wrangler.sh | bash
```

---

## 🔑 8. Login ke Cloudflare (Opsional)
```sh
wrangler login
```
Jika Termux tidak mendukung browser, gunakan **API Token**:
```sh
wrangler config
```
Masukkan **API Token** dari **Cloudflare Dashboard**.

---

## 📝 9. Coba Buat Proyek Wrangler
```sh
wrangler init my-worker
cd my-worker
wrangler dev
```

---

## 🚪 10. Keluar dari Ubuntu
```sh
exit
```

---

## ❌ 11. Menghapus Ubuntu (Jika Dibutuhkan)
```sh
proot-distro remove ubuntu
```

---

## ✅ **Selesai! 🎉**
Sekarang **Ubuntu dan Wrangler telah berhasil diinstal di Termux**! 🚀  
Jika ada kendala, cek log dengan:
```sh
cat /root/.npm/_logs/*.log
```

💡 **Selamat coding!** 🛠️🔥
