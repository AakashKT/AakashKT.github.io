---
layout: page
title: Bringing Linearly Transformed Cosines to Anisotropic GGX
permalink: /ltc_anisotropic.html
authors: Aakash KT<sup>1</sup>, Eric Heitz<sup>2</sup>, Jonathan Dupuy<sup>2</sup> and P. J. Narayanan<sup>1</sup>
affiliation: <sup>1</sup>CVIT, KCIS, IIIT Hyderabad <br> <sup>2</sup> Unity Technologies
conference: ACM SIGGRAPH Symposium on Interactive 3D Graphics and Games (I3D) 2022

---

<hr>
<img src="/assets/img/i3d2022_teaser.jpg" style="width:100% ; height: auto">

<h3><b>Abstract</b></h3>
<p>
Linearly Transformed Cosines (LTCs) are a family of distributions that are used for real-time area-light shading thanks to their analytic integration properties. 
Modern game engines use an LTC approximation of the ubiquitous GGX model, but currently this approximation only exists for isotropic GGX and thus anisotropic GGX is not supported. 
While the higher dimensionality presents a challenge in itself, we show that several additional problems arise when fitting, post-processing, storing, and interpolating LTCs in the anisotropic case.
Each of these operations must be done carefully to avoid rendering artifacts.
We find robust solutions for each operation by introducing and exploiting invariance properties of LTCs. 
As a result, we obtain a small 8<sup>4</sup> look-up table that provides a plausible and artifact-free LTC approximation to anisotropic GGX and brings it to real-time area-light shading.
</p>
<span>
    <a target="_blank" href="https://arxiv.org/abs/2203.11904">[PDF]</a> 
    <a target="_blank" href="https://drive.google.com/file/d/1UmRz1AEGkShMwdG6mJZnpIeC4mfa-hrn/view?usp=sharing">[Supp]</a>
    <a target="_blank" href="https://github.com/AakashKT/LTC-Anisotropic">[Code]</a>
    <a target="_blank" href="https://www.youtube.com/watch?v=P-wRgPe8sDs&t=8500s&ab_channel=I3DSymposium">[Slides]</a>
</span>

<br>
<hr>
<h3><b>Look up tables (LUTs)</b></h3>
Below you can find 8x8x8x8 look up tables for two different parameterizations.

<table class="table table-striped">
    <thead>
        <tr>
            <th scope="col">Parameterization</th>
            <th scope="col">Numpy</th>
            <th scope="col">C++ float array</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>&alpha;<sub>x</sub> , &alpha;<sub>y</sub> , &theta; , &phi;</td>
            <td>
                <a href="https://github.com/AakashKT/LTC-Anisotropic/blob/main/LUT/alphax_alphay_theta_phi.npy">LUT.npy</a>
            </td>
            <td>
                <a href="https://github.com/AakashKT/LTC-Anisotropic/blob/main/LUT/alphax_alphay_theta_phi.cpp">LUT.cpp</a>
            </td>
        </tr>
        <tr>
            <td>&alpha; , &lambda; , &theta; , &phi;</td>
            <td>
                <a href="https://github.com/AakashKT/LTC-Anisotropic/blob/main/LUT/alpha_lambda_theta_phi.npy">LUT.npy</a>
            </td>
            <td>
                <a href="https://github.com/AakashKT/LTC-Anisotropic/blob/main/LUT/alpha_lambda_theta_phi.cpp">LUT.cpp</a>
            </td>
        </tr>
    </tbody>
</table>
<br>
<hr>

<br>
<h3><b>Storing LUTs in a texture</b></h3>
Use with hardware and software interpolation. Three sets of 8x8x64 textures.
<br>
<br>
<div>
    <img src="/assets/img/i3d_project_page.png" style="width:100% height:auto">
</div>
<br>
<hr>

<br>
<h3><b>Fetching LTC matrices</b></h3>
Pseudocode for fetching LTC matrices for both LUT parameterizations is given below.
<br><br>
<div class="row">
    <div class="col-sm-6" align="center">
        <p><b>Parameterization:</b> &alpha;<sub>x</sub> , &alpha;<sub>y</sub> , &theta; , &phi;</p>
        <script src="https://gist.github.com/AakashKT/0d5dbca97e4c61e55f3c1c3162479b2a.js"></script>
    </div>
    <div class="col-sm-6" align="center">
        <p><b>Parameterization:</b> &alpha; , &lambda; , &theta; , &phi;</p>
        <script src="https://gist.github.com/AakashKT/8354e00c22414643661a9b87d2e009a3.js"></script>
    </div>
</div>
<br>
<hr>

<br>
<div align="center">
    <iframe width="560" height="315" src="https://youtube.com/embed/DwHkPr7WAb8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
<hr>
<p><b>Acknowledgements</b><br>
    Thanks to Thomas Deliot for making a prototype in the Unity engine and to Stephen Hill for his feedback.<br> Aakash KT was funded by the "Kohli Fellowhip" of KCIS.
</p>