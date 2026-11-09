# ADR-0001: Initial VPS Deployment Architecture

## Status
Accepted

## Context
MediRemind dijalankan pada satu VPS AWS EC2 t3.micro dengan RAM
± 1 GB dan disk 20 GB. Stack harus ringan, mudah dipahami, dan
mencerminkan arsitektur deployment nyata.

## Decision
Menggunakan Flask sebagai aplikasi web, Gunicorn (1 worker) sebagai
application server yang hanya listen di 127.0.0.1:8000, systemd untuk
mengelola service, dan Caddy sebagai reverse proxy di port 80.

## Alternatives Considered
- Flask development server: tidak layak untuk deployment publik
- Gunicorn langsung di port publik: backend terekspos ke internet
- Container (Docker): ditunda ke Pertemuan 6 sesuai kurikulum
- Managed platform: biaya lebih tinggi dan kurang sesuai tujuan
  pembelajaran deployment VPS

## Consequences
Positif:
- Footprint kecil, sesuai RAM terbatas
- Backend tidak terekspos langsung
- Siap dikembangkan ke HTTPS otomatis (Caddy) pada Pertemuan 4

Negatif / trade-off:
- Satu server (single point of failure)
- Deployment masih manual
- Kapasitas terbatas, jumlah worker harus dijaga
