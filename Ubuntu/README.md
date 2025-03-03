

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
``sh
pkg update && pkg upgrade -y
pkg install proot-distro -y
```

---

🏗️ 3. Install Ubuntu

Untuk Ubuntu 24.04:

proot-distro install ubuntu

Untuk Ubuntu 22.04:

proot-distro install ubuntu-22.04


---

🚀 4. Menjalankan Ubuntu

proot-distro login ubuntu

Atau, jika menggunakan versi lain:

proot-distro login ubuntu-22.04


---

🔗 5. Membuat Skrip ubuntu.sh

Agar bisa menjalankan Ubuntu dengan mudah:

echo 'proot-distro login ubuntu' > ubuntu.sh
chmod +x ubuntu.sh

Sekarang bisa dijalankan dengan:

./ubuntu.sh

Agar bisa dipanggil dari mana saja:

mv ubuntu.sh $PREFIX/bin/ubuntu

Sekarang cukup ketik:

ubuntu


---

🔄 6. Update Sistem Ubuntu

apt update && apt upgrade -y


---

⚙️ 7. Install Wrangler (Cloudflare Workers CLI)

🔹 a) Install Dependensi

apt install curl npm -y

Cek versi:

node -v
npm -v

🔹 b) Bersihkan Cache npm (Jika Perlu)

npm cache clean --force

🔹 c) Install Wrangler

npm install -g wrangler --unsafe-perm=true

Cek apakah sudah terpasang:

wrangler --version

Jika ada error, coba instal langsung via skrip resmi Cloudflare:

curl -fsSL https://workers.cloudflare.com/get-npm-wrangler.sh | bash


---

🔑 8. Login ke Cloudflare (Opsional)

wrangler login

Jika Termux tidak mendukung browser, gunakan API Token:

wrangler config

Masukkan API Token dari Cloudflare Dashboard.


---

📝 9. Coba Buat Proyek Wrangler

wrangler init my-worker
cd my-worker
wrangler dev


---

🚪 10. Keluar dari Ubuntu

exit


---

❌ 11. Menghapus Ubuntu (Jika Dibutuhkan)

proot-distro remove ubuntu


---

✅ Selesai! 🎉

Sekarang Ubuntu dan Wrangler telah berhasil diinstal di Termux! 🚀
Jika ada kendala, cek log dengan:

cat /root/.npm/_logs/*.log

💡 Selamat coding! 🛠️🔥

---
