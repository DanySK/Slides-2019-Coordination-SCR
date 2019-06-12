+++
title = "Self-organising Coordination Regions: a Pattern for Edge Computing by Danilo Pianini"
outputs = ["Reveal"]
+++

<script src="prism.js"></script>
<link rel="stylesheet" href="prism.css">

## [Self-organising Coordination Regions](https://danysk.github.io/Slides-2019-PSLab-SGCG/)
### [a Pattern for Edge Computing](https://danysk.github.io/Slides-2019-PSLab-SGCG/)

Roberto Casadei, __Danilo Pianini__,

Mirko Viroli, Antonio Natali

---

{{< slide background-image="assets/aerial-shot.jpg" >}}

---

{{< slide background-image="assets/aerial-shot-bg.jpg" >}}

## Motivating case studies

[Metropolitan collaborative surveillance](https://doi.org/10.1002/spe.2586)

* {{% fragment %}}Discovery and integration of smart cameras{{% /fragment %}}
* {{% fragment %}}Multiple video streams to be fused and synchronized{{% /fragment %}}
* {{% fragment %}}Object detection, tracking, analysis{{% /fragment %}}
* {{% fragment %}}Processing can be on cloud, on fog, on edge{{% /fragment %}}

See paper by Dautov et al.

---

{{< slide background-image="assets/360gaming.jpg" >}}

---

{{< slide background-image="assets/360gaming-bg.jpg" >}}

## Motivating case studies

[360° multi-view multiplayer gaming](https://doi.org/10.1109/FMEC.2017.7946410)

* {{% fragment %}}Multi-view (see what others are seeing){{% /fragment %}}
* {{% fragment %}}Augmented or Virtual Reality: free movement{{% /fragment %}}
* {{% fragment %}}Delay intolerance{{% /fragment %}}
* {{% fragment %}}Excessive bandwidth usage{{% /fragment %}}

See paper by Bilal et al.

---

{{< slide background-image="assets/bg.png" >}}

## Problem and forces

* {{% fragment %}}**heterogeneity**: *asymmetry among device capabilities*{{% /fragment %}}
* {{% fragment %}}**locality**: *information is more valuable when is close to its source, moving it is expensive*{{% /fragment %}}
* {{% fragment %}}**hybrid coordination**: *information aggregation is required, full centralization brings unacceptable costs*{{% /fragment %}}
* {{% fragment %}}**dinamicity** *environment, network, and system structure changes at runtime*{{% /fragment %}}

---

{{< slide background-image="assets/bg.png" >}}

## Well Known in literature?

* [Decentralised service orchestration](https://doi.org/10.1002/cpe.3655), Jaradat et al.
* [TCMote, a WSN middleware](https://doi.org/10.1109/ICW.2005.5), Diaz et al.
* [TS-Mid, tuple-based WSN middleware](https://doi.org/10.1109/WAINA.2008.244), Lima et al.
* [Leader-based swarm coordination](https://doi.org/10.1145/2157689.2157704), Walker et al.
* [Distributed sensing](https://doi.org/10.1007/978-3-030-00302-9_4), Casadei et al.
* [Self-stabilizing target counting](https://doi.org/10.1109/SASO.2017.10), Pianini et al.
* [Group management for target tracking](https://doi.org/10.1023/B:TELS.0000029041.37854.92), Liu et al.
* [Crowd tracking and steering](https://doi.org/10.1109/MC.2015.261), Beal et al.
* ...

---

{{< slide background-image="assets/bg.png" >}}

General solution to a commonly occurring problem

<span class="fragment" >
--> We propose a [design pattern](https://en.wikipedia.org/wiki/Software_design_pattern)
(discovered in literature)
</span>

<span class="fragment" style="color: #3ea0e4;">
**SELF-ORGANISING COORDINATION REGIONS**
</span>

---

{{< slide background-image="assets/bg.png" >}}

## Shared solution elements

<span class="fragment">
1. *Election of leaders* -- from a set of candidates
</span>

<span class="fragment">
2. *Formation of regions* -- by assigning each user to a single leader
</span>

<span class="fragment">
3. *Upstream information flow* -- from users to leaders
</span>

<span class="fragment">
4. *Downstream information flow* -- from leaders to users
</span>

---

{{< slide transition="slide-in fade-out" >}}

#### 1 of 4 -- Leader election

<img src="assets/network-1.svg" width="50%" height="50%" />

(logical) network of devices

---

{{< slide transition="fade-in fade-out" >}}

#### 1 of 4 -- Leader election

<img src="assets/network-candidates.svg" width="50%" height="50%" />

<span style="color: #f97b00;"> orange</span> devices are leader candidates

---

{{< slide transition="fade-in fade-out" >}}

#### 1 of 4 -- Leader election

<img src="assets/network-leaders.svg" width="50%" height="50%" />

<span style="color: #f90000;"> red</span> devices are elected leaders

---

{{< slide transition="fade-in fade-out" >}}

#### 2 of 4 -- Formation of regions

<img src="assets/network-regions.svg" width="50%" height="50%" />

one color per region, one leader per region

---

{{< slide transition="fade-in fade-out" >}}

#### 3 of 4 -- Upstream communication

<img src="assets/network-upstream.svg" width="50%" height="50%" />

from users to leaders

---

{{< slide transition="fade-in slide-out" >}}

#### 4 of 4 -- Downstream communication

<img src="assets/network-downstream2.svg" width="50%" height="50%" />

from leaders to users

---

{{< slide background-image="assets/bg.png" >}}

#### Implementation issues
### Leader Election


* {{% fragment %}} **Candidate selection** -- *heterogeneity of devices and network*{{% /fragment %}}
* {{% fragment %}}**Consensus strategy** -- *centralized or distributed?*{{% /fragment %}}
* {{% fragment %}}**Dinamicity and adaptivity** -- *select leaders statically, elect them once, elect them at time intervals, elect them continuously*{{% /fragment %}}

---

{{< slide background-image="assets/bg.png" >}}

#### Implementation issues
### Formation of regions and downstream

Similar issues, information flows from leader to users

* {{% fragment %}}*Gossip* -- monotonic information{{% /fragment %}}
* {{% fragment %}}*Time-replicated gossip* -- [from Coordination 2016](https://doi.org/10.1007/978-3-319-39519-7_12){{% /fragment %}}
* {{% fragment %}}*Gradient-cast* -- Distance-metric based, different gradients -> different performance{{% /fragment %}}

---

{{< slide background-image="assets/bg.png" >}}

#### Implementation issues
### Upstream: accumulation

Tougher than downstream in non star-networks

* {{% fragment %}}*Gossip* -- monotonic, requires idempotence, expensive{{% /fragment %}}
* {{% fragment %}}*Time-replicated gossip* -- tackles monotonicity and idempotence, but even more expensive{{% /fragment %}}
* {{% fragment %}}*Spanning-tree accumulation* -- Scalable but fragile{{% /fragment %}}
* {{% fragment %}}*Multi-path techniques* -- Slower convergence, higher reliability{{% /fragment %}}

---

{{< slide transition="slide-in fade-out" background-image="assets/bg.png" >}}

### Dynamics

![SCR dynamics](assets/dynamics-base.svg)

* Perturbations are unavoidable

---

{{< slide transition="fade-in fade-out" background-image="assets/bg.png" >}}

### Dynamics

![SCR dynamics](assets/dynamics-f1.svg)

* Computation results may influence future decisions

---

{{< slide transition="fade-in fade-out" background-image="assets/bg.png" >}}

### Dynamics

![SCR dynamics](assets/dynamics-f2.svg)

* Including region sizes

---

{{< slide transition="fade-in slide-out" background-image="assets/bg.png" >}}


### Dynamics

![SCR dynamics](assets/dynamics-all.svg)

* Oscillations however are to be considered

---

<!--

{{< slide background-image="assets/bg.png" >}}

{{% section %}}

### Feedback loops

* Dynamic tuning and advanced adaptation
  * e.g. load balacing by resizing regions, adapting to upstreamed data
* Feedbacks introduce further complexity
  * The system may oscillate
  * Low-pass filtering often advisable (e.g. exponential backoff)

---
{{< slide background-image="assets/bg.png" >}}

### Apply when...

* larger-than-local perspective, globality inconvenient
* Information is relevant in the proximity of its source
* Deployment is unknown or subject to changes
  * The software must be able to run on the cloud or on the edge depending on specific deployment or even runtime contingencies

---

{{< slide background-image="assets/bg.png" >}}

### Not to be used when...

* decision making can be purely local
* decision making can be centralised
  * (single leader election is possible, but often inefficient)
* Deployment is well-known, network is static

---

{{% /section %}}

-->

{{< slide background-image="assets/bg.png" >}}

#### Implementation template

```scala
class SCR extends AggregateProgram with BlockG with BlockC with BlockS {
  def main = {
        // Field of leaders, with at least grain distance
        val leader = branch(isCandidate) { S(grain) } { false }
        // Gradient from leaders based on a given distance metric
        val potential = distanceTo(leader, metric)
        // gathers local values towards leaders by aggregation
        val convergeCast = C(potential, local, aggregationFun)
        // on leaders, takes a decision based on received data
        val decision = decisionMaking(leader, convergeCast)
        // broadcast decisions and take action
        val divergeCast = G(leader, metric, decision)
        localAction(divergeCast)
    }}
```

Written in [Scala](https://www.scala-lang.org/) with the [Scafi](https://scafi.github.io) DSL

[Aggregate programming](https://doi.org/10.1109/MC.2015.261) is a natural fit for SCR

---

{{< slide background-image="assets/bg.png" >}}

#### Manifesto of aggregate computing

<span style="color: #3ea0e4;">
program the **aggregate**, not single devices
<span>

* **Computing machine** -- *aggregate of devices as a single entity, fading to actual space*
* **Elaboration process** -- *atomic manipulation of a collective data structure*
* **Networking and protocols**: *hidden under the hood*

---

{{< slide background-image="assets/bg.png" >}}

## Case study

#### Urban video streaming collection

* {{% fragment %}}Urban center (mid-sized Italian city){{% /fragment %}}
* {{% fragment %}}200 edge servers, randomized grid deployment{{% /fragment %}}
* {{% fragment %}}Dynamically selected set of edge servers as leaders (one every ~200m){{% /fragment %}}
* {{% fragment %}}*Feedback system*: the more users stream content to an edge server, the more its served area shrinks{{% /fragment %}}
* {{% fragment %}}After ten minutes, we suddenly turn off a percentage of the leaders, and see how the system reacts{{% /fragment %}}
* {{% fragment %}}The [experiment is reproducible](https://bitbucket.org/danysk/experiment-2019-coordination-dynamic-orchestration/src/master/){{% /fragment %}}

---

{{< slide background-image="assets/screen1.png" >}}

---

{{< slide background-image="assets/screen3.png" >}}

---

{{< slide background-image="assets/bg.png" >}}

### Parameters / Symbols

| Parameter | Meaning |
|----------|:------:|
| α | exponential backoff parameter. lower values, smoother output |
| fb | `on` if feedback enabled, `off` otherwise |
| ρ |  probability for a leader to shut down |
| E | expected value / statistic mean |
| σ | standard deviation |
| Σ  | sum |

---

{{< slide background-image="assets/bg.png" >}}

#### Feedback loop tuning

<img src="assets/feedbackalpha0.svg" height="400em" />

* trade-off between smoothness and reactivity

---

{{< slide background-image="assets/bg.png" >}}

#### Resilience to disruption

<img src="assets/SumResilience.svg" height="400em" />

* quick recover from large and small perturbations

---

{{< slide background-image="assets/bg.png" >}}

#### Load balancing

<img src="assets/StandardDeviationResilience.svg" height="400em" />

* cold lines have lower variance --> better load sharing

---

{{< slide background-image="assets/bg.png" >}}

#### Conclusion

* General solution to a commonly occurring problem
  * --> [New design pattern](https://en.wikipedia.org/wiki/Software_design_pattern)!

1. Elect leaders
2. Set up influence areas (*regions*)
3. Build downstream communication
4. Build upstream communication

* {{% fragment %}}Hybrid coordination: between centralized and decentralized{{% /fragment %}}
* {{% fragment %}}One possible implementation provided and evaluated in the aggregate computing framework{{% /fragment %}}
* {{% fragment %}}Particularly relevant for mixed edge/cloud systems {{% /fragment %}}
