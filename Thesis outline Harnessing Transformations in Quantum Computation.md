# Thesis outline: Harnessing Transformations in Quantum Computation

Oct 12, 2026 · @Oliver

The thesis has 11 chapters in three parts, each part named after one phrase of the subtitle, tied together by one claim: the right transformation turns a hard quantum task into a tractable one.

## Title, abstract and keywords

**Title:** Harnessing Transformations in Quantum Computation: Fermion-to-Qubit Mappings, Quantum Metropolis Sampling and Trapped-Ion Experiments

**Abstract plan (one paragraph per beat, about 300 words):**

1. Thesis statement: many tasks in quantum simulation become efficient once written in the right basis; this thesis builds new transformations and harnesses existing ones.
2. Part I: fermion-to-qubit mappings (fermionic encodings): hybrid Jordan-Wigner/Bravyi-Kitaev mapping at 1.016 qubits per fermion; unitary local Jordan-Wigner on the torus, include something based of the discussino with joel to explain this jordan-wigner on a torus paper in their language; spin-adapted Paldus transform with O(log N) operators. I also need to add the hubbard model example in this section.
3. Part II: improving phase estimation by designing its window in the Fourier domain: a B-spline window made by a general state-preparation method, piecewise QSVT, with 50× fewer Toffolis than Kaiser; then complementary sech/tanh windows that make BSI-QPE possible and revive the Quantum Metropolis algorithm for Gibbs sampling / thermal state preparation. Somewhere in this see if we can briefly add in the work from the spectral sieve main.tex however this probably needs caveats that it does not outperform just doing QPE and then post selecting a range of energies.
4. Part III: first non-abelian hidden subgroup problem on hardware (IonQ Forte); particle-to-string conversion across duality defects on Quantinuum H2.
5. One closing line on the common lesson: the basis sets the cost.

**Repository keywords (Apollo):** fermion-to-qubit mapping; fermionic encoding; Jordan-Wigner transformation; Bravyi-Kitaev; quantum Metropolis algorithm; Gibbs sampling; thermal state preparation; quantum phase estimation; QSVT; state preparation; hidden subgroup problem; duality defects; generalized symmetries; trapped-ion quantum computing; spin adaptation; GUGA.

## Chapter 1: Introduction

The introduction makes the case that a quantum computation is only as cheap as the representation it runs in, then shows each chapter as building or harnessing one transformation. Target length: 15–20 pages.

1. **Motivation.** Simulating fermions and thermal states is a leading use of quantum computers; the sign problem limits classical Monte Carlo.
2. **The central idea: change of basis.** The same physics or problem can be cheap or expensive depending on its representation: Pauli weight, qubit count, Toffoli count, oracle queries.
3. **Two families of transformation.**
   1. Dualities: maps between equivalent descriptions, which exist because of a symmetry (gauging fermion parity, Kramers-Wannier, spin adaptation).
   2. Fourier and spectral transformations: maps to a basis where the quantity of interest can be read out (QPE, QSVT, group Fourier transforms).
4. **Why they are the same idea.** Both are representation theory: a group Fourier transform moves from group elements to irreps; gauging an abelian group G gives a dual with symmetry Ĝ, with Kramers-Wannier as the Z2 case; the Paldus transform couples to U(1)×SU(2) irreps, a cousin of the Schur transform.
5. **Building versus harnessing.** Which chapters construct new transformations (3, 4, 5, 6, 7) and which put them to work (6, 8, 9, 10).
6. **Recurring lessons.** Transformations have flaws, and much of the work repairs them: non-local strings, missing sectors, Fourier tails, a no-go theorem.
7. **Contributions and publications.** One line per paper with its venue, plus a statement of the author's own contribution to each co-authored paper.
8. **Chapter map.** How the parts connect, as a diagram.

&#91;embedded content: chapter map · 3 parts, 3 bridges\]

Each part builds or harnesses one kind of transformation; the coloured arrows mark where one chapter's idea returns in another, and the highlighted box is the headline result.

## Chapter 2: Background

The background gives every later chapter its notation once, so the paper chapters can drop their own preliminaries. Target length: 25–35 pages.

1. **Fermions on qubits.** Second quantisation, Majorana operators, Jordan-Wigner, parity and Bravyi-Kitaev mappings; Pauli weight and qubit-per-fermion ratio as cost measures.
2. **Gauging and dualities.** Gauging the Z2 fermion parity; Kramers-Wannier and Kennedy-Tasaki dualities; symmetry sectors and twisted boundary conditions.
3. **Tensor-network intertwiners.** MPOs and PEPOs, graded (fermionic) tensor networks, fusion trees, F and R symbols. Shared by Chapters 4, 5 and 10.
4. **Block encodings and QSVT.** Block encodings, quantum signal processing, polynomial approximation.
5. **Quantum phase estimation.** Standard QPE, Fourier tails, window functions (Kaiser, DPSS, B-spline) and boosting.
6. **Group Fourier transforms.** Representation theory of finite groups, abelian and non-abelian QFT, weak and strong Fourier sampling.
7. **Gibbs sampling.** Thermal states, classical Metropolis-Hastings, the sign problem, quantum detailed balance, Davies generators and Lindbladian samplers.
8. **Trapped-ion hardware.** Native gates, noise, zero-noise extrapolation by gate folding.

## Part I: Fermion-to-Qubit Mappings and Dualities

Part I builds three dualities, each trading a non-local representation for a local or cheaper one. A one-page part opener states this and points back to Chapter 2.

Somewhere I need to add the hubbard model example in this section.

### Chapter 3: Hybrid fermion-to-qubit mappings

Source: O'Brien and Strelchuk, PRB 109, 115149 (2024), Editors' Suggestion.

1. Applying two mappings at different scales: Bravyi-Kitaev inside n×n cells, Jordan-Wigner between them.
2. Non-local hybrid: 98% shorter Pauli strings than Jordan-Wigner.
3. Local Hybrid+ family: 1 + 1/n² qubits per fermion, 1.016 at n = 8 against 1.25 for Chen-Xu, with O(log n) circuit length.
4. Bridge out: linear versus tree orderings return in Chapter 5.

### Chapter 4: Local Jordan-Wigner transformations on the torus

Source: O'Brien, Lootens and Verstraete, PRB 111, 115126 (2025).

1. The mapping as gauging Z2 fermion parity, written as a graded PEPO intertwiner on arbitrary graphs.
2. The 1D warm-up: (anti-)periodic rings in even and odd charge sectors as MPOs.
3. The 2D torus: the interplay of charge sectors and boundary conditions.
4. Ancilla qubits store the sector, making the intertwiner unitary.
5. Need to add stuff based of Joel discussion.

### Chapter 5: The quantum Paldus transform

Source: draft (results in progress).

1. GUGA recast as an MPO duality between the occupation basis and the spin-adapted U(1)×SU(2) basis; matrix elements from F and R symbols, no unitary group needed.
2. Tree-like coupling: one-body operators touch O(log N) tensors instead of N, the spin-adapted analogue of parity → Bravyi-Kitaev.
3. Storage cost: about 3.7N bits per configuration state function against 2N for standard GUGA.
4. Benchmarks of tree-like against standard GUGA (to do).

## Part II: Quantum Metropolis Sampling

Part II builds up to its headline result: the Quantum Metropolis algorithm, revived around a no-go theorem. QPE's error is set by the Fourier transform of the amplitudes on its ancilla register, so the part designs phase estimation in the Fourier domain. Chapter 6 shows how with a prepared window; Chapter 7 finds windows that work for any register input; Chapter 8 uses them to sample Gibbs states.

Somewhere in this part I need to add stuff about the spectral sieve.

### Chapter 6: Phase estimation in the Fourier domain

Source: O'Brien and Sünderhauf, Quantum (2025). Kept short: this is the toolkit chapter for the part.

1. Why QPE has fat tails: an unboosted register is a rectangular window, whose Fourier transform decays only as 1/k.
2. Boosting: prepare a window with a narrow Fourier transform; Kaiser is the state of the art at O(log log 1/δ) extra ancillas.
3. The B-spline window: an m-fold self-convolution of a box, so its Fourier transform is a power of sinc. Theorem: O(log 1/ε + log log 1/δ) ancillas, matching Kaiser.
4. Preparing it cheaply: piecewise QSVT with a piecewise linear diagonal block encoding, 50× fewer Toffolis than the Kaiser window.
5. The same method in general: x^α and log x amplitudes (short section or appendix).
6. The open problem it leaves: a prepared window only works when the register starts in |0⟩.

### Chapter 7: Boosted state-independent phase estimation

Source: O'Brien, Achutha and Verstraete, arXiv, Section II and Appendix C.

1. What Quantum Metropolis needs: boosted, shift-invariant QPE on a register that is reused without resetting.
2. The no-go theorem for that QPE, and why it pushed the field to Lindbladian samplers.
3. BSI-QPE: windows applied by controlled RY rotations instead of a prepared state, with a flag qubit recording the sign of the shift.
4. The Fourier-domain requirement: a complementary pair with α² + β² = 1 whose discrete Fourier transforms both decay exponentially. DPSS, Kaiser, Gaussian and B-spline windows cannot form such a pair; sech/tanh gives |α̂(k)|, |β̂(k)| = O(e^(−ν|k|)).
5. Why boosting is necessary: the rectangular window's O(1/k) tails give an error bound above 1.
6. Uses beyond Metropolis: any algorithm that needs coherent phase estimation, such as HHL.

### Chapter 8: Quantum Metropolis sampling revived

Source: O'Brien, Achutha and Verstraete, arXiv, Sections III–V and Appendices A, B, D and E. The headline result of the thesis.

1. Gibbs sampling and the sign problem; the original Quantum Metropolis algorithm of Temme et al. and its rewinding step.
2. The modified algorithm with BSI-QPE: accept and reject branches, controlled on the flag qubit.
3. Approximate quantum detailed balance: a branch-wise criterion that absorbs the exponentially small tails of BSI-QPE.
4. Main theorem: the Gibbs state is an approximate fixed point; proofs for the acceptance and rejection branches.
5. Convergence: exponentially fast under the strict trace-norm contractivity assumption of Temme et al.
6. Comparison with Lindbladian and weak-measurement samplers, and costs for fault-tolerant hardware.

## Part III: Trapped-Ion Experiments

Part III runs transformations on real hardware: a non-abelian Fourier transform on IonQ Forte, and a duality made physical on Quantinuum H2. A short shared section on hardware and error mitigation can sit in the part opener.

### Chapter 9: The non-abelian hidden subgroup problem on hardware

Source: arXiv

1. The HSP, Fourier sampling, and why the non-abelian case matters (dihedral group and lattices, symmetric group and graph isomorphism).
2. q-hedral groups Z_p ⋊ Z_q: weak sampling is blind, so the basis inside each irrep decides everything.
3. Circuits: state preparation, permutation-hidden oracle, QFT over the group; 62 circuits per (p, q), 8–52 two-qubit gates, at most 9 qubits.
4. Results for adapted-basis, adjacent-pair and forgetful sampling; ZNE lifts the adapted peak at p = 7, q = 6 from 0.612 to 0.749 (ideal 0.857).
5. Honest comparison: at these sizes the best classical algorithm needs fewer queries; the adapted basis leads only at budgets of one and two queries when q = p − 1.

### Chapter 10: Monopoles, scattering and duality defects

Source: O'Brien, Ueda, Granet, Dreyer and Verstraete (with Quantinuum), arXiv

1. The monopole paradox and its resolution through twisted sectors.
2. Spin-chain analogue: a Kramers-Wannier defect turns a local excitation into a domain wall with a disorder string.
3. Unitary preparation of a localized quasiparticle wavepacket on top of the ground state.
4. Results on H2: transverse-field Ising and the cluster-model SPT phase with Kennedy-Tasaki regions.
5. Bridge back: the twisted sectors of Chapter 4, now as excitations you can measure.

## Chapter 11: Conclusion and outlook

The conclusion returns to the thesis statement and closes the loop: encode, prepare, sample, then test on hardware. Target length: 8–10 pages.

1. **Summary by transformation.** One paragraph per family: what was built and what it bought, with each headline number.
2. **What the chapters taught together.**
   1. The basis sets the cost.
   2. Flaws in transformations can be repaired, or worked around in the case of the no-go theorem.
   3. Linear versus tree orderings (Chapters 3 and 5).
   4. Dualities move from bookkeeping to physics (Chapters 4 and 10).
3. **Outlook.**
   1. Combining the pieces: spin-adapted encodings feeding a Quantum Metropolis sampler for chemistry.
   2. Other uses of BSI-QPE, for example coherent phase estimation inside HHL.
   3. Non-invertible symmetries and duality defects as state-preparation tools.
   4. Larger non-abelian HSP instances once hardware noise falls.

## Appendices and front matter

Long proofs and derivations from the papers move to appendices so the chapters read as a story.

**Front matter:** declaration of originality and statement of contributions to co-authored work; abstract; acknowledgements; list of publications; notation table (one symbol set across all chapters).

**Appendices:**

**Back matter:** bibliography; index (optional).
