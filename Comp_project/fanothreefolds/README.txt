The Fano 3-fold database
========================
This is a dataset that relates to the graded (homogeneous coordinate) rings of possible algebraic varieties: complex Fano 3-folds with Fano index 1. Each entry in this dataset records the (anticanonical) Hilbert series of a possible Fano 3-fold X, along with the result of some analysis about how X may be (anticanonically) embedded in weighted projective space P(w_1,w_2,...,w_s).

For details, see the paper [BK22], which is a companion and update to the original paper [ABR02].

If you make use of this data, please consider citing [BK22] and the DOI for this data:

doi:10.5281/zenodo.5820338

The data consists of two files in key:value format, "fano3.txt" and "matchmaker.txt". The files "fano3.sql" and "matchmaker.sql" contain the same data as the key:value files, but formatted ready for inserting in sqlite.

fano3.txt
---------
This file contains data that relates to the graded (homogeneous coordinate) rings of possible algebraic varieties. For each entry, the essential characteristic data is the genus and basket; everything else follows (with the exception of the ID). Briefly, this essential data determines a power series, the Hilbert series, Hilb(X,-K) = 1 + h1*t + h2*t^2 + ... that can be written as a rational function of the form (polynomial numerator in t) / ((1-t^(w_1))*...*(1-t^(w_s)), where w_1,w_2,..,w_s are (positive integer) weights.

The data consists of 52646 entries. The 39550 stable entries (that is, with 'stable' equal to 'true') are assigned an ID 'id' in the range 1-39550. The 13096 unstable entries (that is, with 'stable' equal to 'false') are assigned an ID in the range 41515-54610. IDs in the range 39551-41514 are assigned to the higher index Fano varieties, and are not included in this dataset.

Example entry
-------------
id: 1
weights: 5,6,7,...,16
has_elephant: false
genus: -2
h1: 0
h2: 0
...
h10: 4
numerator: t^317 - t^300 - 6*t^299 - ... + 1
codimension: 24
basket: 1/2(1,1,1),1/2(1,1,1),1/3(1,1,2),...,1/5(1,2,3)
basket_size: 7
equation_degrees: 17,18,18,...,27
degree: 1/60
k3_rank: 19
bogomolov: -8/15
kawamata: 1429/60
stable: true

(Some data truncated for readability.)

Brief description of an entry
-----------------------------
id:			a unique integer ID for this entry
genus:		h^0(X,-K) - 2
basket:		multiset of quotient singularities 1/r(f,a,-a)
basket_size: number of elements in the 'basket'
k3_rank:	sum(r-1) taken over the 'basket'
kawamata:	sum(r-1/r) taken over the 'basket'
bogomolov:	sum of terms over 'basket' relating to stability (see [BK22])
stable:		true if and only if 'bogolomov' <= 0
degree:		anticanonical degree (-K)^3 of X, determined by above data (see [BK22])
h1,h2,...,h10: coefficients of t,t^2,...,t^10 in the Hilbert series Hilb(X,-K)
weights:	suggestion of weights w_1,w_2,...,w_s for the anticanonical embedding X in P(w_1,w_2,...,w_s)
numerator:	polynomial such that the Hilbert series Hilb(X,-K) is given by the power series expansion of
				'numerator' / ((1-t^(w_1))*...*(1-t^(w_s))
			where the w_i in the denominator range over the 'weights'
codimension: the codimension of X in the suggested embedding, equal to s - 4
has_elephant: true if and only if h1 > 0

matchmaker.txt
--------------
This file contains a set of pairs of IDs, in each case one from the canonical toric Fano classification [Kas10,toric] and one from "fano3.txt". The meaning is that the Hilbert series of the two agree, and this file contains all such agreeing pairs.

Example entry
-------------
toric_id: 1
fano3_id: 27334

Brief description of an entry
-----------------------------
toric_id:	integer ID in the range 1-674688, corresponding to an 'id' from canonical toric Fano dataset [Kas10,toric]
fano3_id:	an integer ID in the range 1-39550 or 41515-54610, corresponding to an 'id' from "fano3.txt"


fano3.sql and matchmaker.sql
----------------------------
The files "fano3.sql" and "matchmaker.sql" contain sqlite-formatted versions of the data described above, and can be imported into an sqlite database via, for example:

$ cat fano3.sql matchmaker.sql | sqlite3 fano3.db

This can then be easily queried. For example:

$ sqlite3 fano3.db
> SELECT id FROM fano3 WHERE degree = 72 AND stable IS TRUE;
39550
> SELECT toric_id FROM fano3totoricf3c WHERE fano3_id = 39550;
547334
547377

References
----------
[ABR02] Selma Altinok, Gavin Brown, and Miles Reid, "Fano 3-folds, K3 surfaces and graded rings", in "Topology and geometry: commemorating SISTAG", volume 314 of Contemp. Math., pages 25-53. Amer. Math. Soc., Providence, RI, 2002.
[BK22] Gavin Brown and Alexander Kasprzyk, "Kawamata boundedness for Fano threefolds and the Graded Ring Database", 2022.
[Kas10] Alexander Kasprzyk, "Canonical toric Fano threefolds", Canadian Journal of Mathematics, 62(6), 1293-1309, 2010.
[toric] Alexander Kasprzyk, "The classification of toric canonical Fano 3-folds", doi:10.5281/zenodo.5866330
