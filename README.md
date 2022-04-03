# dma

A prosthetic device for doing math. Create and manipulate well-formed formulas.

## Notes on Notation

We ignore the parsing issue and focus on representations amenable to algorithms.

Everything is a set and ee use algebraic data types ∏<sub>i ∈ I</sub> A<sub>i</sub> for the cartesian product
and ∐<sub>i ∈ I</sub> A<sub>i</sub> for the coproduct, or disjoint union.

The product ∏<sub>i ∈ I</sub> A<sub>i</sub> = { (a<sub>i</sub>)) }
has projections π<sub>j</sub>:∏<sub>i ∈ I</sub> A<sub>i</sub> → A<sub>j</sub> where π<sub>j</sub>((a<sub>i</sub>)) = a<sub>j</sub>, j ∈ I.

The coproduct ∐<sub>i ∈ I</sub> A<sub>i</sub> = { (i, a<sub>i</sub>) : i ∈ I, a<sub>i</sub> ∈ A<sub>i</sub> }
has injections ν<sub>j</sub>: A<sub>j</sub> → ∐<sub>i ∈ I</sub> A<sub>i</sub> where ν<sub>j</sub>(a<sub>j</sub>) = (j, a<sub>j</sub>). 

×

## Use cases

Use S-expressions `e = (e0 e1 e2 ...)`.

`(car e) -> e0`, `(cdr e) -> (e1 e1 ...)`, `(cons (car e) (cdr e)` => e` 

`(index i e) -> ei = e[i]`

```
(+ (+ (^ x 2) (* 2 x)) 5) // x^2 + 2 x + 5
  <_ = (+ 0 _), [2]> // x = 0 + x
(+ (+ (^ x 2) (* 2 x)) (+ 0 5)) // x^2 + sx + 0 + 5


Statement: well-formed formula that is either true or false.

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
