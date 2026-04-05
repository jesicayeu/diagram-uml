---
config:
  layout: elk
  theme: neutral
---
classDiagram
  direction TB

  class Kasir {
    tabel kasir
    id PK
    nama
    email UK
    password hash
    status_akun aktif nonaktif
    foto_profil opsional
    timestamps
  }
  class Transaksi {
    tabel transaksi
    id PK
    kasir_id FK pencatat
    jenis pemasukan pengeluaran
    status_ui
    nominal Rp
    keterangan
    path_bukti opsional
    waktu_catat
    diperbarui
  }
  class Hutang {
    tabel hutang
    id PK
    kasir_id FK pencatat
    nama_hutang
    status_hutang
    nama_barang
    nominal
    path_bukti opsional
    waktu_catat
    diperbarui
  }
  class Chat {
    tabel chat
    id PK
    kasir_id FK konteks thread
    pengirim kasir atau pemilik
    isi pesan
    lampiran opsional
    transaksi_id FK opsional
    hutang_id FK opsional
    waktu_kirim
  }

  Kasir "1" --> "*" Transaksi : kasir_id
  Kasir "1" --> "*" Hutang : kasir_id
  Kasir "1" --> "*" Chat : kasir_id
  Chat "*" --> "0..1" Transaksi : transaksi_id opsional
  Chat "*" --> "0..1" Hutang : hutang_id opsional
