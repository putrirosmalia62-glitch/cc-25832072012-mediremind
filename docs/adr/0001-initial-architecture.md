# ADR-0001: Initial VPS Deployment Architecture

## Status
Accepted

## Context
VPS AWS EC2 t3.micro: 2 vCPU (batas praktikum template: 1 vCPU), RAM 909 MiB (sekitar 1 GB), disk 20 GB, Ubuntu Server 24.04.5 LTS. Akun AWS Free Plan (maksimal 6 bulan, berakhir 06-04-2027). Aplikasi: MediRemind, pengingat obat keluarga skala kecil (sekitar 10 pengguna uji).

## Decision
- Flask
- Gunicorn 1 worker
- systemd
- Caddy
- UFW
- GitHub

## Alternatives
1. Node.js + PM2
2. NGINX + Gunicorn
3. Docker
4. PHP-FPM
5. Database atau platform terkelola (ditolak)
6. Celery + Redis untuk penjadwal (ditolak)

## Rationale
- Flask + Gunicorn: ringan dan cukup untuk beban kecil; satu worker menghemat RAM.
- systemd: restart otomatis dan pengelolaan service bawaan Ubuntu.
- Caddy: konfigurasi singkat dan HTTPS otomatis (Pertemuan 4).
- UFW: firewall sederhana yang konsisten dengan AWS Security Group.
- Node.js + PM2: menambah runtime baru tanpa manfaat untuk kebutuhan ini.
- NGINX + Gunicorn: sah, tetapi konfigurasi HTTPS lebih panjang dibanding Caddy.
- Docker: ditunda ke M06 karena overhead memori pada RAM sekitar 1 GB.
- PHP-FPM: tidak sesuai dengan stack Python yang dipilih.
- Database/platform terkelola: biaya tambahan dan berlebihan untuk beberapa tabel kecil.
- Celery + Redis: memakan RAM; penjadwal cukup dengan systemd timer.

## Consequences
### Positive
- Sederhana, murah, kontrol penuh, sesuai kurikulum.
- Kebutuhan memori rendah.
### Negative
- Single point of failure; operasional dan keamanan ditanggung sendiri.
- Belum ada HTTPS dan database persisten pada M03.

## Review Trigger
Review pada M06/M07.
