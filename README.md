# GenAI: Catch 'Em All!

Generating Pokémon sprites with Variational Autoencoders (VAE) and Generative Adversarial Networks (GAN) in PyTorch.

M2 Vision et Machine Intelligente — Generative AI lab, Université Paris Cité.

## Experimental setup

40,597 RGB sprites resized to 64 × 64 pixels, split by Pokémon folder into 32,469 training and 8,128 validation images. Six configurations were trained for 20 epochs with batch size 128, Adam and seed 42.

## VAE experiments

| Model | Latent dimension | Learning rate | FID ↓ | KID ↓ | MSE ↓ | PSNR ↑ | SSIM ↑ |
|---|---:|---:|---:|---:|---:|---:|---:|
| VAE1 | 128 | 0.001 | 292.48 | 0.2662 | 0.03389 | 14.96 | 0.4199 |
| VAE2 | 64 | 0.001 | 293.76 | 0.2688 | 0.03495 | 14.83 | 0.4129 |
| VAE3 | 128 | 0.0005 | **290.44** | **0.2579** | **0.03050** | **15.42** | **0.4512** |

VAE3 performed best on the final reconstruction and generation metrics. Training and validation losses suggest possible overfitting.

## GAN experiments

All three GANs use latent dimension 100.

| Model | Generator LR | Discriminator LR | FID ↓ | KID ↓ | Final G loss | Final D loss | D accuracy |
|---|---:|---:|---:|---:|---:|---:|---:|
| GAN1 | 0.0002 | 0.0002 | 201.83 | 0.1350 | 3.701 | 0.631 | 87.78% |
| GAN2 | 0.0002 | 0.0001 | **201.07** | **0.1332** | 3.234 | 0.314 | 97.44% |
| GAN3 | 0.0002 | 0.00005 | 227.19 | 0.1881 | 1.573 | 0.719 | 90.06% |

GAN2 achieved the lowest FID and KID, although its advantage over GAN1 was small. GAN3 had a lower generator loss but worse distribution metrics.

## Discussion

GAN2 obtained better generation metrics than VAE3, while VAE3 trained faster (270.56 s versus 985.31 s, excluding evaluation and plotting). Each configuration was run once, so small differences are not evidence of statistical significance. FID and KID use 512 real and 512 generated images and Inception features pretrained on natural images, which limits their interpretation for sprites.

## Notebook

[Initial executed VAE/GAN notebook](./genai-catch-em-all%20%281%29.ipynb). The six-configuration results above are from a subsequent experimental run; the repository notebook is still the initial version until the latest executed notebook is uploaded.

To run on Kaggle, enable GPU acceleration and Internet access, then execute the cells in order.

## Credits

- Generative AI course lab, Université Paris Cité.
- Exercises adapted from [Dive into Deep Learning](https://d2l.ai/).
- Sprite source: [Pokémon Database](https://pokemondb.net/sprites).
- Pokémon images © Nintendo/Game Freak, as credited in the original lab. Educational, unofficial project.
