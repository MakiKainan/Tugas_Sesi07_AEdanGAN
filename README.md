# Tugas Sesi 07 — Studi Komparatif Generative Models (Fashion-MNIST)

Kevin Sukias K — 2802526416

Vanilla AE, Sparse AE, VAE, Vanilla GAN (MLP), DCGAN, dan DDPM pada Fashion-MNIST (split stratified 80/10/10, seed 42),
ditambah eksperimen batasan MLP Classifier untuk image generation (Tahap 1–5).

## Menjalankan
```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace KevinSukias_Generative_Models.ipynb
# smoke test cepat (1 epoch, FID-200, DDPM T=50):
QUICK=1 jupyter nbconvert --to notebook --execute KevinSukias_Generative_Models.ipynb
```
Seluruh run penuh ±2 jam di CPU 2 core. Checkpoint tersimpan di `checkpoints/`; kalau sudah ada, training dilewati.

## Luaran (`outputs/`)
- `metrics_table.csv` / `.md` — tabel komparasi (Bagian IV)
- `training_stability.csv`, `mlp_proof_metrics.csv`, `interpolation_midpoint.csv`
- `all_metrics.json` — semua angka mentah; `all_epoch_logs.csv` — log per epoch
- `figures/` — Figur 1–5 + figur tambahan
