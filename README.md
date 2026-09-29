# ProChess by ProKuiz ♞

App catur: **Lawan Bot** (Mudah / Sederhana / Sukar), **Lawan Online** (Firebase) dan **2 Pemain** atas satu phone.
BM | EN · keyboard dalam app · butang back Android · auto update.

## Sebelum upload
1. **Nama repo** — `index.html` → `const UPDATE_REPO = 'alemmaxx/ProChess'`. Tukar kalau nama repo lain.
2. **Firebase** — isi `FIREBASE_CONFIG` dalam `index.html` (lihat `CARA-SETUP-ONLINE.md`).

## Setup repo (sekali sahaja)
1. Upload semua fail (termasuk folder `.github`) ke repo baru, branch `main`. Repo mesti **Public** supaya auto update boleh baca release.
2. **Settings → Secrets and variables → Actions → New repository secret**
   - Name: `KEYSTORE_BASE64`
   - Value: isi fail `KEYSTORE_BASE64.txt` (sama macam ProSudoku)
   → supaya update APK tak perlu uninstall.
3. Tab **Actions** → **Build ProChess APK** jalan sendiri.

## Dapatkan APK
Tab **Releases** → versi terbaru (cth `v1.0.1`) → muat turun `ProChess.apk`.
Setiap kali push ke `main`, versi baru dibina dan app pengguna akan tunjuk pop up **Kemas Kini**.

## Struktur
| Fail | Fungsi |
|---|---|
| `index.html` | Seluruh app |
| `assets/` | Ikon & splash screen |
| `capacitor.config.json` | ID app `com.prokuiz.chess` |
| `.github/workflows/build-apk.yml` | Build APK + terbit release |
