---
layout: default
title: videos
permalink: /videos/
description: 
nav: false
horizontal: true
---

#### Table of Contents

- [Learning from Human Directional Corrections](#LFDC)
- [Safe Pontryagin Differentiable Programming](#SafePDP)
- [Learning from Sparse Demonstrations](#LFSD)
- [Pontryagin Differentiable Programming: An End-to-End Learning and Control Framework](#PDP)





<a name="LFDC"></a> 

<br /> 
<br /> 

#### [Learning from Human Directional Corrections](https://arxiv.org/abs/2011.15014){:target="_blank"}

<p style="margin-bottom:0.8cm; margin-left: 0.5cm"> </p>

<img src="{{ '/collections/figures/lfdc.png' | relative_url }}" alt="Kitten" align="left" title="SafePDP" width="350" hspace=20  />
This paper proposes an approach which enables a robot to learn a control
objective function incrementally from human's directional corrections. Existing
methods learn from human's magnitude corrections and require a human to
carefully choose correction magnitudes, which otherwise can easily lead to
over-correction and learning inefficiency. The proposed method only requires
human's directional corrections --- corrections that only indicate the
direction of a control change without indicating its magnitude --- applied at
some time instances during the robot's motion. We only assume that each of
human's corrections, regardless of its magnitude, points in a direction that
improves the robot's current motion relative to an implicit control objective
function. Thus, human's valid corrections always account for half of the
correction space. The proposed method uses the direction of a correction to
update the estimate of the objective function based on a cutting plane
technique. We have established the theoretical results to show that this
process guarantees the convergence of the learned objective function to the
implicit one. The proposed approach has been examined by numerical examples, a
user study on two human-robot games, and a real-world quadrotor experiment. The
results confirm the convergence of the approach and show that the approach is
significantly more effective (higher success rate), efficient/effortless (less
human corrections needed), and accessible (fewer early wasted trials) than the
state-of-the-art robot interactive learning schemes.


<!-- <div class="row">
    <div class="col-sm mt-2 mt-md-0">
        <iframe width="360" height="202" src="https://www.youtube.com/embed/sXXwBNZ9oP4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
            Quadrotor learns from human's directional corrections in Environment 1.
        </div>
    </div>
    <div class="col-sm mt-2 mt-md-0">
        <iframe width="360" height="202" src="https://www.youtube.com/embed/6fP6uIAWxgs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
          <div class="caption">
            Quadrotor learns from human's directional corrections in Environment 2.
        </div>
    </div>
</div>
 -->


<div class="row">
      <div class="col-sm mt-3 mt-md-0">
    </div>
      <div class="col-sm mt-3 mt-md-0">
<iframe width="700" height="394" src="https://www.youtube.com/embed/6XavhnE2q1s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
A drone learns from human's directional corrections.
      </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
    </div>
</div>







Codes (in Python): [https://github.com/wanxinjin/Learning-from-Directional-Corrections](https://github.com/wanxinjin/Learning-from-Directional-Corrections){:target="_blank"}<br />
Paper: [https://arxiv.org/abs/2011.15014](https://arxiv.org/abs/2011.15014){:target="_blank"}<br />

<br /> 

----


<a name="SafePDP"></a> 

<br /> 
<br /> 


#### [Safe Pontryagin Differentiable Programming](https://arxiv.org/abs/2105.14937){:target="_blank"}

<p style="margin-bottom:0.8cm; margin-left: 0.5cm"> </p>

<img src="{{ '/collections/figures/SafePDP.png' | relative_url }}" alt="Kitten" align="left" title="SafePDP" width="250" hspace=20  />


We propose a Safe Pontryagin Differentiable Programming (Safe PDP) methodology, which establishes a theoretical and algorithmic framework to solve a broad class of safety-critical learning and control tasks -- problems that require the guarantee of safety constraint satisfaction at any stage of the learning and control progress. In the spirit of interior-point methods, Safe PDP handles different types of system constraints on states and inputs by incorporating them into the cost or loss through barrier functions. We prove three fundamentals of the proposed Safe PDP: first, both the solution and its gradient in the backward pass can be approximated by solving their more efficient unconstrained counterparts; second, the approximation for both the solution and its gradient can be controlled for arbitrary accuracy by a barrier parameter; and third, importantly, all intermediate results throughout the approximation and optimization strictly respect the constraints, thus guaranteeing safety throughout the entire learning and control process. We demonstrate the capabilities of Safe PDP in solving various safety-critical tasks, including safe policy optimization, safe motion planning, and learning MPCs from demonstrations, on different challenging systems such as 6-DoF maneuvering quadrotor and 6-DoF rocket powered landing.


<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        <iframe width="360" height="202" src="https://www.youtube.com/embed/sC81qc2ip8U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
            Safe PDP for safe neural policy optimization.
        </div>
    </div>
    <div class="col-sm mt-2 mt-md-0">
          <iframe width="360" height="202" src="https://www.youtube.com/embed/vZVxgo30mDs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
          <div class="caption">
            Safe PDP for safe motion planning.
        </div>
    </div>
</div>


<div class="row">
      <div class="col-sm mt-3 mt-md-0">
    </div>
      <div class="col-sm mt-3 mt-md-0">
        <iframe width="360" height="202" src="https://www.youtube.com/embed/OBiLYYlWi98" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
          Safe PDP for learning MPCs (i.e., jointly learning dynamics,  constraints, and control cost) from demonstrations.
      </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
    </div>
</div>



Safe-PDP Package (in Python): [https://github.com/wanxinjin/Safe-PDP](https://github.com/wanxinjin/Safe-PDP){:target="_blank"}<br />
Safe-PDP Paper: [https://arxiv.org/abs/2105.14937](https://arxiv.org/abs/2105.14937){:target="_blank"}<br />

<br /> 



----

<a name="LFSD"></a> 

<br /> 
<br /> 


#### [Learning from Sparse Demonstrations](https://arxiv.org/abs/2008.02159){:target="_blank"}



<p style="margin-bottom:0.8cm; margin-left: 0.5cm"> </p>




<img src="{{ '/collections/figures/lfsd_viode_pic.png' | relative_url }}" alt="Kitten" align="left" title="SafePDP" width="350" hspace=20  />

 This paper develops the Continuous Pontryagin Differentiable Programming
(Continuous PDP) method that enables a robot to learn a control utility
function from a few number of sparsely demonstrated keyframes. The keyframes
are few desired sequential outputs that a robot is wanted to follow at certain
time instances. The duration of the keyframes may be different from that of the
robot actual execution. The method jointly searches for a robot control utility
function and a time-warping function such that the robot motion sequentially
follows the given keyframes with minimal discrepancy loss. Continuous PDP
minimizes the discrepancy loss using projected gradient descent, by efficiently
solving the gradient of robot motion with respect to the unknown parameters.
The method is first evaluated on a simulated two-link robot arm, and then
applied to a 6-DoF maneuvering quadrotor to learn a utility function from
keyframes for its motion planning in un-modeled environments with obstacles.
The results show the efficiency of the method, its ability to handle time
misalignment between keyframes and robot execution, and the generalization of
the learned utility function into unseen motion conditions.


<div class="row">
      <div class="col-sm mt-3 mt-md-0">
    </div>
      <div class="col-sm mt-3 mt-md-0">
<iframe width="700" height="394" src="https://www.youtube.com/embed/BYAsqMxW5Z4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
A drone learns from human's directional corrections.
      </div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
    </div>
</div>

<p style="margin-bottom:0.4cm; margin-left: 0.5cm"> </p>




<div class="row">
    <div class="col-sm mt-2 mt-md-0">
<iframe width="360" height="202" src="https://www.youtube.com/embed/yHBjVdPXmEw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
            Robot arm learns from sparse demostrations.
        </div>
    </div>
    <div class="col-sm mt-2 mt-md-0">
<iframe  width="360" height="202" src="https://www.youtube.com/embed/42AVnALrr_M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
          <div class="caption">
            Quadrotor learns from sparse demostrations.
        </div>
    </div>
</div>







Codes (in Python): [https://github.com/wanxinjin/Learning-from-Sparse-Demonstrations](https://github.com/wanxinjin/Learning-from-Sparse-Demonstrations){:target="_blank"}<br />
Paper: [https://arxiv.org/abs/2008.02159](https://arxiv.org/abs/2008.02159){:target="_blank"}<br />

<br /> 

---



<a name="PDP"></a> 

<br /> 
<br /> 


#### [Pontryagin Differentiable Programming: An End-to-End Learning and Control Framework](https://papers.nips.cc/paper/2020/file/5a7b238ba0f6502e5d6be14424b20ded-Paper.pdf){:target="_blank"}

<p style="margin-bottom:0.8cm; margin-left: 0.5cm"> </p>




<img src="{{ '/collections/figures/PDP.png' | relative_url }}" alt="Kitten" align="left" title="SafePDP" width="250" hspace=20  />

This paper develops a Pontryagin Differentiable Programming (PDP) methodology, which establishes a unified framework to solve a broad class of learning and control tasks. The PDP distinguishes from existing methods by two novel techniques: first, we differentiate through Pontryagin’s Maximum Principle, and this allows to obtain the analytical derivative of a trajectory with respect to tunable parameters within an optimal control system, enabling end-to-end learning of dynamics, policies, or/and control objective functions; and second, we propose an auxiliary control system in the backward pass of the PDP framework, and the output of this auxiliary control system is the analytical derivative of the original system’s trajectory with respect to the parameters, which can be iteratively solved using standard control tools. We investigate three learning modes of the PDP: inverse reinforcement learning, system identification, and control/planning. We demonstrate the capability of the PDP in each learning mode on different high-dimensional systems, including multi-link robot arm, 6-DoF maneuvering quadrotor, and 6-DoF rocket powered landing.










<div class="row">
    <div class="col-sm mt-2 mt-md-0">
<iframe width="360" height="202"  src="https://www.youtube.com/embed/5Jsu772Sqcg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
            PDP for optimal control.
        </div>
    </div>

        <div class="col-sm mt-2 mt-md-0">
<iframe width="360" height="202"  src="https://www.youtube.com/embed/awVNiCIJCfs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        <div class="caption">
            PDP for inverse reinforcement learning.
        </div>
    </div>

</div>



PDP Package (in Python): [https://github.com/wanxinjin/Pontryagin-Differentiable-Programming](https://github.com/wanxinjin/Pontryagin-Differentiable-Programming){:target="_blank"}<br />
PDP Paper: [https://papers.nips.cc/paper/2020/hash/5a7b238ba0f6502e5d6be14424b20ded-Abstract.html](https://papers.nips.cc/paper/2020/file/5a7b238ba0f6502e5d6be14424b20ded-Paper.pdf){:target="_blank"}<br />

<br /> 

---

<br /> 

<div style="text-align: right"> <a href="#top">Back to top</a> </div>