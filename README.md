# dma

A prosthetic device for doing math. Create and manipulate well-formed formulas.

## Notes on Notation

We ignore the parsing issue and focus on representations amenable to algorithms.

Everything is a set and we use algebraic data types ∏<sub>i ∈ I</sub> A<sub>i</sub> for the cartesian product
and ∐<sub>i ∈ I</sub> A<sub>i</sub> for the coproduct, or disjoint union.

The product ∏<sub>i ∈ I</sub> A<sub>i</sub> = { (a<sub>i</sub>)) }
has projections π<sub>j</sub> : ∏<sub>i ∈ I</sub> A<sub>i</sub> → A<sub>j</sub> where π<sub>j</sub>((a<sub>i</sub>)) = a<sub>j</sub>, j ∈ I.
The product of two sets is written A × B.

The coproduct ∐<sub>i ∈ I</sub> A<sub>i</sub> = { (i, a<sub>i</sub>) : i ∈ I, a<sub>i</sub> ∈ A<sub>i</sub> }
has injections ν<sub>j</sub> : A<sub>j</sub> → ∐<sub>i ∈ I</sub> A<sub>i</sub> where ν<sub>j</sub>(a<sub>j</sub>) = (j, a<sub>j</sub>). 
The disjoint union of two sets is written A ⨆ B or A | B.

Both operations are monoids so we can write finite products and coproducts unambiguously. 

## Use cases

x<sup>2</sup> + 2x + 5 can be parsed to (+ (^ x 2) (* 2 x) 5).

The rule x -> x + y - y

Expression: well-formed tree of symbols.

Symbols: variable, constant, operator, quantifier.

Relation: subset of the cartesian product of expression times expression.

`Stmt` ≔ `Expr` `Rel` `Expr`

`Rel` ≔ `=` | `≠` | `≤` | … 

`Expr` ≔ `Var` | `Const` | `Fun` | `Quant`

`Var` ≔ `Char` | `String`

`Const` ≔ `Var` (cannot be used in η-conversion)

`Fun` ≔ `fun(expr, …)`

`Quant` ≔  `∀` `Var` `Expr` | `∃` `Var` `Expr`

## Manipulation

Beta reduction. Replace free occurences of a variable in an expression by an expression.

Eta conversion. Rename bound occurences of a variable by another variable.

## References

Martin Hyland, [_Classical lambda calculus in modern dress_](https://arxiv.org/pdf/1211.5762)

R.A.G. Seely, [_Modelling Computations: a 2-Categorical Framework_](https://www.math.mcgill.ca/~rags/WkAdj/LICS.pdf)
