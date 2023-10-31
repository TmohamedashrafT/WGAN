# WGAN
Application of Wasserstein Generative Adversarial Networks on Fashion MNIST using PyTorch

### GANs problems
During the normal training of GANs, several problems are commonly encountered, including mode collapse and vanishing gradients. These issues arise because the discriminator tends to become more powerful than the generator, given the relatively easier task it has. Consequently, the discriminator can easily predict that all generator images are generated, making it difficult for the generator to learn and improve its image generation in a meaningful manner

## Wasserstein GANs overview
The Wasserstein distance addresses this problem by providing a way to calculate the distance between two probability distributions. Instead of the gradients vanishing when the real and generated distributions are far from each other, the Wasserstein distance calculates the distance between the real distribution and the generated distribution.

![image](https://github.com/TmohamedashrafT/WGAN/blob/main/WGAN_img.webp)



In the WGAN, the Critic loss aims to maximize the distance between the real distribution and the generated distribution, as indicated in line 5. To ensure stable training and maintain continuity, it is necessary to enforce Lipschitz continuity, which ensures that the gradient at each point is smaller than or equal to a constant value, denoted as "k" ( go to [this link](https://ai.stackexchange.com/questions/29904/what-is-lipschitz-constraint-and-why-it-is-enforced-on-discriminator) for more details about Lipschitz constraint with critic) .

There are two methods commonly used to enforce Lipschitz continuity: gradient penalty and weight clipping. However, in this project, the approach of clipping weights is employed, as mentioned in line 7. Weight clipping directly limits the weights of the Critic network to enforce Lipschitz continuity. After each weight update, the weights are clipped to ensure they do not exceed a predefined threshold.

The generator aims to minimize the distance between the real distribution and the generated distribution, making it more challenging for the critic to distinguish between real and fake data. In line 10, the equation represents the negative mean output of the critic network. For example, if the output of the critic is positive, it indicates that the data is perceived as real. Consequently, the generator loss will be negative. Conversely, if the output of the critic is negative, it indicates that the data is perceived as fake, resulting in a positive generator loss. Therefore, the generator needs to minimize the generation of fake data in order to improve its performance.(go to [this link](https://ai.stackexchange.com/questions/36042/what-is-being-optimized-with-wgan-loss-is-the-generator-maximizing-or-minimizin) for more details)

![image](https://github.com/TmohamedashrafT/WGAN/blob/main/wganloss_.png)

# Reference 
- https://arxiv.org/abs/1701.07875v3
  
