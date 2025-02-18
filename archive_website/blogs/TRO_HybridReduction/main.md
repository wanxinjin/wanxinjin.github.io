---
layout: clean
permalink: /td_hybridreduction/
title: manipulation
nav: false
navbar_fixed: false
bibliography: blogs/TRO_HybridReduction/mybib.bib
---






<center>
  <h1>
  <strong>Task-Driven Hybrid Model Reduction for Dexterous Manipulation</strong>
</h1>
</center>

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

<center>
<h5>
<a href="https://wanxinjin.github.io/" target="_blank">Wanxin Jin</a>
&nbsp;
and 
&nbsp;
<a href="https://dair.seas.upenn.edu/" target="_blank">Michael Posa</a>
</h5>
The GRASP Laboratory, University of Pennsylvania
</center>



<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

<center>
<h5>
<a href="https://github.com/wanxinjin/Task-Driven-Hybrid-Reduction" target="_blank">
<img src="../blogs/TRO_HybridReduction/figures/github.png" width="35" target="_blank">&nbsp;
Code (Github)</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="https://arxiv.org/abs/2211.16657" target="_blank">
<img src="../blogs/TRO_HybridReduction/figures/arxiv.png" width="60" target="_blank"> &nbsp;
Paper (Arxiv)</a>
</h5>
</center>

<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>





<p style="color:#828282;">
<b>Abstract</b>: Many critical tasks in robotics, like dexterous manipulation, are inherently contact-rich; the hybrid nature of making and breaking contact creates significant challenges for model representation and control. Specifically, for a task like in-hand manipulation, the combinatoric complexity in representing and choosing potential contact locations and sequences between robot and object, where there are thousands of potential hybrid modes, is not generally tractable. In this paper, we are inspired by the key observation that far fewer modes are actually necessary to accomplish many tasks. Building on our prior work in learning hybrid models, represented as linear complementarity systems, we find a reduced-order hybrid model requiring only a limited number of task-relevant modes. This simplified representation, in combination with a model predictive controller, enables real-time control and is sufficient for achieving high performance on tasks like multi-finger dexterous manipulation. We show that reduced-order model learning with on-policy data provably bounds closed-loop performance, leading to a simple iterative method to improve the reduced-order model and controller. We demonstrate the proposed method first on synthetic hybrid systems, reducing the mode count by multiple orders of magnitude while achieving task performance loss of less than 5%. Second, in simulation environment, we apply the proposed method to solve three-finger robotic hand manipulation for object reorientation. With no prior knowledge, we achieve state-of-the-art closed-loop performance in less than five minutes of online learning.
</p>

<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

## **Overview Video**
<p style="margin-bottom:0.8cm; margin-left: 1.5cm"> </p>

<center>
<iframe width="840.0" height="482" src="https://www.youtube.com/embed/OvhTOQoagTM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>





<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>


## **Our Method**

<p style="margin-bottom:0.8cm; margin-left: 1.5cm"> </p>


<div style="background-color:rgba(0, 0, 0, 0.0470588);  vertical-align: middle; padding:10px; padding-left: 20px; padding-right: 20px;">
<center>
  <img src="../blogs/TRO_HybridReduction/figures/algorithm.png"  width="800"  align="centering" hspace="0" vspace=0 />
</center>
<p align = "center">
Fig. 1: Components of task-driven hybrid model reduction algorithm. There are three main components: learning reduced-order LCS, Trustregion
LCS model predictive controller, and Rollout Buffer, each of which is detailed below.
</p>
</div>






<p style="margin-bottom:0.8cm; margin-left: 1.5cm"> </p>

##### **Learning Reduced-Order Linear Complementarity System (LCS)**

Linear Complementarity System (LCS), denoted as
<center>
  <img src="../blogs/TRO_HybridReduction/figures/lcs.png"  width="320"  align="centering" hspace="0" vspace=0 />
</center>
<p style="margin-bottom:0.2cm; margin-left: 1.5cm"> </p>
is a compact representation of a piecewise affine system. Here,   zero or non-zero of each entry of $$ \boldsymbol{\lambda} $$ determine the linear affine dynamics in each mode. The maximum number of potential modes is $$\color{red}2^{\dim \boldsymbol{\lambda}}$$. 
For a reduced-order LCS, one can
explicitly restrict the number of potential modes in LCS by
setting $$\color{red}\dim \boldsymbol{\lambda}$$.

The learning of a LCS  i.e., identifying all  matrices $$(A,B,C,\boldsymbol{d},D,E,F,\boldsymbol{c})$$, is based on our prior work <d-cite key="jin2022learning"></d-cite>, which enables efficiently learning a piecewise affine model with up
to thousands of  modes and effectively handles the stiff
dynamics that arises from contact. 





<p style="margin-bottom:0.8cm; margin-left: 1.5cm"> </p>


##### **Trust-Region LCS-based Model Predictive Controller**


We developed the LCS-based MPC controller, as part of our learning algorithm for on-policy data
collection and closed-loop control. The MPC controller is built on the direct method of trajectory optimization <d-cite key="posa2014direct"></d-cite>. This  MPC controller can run real-time with frequency up to 50Hz on robotic manipulation system.





<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>


## **Model Reduction on Synthetic Hybrid Control Systems**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>


The task is to stabilize a piecewise affine (full-order) system, with a  quadratic cost function. The full-order dynamics, denoted as $$\boldsymbol{f}()$$, has more than 100 modes. The reduced-order LCS to be learned, denoted as  $$\color{red}\boldsymbol{g}()$$, has $$\color{red}\dim \boldsymbol{\lambda}=2$$ (i.e., max. 4 modes). Below is the phase plot of the full-order dynamics $$\boldsymbol{f}$$ with full-order MPC controller $$\boldsymbol{u}=\boldsymbol{f}$$-MPC$$(\boldsymbol{x})$$, versus with reduced-order MPC controller $$\boldsymbol{u}=\color{red}\boldsymbol{g}$$-MPC$$(\boldsymbol{x})$$. Different colors indicate different hybrid modes. 

<center>
  <img src="../blogs/TRO_HybridReduction/figures/lcs_progressgif.gif"  width="850"  align="centering" hspace="0" vspace=0 />
</center>
<sub>
  Left:  phase plot of $$\boldsymbol{f}$$ with full-order MPC  controller, 43 modes (colors) are shown. Middle:  phase plot of $$\boldsymbol{f}$$ with reduced-order MPC  controller at different learning iterations, 4 modes are shown. Right:  Overlap comparison between the two phase plots. 
</sub>











<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

The task is to stabilize a full-order LCS, with a  quadratic cost function. The given full-order LCS,  denoted as $$\boldsymbol{f}()$$, has $$\dim \boldsymbol{\Lambda}=12$$ (>1000 modes). The reduced-order LCS to be learned, denoted as  $$\color{red}\boldsymbol{g}()$$, has $$\color{red}\dim \boldsymbol{\lambda}=3$$ (max. 8 modes). 
Below is the policy rollout on the full-order LCS $$\boldsymbol{f}$$ with the full-order MPC controller, versus with the learned reduced-order MPC controller. Different colors indicate different hybrid modes. 


<center>
  <img src="../blogs/TRO_HybridReduction/figures/lcs_rollout.gif"  width="600"  align="centering" hspace="0" vspace=0 />
</center>
  <sub>
  Upper: the mode activation in each dimension of $$\boldsymbol{\Lambda}$$ in $$\boldsymbol{f}()$$ and in each dimension $$\boldsymbol{\lambda}$$ in $$\color{red}\boldsymbol{g}()$$ . Black indicate $$>0$$ and blank indicate $$=0$$. Lower: closed-loop state trajectory of  $$\boldsymbol{f}$$. Different colors indicate different modes.
</sub>





<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

---

<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>


## **Three-Finger Robotic Hand Manipulation**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>


### **Manipulation Task 1: Cube Turning**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

The task is to let three robotic fingers turn the cube to any random orientation, sampled from $$\alpha^{\text{goal}}\sim U[−1.5, 1.5]$$  (rad). __No prior knowledge of the system dynamics model and no prior knowledge of the object is available__. The system is estimated to have thousands of potential modes. 




##### **Learning without prior knowledge in 5 mins**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>
With no prior knowledge about the system, our method learns a task-driven reduced-order LCS (with $$\color{red}\dim \boldsymbol{\lambda}=5$$) to solve the cube turning task with less than 5 mins of real data. The video here is the real-time running of the learned reduced-order MPC controller on the system. 

<center>
  <video width="600"  controls>
    <source src="../blogs/TRO_HybridReduction/figures/turning_webpage.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>
</center>


<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

##### **Empirical correspondence between mode activation of LCS and physical contact interaction**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

An example rollout of running the learned reduced-order MPC controller on the three-finger manipulation system (0.1 x speed).  Left: Mode activation in the learned reduced-order LCS (upper) and cube angle trajectory (lower)
Right: physical contact interaction in the three-finger robotic hand manipulation
<center>
  <video src="../blogs/TRO_HybridReduction/figures/turning_mode1_com_crop.mov" autoplay loop muted width="650" ></video>
  <!-- <video src="figures/turning_mode2_com_crop.mov" autoplay loop muted width="650"  ></video> -->
</center>


<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

##### **Robustness of the learned reduced-order MPC controller**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

We apply random (uniform distribution) external disturbance torque to the cube at each time step during the MPC policy rollout. Below, we vary the disturbance magnitude. Left: disturbance magnitude is 100 times the cube inertia,
middle: disturbance magnitude is 1000 times the cube inertia, and 
right: disturbance magnitude is 5000 times the cube inertia.

<video src="../blogs/TRO_HybridReduction/figures/turning_disturb_com_crop.mov" autoplay loop muted width="850" >
</video>


<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

### **Manipulation Task 2: Cube Moving**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

 The task is to let three fingers move the cube to a random target pose $$(\boldsymbol{p}^{\text{goal}}, \alpha^{\text{goal}})$$, where the target position and angle are sampled from   $$\boldsymbol{p}^{\text{goal}}\sim U[−0.06, 0.06]$$  (m) and $$\alpha^{\text{goal}}\sim U[−1.5, 1.5]$$  (rad), respectively. __No prior knowledge of the system dynamics model and no prior knowledge of the object is available__. The system is estimated to have thousands of potential modes. 



##### **Learning with no prior knowledge within 5 minutes**

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>
With no prior knowledge, our method learns a reduced-order LCS (with $$\color{red}\dim \boldsymbol{\lambda}=5$$) to solve the task with less than 5 mins of real data. The video here is the real-time running of the learned reduced-order MPC controller on the system.

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>
<center>
  <video src="../blogs/TRO_HybridReduction/figures/moving_webpage.mp4" controls width="600" >
</video>
</center>

<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

##### **Different contact strategies for different targets**

The following videos show different contact strategies generated by the same learned reduced-order LCS in its MPC rollout given different
targets.  Notably, as shown here, for different targets, the learned reduced-order LCS can produce different contact strategies between fingertips and the cube, such as separate, slip, and stick, and different decisions about which fingertip touches which face of the cube.

<p style="margin-bottom:0.5cm; margin-left: 1.5cm"> </p>

<center>
  <video autoplay loop muted width="410">
    <source src="../blogs/TRO_HybridReduction/figures/moving_strategy1_com.mp4" type="video/mp4">
</video>
<video autoplay loop muted width="410">
    <source src="../blogs/TRO_HybridReduction/figures/moving_strategy2_com.mp4" type="video/mp4">
</video>
<video autoplay loop muted width="410">
    <source src="../blogs/TRO_HybridReduction/figures/moving_strategy3_com.mp4" type="video/mp4">
</video>
<video autoplay loop muted width="410">
    <source src="../blogs/TRO_HybridReduction/figures/moving_strategy4_com.mp4" type="video/mp4">
</video>
</center>
<center>
  <sub>
  The bottom left window shows the mode activation of the LCS, and the right window shows the zoom-in details of contact interaction (0.1 x speed).
</sub>
</center>



<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>

##### **Robustness of the learned reduced-order MPC controller**

<p style="margin-bottom:0.4cm; margin-left: 1.5cm"> </p>

We apply random (uniform distribution) external disturbance forces to the cube at each time step during the reduced-order MPC rollout. Below, we vary the disturbance magnitude. Left: the disturbance magnitude is 0.4 times the cube mass, middle:  the disturbance magnitude is 0.7 times the cube mass, and right:  the disturbance magnitude is 1.0 times the cube mass,

<video src="../blogs/TRO_HybridReduction/figures/moving_disturb_com_crop.mov" autoplay loop muted width="850" >
</video>

<p style="margin-bottom:2.0cm; margin-left: 1.5cm"> </p>

##### **Final remarks: for more technical details and experiments, please check out our [paper](https://github.com/wanxinjin/Task-Driven-Hybrid-Reduction) and [code](https://github.com/wanxinjin/Task-Driven-Hybrid-Reduction).**

<p style="margin-bottom:2.0cm; margin-left: 1.5cm"> </p>
---
<p style="margin-bottom:1.0cm; margin-left: 1.5cm"> </p>


## **Acknowledgements**
<p style="margin-bottom:0.4cm; margin-left: 1.5cm"> </p>

Toyota Research Institute provided funds to support this
work.

<center>
  <img src="../blogs/TRO_HybridReduction/figures/tri_logo.png"  width="400"  align="centering" hspace="0" vspace=0 />
</center>
