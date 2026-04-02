# Diffusion

# LinguaScribe: Multi-Lingual Handwriting Synthesis via Latent Diffusion

<p align="center">
  <img src="assets/architecture_diagram.jpg" width="800" alt="Diffusion Model Architecture">
  <br>
  <em>Figure 1: The Core Architecture — Utilizing VAEs and Diffusion for Stylized Generation.</em>
</p>

## 🖋️ The Vision
Handwriting is more than just text; it is a personal signature of identity. **LinguaScribe** is a deep learning framework designed to capture the unique "DNA" of a person's handwriting across different languages and scripts.

### Key Capabilities:
* **Few-Shot Style Transfer:** Give the model 5 snippets of your writing, and it learns your stroke dynamics.
* **Cross-Lingual Adaptation:** Moving beyond Latin scripts to complex Devanagari characters.
* **High-Fidelity Synthesis:** Using Latent Diffusion to ensure crisp, realistic ink-on-paper textures.

<p align="center">
  <img src="assets/f1_english.png" width="45%" />
  <img src="assets/hindi_sample_1.png" width="45%" /> 
</p>
<p align="center">
  <img src="assets/hindi_sample_2.jpg" width="60%" />
  <br>
  <em>Figure 2: Diversity in Training Data — From English F1 commentary to Devanagari script.</em>
</p>

## 🔬 How it Works
The system operates in two distinct phases as shown in the architecture diagram:

1.  **The Training Phase:** We utilize a **VAE (Variational Autoencoder)** to compress images into a latent space ($z_0$). A **UNet** is then trained to predict noise ($\epsilon_\theta$) based on both a text prompt ($c_T$) and a style-representative sample ($c_s$).
2.  **The Sampling Phase:** Starting from random noise, the model uses **DDIM Steps** to iteratively refine the latent representation, guided by the desired style, before the VAE Decoder reconstructs the final "handwritten" image.
