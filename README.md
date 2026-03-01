# Valiant (1984) - A Theory of the Learnable

A LaTeX transcription of L.G. Valiant's seminal 1984 paper "A Theory of the Learnable," originally published in the Proceedings of the Sixteenth Annual ACM Symposium on Theory of Computing (STOC '84).

This paper introduced the Probably Approximately Correct (PAC) learning framework, which became foundational to computational learning theory.

## About the Paper

Before this paper, the study of learning was spread across disconnected fields -- pattern recognition, artificial intelligence, inductive inference -- each with its own definitions and standards of rigor. Valiant's contribution was to ask a precise computational question: what can a machine provably learn in polynomial time?

The paper defines a *learning protocol* consisting of two information sources. The first is a routine called EXAMPLES, which supplies randomly drawn positive examples of a concept according to some arbitrary, unknown probability distribution. The second is an ORACLE that, when queried with a data point, reports whether the concept is true or false for that point. A *deduction procedure* then uses information from these sources to construct a recognition program for the concept being learned.

The central definition is *learnability*: a class of concepts is learnable if there exists an algorithm that, for any concept in the class and any probability distribution over examples, produces with high probability a program that closely approximates the target concept. Crucially, the approximation is measured against the same unknown distribution that generates the examples. The algorithm is allowed to fail with small probability and to produce an approximation that disagrees with the target on a small fraction of the probability space -- hence the name "Probably Approximately Correct." The algorithm must run in time polynomial in the relevant parameters.

Valiant then identifies three concrete classes of Boolean expressions that are learnable under this framework. First, he shows that *k*-CNF expressions (conjunctive normal form with at most *k* literals per clause) can be learned from positive examples alone, with no oracle calls needed. The algorithm initializes a formula containing every possible clause and eliminates clauses that are inconsistent with observed examples. Second, he proves that monotone DNF expressions (disjunctive normal form without negation) are learnable using both EXAMPLES and ORACLE. Third, he introduces *mu-expressions* -- arbitrary Boolean expressions where each variable appears at most once -- and shows they can be learned using more powerful oracles that answer questions about prime implicants and variable relevance.

A key technical ingredient is a combinatorial bound (the Proposition in Section 4) showing that the number of examples needed to learn is controlled by the logarithm of the number of candidate programs, scaled by the desired accuracy. This bound, derived from Chernoff-type inequalities, is what makes the probabilistic convergence argument work across all three learnability results.

The paper also argues that the class of learnable concepts may be inherently limited. Drawing on cryptography, Valiant observes that if there exist cryptographic functions that are easy to compute but hard to invert even given polynomially many input-output pairs, then those functions are by definition not learnable. This suggests that learnability is a strict subset of computational feasibility.

The framework introduced here launched computational learning theory as a field. The PAC model became the standard setting for proving learnability results, and the questions Valiant raised -- about the boundaries between learnable and unlearnable, about the role of the representation language, and about the relationship between learning and cryptography -- remain active areas of research.

## Repository Contents

```
.
├── Valiant1984.pdf                  # Original paper (scanned PDF, cover page removed)
├── Valiant1984-transcribed.tex      # Main LaTeX file (compiles the full paper)
├── Valiant1984-transcribed.pdf      # Compiled LaTeX output
├── sections/                        # Individual section files
│   ├── 00-abstract.tex
│   ├── 01-introduction.tex
│   ├── 02-learning-protocol-for-boolean-functions.tex
│   ├── 03-learnability.tex
│   ├── 04-a-combinatorial-bound.tex
│   ├── 05-bounded-cnf-expressions.tex
│   ├── 06-dnf-expressions.tex
│   ├── 07-mu-expressions.tex
│   ├── 08-remarks.tex
│   └── 09-references.tex
└── README.md
```

## How It Was Made

The paper was transcribed from the original scanned PDF into LaTeX using AI-assisted transcription. Nine parallel agents were each assigned a section of the paper and independently transcribed their section from the PDF into LaTeX. The introduction and abstract were transcribed manually due to a content filter issue with the automated agent.

The LaTeX source uses the `acmart` document class with `sigconf` format to match ACM conference proceedings styling. All mathematical notation, theorem environments, proofs, and algorithm pseudocode have been faithfully reproduced.

## Building

Requires a LaTeX distribution with the `acmart` class (included in TeX Live):

```bash
pdflatex Valiant1984-transcribed.tex
pdflatex Valiant1984-transcribed.tex  # second pass to resolve references
```

## Citation

```bibtex
@inproceedings{valiant1984,
  author    = {Valiant, L.G.},
  title     = {A Theory of the Learnable},
  booktitle = {Proceedings of the Sixteenth Annual ACM Symposium on Theory of Computing},
  series    = {STOC '84},
  year      = {1984},
  pages     = {436--445},
  publisher = {ACM},
  address   = {New York, NY, USA},
  doi       = {10.1145/800057.808710}
}
```

## Copyright Notice

Permission to copy without fee all or part of this material is granted provided that the copies are not made or distributed for direct commercial advantage, the ACM copyright notice and the title of the publication and its date appear, and notice is given that copying is by permission of the Association for Computing Machinery. To copy otherwise, or to republish, requires a fee and/or specific permission.

Copyright 1984 ACM 0-89791-133-4/84/004/0436 $0.75
