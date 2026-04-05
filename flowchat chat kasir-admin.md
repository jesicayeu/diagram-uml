---
config:
  theme: neutral
---
flowchart LR
    K["Kasir Kirim Pesan"] --> M[("Pesan Tersimpan")]
    M --> P["Pemilik Baca Balas"]
    P --> M
