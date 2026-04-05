---
config:
  theme: neutral
---
flowchart LR
    K["Kasir Simpan Transaksi"] --> D[("Basis Data")]
    D --> N["Notifikasi Pemilik Toko"]
    N --> P["Pemilik Verifikasi"]
    P --> D
