# Deployment Notes (M03)

Status per 09-11-2026. Bagian bertanda [ ] belum selesai.

## Infrastruktur
| Item | Nilai |
|---|---|
| Provider | Amazon Web Services, EC2 |
| Instans | t3.micro (VPS-Ubuntu-PTI) |
| Region | Asia Pacific (Sydney), ap-southeast-2b |
| OS | Ubuntu Server 24.04.5 LTS |
| Kapasitas | 2 vCPU (nproc), RAM 909 MiB, swap 1 GB, disk 20 GB gp3 |
| IP publik | 15.134.62.116 (Elastic IP) |
| Domain | Belum ada (rencana M04) |

## Keamanan Dasar (selesai)
- [x] Akun administrasi non-root dibuat
- [x] SSH key-only (Ed25519), login password dinonaktifkan
- [x] Login root SSH dinonaktifkan
- [x] UFW aktif (OpenSSH dan 80/tcp)
- [x] AWS Security Group: hanya TCP 22 dan 80
- [x] Disk diperbesar dari 8 GiB ke 20 GiB (07-11-2026)

## Perintah Verifikasi
```bash
sudo sshd -T | grep -E "permitrootlogin|passwordauthentication"
sudo ufw status
nproc
free -h
df -h
```

## Aplikasi (belum selesai)
- [ ] Flask + Gunicorn berjalan sebagai service systemd
- [ ] Gunicorn hanya listen di 127.0.0.1:8000
- [ ] Caddy reverse proxy di port 80
- [ ] GET /health mengembalikan HTTP 200

## Uji Penerimaan AT-03
Status: BLOCKED (menunggu aplikasi berjalan).

```bash
curl -i http://15.134.62.116/health
```
Hasil dan log disimpan di docs/evidence/m03/ setelah uji dijalankan.

## Rollback
Checkout tag sebelumnya dan restore backup database (backup dan restore
direncanakan pada M05).

## Catatan
Tidak ada password, private key, atau token di dokumen ini.
