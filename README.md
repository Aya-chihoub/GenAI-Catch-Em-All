# GenAI: Catch 'Em All! ⚡

Generating new Pokémon sprites with Variational Autoencoders (VAE) and Generative Adversarial Networks (GAN) using PyTorch.

This project was developed as part of the M2 Vision et Machine Intelligente (VMI) Generative AI lab at Université Paris Cité.

## Notebook

[Explore the executed notebook](./genai-catch-em-all%20%281%29.ipynb) for the implementation, training curves, generated sprites, latent interpolations and evaluation results.

## Approach

- **VAE:** learns a probabilistic latent representation through reconstruction and KL divergence.
- **GAN:** trains a generator and discriminator through adversarial learning.
- Both models are trained for 20 epochs, with held-out data used for evaluation.

## Results

| Metric | VAE | GAN |
|---|---:|---:|
| FID ↓ | 308.57 | **232.91** |
| KID ↓ | 0.259301 | **0.131353** |
| Training time (s) ↓ | **274.71** | 994.40 |
| Training throughput (images/s) ↑ | **2363.84** | 653.04 |

VAE reconstruction metrics: MSE = 0.033014, PSNR = 15.08 dB, SSIM = 0.430009.

The GAN achieved lower FID and KID scores, while the VAE trained faster. The VAE showed signs of overfitting, and the GAN discriminator reached 99.77% training accuracy, suggesting an imbalance in adversarial training.

FID and KID should be interpreted cautiously: the evaluation uses a limited sample size and Inception features pretrained on natural images rather than Pokémon sprites. Training times exclude evaluation and plotting.

## Running the project

Open the notebook in Kaggle, enable a GPU accelerator and Internet access, and run the cells in order. The notebook includes dataset preparation, model training, evaluation and checkpoint saving.

## Credits

- Course lab: Generative AI, Université Paris Cité.
- Exercises adapted from [Dive into Deep Learning](https://d2l.ai/).
- Sprite source: [Pokémon Database](https://pokemondb.net/sprites).
- Pokémon images © Nintendo/Game Freak, as credited in the original lab. This is an educational, unofficial project.
