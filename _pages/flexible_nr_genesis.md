---
layout: page
title: Genesis - A Flexible Neural Renderer for Material Visualization
permalink: /flexible_nr_genesis

---

This project began by noticing a small limitation of the excellent paper <a href="https://users.cg.tuwien.ac.at/zsolnai/gfx/gaussian-material-synthesis/">Gaussian Material Synthesis</a>. Specifically, the limitation was in the "Neural Rendering" module -- it could only handle constant (non spatially varying) materials, and the lighting was always fixed. To add to that, the network size was huge, considering the task at hand. 

Fixing all of the above meant greater flexibility in visualization of materials, without having to wait for the rendering to finish. In the end, allowing greater material parameter iteration times with a fast & flexible visualization.
