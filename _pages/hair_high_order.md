---
layout: page
title: Accelerating Hair Rendering by Learning High-Order Scattered Radiance
permalink: /hair_high_order.html
authors: Aakash KT<sup>1, 2</sup>, Adrian Jarabo<sup>1</sup>, Carlos Aliaga<sup>1</sup>, Matt Jen-Yuan Chiang<sup>1</sup>, <br> Olivier Maury<sup>1</sup>, Christophe Hery<sup>1</sup>, P. J. Narayanan<sup>2</sup>, Giljoo Nam<sup>1</sup>
affiliation: <sup>1</sup>Meta Reality Labs Research <br> <sup>2</sup>CVIT, International Institute of Information Technology, Hyderabad (IIIT-H)
conference: Eurographics Symposium on Rendering (EGSR), 2023 <br> Computer Graphics Forum (CGF) Vol 42, Number 4

---



<hr>
<img src="/assets/img/egsr2023_teaser.png" style="width:100% ; height: auto">

<h3><b>Abstract</b></h3>
<p>
Efficiently and accurately rendering  hair accounting for multiple scattering is  a challenging  open problem. Path tracing in hair takes long to converge while other techniques are  either too approximate while still being computationally expensive or make assumptions about the scene. We present a technique to infer the higher order scattering in hair in constant time within the path tracing framework, while achieving better computational efficiency. Our method makes no assumptions about the scene and provides control over the  renderer's bias & speedup. We achieve this by training a small multilayer perceptron (MLP) to learn the higher-order radiance online, while rendering progresses. We describe how to robustly train this network and thoroughly analyze our resulting renderer's characteristics. We evaluate our method on various hairstyles and lighting conditions. We also compare our method against a recent learning based & a traditional real-time hair rendering method and demonstrate better quantitative & qualitative results. Our method achieves a significant improvement in speed with respect to path tracing, achieving a run-time reduction of 40% - 70% while only introducing a small amount of bias. 
</p>
<span>
    <a target="_blank" href="http://cvit.iiit.ac.in/images/ConferencePapers/2023/Hair_Path_Tracing_Acceleration.pdf">[Author's Version PDF]</a>
    <a target="_blank" href="https://diglib.eg.org/handle/10.1111/cgf14895">[Publisher's Version PDF]</a> 
    <a target="_blank" href="https://github.com/facebookresearch/HairMSNN">[Code]</a>
    <a target="_blank" href="https://iiitaphyd-my.sharepoint.com/:b:/g/personal/aakash_kt_research_iiit_ac_in/EWr6HZmMUjlKirzrBvrk1woBCWgrk9Qw6PAJcqrl2TaKaQ?e=6Cgr8k">[Slides]</a>
</span>

<hr>
<br>
<h3><b>Interactive Results</b></h3>
Each hair style is shown with two $$\beta$$ values for our method and compared to path tracing, for <b>equal spp</b>. Both $$\beta$$ values are choosen to be approximately near peak efficiency, obtained by analyzing the efficiency graphs shown below.
<br><br>
<b>Click on the diamond to interact.</b>

<br>

<h5>Messy White Hair (Indoor HDR)</h5>
<hr>
$$\beta=13$$
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 2.6 sec</div>
                <img src="https://drive.google.com/uc?id=1gmHyUXKQjzPtjiK-7t49V5R5T7YYoWo_" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 2.4 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1YMVHZgOwhq6AHCXbex58qETVtBNUmBOk" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">10 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 16.4 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1IFoFoND23N0mPVgv-gPJJgkQY73lgxUo" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 22.8 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=14W92LG3OfMvvyeQtIB15QcrLkR20Sr5R" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">100 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 154.5 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1nbrvJ1Mip-FhXNs3EWnRJx4gXnp_9oqV" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 227.6 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1DXngtO78NbMUsrcVBZSNG3NB4uWdjrsG" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">1000 samples per pixel</div>
        </div>
    </div>
</div>

$$\beta=5$$
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 2.0 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1KQxhX4b2spXe8j07B06djtZRUuoXi9Zp" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 2.4 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1YMVHZgOwhq6AHCXbex58qETVtBNUmBOk" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">10 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 10.1 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=14gUf9-rz_FFPWKWprVd9t_0CAEIWj3IN" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 22.8 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=14W92LG3OfMvvyeQtIB15QcrLkR20Sr5R" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">100 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 92.5 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1mMwIEe47guZxmbtChf_p79ocoYaztFWx" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 227.6 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1DXngtO78NbMUsrcVBZSNG3NB4uWdjrsG" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">1000 samples per pixel</div>
        </div>
    </div>
</div>

<h5>Messy Blond Hair (Indoor HDR)</h5>
<hr>
$$\beta=5$$
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 1.7 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=17qxKkQ40og9b_SsxPa9fPHfnciNnUYIG" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 1.3 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=16kw1SFHbs2e9hjjfwmWvxouasjvgmq0V" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">10 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 8.2 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=143yLFR6kziN7995DVAfqe-Ih0in8jw4u" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 11.9 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1AhDLM-qvaPohXBc8YoQsAdDIKIGZv5AJ" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">100 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 73.0 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1sRfK1xVMpSd7piWMu-zHls4KTF-DASAF" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 119.5 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1GYbBKTH65r8weVmP3k1_rSSzls5RQQNS" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">1000 samples per pixel</div>
        </div>
    </div>
</div>

$$\beta=1$$
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 1.4 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=10xIxwy74reWBEskyEzoDe8vsUe30ghVc" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 1.3 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=16kw1SFHbs2e9hjjfwmWvxouasjvgmq0V" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">10 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 4.9 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1g9uKy5KC-L9yTjHkEyaahHmio8CjvkSS" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 11.9 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1AhDLM-qvaPohXBc8YoQsAdDIKIGZv5AJ" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">100 samples per pixel</div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours, 40.2 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1f6wpjKJrTZr7geJK0UdK5r000rFKdHUP" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Path Tracing, 119.5 sec</div>
                <img src="https://drive.google.com/uc?export=view&id=1GYbBKTH65r8weVmP3k1_rSSzls5RQQNS" alt="Path Tracing">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
            <!-- All global captions if exist can go on the div bellow -->
            <div class="caption">1000 samples per pixel</div>
        </div>
    </div>
</div>

<hr>
<h3><b>Efficiency Graphs</b></h3>
<br>
<img src="/assets/img/egsr2023_efficiency_graph.png" style="width:100% ; height: auto">

<hr>
<br>
<h3><b>Comparisons</b></h3>
Comparisons with previous methods: NRC, NRC++ & Dual scattering for 5000spp. For details, please see the paper.

<h5>Curly Blond Hair (Indoor HDR)</h5>
<hr>
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1Ziq5cOVp3EXK7cuJoHN0FLHup6dWIIGG" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">NRC</div>
                <img src="https://drive.google.com/uc?export=view&id=195xQMGi1M86fjFrWhIyLUfhymfLTrzFv" alt="NRC">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1Ziq5cOVp3EXK7cuJoHN0FLHup6dWIIGG" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">NRC++</div>
                <img src="https://drive.google.com/uc?export=view&id=1A73HJOvtoY-Y4u7eS5DJ3c4kRp9k1Ona" alt="NRC++">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1Ziq5cOVp3EXK7cuJoHN0FLHup6dWIIGG" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Dual Scattering</div>
                <img src="https://drive.google.com/uc?export=view&id=17BjdkcoApkFbHRz8jnPceCzroiVUgkqc" alt="Dual Scattering">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
</div>

<h5>Curly Blond Hair (Outdoor HDR)</h5>
<hr>
<div class="row">
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1d9Mly9VpYyH4QUxczc6gnOCzsmecY2Dc" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">NRC</div>
                <img src="https://drive.google.com/uc?export=view&id=1n-gnY1TadJmTs7Fomk5eTBHLOGVQyNcZ" alt="NRC">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1d9Mly9VpYyH4QUxczc6gnOCzsmecY2Dc" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">NRC++</div>
                <img src="https://drive.google.com/uc?export=view&id=1mZYApAobJ3K26ET08MH3dWfnpKClDMtx" alt="NRC++">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
    <div class="col-sm-4">
        <div class="comparison-slider-wrapper">
            <!-- Comparison Slider - this div contain the slider with the individual images captions -->
            <div class="comparison-slider">
                <div class="overlay">Ours (beta=1)</div>
                <img src="https://drive.google.com/uc?export=view&id=1d9Mly9VpYyH4QUxczc6gnOCzsmecY2Dc" alt="Ours">
                <!-- Div containing the image layed out on top from the left -->
                <div class="resize">
                    <div class="overlay">Dual Scattering</div>
                <img src="https://drive.google.com/uc?export=view&id=1JEqsaskEXLyqXGrrtBy5LesD16XDPcdQ" alt="Dual Scattering">
                </div>
                <!-- Divider where user will interact with the slider -->
                <div class="divider"></div>
            </div>
        </div>
    </div>
</div>

<hr>
<br>
<div class="row">
    <div class="col-sm-12" align="center">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/DrW88l6kMdg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </div>
</div>