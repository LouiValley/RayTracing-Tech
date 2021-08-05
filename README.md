# Ray Tracing Tech 
Ray tracing is a rendering technique that can produce incredibly realistic lighting effects. Essentially, an algorithm can trace the path of light, and then simulate the way that the light interacts with the virtual objects it ultimately hits in the computer-generated world. 

Here is a vedio to show you.
[**12 Games That Look INSANE Due To Ray Tracing**](https://www.youtube.com/watch?v=lNSpiret-9g)

This is a collection organized by myself about the most important techs and some hard core knowledge about ray tracing. 
These contents includes the API, ray tracing algotithms(acceleration structure building, ray traversal& intersection& denoise& AI tech), benchmarks and so on.
This is my review of my knowledge system about ray tracing, and it can also help researchers engaged in research to quickly master the knowledge of ray tracing.

There is a collection of papers that interest me. The emphasis is focused on, but not limited to raytracing itself. Papers of significance are marked in **bold**. My comments are marked in *italic*.



## Intro about myself
I got my master degree in Tsinghua University (2019), advised by Prof.Shouyi Yin, and I focus on energy-efficient architecture design for deep learning. Some featured works are presented here. 

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

I worked as a Senior Engineer at Hisilicon (2019~2021), and did some researches and engineering work about ray tracing tech on a mobile GPU. I was very familiar with acceleration structure in RT and I was the AS building algorithm owner for the hardware design, moreover I also did some researches about other necessary knowledge aspects about ray tracing including: ray traversal&intersection, AI tech in raytracing(reinforcement learning in ray sampling), denoise tech for ray tracing and others.

## What I have  to doing now
Now I am pursing my Ph.D degree at Tokyo Tech University (From 2021~), advised by Prof.Motomura. And my interesting topics include deep learning, computer architecture, GPU, Ray-tracing.

## Table of Contents
 - [My Contributions](#my-contributions)
  - [Important Topics](#important-topics)
   - [Tutorial about RayTracing](#tutorial-and-survey) 
   - [Acceleration Structure in RT](#BVH)
   - [Traversal in RayTracing](#RTU)
   - [AI tech in RayTracing](#AIRT) 
   - [Denoise](#denoise)
   - [API about RayTracing](#API)
   - [Benchmarks](#benchmarks)
   - [Other Topics](#other-topics)
 - [Industry Contributions](#industry-contributions)

## Important Topics
### Tutorial about RayTracing
If you are a freshman and know nothing about the ray tracing, I strongly recommand you to read the following trilogy.
- **[Ray Tracing in One Weekend](https://raytracing.github.io/books/RayTracingInOneWeekend.html)** 
  - *Basic knowledge about ray tracing*
- **[Ray Tracing The Next Week](https://raytracing.github.io/books/RayTracingTheNextWeek.html)** 
  - *Advanced knowledge about ray tracing*
- **[Ray Tracing The Rest of Your Life](https://www.realtimerendering.com/raytracing/Ray%20Tracing_%20the%20Rest%20of%20Your%20Life.pdf)** 
  - *You can be a Ray tracing master*
  

### Acceleration Structure Building in Ray Tracing

Here we focus on the Bounding Volume Hierarchy (BVH), which is a popular ray tracing acceleration technique that uses a tree-based “acceleration structure” that contains multiple hierarchically-arranged bounding boxes (bounding volumes) that encompass or surround different amounts of scene geometry or primitives. 

 - **[Fast BVH Construction on GPUs](http://graphics.snu.ac.kr/class/graphics2011/references/2007_lauterbach.pdf)**(EUROGRAPHICS 2009)
   - *It presents two novel parallel algorithms for rapidly constructing bounding volume hierarchies on manycore GPUs. The first uses a linear ordering derived from spatial Morton codes to build hierarchies extremely quickly and with high parallel scalability. The second is a top-down approach that uses the surface area heuristic (SAH) to build hierarchies optimized for fast ray tracing.*

 - **[HLBVH: hierarchical LBVH construction for real-time ray tracing of dynamic geometry.](https://research.nvidia.com/sites/default/files/pubs/2010-06_HLBVH-Hierarchical-LBVH/HLBVH-final.pdf)** (Pantaleoni, Jacopo, and David Luebke. Proceedings of the Conference on High Performance Graphics. 2010.)
   - *It presents HLBVH and SAH-optimized HLBVH, two high performance BVH construction algorithms targeting real-time ray tracing of dynamic geometry.*

 - **[Heuristics for Ray Tracing Using Space Subdivision.](https://graphicsinterface.org/wp-content/uploads/gi1989-22.pdf)**
    - *This paper reports new construction algorithms which represent considerable improvement over conventional methods in terms of reducing the number of nodes, leaves, and objects visited by a ray . The algorithms employ the surface area heuristic and a heuristic for estimating the optimal splitting plane between the spatial median and the object median.*
 - **[PLOCTree: A Fast, High-Quality Hardware BVH Builder](https://dl.acm.org/doi/abs/10.1145/3233309)**
    - *This paper proposes PLOCTree, an accelerator for tree construction based on the Parallel Locally-Ordered Clustering (PLOC) algorithm*

### Traversal in Ray Tracing
It involves how light traverses objects in acceleration structures. It mainly involves two major strategies full stack and stackless.

- **Full Stack**
- **[Fast Ray Sorting and Breadth-First Packet Traversal for GPU Ray Tracing](http://charlesloop.com/GaranzhaLoop2010.pdf)** (Computer Graphics Forum, 2010)
  - *It presents a novel approach to ray tracing execution on commodity graphics hardware using CUDA.* 
  - *It includes sort rays, frustum creation, breadth-first Frustum Traversal three techs*

- **Stackless**
- **[Efficient Stack-less BVH Traversal for Ray Tracing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.445.7529&rep=rep1&type=pdf)** (SCCG 2011 conference)
  - *It presents a traversal algorithm for BVH that does not need a stack and hence minimizes the memory needed for a ray*
- **[KD-Tree Acceleration Structures for a GPU Raytracer](https://graphics.stanford.edu/papers/gpu_kdtree/kdtree.pdf)**(Siggraph 2005)
  - *It presents kd-tree traversal algorithms kd-restart and kd-backtrack that run without a stack.*
- **[restart trail for stackless BVH traversal](https://research.nvidia.com/publication/restart-trail-stackless-bvh-traversal)** (HPG2010)
  - *In this paper, it introduces restart trail, a simple algorithmic method that makes restarts possible regardless of the type of hierarchy by storing one bit of data per level.*

### AI tech in RayTracing
- **[Learning light transport the reinforced way.](https://arxiv.org/abs/1701.07403)** (NVIDIA Research Team In ACM SIGGRAPH 2017 Talks(SIGGRAPH ’17))
  - *Combine reinforcement learning process with the ray tracing, brings up a new idea from the rendering equation.*
  - *Using neural network to do some inference to compute the ray direction instead of the importance sampling.*

### DeNoise
- **[Spatiotemporal Variance-Guided Filtering: Real-Time Reconstruction for Path-Traced Global Illumination.](https://research.nvidia.com/publication/2017-07_Spatiotemporal-Variance-Guided-Filtering%3A)** (High Performance Graphics 2017)
  - *It uses spatiotemporal variance-guided filtering to rebuild the statistic figures processed by ray tracing method*


- **[Reconstruction of Monte Carlo Image Sequences using a Recurrent Denoising Autoencoder.](https://research.nvidia.com/sites/default/files/publications/dnn_denoise_author.pdf)** (Chaitanya C R A , Kaplanyan A S , Schied C , et al. Acm Transactions on Graphics, 2017, 36(4):1-12.)
  - *A machine learning technique for reconstructing image sequences rendered using Monte Carlo methods.* 

### API about RayTracing
  - [DirectX Raytracing(DXR) Functional Spec](https://microsoft.github.io/DirectX-Specs/d3d/Raytracing.html)
  - [Ray Tracing In Vulkan - The Khronos Group](https://www.khronos.org/registry/vulkan/specs/1.2-extensions/html/index.html)

## Industry Contributions
 - [NVIDIA](http://www.nvidia.com/)
   - RTX 2080/3080: PC platform for ray tracing. 
 - [Local Ray](https://www.adshir.com/)
   - Adshir's LocalRay™ is a Ray Tracing Graphics Enging scaling from High-End Gaming GPUs to mobile devices.

## BenchMarks
 - [Sponze]
 - [Cornell Boxes]

