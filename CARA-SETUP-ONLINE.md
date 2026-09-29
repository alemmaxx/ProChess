# ProChess — Setup Mod Online (Firebase)

Mod **Lawan Bot** dan **2 Pemain** jalan terus tanpa internet. Mod **Lawan Online** perlukan Firebase (percuma).

## 1. Cipta projek Firebase
1. Buka https://console.firebase.google.com → **Add project** (cth: `prochess`).
2. Menu kiri: **Build → Realtime Database → Create Database** → pilih lokasi **Singapore (asia-southeast1)** → *Start in locked mode*.
3. Tab **Rules**, tampal ini dan tekan **Publish**:

```json
{
  "rules": {
    "prochess_rooms": {
      ".read": true,
      ".indexOn": ["status"],
      "$code": { ".write": true }
    }
  }
}
```

> **Guna projek Firebase sedia ada?** Boleh. Data ProChess disimpan di bawah `prochess_rooms`, jadi tak bercampur dengan app lain. Tapi **jangan ganti** rules yang sedia ada — cuma tambah blok `"prochess_rooms": {...}` di dalam `"rules"` bersama rules lama.

## 2. Ambil config
1. **Project settings** (ikon gear) → **Your apps** → ikon **Web `</>`** → daftar app.
2. Salin objek `firebaseConfig` (pastikan ada `databaseURL`).

## 3. Masukkan config — pilih SATU cara
- **Cara A (disyorkan untuk APK):** buka `index.html`, cari `const FIREBASE_CONFIG` di atas bahagian `<script>`, isi semua nilai.
- **Cara B:** buka app → Lawan Online → tampal config dalam kotak → Simpan (disimpan dalam phone tu sahaja).

## 4. Cara main online
- **Cari Lawan Rawak** — padankan dengan pemain lain yang sedang mencari.
- **Cipta Bilik** — dapat kod 4 digit, kawan masuk guna **Masuk**.
- Warna (putih/hitam) dipilih rawak, dan bertukar setiap kali "Main Lagi".
- Keluar semasa main = menyerah kalah.

## Build APK
Sama macam app ProKuiz lain: letak `index.html` dalam repo GitHub dan guna workflow build APK yang sama.
