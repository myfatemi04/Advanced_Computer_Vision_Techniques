# Diffusion Models

General notation rule of thumb: modeling a distribution is usually written as P(x|x0).

Diffusion models > GANs. [https://arxiv.org/pdf/2105.05233.pdf](https://arxiv.org/pdf/2105.05233.pdf)

- Given a noisy image x_t, generate x_t-1 that is less noisy. This is done by estimating the noise epsilon, where loss is mse(epsilon bar, epsilon).
- We are essentially modeling P_theta(x_t-1 | x_t).
- Noise is sampled with diagonal Gaussian.

DALL•E 2: [https://cdn.openai.com/papers/dall-e-2.pdf](https://cdn.openai.com/papers/dall-e-2.pdf)

- DALL•E 2 uses a diffusion model to generate an image based on an image embedding. The image embedding is generated from a text caption.
