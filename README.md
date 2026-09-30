# ProChess by ProKuiz ♞

Catur premium — **Lawan Bot** (Mudah / Sederhana / Sukar), **Lawan Online 1v1** dengan rating & ranking, **2 Pemain** atas satu phone.
Konsep sama macam ProSudoku: APK buka versi live di GitHub Pages → **kemas kini automatik tanpa download APK baru**.

## Ciri
- BM | EN, keyboard dalam app, butang back Android + pop up keluar
- Profil pemain (nama, rating ⭐, rekod M-K-S) · Ranking (Rating / Menang / Main) + padam ranking guna password admin
- Online: senarai pemain online + **Ajak lawan**, Cari Lawan Rawak (bot ganti lepas 25 saat), Bilik kod 5 huruf, Main Lagi (warna bertukar)
- Lawan bot disimpan automatik → **Sambung Permainan**
- PWA (iPhone: Add to Home Screen), halaman offline, service worker

## Setup (sekali sahaja)
1. **Repo GitHub `alemmaxx/ProChess`** (Public) → upload semua fail ini ke branch `main` (termasuk `.github`, `.nojekyll`).
2. **GitHub Pages**: Settings → Pages → *Deploy from a branch* → `main` / `(root)` → Save.
   App akan hidup di `https://alemmaxx.github.io/ProChess/`
3. **Secret** `KEYSTORE_BASE64` (Settings → Secrets and variables → Actions) — isi sama macam ProSudoku.
4. **Firebase** (projek `prokuiz-aplikasi-b518a`, sama dengan ProSudoku):
   - Authentication → Anonymous → **Enable** (sepatutnya dah on untuk ProSudoku)
   - **Firestore Database → Rules** → ganti dengan isi fail `firestore.rules` → **Publish**
     (fail ini = rules ProSudoku sedia ada + blok ProChess; ProSudoku tak terjejas)
5. Tab **Actions** → build siap → **Releases** → muat turun `ProChess.apk` → pasang.

## Kemas kini app selepas ini
1. Edit `index.html` → **naikkan `APP_VERSION`** (cth `'1.0.0'` → `'1.0.1'`).
2. Push ke `main`. Dalam beberapa minit, app pengguna tunjuk bar **Kemas Kini** berkelip → tekan → siap.
   APK baru hanya perlu kalau tukar `capacitor.config.json` / ikon / plugin.

## Password admin padam ranking
Sama dengan ProSudoku (`adminPassword()` dalam `firestore.rules`). ProChess guna dokumen `config/chess`, jadi padam ranking ProChess tak kacau ranking ProSudoku.

## Struktur
| Fail | Fungsi |
|---|---|
| `index.html` | Seluruh app |
| `sw.js`, `manifest.webmanifest`, `icons/` | PWA / iPhone / cache offline |
| `offline.html` | Skrin "Tiada Internet" dalam APK |
| `capacitor.config.json` | APK buka `https://alemmaxx.github.io/ProChess/` |
| `firestore.rules` | Rules gabungan ProSudoku + ProChess |
| `.github/workflows/build-apk.yml` | Build APK + release |
