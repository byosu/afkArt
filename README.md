# AFKArena Artifact match
Find optimal artifact configuration for heroes in AFKArena with bipartite graph matching

## Problem description

Dura's Artifacts are items in the game AFKArena that can be equipped by heroes to boost their stats. There are 7 Dura's Artifacts in the game: Blade, Eye, Conviction, Call, Chalice, Grace, Drape. Each artifact has a capacity which defines how many heroes can simultaneously be equipped with it. Heroes benefit more from different artifacts. The ideal hero-artifact matches are discussed in [Dura's Artifact Preliminary Guide](https://www.reddit.com/r/afkarena/comments/iu1dku/duras_artifact_preliminary_guide/) by [u/Shizzam_](https://www.reddit.com/user/Shizzam_) and [Grub's Artifact Overview](https://www.reddit.com/r/afkarena/comments/im0n3h/grubs_artifact_overview/) by [u/Crymeseveralrivers](https://www.reddit.com/user/Crymeseveralrivers). This program takes in available artifacts and their capacities, heroes to be equipped and their priority levels, and outputs the optimal configuration for each artifact.

## Algorithm

The matching between heroes and artifacts are described with a bipartite graph *G*(*U*,*V*,*E*), where *U* is the set of heroes, *V* is the set of artifacts. Edge *e*=*u*→*v* exists if the hero-artifact pairing (*u*,*v*) exists in Shizzam's or Grub's guide. The weight of the edge *w*<sub>e</sub>=*M*.*H*. Multiplier *M* is as follows. (*B*<sub>S</sub>=(*u*,*v*) exists in Shizzam's guide, *B*<sub>G</sub> = (*u*,*v*) exists in Grub's guide)

||*B*<sub>G</sub>|!*B*<sub>G</sub>|
|-|-|-|
|*B*<sub>S</sub>|1|.5|
|!*B*<sub>S</sub>|.7|0|

*H* is hero priority defined which is a part of the input.

The algorithm returns with a set of non-intersecting edges where the total weight is maximized.
