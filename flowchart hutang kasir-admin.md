---
config:
  theme: neutral
---
flowchart LR
    K["Kasir Simpan Hutang"] --> D[("Basis Data")]
    D --> N["Notifikasi Pemilik"]
    N --> P["Pemilik Verifikasi"]
    P --> D
