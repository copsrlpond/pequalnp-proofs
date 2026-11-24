L-gct-232 over the complex numbers

Write J for the all-ones 4 by 4 matrix. For a complex linear subspace L of
symmetric matrices satisfying per(J+X)=24 for every X in L, the largest
possible dimension is either two or three. Whether dimension three occurs
is unresolved in these calculations.

The proof of the upper bound is in bound/BOUND.md. The 55 charts in that
directory exclude a three-space on which the first diagonal entry vanishes
and the first-row projection has rank at most two. Any four-dimensional
level space would contain such a three-space. The directory includes all
inputs, the 19 nontrivial solver verdicts, and independent reconstruction
of the equations. Instructions for rerunning the solver are in BOUND.md.

The lower bound is attained by the symmetric star on one row and its matching
column, with zero diagonal and three edge weights u, v, -u-v. In the Lean
file SymmetricStar.lean, star_attains verifies the permanent identity and
maximal_star proves that no independent direction can extend this example.
The file uses Mathlib with the project's Lean 4.36.0 toolchain.

Any three-dimensional example would satisfy all of the following.

1. It contains no nonzero matrix with rational entries. More generally
   it contains no direction defined over a number field with a residue
   degree one prime over 5 or 7. See directions/README.txt and verify.py.

2. Its stabilizer under simultaneous row and column permutations is trivial.
   The maps to the four diagonal entries and to the four row sums both
   have rank at least two. See symmetry/README.md and verify.cjs.

3. The projection onto each individual row has rank at least two. If the
   rank were at most one, its kernel would contain a two-dimensional level
   space with that row and column zero. The four Witt charts for this
   principal 3 by 3 support all have unit ideal over the algebraic closure
   of F_5. The vanishing and support conditions are closed in the projective
   Grassmannian, so the same exclusion holds over C. In the directions
   directory, run python principal.py with NumPy and assertions enabled.

The dimension-three exclusions use exact computations over finite fields
and projective specialization. No floating-point optimization is needed
to reproduce them. The Lean file covers only the star statements.
