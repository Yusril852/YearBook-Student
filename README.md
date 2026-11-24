# Platform profil yearbook 7F

Isi paket:

- `index.html`: halaman murid. Murid masuk dengan kode, lalu mengisi profil dan mengunggah foto.
- `guru.html`: dashboard guru. Membuat kode, memantau pengisian, mengunduh data untuk yearbook.
- `firebase-config.js`: konfigurasi Firebase (harus diisi).
- `firestore.rules`: aturan keamanan database (harus dipasang).

## Penyiapan (sekitar 15 menit)

1. Buka https://console.firebase.google.com lalu buat proyek baru, misalnya `yearbook-7f`.
2. Build > Firestore Database > Create database. Pilih mode produksi dan wilayah terdekat.
3. Build > Authentication > Get started. Aktifkan dua metode masuk:
   - Anonymous (untuk murid).
   - Email/Password (untuk guru).
4. Authentication > Users > Add user. Buat akun guru dengan email dan kata sandi Bapak.
5. Firestore Database > Rules. Tempel isi `firestore.rules`, ganti `GANTI_EMAIL_GURU@contoh.com` dengan email akun guru, lalu Publish.
6. Project settings > Your apps > tambah Web app. Salin objek konfigurasinya ke `firebase-config.js`.
7. Unggah seluruh folder ini ke hosting yang biasa Bapak pakai untuk MathLab (Firebase Hosting, Netlify, GitHub Pages, atau lainnya).
8. Jika alamat hosting Bapak bukan `*.web.app` atau `*.firebaseapp.com`, tambahkan domainnya di Authentication > Settings > Authorized domains.

## Cara pakai

1. Buka `guru.html`, masuk dengan akun guru.
2. Tempel daftar nama murid (opsional), lalu klik **Buat 32 kode**.
3. Bagikan kode atau tautan tiap murid. Gunakan **Unduh daftar kode (CSV)** atau **Cetak daftar kode**. Kode bersifat rahasia per murid.
4. Pantau progres di dashboard.
5. Setelah murid mengisi, klik **Unduh data untuk yearbook** (file `yearbook-7F-data.json`).
6. Buka yearbook 7F dengan akun Bapak, klik **Impor data siswa**, pilih file tadi. Data dan foto langsung masuk ke yearbook. Ulangi langkah 5 dan 6 kapan saja untuk memperbarui.

## Keamanan dan privasi

- Data murid di bawah umur (alamat, kontak, foto). Minta persetujuan orang tua. Form sudah memuat kotak persetujuan.
- Murid hanya bisa membuka dan mengubah dokumennya sendiri lewat kode rahasianya. Hanya akun guru yang bisa melihat semua data.
- Tautan `guru.html` tidak perlu dibagikan ke murid. Akses data tetap dikunci oleh login guru.
- Setelah yearbook final, hapus data di Firestore jika tidak dibutuhkan lagi.
