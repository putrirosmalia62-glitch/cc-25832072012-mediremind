# MediRemind

Layanan cloud pengingat obat dan catatan kesehatan keluarga.

Cloud Computing — PTI 2802
Pertemuan 3 — Project Inception

## Author
- Nama: Meyliza Rosmalia Putri
- NIM: 25832072012
- Kelas: PTI 2B

## Problem
Pasien rawat jalan, penderita penyakit kronis, dan lansia sering lupa
atau salah jam minum obat, sementara keluarga tidak tahu bila dosis
terlewat. Alarm ponsel hanya berbunyi: tidak mencatat apakah obat
diminum dan tidak memberi tahu siapa pun.

## Target Users
- Pasien atau anggota keluarga yang minum obat rutin
- Pengawas keluarga (anak, pasangan, pengasuh)

## Features M03
- Halaman utama aplikasi (baseline)
- Health endpoint: GET /health
- Deployment awal di VPS

## Planned Features
Profil keluarga, jadwal obat, pengingat via Telegram, konfirmasi
"sudah diminum", eskalasi ke pengawas bila tidak terkonfirmasi
dalam 30 menit, pengingat stok obat, dan ringkasan riwayat untuk dokter.

## Architecture
Caddy -> Gunicorn -> Flask -> SQLite

## Infrastructure
- AWS EC2 t3.micro (Sydney, ap-southeast-2)
- Ubuntu Server 24.04 LTS
- Flask, Gunicorn, systemd, Caddy

## Security
- SSH key-only, login root dinonaktifkan
- UFW aktif
- Tidak ada secret atau token di repository
- Hanya data sintetis, tanpa data pasien nyata

## Current Limitations
- Masih HTTP (HTTPS pada Pertemuan 4)
- Belum ada database
- Deployment manual

## Roadmap
M04 Domain/HTTPS, M05 Data dan backup, M06 Container,
M07 IaC, M09 CI/CD, M16 Release v1.0.0
