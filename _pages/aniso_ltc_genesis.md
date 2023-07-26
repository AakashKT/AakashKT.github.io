---
layout: page
title: Genesis - Bringing Linearly Transformed Cosines to Anisotropic GGX
permalink: /aniso_ltc_genesis

---

After our EGSR 2021 paper, searching for a next project, I was sure (naively) that this method could be worked out to run on the GPU. And, this would mean near real time shading from area lights! We were also thinking lightly about another direction for exploration -- the fact that LTCs are limited to isotropic BSDFs, and had some "neural" ideas there.

Excited by the first prospect, and wanting to see it in production, I emailed the whole team of <a href="https://unity-grenoble.github.io/website/">Unity Research, Grenoble</a>, which included <a href="https://eheitzresearch.wordpress.com/">Eric Heitz</a> & <a href="https://onrendering.com/">Jonathan Dupuy</a>.

Eric was kind enough to explain in great detail why he thinks this is not a great idea, and why it won't work on the GPU. He was also thinking about the LTC extension to anisotropy. Thats how we started collaborating.

We explored several directions, including the "neural" one. The one that ultimately worked is what you see in the I3D paper.
