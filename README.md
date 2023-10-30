# WGAN
Application of Wasserstein Generative Adversarial Networks on Fashion MNIST using PyTorch

### GANs problems
During the normal training of GANs, several problems are commonly encountered, including mode collapse and vanishing gradients. These issues arise because the discriminator tends to become more powerful than the generator, given the relatively easier task it has. Consequently, the discriminator can easily predict that all generator images are generated, making it difficult for the generator to learn and improve its image generation in a meaningful manner

## Wasserstein GANs overview
The Wasserstein distance addresses this problem by providing a way to calculate the distance between two probability distributions. Instead of the gradients vanishing when the real and generated distributions are far from each other, the Wasserstein distance calculates the distance between the real distribution and the generated distribution.

![image](https://github.com/TmohamedashrafT/WGAN/blob/main/WGAN_img.webp)
