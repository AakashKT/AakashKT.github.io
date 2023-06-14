---
layout: page
title: A Flexible Neural Renderer for Material Visualization
permalink: /flexible_nr
authors: Aakash KT<sup>1</sup>, Parikshit Sakurikar<sup>1, 2</sup>, Saurabh Saini<sup>1</sup> and P. J. Narayanan<sup>1</sup>
affiliation: <sup>1</sup>IIIT Hyderabad <br> <sup>2</sup>DreamVu Inc.
conference: ACM SIGGRAPH Asia 2019, Technical Briefs

---

<hr>
<img src="/assets/img/flexible_nr_teaser.jpg" style="width:100% ; height:auto">
<br><br>
<h3>Abstract</h3>
<p>
    Photo realism in computer generated imagery is crucially dependent on how well an artist is able to recreate real-world materials in the scene. The workflow for material modeling and editing typically involves manual tweaking of material parameters and uses a standard path tracing engine for visual feedback. A lot of time may be spent in iterative selection and rendering of materials at an appropriate quality. In this work, we propose a convolutional neural network that quickly generates high-quality ray traced material visualizations on a shaderball. Our novel architecture allows for control over environment lighting which assists in material selection and also provides the ability to render spatially-varying materials. Comparison with state-of-the-art denoising and neural rendering techniques suggests that our neural renderer performs faster and better. We provide an interactive visualization tool and an extensive dataset to foster further research in this area.
</p>
<span>
    <a target="_blank" href="https://arxiv.org/abs/1908.09530">[arXiv]</a>
    <a target="_blank" href="https://dl.acm.org/doi/10.1145/3355088.3365160">[PDF]</a>
    <a target="_blank" href="https://github.com/AakashKT/NeuralMaterialVisualization">[Code]</a>
    <a target="_blank" href="https://drive.google.com/drive/folders/1DXcVPr-g7H5SefmrOSs3xRGdMof0SBwZ?usp=sharing">[Data]</a>
</span>
<br><br>
<div align="center">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/X4ShR70rZAk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
<hr>
<p><b>Acknowledgements</b><br>
    We thank the reviewers of our SIGGRAPH Asia 2019 submission for their valuable comments and suggestions.
</p>