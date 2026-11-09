# ADR-0001: Flask + SQLite pada single VPS AWS EC2

## Status
Proposed

## Konteks dan Constraint
Aplikasi pengingat obat keluarga skala kecil. Lingkungan: VPS AWS EC2
t3.micro dengan 2 vCPU, RAM ± 1 GB, dan disk 20 GB. Biaya infrastruktur
sekitar Rp252.000/bulan (ESTIMASI, dipotong dari kredit Free Plan).
Aplikasi menyangkut data kesehatan sehingga hanya data sintetis yang
dipakai. Jumlah pengguna uji sekitar 10 orang.

## Keputusan
Menggunakan Flask + Gunicorn (1 worker) + Caddy + SQLite + systemd timer
pada satu VPS Ubuntu 24.04.

## Alternatif dan Alasan Penolakan
1. Database atau platform terkelola: biaya lebih tinggi dan berlebihan
   untuk beberapa tabel saja.
2. Celery + Redis untuk penjadwal: memakan RAM pada VPS 1 GB.
3. SaaS pengingat obat: kontrol data terbatas dan tidak melatih
   kompetensi cloud.

## Dampak Positif
Sederhana, murah, kontrol penuh, dan sesuai kurikulum.

## Konsekuensi Negatif dan Lock-in
- Single point of failure
- Operasional dan keamanan ditanggung sendiri
- Lock-in rendah

## Risiko dan Mitigasi
R01, R04, R08, R09 (lihat bagian 11.1 pada laporan studi kelayakan).

## Kondisi Peninjauan Ulang
- Jumlah pengguna bertambah
- Muncul kebutuhan peran tenaga kesehatan
- Biaya berubah

## Tautan Issue dan Commit
Akan ditambahkan setelah issue terkait dibuat di repository.
