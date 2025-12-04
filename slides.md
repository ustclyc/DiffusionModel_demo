---
theme: seriph
title: Diffusion Model
transition: slide-left
# background: https://cover.sli.dev

---

# From Noise to Masterpiece
<div class="text-3xl text-right">---The Magic of Diffusion Models</div>
<br><br>
<div class="text-2xl"> presenter:Yichen Li</div>


---

# What is Diffusion Model?
<img src=https://arthurchiao.art/assets/img/rise-of-diffusion-based-models/generative-models.png width="600" />

---

# In one sentence:
<div class="text-2xl"> Gradualy add Gaussian noise and then reserve </div>
<br><br><br>
<img src=https://cdn.prod.website-files.com/614c82ed388d53640613982e/66b37e8b2ea6e35611d24c2f_66b37e2e4af07a0baef9484c_consistency-models.webp width="700" />


---

# Forward diffusion process

<div class="opacity-100 text-current">

$$ x_0 :a \ real \ data \qquad x_1,...x_t :sequence \ of \ noisy \ samples $$

$$ q(x_t | x_{t-1}) = \mathcal{N}(x_t; \sqrt{1 - \beta_t} x_{t-1}, \beta_t \mathbf{I}) $$

$$ x_t = \sqrt{\alpha}_t x_{t-1} + \sqrt{1-\alpha_t} \epsilon \qquad \qquad one-step \ transition $$

$$\bar{\alpha}_t = \prod_{i=1}^t \alpha_i $$

$$ x_t = \sqrt{\bar{\alpha}_t} x_0 + \sqrt{1-\bar{\alpha}_t} \epsilon \qquad \qquad The \ Reparameterization \ Trick$$

</div>

---

# Reverse diffusion process
<div class="opacity-100 text-current">

$$given \ x_t,t$$
$$How \ to \ predict \ x_{t-1} \ ?$$

</div>

<br>

$\displaystyle The \ true \ 
p_\theta(x_{t-1} | x_t) \ is \ unknown \ and \ complex$

$\displaystyle Small \ Step \ Hypothesis: \\ If \ the \ forward \ noise \ is \ added \ in \ very \ small \ steps \ (\beta_t \to 0),\\
 the \ reverse \ process \ is \ mathematically \ guaranteed \ to \ be \ a \ Gaussian \ distribution.$

$\displaystyle p_\theta(x_{t-1} | x_t) = \mathcal{N}(x_{t-1}; \mu_\theta(x_t, t), \Sigma_\theta(x_t, t))$

$\displaystyle now \ we \ can \ focus \ on \ the \ \text{\bf mean} \ and \ the \ \text{\bf variance}$
---

# Reverse diffusion process
<br>

$$ p_\theta(x_{t-1} | x_t) = \mathcal{N}(x_{t-1}; \mu_\theta(x_t, t), \Sigma_\theta(x_t, t))$$

$\displaystyle  \text{you may notice the subscript} \ \theta
,\text{it indicates that the distribution or function is predicted} \\
\text{by a neural network.} \\
\text{In fact , the neural network predicts }$

$$ \epsilon_\theta(x_t, t) \approx \epsilon$$

$\displaystyle \text{in stead of directly the mean and the varience. } \\ \text{But why would it work?}$


---

# Reverse diffusion process
<br>

$$\mu_\theta(x_t, t) = \frac{1}{\sqrt{\alpha_t}} \left( x_t - \frac{1 - \alpha_t}{\sqrt{1 - \bar{\alpha}_t}} \epsilon_\theta(x_t, t) \right),$$

$$\Sigma_\theta(x_t, t) \ is \ fixed \$$
<br>

$\displaystyle Then$
$$ \boxed{x_{t-1} = \mu_\theta(x_t, t)+ \sigma_t z} $$

---

# Algorithm
<img src=https://lilianweng.github.io/posts/2021-07-11-diffusion-models/conditioned-DDPM.png width="700" />

---

# Further applications

<br>

### Image Generation & Editing

- **Text-to-Image Generation** (e.g., Midjourney, SDXL)
  - <span class="text-gray-400 text-sm">Transforming natural language prompts into photorealistic visuals.</span>

- **Image Inpainting & Outpainting** (e.g., Adobe Firefly)
  - <span class="text-gray-400 text-sm">Restoring missing regions or extending canvas boundaries seamlessly.</span>

- **Structural Conditioning** (e.g., ControlNet, T2I-Adapter)
  - <span class="text-gray-400 text-sm">Guiding generation with edges, poses, or depth maps for precise control.</span>
  

---

# Further applications

<img src=https://substackcdn.com/image/fetch/$s_!W6tU!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F53f44c06-b970-43ce-af93-1feec1434e95_1134x650.png width="700" />

---

# Further applications
### Frontiers: Video, 3D & Science

- **Video & Motion Synthesis** (e.g., Sora, Runway Gen-2)
  - <span class="text-gray-400 text-sm">Generating temporally coherent sequences with simulated physics.</span>

- **3D Asset Generation** (e.g., DreamFusion, Point-E)
  - <span class="text-gray-400 text-sm">Synthesizing 3D geometry and textures from 2D images or text.</span>

- **Scientific Discovery** (e.g., RFdiffusion, Drug Design)
  - <span class="text-gray-400 text-sm">Modeling complex biological structures for protein design and meteorology.</span>

---

# Further applications
<img 
  src="\20240219140550_65d2efbedd031.gif" 
  class="h110 rounded-xl shadow-lg border border-gray-200" 
/>

---

# Further applications
<img 
  src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*L2SEvdr6r0ZZ0932gOqMjQ.gif" 
  class="h-110 rounded-xl shadow-lg border border-gray-200" 
/>

---

# Further application

<img 
  src="https://spectrum.ieee.org/media-library/two-examples-of-protein-targets-in-the-free-modelling-category-in-green-is-the-experimental-result-in-blue-is-the-computationa.gif?id=25559695&width=2400&height=1358"
  class="h-110 rounded-xl shadow-lg border border-gray-200" 
/>

---
layout: cover
background: https://source.unsplash.com/collection/94734566/1920x1080
# 或者换成你自己的 AI 生成图路径: background: /my-ai-art.png
---

# Thank You













