---
layout: post
title: Jacobian of the LTC transformation
date: 2022-06-11
description: Deriving the jacobian of the LTC transform. In-detail walkthrough.
permalink: /blog/2022/ltc-jacobian/
---

My recent <a href="ltc_anisotropic.html">paper</a> builds on this <a href="https://eheitzresearch.wordpress.com/415-2/">Linearly Transformed Cosines paper</a> by Eric Heitz. Infact, this was a collaboration with Eric himself! Linearly Tranformed Cosines or LTCs are a transformation of the rendering integral under specific assumptions, which lead to analytic solutions of it. One of the outcomes of my new work was the relaxation of the isotropic assumption of LTCs, allowing the use of anisotropic BRDFs.

Although I have read the original paper countless times and worked on an extension of it, I still was puzzled by the LTC jacobian derivation given in the appendix of the original paper:

<br>
<div class="row" align="center">
    <div class="col-sm-6">
        <img src="/assets/img/ltc_jac_1.png">
    </div>
    <div class="col-sm-6">
        <img src="/assets/img/ltc_jac_2.png">
    </div>
</div>
<div class="row" align="center">
    <div class="col-sm-12">
        <b>Figure 1:</b> LTC jacobian derivation from the <a href="https://eheitzresearch.wordpress.com/415-2/">original paper.</a>
    </div>
</div>
<br>

The derivation must be pretty obvious to a lot of people but to me it wasn't so.
This post is an attempt to give a detailed and intuitive derivation of this expression (Eq. 18 above). Why is this important? Well, in my view small details like these expand your horizon, and you can only hope to get new ideas if you throughly understand what's already out there. Also, its always fun to understand things from a mathematical perspective, even if you are a intuitive-first person like I am.

I would like to note that figures in this post have been directly taken from the <a href="https://eheitzresearch.wordpress.com/415-2/">original paper.</a>

<br>

Definitions
-----
Its best if you have read and are confortable with Eric's original paper. However, I am still defining things here to ensure consistency.

Direction vectors on the unit sphere are given by $$\omega = (x, y, z)$$. $$D_o(\omega_o)$$ is the source (clamped cosine) distribution. 
$$D(\omega)$$ is the target (~ GGX BRDF) distribution. Given an LTC matric $$M$$, the direction vectors $$\omega$$ of $$D$$ are obtained by from the direction vectors $$\omega_o$$ of $$D_o$$ by:

<p>
$$
\omega = \frac{M\omega_o}{|| M\omega_o ||}.
$$
</p>
The magnitude at the transformed direction is given by:
<p>
$$
\boxed{ D(\omega) = D_o(\omega_o) \frac{\partial \omega_o}{\partial \omega}. }
$$
</p>
Here, $$\frac{\partial \omega_o}{\partial \omega} $$ is the determinant of jacobian of the transformation (which is frequently referred to as just the jacobian). This is what we will derive in this post.

Another thing we will find useful is the <a href="https://en.wikipedia.org/wiki/Solid_angle#:~:text=Thus%20one%20can,the%20viewer%20as%3A">solid angle subtended by a small facet</a> having area $$A$$, which is given by:
<p>
$$
\partial \omega = \frac{A (\hat{r} \cdot \hat{n})}{r^2},
$$
</p>
where $$\partial\omega$$ is a small solid angle, $$\hat{r}$$ is the normalized position vector of the facet, $$\hat{n}$$ is the surface normal of the facet and $$r^2$$ is the distance to the facet.

Finally, we will find use of the <a href="https://en.wikipedia.org/wiki/Cross_product#:~:text=More%20generally%2C%20the%20cross%20product%20obeys%20the%20following%20identity%20under%20matrix%20transformations%3A"> cross product under linear transforms</a> property:
<p>
$$
M\omega_1 \times M\omega_2 = |M| M^{-T} (\omega_1 \times \omega_2) = |M| M^{-T} \omega_o
$$
</p>
 
<br>

Derivation
-----
First things first. Note that $$D$$ and $$D_o$$ are distributions in <b>2D</b>, although they appear to be distributions in 3D. To see why, note that these are distributions on the unit sphere. Hence, we can write $$\omega = (\sin\theta \cos\phi, \sin\theta \sin\phi, \cos\theta)$$, in turn making $$D$$ and $$D_o$$ dependent on only $$\theta, \phi$$ (thus two dimensional). 

From the <a href="https://en.wikipedia.org/wiki/Jacobian_matrix_and_determinant#:~:text=Jacobian%20determinant%5Bedit%5D">definitaion of jacobian determinants</a>, $$\frac{\partial \omega_o}{\partial \omega} $$ measures how a differential area around $$\omega_o$$ changes. Since this differential area in on the unit sphere, it is basically the <a href="https://en.wikipedia.org/wiki/Solid_angle">solid angle</a>. <b>The jacobian thus measures change in solid angle under the LTC transform</b>.

Our problem now boils down to determining how a differential solid angle changes under $$M$$.

Let's take the differential solid angle $$\color{red}\partial\omega_o$$ in $$D_o$$. Since this is small enough, it can also be considered as a planar facet. Now, define two vectors $$\omega_1, \omega_2$$, which together with $$\omega_o$$ form an orthonormal basis. (Figure 2, left)

<div class="row" align="center">
    <div class="col-sm-12">
        <img src="/assets/img/do_solid_angle.png" style="width: 600px">
    </div>
</div>
<div class="row" align="center">
    <div class="col-sm-12">
        <b>Figure 2:</b> Left: Orthonormal basis in D<sub>o</sub>; Right: The same basis transformed by M.
    </div>
</div>
<br>

Transforming these vectors by LTC $$M$$ results in a new set of vectors (Figure 2, right). The area of the facet $$\color{red}\partial\omega_o$$ is now changed to $$\color{red}\partial\omega_o \cdot A$$, where $$A$$ is the area of parallelogram defined by vectors $$M\omega_1$$ and $$M\omega_2$$. 

A subtelty you may want to note, is that in Figure 2 left, the area of the parallelogram given by $$\omega_1$$ and $$\omega_2$$ is $$1$$, thus the differential area is only $$\partial\omega_o$$. This changes in Figure 2 right, since the area of the parallelogram is not $$1$$ anymore, and thus the differential area is $$\partial\omega_o \cdot A$$.

Alright! Now how about the differential solid angle $$\color{green}\partial\omega$$ after the LTC transform? Its essentialy the <b>solid angle subtended by a small facet</b>! We know this directly (see definitions section):

<p>
$$
\partial\omega = \frac{\partial\omega_o A (\hat{r} \cdot \hat{n})}{r^2}.
$$
</p>

The terms $$\hat{r}, \hat{n}$$ and $$A$$ are simple to define in this case. 

The area is $$A = \|M\omega_1 \times M\omega_2\|$$, which is a <a href="https://en.wikipedia.org/wiki/Cross_product">standard formula.</a>

The unit position vector is $$\hat{r} = \frac{M\omega_o}{\|M\omega_o\|}$$ (the division just normalizes since $$\hat{r}$$ is a unit vector).

And finally, the normal vector is $$\hat{n} = \frac{M\omega_1 \times M\omega_2}{\|M\omega_1 \times M\omega_2\|}$$ (again, division for normalization).

Lets first simplify the dot product $$\hat{r} \cdot \hat{n}$$ by plugging in these definitions:
<p>
$$
\hat{r} \cdot \hat{n} = \frac{M\omega_o}{\|M\omega_o\|} \frac{M\omega_1 \times M\omega_2}{\|M\omega_1 \times M\omega_2\|}
$$
</p>
Using <b>coss product under linear transforms</b> property:
<p>
$$
\hat{r} \cdot \hat{n} = \frac{M\omega_o}{\|M\omega_o\|} \frac{|M| M^{-T} \omega_o}{\|M\omega_1 \times M\omega_2\|}
$$
$$
\ \ \ \ \ \ = \frac{|M| M\omega_o M^{-T} \omega_o}{\|M\omega_o\| \|M\omega_1 \times M\omega_2\|}
$$
</p>
Using the fact that $$M\omega_o = \omega_o^T M^T$$:
<p>
$$
\ \ \ \ \ \ = \frac{|M| \omega_o^{T}{\color{red}M^T M^{-T}} \omega_o}{\|M\omega_o\| \|M\omega_1 \times M\omega_2\|}
$$
$$
\ \ \ \ \ \ = \frac{|M| {\color{red}\omega_o^{T} \omega_o}}{\|M\omega_o\| \|M\omega_1 \times M\omega_2\|}
$$
$$
\Longrightarrow \hat{r} \cdot \hat{n} = \frac{|M|}{\|M\omega_o\| \|M\omega_1 \times M\omega_2\|}
$$
</p>

Finally, substitue into and simplify the expression for $$\partial\omega$$:
<p>
$$
\partial\omega = \frac{\partial\omega_o A (\hat{r} \cdot \hat{n})}{r^2}
$$
$$
\frac{\partial\omega}{\partial\omega_o} = \frac{A (\hat{r} \cdot \hat{n})}{r^2}
$$
$$
\Longrightarrow \frac{\partial\omega}{\partial\omega_o} = \frac{ {\color{red}\|M\omega_1 \times M\omega_2\|} }{\|M\omega_o\|^2} \frac{|M|}{\|M\omega_o\| {\color{red} \|M\omega_1 \times M\omega_2\|} }
$$
$$
\boxed{ \Longrightarrow \frac{\partial\omega}{\partial\omega_o} = \frac{|M|}{\|M\omega_o\|^3}. }
$$
</p>

This is what we are looking for! :smile: