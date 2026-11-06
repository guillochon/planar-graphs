# Planar Graph Atlas — OEIS A005470

**https://guillochon.github.io/planar-graphs/**

[A005470](https://oeis.org/A005470) counts planar graphs on n unlabeled vertices; [A003094](https://oeis.org/A003094)
counts the connected ones and [A021103](https://oeis.org/A021103) the 2-connected ones. All three were known to
n = 15 (n = 14 for A021103), found by generating every graph with plantri and nauty. The terms from n = 16 to 25 are
new:

| n | A005470 (all) | A003094 (connected) | A021103 (2-connected) |
|---|---|---|---|
| 15 | 2516143483576 | 2385519362107 | 1115272493022 |
| 16 | 52408033776878 | 49760001456551 | 22493653916620 |
| 17 | 1114782893212983 | 1059703295702139 | 462624367146705 |
| 18 | 24140058638845459 | 22969738086867520 | 9676037828904898 |
| 19 | 530861925075735556 | 505542319715022144 | 205363624344678050 |
| 20 | 11832495146001556996 | 11276122690200599855 | 4415099749028218062 |
| 21 | 266892197689888343244 | 254499290386523690634 | 96009973957009506442 |
| 22 | 6084033586294190154202 | 5804661393043936816211 | 2109220961695218583498 |
| 23 | 140012314430574390754809 | 133647000805745363204565 | 46763841586042636362681 |
| 24 | 3249784959167329158913333 | 3103364947739587802644026 | 1045438229538044361911334 |
| 25 | 76016793864553053210040815 | 72619635686723255869114898 | 23548181230365705962266586 |

They are counted by formula, not by generation:

1. **3-connected planar graphs** (polyhedra, [A000944](https://oeis.org/A000944)) with their full cycle index: by
   Whitney's theorem their symmetries are those of the polyhedron, and the polyhedra formula of the
   [Polyhedra Sampler](https://guillochon.github.io/polyhedra-sampler/) is refined to record how each rotation or
   reflection permutes vertices and edges.
2. **Networks** (two-pole graphs): an edge, a series chain, a parallel bundle, or a polyhedron with one edge removed
   and every other edge replaced by a network.
3. **2-connected graphs** by the dissymmetry theorem on the SPQR tree.
4. **Connected graphs** by Robinson's formula for trees of blocks.
5. **All graphs** by the Euler transform.

All arithmetic is modulo several primes below 2^24, recombined by the Chinese remainder theorem; the largest
convolutions in step 1 run on a GPU. The method reproduces every previously known term.

## The page

- **Gallery.** Every planar graph on up to 8 vertices (from nauty, `geng n | planarg`), grouped by number of edges and
  colored by connectivity: disconnected, connected with a cut vertex, 2-connected, 3-connected. Filters by class. The
  class counts agree with the four sequences for every n shown.
- **Inspector.** The selected graph taken apart: cut vertices (ringed), blocks, and for each block its SPQR tree,
  drawn piece by piece: S (a cycle), P (parallel edges) and R (3-connected), glued along dashed virtual edges. Point
  at a piece to see its edges in the graph. The address bar keeps the selected graph (`#g7-123`).
- **Counts.** The four sequences on a log scale, the share of each connectivity class, the ratio a(n)/a(n−1) against
  the known bounds on the growth constant, and the full table with new terms marked.

Drawings are straight-line and crossing-free: candidate layouts (Kamada–Kawai, Tutte embeddings, random starts) are
relaxed by a force model that rejects any move creating a crossing, and the clearest result is kept. SPQR trees come
from splitting each block at separation pairs and merging adjacent cycles and bundles.

Made by James Guillochon with Claude. The source lives in the oeis-sniper project (`viz/A005470/`); this repo holds
the published copy.
