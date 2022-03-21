# dma
A prosthetic device for doing math

Create and manipulate well-formed formulas.

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
