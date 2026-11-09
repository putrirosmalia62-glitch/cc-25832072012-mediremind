# MediRemind

Layanan cloud pengingat obat dan catatan kesehatan keluarga.

Cloud Computing — PTI 2802
Pertemuan 3 — Project Inception

## Author
- Nama: Meyliza Rosmalia Putri
- NIM: 25832072012
- Kelas: PTI 2B

## Problem
Semua orang pernah perlu minum obat sesuai jadwal, dan banyak yang pernah lupa, salah jam, atau berhenti sebelum obat habis (ASUMSI; akan diukur lewat survei dan wawancara). Masalahnya terasa paling berat pada lansia, penderita penyakit kronis, dan orang tua yang mengurus obat anak, karena keluarga tidak tahu bila dosis terlewat. Alarm ponsel hanya berbunyi: tidak mencatat apakah obat diminum dan tidak memberi tahu siapa pun.

## Target Users
- Semua keluarga yang anggotanya minum obat sesuai jadwal.
- Paling terbantu: lansia, penderita penyakit kronis, dan orang tua yang mengurus obat anak.
- Pengawas keluarga yang ingin tahu bila dosis terlewat.

## Features M03
- Halaman utama aplikasi (baseline)
- Health endpoint: GET /health
- Deployment awal di VPS

## Planned Product Features (M04–M16)
- Login dan profil keluarga
- Jadwal obat per anggota keluarga
- Pengingat terjadwal (prototipe: Telegram; alternatif: email)
- Konfirmasi "sudah diminum" dan riwayat kepatuhan
- Eskalasi ke pengawas keluarga bila tidak terkonfirmasi dalam 30 menit
- Pengingat stok obat dan ringkasan riwayat untuk dokter

## Architecture
Caddy -> Gunicorn -> Flask -> SQLite

## Infrastructure
- Provider: AWS EC2 (Asia Pacific Sydney), instans t3.micro
- Ubuntu Server 24.04.5 LTS
- 2 vCPU (hasil nproc; batas praktikum template: 1 vCPU)
- RAM 909 MiB, swap 1 GB
- Disk 20 GB (EBS gp3)
- Caddy
- Gunicorn

## Public Endpoint
http://15.134.62.116/

## Health Check
GET /health

## Deployment
See docs/deployment.md.

## Security
- key-only SSH
- root SSH disabled
- UFW enabled
- AWS Security Group: hanya TCP 22 dan 80
- backend loopback-only

## Current Limitations
- HTTP only
- no persistent database
- no container
- single VPS (single point of failure)
- AWS Free Plan berakhir 06-04-2027

## Roadmap
M04 Domain/HTTPS, M05 Data dan backup, M06 Container,
M07 IaC, M09 CI/CD, M16 Release v1.0.0

