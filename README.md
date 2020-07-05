# Ray Tracing Tech 

Nowadays ray tracing is a fantastic tech in a rendering pipeline.
This is a paper list about the most important techs and some hard core knowledge about ray tracing.
There will be a collection of papers that interest me. The emphasis is focused on, but not limited to raytracing itself. Papers of significance are marked in **bold**. My comments are marked in *italic*.

## My Contributions
I used to purchase my master degree in Tsinghua University, and I focus on energy-efficient architecture design for deep learning. Some featured works are presented here. 

- [**Deep Convolutional Neural Network Architecture with Reconfigurable Computation Patterns.**](https://ieeexplore.ieee.org/document/8412607) (**IEEE TRANS TCAD**)
  - *This work aims to accelerate a generative network, which includes CONV layers, DeCONV layers and residual blocks.*
  - *A dual convolution mapping method for CONV and DeCONV layers to make full use of the available PE resources.*
  - *Precision-adaptive PEs and buffer bandwidth reconfiguration are used to support flexible bitwidths for both inputs and weights in deep neural networks*
  - *A cross-layer scheduling method is also proposed to avoid extra off-chip memory access in residual block processing*


- [**Research on low-power neural network computing accelerator.**](http://engine.scichina.com/publisher/scp/journal/SSI/49/3/10.1360/N112018-00282?slug=fulltext) (**SCIENTIA SINICA**)
  - *This study aims to propose a reconfigurable hardware architecture to meet the flexibility requirements of a neural network.*
  - *Based on the proposed architecture, the corresponding data access optimization schemes are explored to reduce the power consumption.*
  - *In the optimization of the storage system, an acceleration scheme of neural network based on eDRAM and ReRAM scheme, which is used for computing and storage integration, satisfy the requirement of neural network computing.*
  - *Regarding high-performance computing, we have proposed convolution optimization schemes based on integral and filter splitting feature reconstruction to enable low bit neural network operations to meet high-performance requirements.*

And now I have been working in a fabless company, and do some researches and engineering work with ray tracing tech.

## Table of Contents
 - [My Contributions](#my-contributions)
  - [Important Topics](#important-topics)
   - [Tutorial about RayTracing](#tutorial-and-survey) 
   - [Acceleration Structure in RT](#BVH)
   - [Traversal in RayTracing](#RTU)
   - [AI tech in RayTracing](#AIRT) 
   - [Denoise](#denoise)
   - [Benchmarks](#benchmarks)
   - [Other Topics](#other-topics)
 - [Industry Contributions](#industry-contributions)

## Important Topics
### Tutorial about RayTracing
- **Ray Tracing in One Weekend** 
  - *Basic knowledge about ray tracing*
- **Ray Tracing The Next Week** 
  - *Advanced knowledge about ray tracing*
- **Ray Tracing The Rest of Your Life** 
  - *You can be a Ray tracing master*
  

### Acceleration Structure in RT
Acceleration structure is used to acceleration ray traversal 

1. BVH, Bounding Volume Hierarchy (BVH) is a popular ray tracing acceleration technique that uses a tree-based “acceleration structure” that contains multiple hierarchically-arranged bounding boxes (bounding volumes) that encompass or surround different amounts of scene geometry or primitives. 

 - **"HLBVH: hierarchical LBVH construction for real-time ray tracing of dynamic geometry."** (Pantaleoni, Jacopo, and David Luebke. Proceedings of the Conference on High Performance Graphics. 2010.)
   - *It presents HLBVH and SAH-optimized HLBVH, two high performance BVH construction algorithms targeting real-time ray tracing of dynamic geometry.*

### AI tech in RayTracing
- **Learning light transport the reinforced way.** (NVIDIA Research Team In ACM SIGGRAPH 2017 Talks(SIGGRAPH ’17))
  - *Combine reinforcement learning process with the ray tracing, brings up a new idea from the rendering equation.*
  - *Using neural network to do some inference to compute the ray direction instead of the importance sampling.*

### DeNoise
- **Spatiotemporal Variance-Guided Filtering: Real-Time Reconstruction for Path-Traced Global Illumination.** (High Performance Graphics 2017)
  - *It uses spatiotemporal variance-guided filtering to rebuild the statistic figures processed by ray tracing method*


- **Reconstruction of Monte Carlo Image Sequences using a Recurrent Denoising Autoencoder.** (Chaitanya C R A , Kaplanyan A S , Schied C , et al. Acm Transactions on Graphics, 2017, 36(4):1-12.)
  - *A machine learning technique for reconstructing image sequences rendered using Monte Carlo methods.* 

 
## Industry Contributions
 - [NVIDIA](http://www.nvidia.com/)
   - RTX 2080/3080: PC platform for ray tracing. 

## BenchMarks
 - [Sponze]
 - [Cornell Boxes]

