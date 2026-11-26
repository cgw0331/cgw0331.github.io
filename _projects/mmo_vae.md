---
layout: page
title: MMO-VAE
description: Mask-guided multi-objective molecular optimization with a SELFIES-based variational autoencoder
importance: 1
category: research
---

MMO-VAE is a SELFIES-based VAE framework for de novo drug design. It learns property-specific masks over the latent coordinates and reuses the learned mask logits as coordinate-wise gradient multipliers, so that optimization in latent space pushes harder on the coordinates that matter for each property while still updating the rest.

- Code: [github.com/cgw0331/MMO-VAE](https://github.com/cgw0331/MMO-VAE)
