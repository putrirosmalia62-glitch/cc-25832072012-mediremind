# Requirements

## Problem Statement
Pasien rawat jalan, penderita penyakit kronis, dan lansia kerap lupa
atau salah jam minum obat, sementara keluarga tidak tahu bila dosis
terlewat. MediRemind menyediakan pengingat terjadwal, konfirmasi
dosis, dan pemberitahuan ke pengawas keluarga sehingga dosis terlewat
dapat diketahui lebih cepat.

## Target Users
- Pasien atau anggota keluarga yang minum obat rutin
- Pengawas keluarga (anak, pasangan, pengasuh)

## User Need
Sebagai pengawas keluarga, saya ingin diberi tahu bila obat anggota
keluarga tidak terkonfirmasi diminum, sehingga saya dapat segera
menindaklanjuti tanpa harus menelepon.

## Functional Requirements
- FR-01 Pengguna dapat mendaftar, login, dan mengelola profil anggota keluarga miliknya (Must)
- FR-02 Sistem menyimpan jadwal obat per anggota dan data tetap ada setelah restart/reboot (Must)
- FR-03 Sistem menyediakan GET /health untuk status proses (Must)
- FR-04 Pengguna hanya dapat mengakses jadwal milik keluarganya (Should)
- FR-05 Input tidak valid ditolak dengan pesan jelas, tanpa membocorkan detail internal (Should)
- FR-06 Sistem mengirim pengingat via Telegram dan mencatat konfirmasi "Sudah diminum" (Must)
- FR-07 Bila tidak terkonfirmasi dalam 30 menit, pengawas keluarga diberi tahu (Must)
- FR-08 Stok obat berkurang saat dosis terkonfirmasi dan ada peringatan stok menipis (Should)
- FR-09 Riwayat kepatuhan mingguan, alergi, dan riwayat sakit dapat dilihat dan dicatat (Should)
- FR-10 Ringkasan untuk dokter dapat diekspor ke halaman cetak/PDF (Could)

## Non-Functional Requirements
- NFR-01 Security: tidak ada secret di Git; SSH key-only; backend hanya listen di loopback
- NFR-02 Privacy: hanya data sintetis atau data dengan izin sah
- NFR-03 Reliability: service restart otomatis; backup dan restore terbukti
- NFR-04 Performance: latency p95 API < 500 ms pada 10 pengguna simultan (TARGET)
- NFR-05 Capacity: CPU/RAM/disk dalam batas VPS
- NFR-06 Compatibility: dapat diakses dari Windows, Linux, iOS, Android
- NFR-07 Maintainability: README, ADR, dan riwayat commit jelas
- NFR-08 Portability: dapat di-containerize pada M06
- NFR-09 Auditability: evidence tiap milestone tercatat di GitHub
- NFR-10 Cost: pemakaian dalam batas kredit AWS Free Plan

## Scope
In scope: akun, profil keluarga, jadwal obat, pengingat, konfirmasi,
eskalasi, stok, ringkasan riwayat.

Out of scope: integrasi SIMRS/SATUSEHAT, saran dosis atau diagnosis,
OCR resep, deteksi interaksi obat, pembayaran, aplikasi native,
data pasien nyata tanpa izin.

## Constraints
- AWS EC2 t3.micro, RAM ± 1 GB, disk 20 GB
- Ubuntu Server 24.04 LTS
- Waktu 16 pertemuan (M03–M16)

## Acceptance Criteria M03
- [ ] Aplikasi baseline dapat diakses lewat browser
- [ ] GET /health mengembalikan HTTP 200
- [ ] Backend hanya listen di loopback
- [ ] Tidak ada secret di repository
