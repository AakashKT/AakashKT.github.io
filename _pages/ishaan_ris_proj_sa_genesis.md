---
layout: page
title: Combining Resampled Importance and Projected Solid Angle Samplings for Many Area Light Rendering
permalink: /ris_projsa_genesis

---

During my time at Meta, one junior from the lab by the name of <a href="https://ishaanshah.github.io/">Ishaan Shah</a> got in touch with me. He was working on vison-y problems and was not very much into them, and wanted to explore computer graphics and specifically rendering.

We decided to work together on a project - extending LTCs to layered and multi-lobed BRDFs. This was pretty fun, but also challenging since neither of us had any experience with layered materials. We lingered around this problem for about 4 months, before finally deciding to shelf it and work on another extension of LTCs -- efficient rendering with LTC and many area lights.

For this exploration, we did a lot of experiments with Light BVH and other data structures -- it turned out finally that ray tracing with RTX hardware is fast enough, that its not worth the extra cost of querying such data structures. <br>
These explorations led us to create the "best" baseline for direct lighting with ray tracing -- combining <a href="https://cs.dartmouth.edu/~wjarosz/publications/bitterli20spatiotemporal.html">RIS from ReSTIR</a> (NVIDIA's work) with <a href="https://momentsingraphics.de/Siggraph2021.html">projected solid angle sampling</a> (Christoph Peter's work from his time at KIT).

Turns out, we can very easily and directly combine the two approaches and improve convergence with each sample -- however, the convergence with time sufffers. Essentially, the compute increases by a lot.<br>
This began a quest to pinpoint the exact problem and source of high compute - the solution is what our method in this paper is!

In a curious turn of events, Ishaan has now shifted to our group with Prof. PJN. He has now abandoned working with me and is working on efficient glint rendering with <a href="https://profs.etsmtl.ca/agruson/">Adrien Gruson</a> and <a href="https://scholar.google.com/citations?user=kLdgISoAAAAJ&hl=en">Luis Gamboa</a>. Jokes aside, glad to have worked with good students like him.
