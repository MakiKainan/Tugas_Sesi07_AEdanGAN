| Model       | Dim laten                      |   Params (G+D) |   Epoch |   Train time / epoch (s) |   Latency (ms / batch 64) | Test MSE   | Test PSNR (dB)   | Test SSIM   | FID-2000           | Mode coverage (H norm)   |
|:------------|:-------------------------------|---------------:|--------:|-------------------------:|--------------------------:|:-----------|:-----------------|:------------|:-------------------|:-------------------------|
| Vanilla AE  | 64                             |         435536 |      20 |                     2.41 |                      0.46 | 0.00687    | 22.72            | 0.8189      | N/A (latent voids) | N/A                      |
| Sparse AE   | 64 (bottleneck) / 256 (sparse) |         435536 |      20 |                     2.78 |                      0.43 | 0.01103    | 20.52            | 0.7361      | N/A (latent voids) | N/A                      |
| VAE         | 64                             |         451984 |      20 |                     2.92 |                      0.21 | 0.01343    | 19.53            | 0.7011      | 97.78              | 0.9904                   |
| Vanilla GAN | 100 (prior noise)              |        2019857 |      40 |                     8.15 |                      1.34 | N/A        | N/A              | N/A         | 127.33             | 0.9918                   |
| DCGAN       | 100 (prior noise)              |         910658 |      15 |                    68.02 |                      9.45 | N/A        | N/A              | N/A         | 36.43              | 0.9854                   |
| DDPM        | 28x28 (dimensi image)          |         445377 |      10 |                   207.21 |                  39574.8  | N/A        | N/A              | N/A         | 50.65              | 0.9845                   |

| Model       |   loss awal |   loss akhir |   min loss |   max loss |   std per-epoch (1/4 akhir) |   std per-iterasi (epoch akhir) |   val loss terbaik @epoch |   loss_D akhir |   D(x) akhir |   D(G(z)) akhir |
|:------------|------------:|-------------:|-----------:|-----------:|----------------------------:|--------------------------------:|--------------------------:|---------------:|-------------:|----------------:|
| Vanilla AE  |      0.0321 |       0.0068 |     0.0068 |     0.0321 |                      0.0002 |                          0.0005 |                        20 |       nan      |     nan      |        nan      |
| Sparse AE   |      0.0415 |       0.0118 |     0.0118 |     0.0415 |                      0.0002 |                          0.0007 |                        20 |       nan      |     nan      |        nan      |
| VAE         |    299.696  |     241.802  |   241.802  |   299.696  |                      0.2737 |                          6.4509 |                        20 |       nan      |     nan      |        nan      |
| Vanilla GAN |      1.116  |       0.8546 |     0.8521 |     2.0935 |                      0.0103 |                          0.0607 |                       nan |         1.3317 |       0.5264 |          0.4737 |
| DCGAN       |      2.3227 |       1.4617 |     1.452  |     2.3227 |                      0.0077 |                          0.3697 |                       nan |         0.88   |       0.6807 |          0.3194 |
| DDPM        |      0.122  |       0.0452 |     0.0452 |     0.122  |                      0.0003 |                          0.0082 |                        10 |       nan      |     nan      |        nan      |

| Eksperimen                              |   Test acc |   test_mse |   test_psnr |   test_ssim |   FID-2000 |   Mode coverage (H norm) |
|:----------------------------------------|-----------:|-----------:|------------:|------------:|-----------:|-------------------------:|
| MLP Classifier (Tahap 1)                |     0.8867 |   nan      |    nan      |    nan      |     nan    |                 nan      |
| W^T dari z_MLP (Tahap 3)                |   nan      |     0.2698 |      5.7409 |      0.0917 |     nan    |                 nan      |
| Frozen decoder dari z_MLP (Tahap 4)     |   nan      |     0.018  |     18.2524 |      0.6464 |     nan    |                 nan      |
| Vanilla AE z_AE (pembanding Tahap 4)    |   nan      |     0.0069 |     22.7223 |      0.8189 |     nan    |                 nan      |
| Prior sampling z_MLP (Tahap 5)          |   nan      |   nan      |    nan      |    nan      |     156.29 |                   0.8631 |
| VAE prior sampling (pembanding Tahap 5) |   nan      |   nan      |    nan      |    nan      |      97.78 |                   0.9904 |
