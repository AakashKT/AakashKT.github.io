---
layout: page
title: Genesis - Fast Analytic Soft Shadows from Area Lights
permalink: /fast_ss_genesis

---

As part of my MS, we submitted to SIGGRAPH Asia 2020 (yes, right at the COVID peak). The paper was, what I believed, a very solid work. However, the reviews were completely opposite -- all rejects! And this was not because it was SIGGRAPH -- the work itself was quite inferior, as I realized after reading the excellent reviews.

The reviews however gave a concrete but different direction to my research. I spent the next months polishing my basics, while throughly analyzing the reviews and trying various ideas. 

One such idea was an intuition -- what if you project occluder geometry somehow, and analytically integrate only on the difference region of the light source using LTCs. This will give analytic soft shadows!

The next few months were spent realizing this idea, iterating over theoritical and implementation details, which resulted in a submission to EGSR 2021.
