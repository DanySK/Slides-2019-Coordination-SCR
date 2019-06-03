+++
title = "My presentation"
outputs = ["Reveal"]
+++

## [Self-organising Coordination Regions](https://danysk.github.io/Slides-2019-PSLab-SGCG/)
### [a Pattern for Edge Computing](https://danysk.github.io/Slides-2019-PSLab-SGCG/)

Roberto Casadei, __Danilo Pianini__,

Mirko Viroli, Antonio Natali

---

{{< slide background-image="assets/aerial-shot-bg.jpg" >}}

## Motivating case studies

[Metropolitan collaborative surveillance](https://doi.org/10.1002/spe.2586)

* Discovery and integration of smart cameras
* Multiple video streams to be fused and synchronized
* Object detection, tracking, analysis
* Processing can be on cloud, on fog, on edge

See paper by Dautov et al.

---

{{< slide background-image="assets/360gaming-bg.jpg" >}}

## Motivating case studies

[360° view multiplayer gaming](https://doi.org/10.1109/FMEC.2017.7946410)

* Multi-view (see what others are seeing)
* Augmented or Virtual Reality: free movement
* Delay intolerance
* Excessive bandwidth usage

---

{{< slide background-image="assets/bg.png" >}}

## Problem and forces

* **heterogeneity**: *asymmetry among device capabilities*
* **locality**: *information is more valuable when is close to its source, moving it is expensive*
* **hybrid coordination**: *information aggregation is required, full centralization brings unacceptable costs*
* **dinamicity** *environment, network, and system structure changes at runtime*

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

## Shared solution elements

1. *Election of leaders* -- from a set of candidates
2. *Formation of regions* -- by assigning each user to a single leader
3. *Upstream information flow* -- from users to leaders
4. *Downstream information flow* -- from leaders to users

---

{{< slide background-image="assets/bg.png" >}}

## Shared solution elements

1. *Election of leaders* -- from a set of candidates
2. *Formation of regions* -- by assigning each user to a single leader
3. *Upstream information flow* -- from users to leaders
4. *Downstream information flow* -- from leaders to users
