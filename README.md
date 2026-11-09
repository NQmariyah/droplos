# DOKTER-OPLOS

Prototipe sistem pakar berbasis aturan (forward chaining) untuk audit kompatibilitas campuran tangki agrokimia, urutan aduk W-A-L-E-S, takaran presisi per tangki, dan estimasi kerugian yang dicegah.

Semua kode ada di satu file, `index.html` (HTML + CSS + JavaScript murni). Tidak butuh server, tidak butuh internet setelah halaman terbuka, dan tidak pernah "sleep".

## Deploy ke GitHub Pages (gratis)
1. Buat repositori publik baru, misalnya `dokter-oplos`.
2. Unggah `index.html` (dan README ini) ke branch `main`.
3. Buka **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pilih `main` / `(root)`, lalu Save.
4. Tunggu 1–2 menit. Link aplikasi: `https://<username>.github.io/dokter-oplos/`

## Deploy ke Cloudflare Pages (gratis)
1. Masuk ke dash.cloudflare.com → **Workers & Pages → Create → Pages**.
2. Pilih **Upload assets** (atau hubungkan repositori GitHub), lalu unggah folder yang berisi `index.html`.
3. Link aplikasi: `https://dokter-oplos.pages.dev`

## Versi Streamlit (folder `streamlit/`), sesuai Subbab 4.1 naskah
Isi folder:
- `engine.py`: basis pengetahuan (10 produk), basis aturan R1–R4, dan mesin inferensi forward chaining
- `app.py`: antarmuka Streamlit
- `requirements.txt`: daftar paket yang dibutuhkan

Menjalankan di laptop:
```
cd streamlit
pip install -r requirements.txt
streamlit run app.py
```

Deploy gratis ke Streamlit Community Cloud:
1. Unggah folder `streamlit/` ke repositori GitHub publik.
2. Buka share.streamlit.io → **Create app** → pilih repositori, branch `main`, dan *Main file path* `streamlit/app.py`.
3. Atur *App URL*, misalnya `dokter-oplos.streamlit.app`, lalu klik **Deploy**.
4. Aplikasi akan "tidur" bila tidak dibuka beberapa hari. Pada hari penjurian, buka link-nya lebih dulu di pagi hari.

Logika versi Streamlit sama persis dengan `index.html`. Jika harga atau dosis diubah, ubah di kedua versi.

## Yang wajib dicek sebelum lomba
- **Harga dan dosis** ada di array `PRODUCTS` di bagian atas `<script>`. Hanya Demolish 18 EC (Rp35.000/100 ml, 1 ml/L) yang diambil dari naskah. Harga lain masih estimasi dan ditandai `hargaOk:false` (tampil dengan tanda * di aplikasi). Ganti dengan hasil survei harga dan label resmi, lalu ubah ke `hargaOk:true`.
- **Aturan** ada di array `RULES` (R1–R4, sesuai Tabel 4 naskah).

## Penyesuaian naskah (Subbab 4.1)
Ganti kalimat pertama menjadi:
> "Prototipe DOKTER-OPLOS dibangun sebagai aplikasi web satu halaman (*single-page web app*) berbasis HTML dan JavaScript yang berjalan sepenuhnya di peramban ponsel, tanpa server dan tanpa pemasangan aplikasi tambahan, serta di-*hosting* gratis melalui GitHub Pages."
