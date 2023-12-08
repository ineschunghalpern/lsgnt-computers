The classification of toric canonical Fano 3-folds
--------------------------------------------------

This dataset describes the classification of all toric canonical Fano 3-folds [1]. Equivalently, it describes the classification of all 3-dimensional convex lattice polytopes with exactly one interior lattice point.

A toric Fano 3-fold X (that is, a 3-dimensional toric variety with ample anticanonical divisor -K) with at worst canonical singularities corresponds to a 3-dimensional convex polytope P with vertices that are primitive integer vectors, and such that P contains exactly one lattice point, the origin, in its strict interior. The fan of X is given by the spanning fan of P: that is, the fan whose cones are spanned by the faces of P. In the language of toric geometry, P is in the lattice N = Z^3. Since two polytopes which are equal after a lattice change of basis give rise to isomorphic toric varieties, a polytope is regarded as being defined only up to the action of GL(Z^3). There are 674688 isomorphism classes.

For details, see the paper [1]. If you make use of this data, please consider citing [1] and the DOI for this data:

doi:10.5281/zenodo.5866330

toricf3c.txt
------------

The file "toricf3c.txt" contains key:value records with keys and values as described below, where each record is separated by a blank line. Each key:value record determines a toric Fano 3-fold X, or equivalently a lattice polytope P, in the classification. There are 674688 records in the file.

Example record
--------------
id: 1
num_vertices: 16
num_faces: 10
num_points: 22
is_terminal: false
is_simplicial: false
is_regular: false
is_reflexive: false
vertex_list: [[2,1,1],[-1,0,-1],[-2,-1,-1],[0,1,1],[0,-1,-1],[0,-1,-2],[-2,-1,0],[0,1,0],[2,1,2],[-1,0,1],[1,1,2],[1,0,1],[1,1,0],[1,0,-1],[-1,-1,0],[-1,-1,-2]]
point_list: [[2,1,1],[-1,0,-1],[-2,-1,-1],[0,1,1],[0,-1,-1],[0,0,-1],[0,-1,-2],[-1,0,0],[-2,-1,0],[1,0,0],[0,1,0],[0,0,1],[-1,-1,-1],[2,1,2],[1,1,1],[-1,0,1],[1,1,2],[1,0,1],[1,1,0],[1,0,-1],[-1,-1,0],[-1,-1,-2]]
dual_list: [[0,-1,1],[0,-1,0],[1,-1,0],[-1,1,0],[0,1,0],[0,1,-1],[1/2,-1/2,-1/2],[-1/2,-1/2,1/2],[-1/2,3/2,-1/2],[1/2,-1/2,1/2]]
ehrhart_delta: [1,19,23,1]
hilbert_delta: [1,7,25,47,47,25,7,1]
normal_form: [[1,0,0],[0,1,0],[1,1,2],[0,-1,-2],[-1,0,-2],[1,-1,0],[-1,1,0],[1,0,2],[0,1,2],[-1,-1,-2],[0,-1,0],[-1,0,0],[-1,1,1],[1,1,1],[-1,-1,-3],[1,-1,1]]
volume: 44
degree: 10
gorenstein_index: 2
h1: 7
h2: 29
h3: 75
h4: 157
h5: 283
h6: 465
h7: 711
h8: 1033
h9: 1439
h10: 1941
e1: 23
e2: 109
e3: 303
e4: 649
e5: 1191
e6: 1973
e7: 3039
e8: 4433
e9: 6199
e10: 8381
picard_rank: 1
automorphism_order: 24
is_barycentre_zero: true
is_dual_barycentre_zero: true

We fix some notation. Let:
	* N = Z^3 be a lattice of rank 3;
	* P denote the lattice polytope in N defined by the key:value record;
	* F denote the spanning fan in N of P;
	* X denote the toric Fano 3-fold corresponding to F;
	* M = Hom(N,Z) denote the lattice dual to N;
	* P^* denote the (rational) polytope in M dual to P (also called the polar polytope);
	* -K denote the anticanonical divisor of X.

The keys and values are as follows.

id: A unique integer ID for this record, in the range 1 to 674688.
num_vertices: A positive integer. The number of vertices #vert(P) of P. Equivalently, the number of rays of F. By duality this is also equal to the number of 2-dimensional faces of P^*.
num_faces: A positive integer. The number of 2-dimensional faces of P. Equivalently, the number of top-dimensional cones of F. By duality this is also equal to the number of vertices of P^*.
num_points: A positive integer. The number of lattice points #(P \cap N).
is_terminal: A boolean. True if and only if X has at worst terminal singularities. Equivalently, true if and only if the only lattice points on the boundary of P are the vertices of P; that is, P \cap N = vert(P) \cup {0}.
is_simplicial: A boolean. True if and only if P is simplicial. Equivalently, true if and only if X is Q-factorial. By duality, this is true if and only if P^* is simple.
is_regular: A boolean. True if and only if X is smooth. Equivalently, true if and only if every 2-dimensional face of P is a triangle whose vertices Z-generate the lattice N. If is_regular is true then both is_simplicial and is_terminal must be true.
is_reflexive: A boolean. True if and only if X is Gorenstein; that is, -K is Cartier. Equivalently, true if and only if P^* is a lattice polytope.
vertex_list: A sequence of lattice points in N. The vertices vert(P) of P. Equivalently, the primitive lattice generators of the rays of F. The number of points is given by num_vertices.
point_list: A sequence of lattice points in N. The lattice points P \cap N. The number of points is given by num_points.
dual_list: A sequence of rational points in M. The vertices vert(P^*) of P^*. These will be lattice points if and only if is_reflexive is true. The number of points is given (via duality) by num_faces.
ehrhart_delta: A sequence (1,a_1,a_2,1) of four integers, the first and last of which are always 1. This is the Ehrhart delta-vector (or h*-vector) of P. The Ehrhart series Ehr(P) of P is given by Ehr(P) = (1 + a_1*t + a_2*t^2 + t^3) / (1 - t)^4.
hilbert_delta: A sequence (b_0,b_1,...,b_N) of integers such that b_i = b_(N - i), and b_0 = b_N = 1. This is called the Ehrhart delta-vector (or h*-vector) of P^*. Write N = 4*r - 1. Then r is the quasiperiod of P^*, and r divides gorenstein_index. The Ehrhart series of P^* is given by Ehr(P^*) = (b_0 + b_1*t + ... + b_N*t^N) / (1 - t^r)^4. The Ehrhart series Ehr(P^*) of P^* is equal to the Hilbert series Hilb(X,-K).
normal_form: A sequence of lattice points in N. The PALP normal form of the vertices of P; see [2,3].
volume: A positive integer. The lattice-normalised volume Vol(P) of P. This is equal to the sum of the ehrhart_delta: Vol(P) = 1 + a_1 + a_2 + 1.
degree: A positive integer. The anticanonical degree (-K)^3 of X. Equivalently, the lattice-normalised volume Vol(P^*) of P^*.
gorenstein_index: A positive integer. The Gorenstein index of X; that is, the smallest multiple m>0 such that -mK is Cartier. Equivalently, the smallest multiple m>0 such that mP^* is a lattice polytope. This is 1 if and only if is_reflexive is true.
h1,...,h10: Positive integers. The value hi is equal to the number of lattice points in the i-th dilation of P^*, that is, hi = #(iP^* \cap M). Equivalently, hi = h^0(X,-iK). The values hi can also be obtained from Ehr(P^*), or equivalently from Hilb(X,-K), via the power-series expansion (b_0 + b_1*t + ... + b_N*t^N) / (1 - t^r)^4 = 1 + h1*t + h2*t^2 + h3*t^3 + ..., where (b_0,b_1,...,b_N) is given by hilbert_delta.
e1,...,e10: Positive integers. The value ei is equal to the number of lattice points in the i-th dilation of P, that is, ei = #(iP \cap N). In particular, e1 is equal to num_points. The values ei can also be obtained from Ehr(P) via the power-series expansion (1 + a_1*t + a_2*t^2 + t^3) / (1 - t)^4 = 1 + e1*t + e2*t^2 + e3*t^3 + ..., where (1,a_1,a_2,1) is given by ehrhart_delta.
picard_rank: Positive integer. The rank of the Picard group of X. When is_simplicial is true, this is equal to #vert(P) - 3.
automorphism_order: Positive integer. The order of the automorphism group Aut(P) <= GL(Z^3) of P.
is_barycentre_zero: A boolean. True if and only if the barycentre of P is equal to the origin in N.
is_dual_barycentre_zero: A boolean. True if and only if the barycentre of P^* is equal to the origin in M.

toricf3c.sql
------------
The file "toricf3c.sql" contain an sqlite-formatted version of the data described above, and can be imported into an sqlite database via, for example:

$ cat toricf3c.sql | sqlite3 toricf3c.db

This can then be easily queried. For example:

$ sqlite3 toricf3c.db
> SELECT COUNT(*) FROM toricf3c;
674688
> SELECT vertex_list FROM toricf3c WHERE degree = 72;
[[-1,-4,-6],[1,0,0],[0,1,0],[0,0,1]]
[[-1,-1,-3],[1,0,0],[0,1,0],[0,0,1]]

References
----------

[1] Alexander M. Kasprzyk. Canonical toric Fano threefolds. Canadian Journal of Mathematics, 62(6):1293–1309, 2010.
[2] Maximilian Kreuzer, Harald Skarke. PALP, a package for analyzing lattice polytopes with applications to toric geometry. Computer Phys. Comm., 157:87-106, 2004.
[3] Roland Grinis, Alexander M. Kasprzyk. Normal forms of convex lattice polytopes. arXiv:1301.6641 [math.CO], 2013.
