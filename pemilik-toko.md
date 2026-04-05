---
config:
  layout: elk
  theme: neutral
---
classDiagram
  direction TB

  class PemilikToko {
    tabel Pemilik Toko
    id PK
    nama
    email UK
    password hash
    status_akun aktif nonaktif
    foto_profil opsional
    timestamps
  }
  class KelolaAkun {
    tabel kelola akun
    id PK
    pemilik_toko_id FK yang mengelola
    nama akun kasir
    email UK
    password hash
    status_akun aktif nonaktif
    foto_profil opsional
    timestamps
  }
  class Transaksi {
    tabel transaksi
    id PK
    kasir_id FK pencatat opsional
    pemilik_pencatat_id FK opsional
    verified_by FK Pemilik Toko opsional
    status_verifikasi_admin opsional
    catatan_verifikasi
    status_ui kasir
    jenis pemasukan pengeluaran
    nominal
    keterangan
    path_bukti opsional max 5MB
    waktu_catat
  }
  class Hutang {
    tabel hutang
    id PK
    kasir_id FK pencatat opsional
    pemilik_pencatat_id FK opsional
    verified_by FK Pemilik Toko opsional
    status_verifikasi_admin opsional
    catatan_verifikasi
    status_hutang
    nama_hutang
    nama_barang
    nominal
    path_bukti opsional
    waktu_catat
  }
  class Chat {
    tabel chat
    id PK
    pemilik_toko_id FK
    kelola_akun_id FK kasir lawan bicara
    pengirim pemilik atau kasir
    isi pesan
    lampiran opsional
    transaksi_id FK opsional
    hutang_id FK opsional
    waktu_kirim
  }

  PemilikToko "1" --> "*" KelolaAkun : pemilik_toko_id
  KelolaAkun "1" --> "*" Transaksi : kasir_id
  PemilikToko "1" --> "*" Transaksi : pemilik_pencatat
  PemilikToko "1" --> "*" Transaksi : verified_by
  KelolaAkun "1" --> "*" Hutang : kasir_id
  PemilikToko "1" --> "*" Hutang : pemilik_pencatat
  PemilikToko "1" --> "*" Hutang : verified_by
  PemilikToko "1" --> "*" Chat : pemilik_toko_id
  KelolaAkun "1" --> "*" Chat : kelola_akun_id
  Chat "*" --> "0..1" Transaksi : transaksi_id opsional
  Chat "*" --> "0..1" Hutang : hutang_id opsional
