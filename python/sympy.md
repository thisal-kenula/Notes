# SymPy

[🔗 Documentation](https://docs.sympy.org/latest/tutorials/intro-tutorial/index.html)2

## $\LaTeX{}$ Symbols

### **Mathematical Symbols**

- **Plus-minus**: `\pm` : $\pm$
- **Multiplication dot**: `\cdot` : $\cdot$
- **Multiplication:** `\times` $\times$
- **Division slash**: `\div` : $\div$
- **Infinity**: `\infty` : $\infty$
- **Greater than or equal to**: `\geq` : $\geq$
- **Less than or equal to**: `\leq` : $\leq$
- **Not equal to**: `\neq` : $\neq$
- **Approximately equal**: `\approx` : $\approx$
- **Square root**: `\sqrt{a}` : $\sqrt{a}$
- **N-th root**: `\sqrt[n]{a}` : $\sqrt[n]{a}$
- **Summation**: `\sum_{i=1}^{n} i` : $\sum_{i=1}^{n} i$
- **Product**: `\prod_{i=1}^{n} i` : $\prod_{i=1}^{n}i$
- **Integral**: `\int_{a}^{b} f(x) \, dx` : $\int_{a}^{b} f(x) , dx$
- **Partial derivative**: `\frac{\partial f}{\partial x}` : $\frac{\partial f}{\partial x}$
- **Gradient**: `\nabla f` : $\nabla f$
- **Limits:** `\lim_{x \to \infty} expression` : $\lim_{x \to \infty} expression$
- **Binomial:** `\binom{n}{k}` : $\binom{n}{k}$
- **Logarithm**: `\log_{base}(argument)` : $\log_{base}(argument)$
- **Matrix:**  $\begin{matrix}
a & b \\
c & d
\end{matrix}$
- **Brackets Matrix:** $\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}$
- **Sine**: `\sin(x)` : $\sin(x)$ cos, tan the same way
- **Infinity**: `\infty` : $\infty$
- **Proportional:** `\propto` : $\propto$

### **Greek Letters**

- **Alpha**: `\alpha` : $\alpha$
- **Beta**: `\beta` : $\beta$
- **Gamma**: `\gamma` : $\gamma$
- **Delta**: `\delta` : $\delta$
- **Epsilon**: `\epsilon` : $\epsilon$
- **Zeta**: `\zeta` : $\zeta$
- **Eta**: `\eta` : $\eta$
- **Theta**: `\theta` : $\theta$
- **Iota**: `\iota` : $\iota$
- **Kappa**: `\kappa` : $\kappa$
- **Lambda**: `\lambda` : $\lambda$
- **Mu**: `\mu` : $\mu$
- **Nu**: `\nu` : $\nu$
- **Xi**: `\xi` : $\xi$
- **Omicron**: `o` : $o$
- **Pi**: `\pi` : $\pi$
- **Rho**: `\rho` : $\rho$
- **Sigma**: `\sigma` : $\sigma$
- **Tau**: `\tau` : $\tau$
- **Upsilon**: `\upsilon` : $\upsilon$
- **Phi**: `\phi` : $\phi$
- **Chi**: `\chi` : $\chi$
- **Psi**: `\psi` : $\psi$
- **Omega**: `\omega` : $\omega$

### **Set Theory Symbols**

- **Element of**: `\in` : $\in$
- **Not an element of**: `\notin` : $\notin$
- **Subset of**: `\subset` : $\subset$
- **Superset of**: `\supset` : $\supset$
- **Subset or equal to**: `\subseteq` : $\subseteq$
- **Superset or equal to**: `\supseteq` : $\supseteq$
- **Empty set**: `\emptyset` : $\emptyset$
- **Intersection**: `\cap` : $\cap$
- **Union**: `\cup` : $\cup$
- **Universal set**: `\mathbb{U}` : $\mathbb{U}$

### **Logic Symbols**

- **And**: `\land` : $\land$
- **Or**: `\lor` : $\lor$
- **Not**: `\neg` : $\neg$
- **Implies**: `\implies` : $\implies$
- **If and only if**: `\iff` : $\iff$
- **For all**: `\forall` : $\forall$
- **There exists**: `\exists` : $\exists$

### **Miscellaneous Symbols**

- **Degree**: `^\circ` : $^\circ$
- **Dot**: `\cdot` : $\cdot$
- **Arrow**: `\rightarrow` : $\rightarrow$
- **Double right arrow:** `\Rightarrow` : $\Rightarrow$
- **Left arrow**: `\leftarrow` : $\leftarrow$
- **Right arrow**: `\rightarrow` : $\rightarrow$
- **Double arrow**: `\leftrightarrow` : $\leftrightarrow$
- **Space:** `\`
- **Vector:** `\vec{F}` : $\vec{F}$
- Display a string in LaTeX format in IPython Notebook
    
    ```python
    from IPython.display import display, Latex
    
    # Your LaTeX string
    latex_string = r"e^{i\pi} + 1 = 0"
    
    # Display the LaTeX
    display(Latex(latex_string))
    ```
    
- $\LaTeX$ into `sympy`
    
    ```python
    from sympy.parsing.latex import parse_latex
    
    # Parse the LaTeX string into a SymPy expression
    equation = parse_latex(r"x^2 - 4 = 0")
    
    # Solve the equation
    solutions = solve(equation, x)
    
    print("Solutions:", solutions)
    ```
    
    - Needs a package
        
        ```bash
        pip3 install antlr4-python3-runtime==4.11
        ```
        

## Basics

### Print to better preview

`init_printing(use_unicode=**True**)`

```python
init_printing() # will automatically enable the best printer available in your environment
```

### Quickly start interactive calculator-type session

```python
from sympy import init_session
**init_session()**
```

### Set assumptions

```python
# by default symbols are Complex
x, a, b = symbols('x a b')
(x**a)**b
```

$\displaystyle \left(x^{a}\right)^{b}$

- Positive
    
    ```python
    x, a, b = symbols('x a b', **positive = True**) # does not include 0
    (x**a)**b
    ```
    
    $\displaystyle x^{a b}$
    
- Non-negative
    
    `nonnegative=True` includes 0
    
- Real
    
    `x, a, b = symbols('x a b', real = True)`
    
- Integer
    
    `integer = True`
    

### Create numbered symbols

```python
x = symbols('x0:5') # (x0, x1, x2, x3, x4)
x[0]+x[1]/x[2]
#Or 
x0, x1, x2, x3, x4 = symbols('x0:5')
x0+x1/x2
```

$\displaystyle x_{0} + \frac{x_{1}}{x_{2}}$

### Directly use symbols(without python variables)

```python
x = symbols('x')
expr = (x**2+2)/(x+3)
del x
# apart(_, x) won't work
apart(_, Symbol('x')) # Will work
```

```python
x = symbols('x')
y = symbols('x')
expr = (x**2+2)/(y+3)
expr # (x**2 + 2)/(x + 3)
# x,y are different python variables, but same Symbol
```

### ∞

∞ is represented by `oo`

### λ

```python
ld = symbols('lamda')
ld # λ
```

### Print in LaTex format

**`from** IPython.display **import** display, Math`
[0, 3]
`display(Math(latex(_)))`
$\displaystyle \left[ 0, \  3\right]$

### Unevaluated numbers

```python
5/3 # 1.666666666
Integer(5)/3 # 5/3
S(5)/3 # 5/3
```

### Commutative

```python
x, y, z = symbols('x y z', **commutative = False**)
1 + x
```

$1 + x$

## Basic operations

SymPy equations are `immutable` (except Matrices)

### Equation

`Eq(y, x*cos(ø))` → $\displaystyle y = x \cos{\left(ø \right)}$

- Equal to 0
    
    `solve(x**2 - 1, x)` instead of `solve(Eq(x**2-1, 0), x)`
    

### Solve

Syntax: `solve(equations, variables)`

> `Eq(y, x*cos(ø))` → $y = x \cos{\left(ø \right)}$
`solve(_, x)`
[y/cos(ø)]
> 

### Substitute

```python
expr = cos(x) + 1
# subs(old, new)
expr.subs(x, y) # cos(y)+1
expr #cos(x)+1 
#(Because sympy equations are **immutable**)
```

- `limit` should be used instead of `subs` whenever the point of evaluation is a singularity
    
    `expr` = $\displaystyle x^{2} e^{- x}$
    `expr.subs(x, oo)` → $\displaystyle \text{NaN}$
    `limit(expr, x, oo)` → $0$
    
- Multiple substitutions
    
    ```python
    expr = x**3 + 4*x*y - z
    expr.subs([(x, 2), (y, 4), (z, 0)]) # 40
    ```
    

### Expand trigonometric

```python
expr = sin(2*x) + cos(2*x)
expand_trig(expr)
```

$2 \sin{\left(x \right)} \cos{\left(x \right)} + 2 \cos^{2}{\left(x \right)} - 1$

### String to SymPy

```python
# x = symbols('x') is not needed
str_expr = 'x**2 + 3*x -1/2'
expr = **sympify**(str_expr)
expr # x**2 + 3*x - 1/2
```

### Evaluate

```python
expr = sqrt(8) # sqrt just returns the positive
expr.evalf() # 2.82842712474619
expr.evalf(25) # 2.828427124746190097603377 (25 digits)
```

- From an expression
    
    ```python
    expr = cos(2*x)
    expr.evalf(**subs = {x: 2.4}**) # 0.0874989834394464
    ```
    
- Roundoff error
    
    ```python
    one = cos(1)**2 + sin(1)**2
    (one - 1).evalf() # -0.e-124
    (one - 1).evalf(**chop=True**) # 0
    ```
    
- Evaluate at many points
    
    ```python
    import numpy
    a = numpy.arange(10) # array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
    expr = sin(x)
    f = **lambdify**(x, expr, numpy)
    f(a)
    '''array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ,
           -0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849])
    '''
    ```
    
- Lambdify
    
    ```python
    def mysin(x):
        return x
    
    expr = sin(x)
    f = lambdify(x, expr, {'sin': mysin}) # {sympy_name:numerical_function}
    f(0.1) # 0.1
    ```
    

## Simplification

### Simplify

`simplify()` tries many simplification functions, thus slow (Use specific functions whenever possible)

```python
simplify(sin(x)**2 + cos(x)**2) # 1
```

```python
a = x**3 + x**2 -x -1
b = x**2 +2*x +1
simplify(a/b) # *x*−1
```

```python
simplify(x**2 +2*x +1) # x**2 + 2*x + 1
```

### Factor

```python
factor(x**2 +2*x +1) 
```

$\left(x + 1\right)^{2}$

- Factor list
    
    ```python
    factor_list(x**2 +2*x +1)
    # (1, [(x + 1, 2)])
    ```
    

### Expand

```python
expand((x + 3)**2) # x**2 + 6*x + 9
```

### Collect

collects common powers of a term

> $x^{3} - x^{2} z + 2 x^{2} + x y + x - 3$
**`collect**(_, x)`
$x^{3} + x^{2} \cdot \left(2 - z\right) + x \left(y + 1\right) - 3$
> 

### Coefficient

> $x^{3} + x^{2} \cdot \left(2 - z\right) + x \left(y + 1\right) - 3$
`_.coeff(x,2)` # (x, n) of $x^n$
$2 - z$
> 

### Cancel

- take any rational function and put it into the standard form
    
    standard canonical form, $p/q$, where $p$ and $q$ are **expanded polnomials** with no **common factors**, and leading coefficients of $p$ and $q$ do not have denominators
    

> $\frac{x^{2} + 2 x + 1}{x^{2} + x}$ 
`cancel(_)`
$\frac{x + 1}{x}$
> 

> $\displaystyle x + \frac{1}{y + \frac{1}{z}}$
`cancel()`
$\displaystyle \frac{x y z + x + z}{y z + 1}$
> 

### Partial function decomposition

> $\frac{x + 3}{x^{2} - 1}$
`apart(_)`
$- \frac{1}{x + 1} + \frac{2}{x - 1}$
> 
- When there are multiple variables
    
    > $\displaystyle \frac{x_{1} + 3}{x_{0}^{2} - 1}$
    `apart(_, x0)` # solves respect to x0
    $\displaystyle - \frac{x_{1} + 3}{2 \left(x_{0} + 1\right)} + \frac{x_{1} + 3}{2 \left(x_{0} - 1\right)}$
    > 

### Trigonometric simplification

> $\operatorname{acos}{\left(x \right)}$
`cos(_)`
$x$
> 
- Simplify
    
     using trigonometric identities (like `simplify()` )
    
    > $\sin^{2}{\left(x \right)} + \cos^{2}{\left(x \right)}$
    `trigsimp(_)`
    $1$
    > 
    
    (also works with hyperbolic functions)
    
- Expand
    
    > $\displaystyle \sin{\left(x + y \right)}$
    `expand_trig(_)`
    $\displaystyle \sin{\left(x \right)} \cos{\left(y \right)} + \sin{\left(y \right)} \cos{\left(x \right)}$
    > 

### Powers

- Simplifications happen only according to assumptions
    
    > `(x**a)**b` → $\displaystyle \left(x^{a}\right)^{b}$ : when a, b, x are Complex
    > 
    
    > `(x**a)**b` → $\displaystyle x^{a b}$: when a, b, x are positive
    > 
- $\displaystyle x^{a} y^{a}$ → $\left(x y\right)^{a}$ and $\  x^{a} x^{b}$ → $x^{a + b}$
    - `powsimp()`
        
        > $\displaystyle x^{a} y^{a}$ ,  $\  x^{a} x^{b}$
        `powsimp(_)` 
        $\left(x y\right)^{a}, x^{a + b}$
        > 
- $\displaystyle x^{a + b}$ → $\displaystyle x^{a} x^{b}$
    
    ```python
    expand_power_exp(_) 
    # only when assumptions valid
    #(or force)
    ```
    
- $\displaystyle \left(x y\right)^{a}$ → $\displaystyle x^{a} y^{a}$
    
    ```python
    expand_power_base(_)
    ```
    
- $\displaystyle \left(x^{a}\right)^{b}$ → $\displaystyle x^{a b}$
    
    `powdenest(_)`
    
- `force` when assumptions aren’t set
    
    `powsimp(_, **force**=**True**)`
    
- When power is a number
    
    $(tz)^2$ →  $\displaystyle t^{2} z^{2}$
    
    ${x^2}{x^3}$ → $\displaystyle x^{5}$ 
    
    will always automatically happen
    

### Logarithms

$log_e(x)$ is `log(x)` or `ln(x)` in SymPy

- Simplifications happen according to assumptions
    
    $log(xy)=log(x)+log(y)$ and
    $log(x^n) = nlog(x)$ are valid only when
    x, y: **`positive** = True` and
    n: **`real** = True`
    
- `expand_log(_)`
    
    $\displaystyle \log{\left(x y \right)}$ → $\displaystyle \log{\left(x \right)} + \log{\left(y \right)}$
    $log(x²)$ → $2log(x)$ 
    
- `logcombine(_)`
    
    opposite of `expand_log(_)`
    
- `force` when assumptions aren’t set
    
    `expand_log(_, **force**=**True**)`
    

### Combinatorial

- Factorial
    
    ```python
    factorial(n) # n!
    factorial(5) # 120
    ```
    
- Binomial
    
    ```python
    binomial(n, r) # nCr
    ```
    
    $\displaystyle {\binom{n}{r}}$
    
- Simplify
    
    > $\displaystyle \frac{n!}{\left(n - 3\right)!}$
    `combsimp(_)`
    $\displaystyle n \left(n - 2\right) \left(n - 1\right)$
    > 

### Expand function

> $\displaystyle {\binom{n}{2}}$
`expand_func(_)`
$\displaystyle \frac{n \left(n - 1\right)}{2}$
> 

### Rewrite

> $\displaystyle \sin{\left(x \right)}$
`_.rewrite(cos)`
$\displaystyle \cos{\left(x - \frac{\pi}{2} \right)}$
> 

### Continued fractions

This note shows a way of solving the problem

```python
from sympy import *
x0, x1, x2, x3, x4 = symbols("x0:5") 

# used to create as a continued fraction
def list_to_frac(l):
    expr = Integer(0) # to make expr a SymPy object
    for i in reversed(l[1:]):
        expr += i
        expr = 1/expr
    return l[0] + expr
```

`expr=` $\displaystyle \frac{x_{0} x_{1} x_{2} x_{3} x_{4} + x_{0} x_{1} x_{3} + x_{0} x_{2} x_{4} + x_{0} + x_{1} x_{2} x_{4} + x_{1} x_{3} x_{4} + x_{1} + x_{4}}{x_{0} x_{1} x_{2} x_{3} + x_{0} x_{2} + x_{1} x_{2} + x_{1} x_{3} + 1}$📘.1

## Calculus

### Limits

$\displaystyle \lim_{x \to 0^+}\left(\frac{\sin{\left(x \right)}}{x}\right)$
`limit(sin(x)/x, x, 0)` → 1

- Unevaluated
    
    **`Limit**((cos(x)-1)/x, x, 0)`
    $\displaystyle \lim_{x \to 0^+}\left(\frac{\cos{\left(x \right)} - 1}{x}\right)$
    `_.doit()`
    $0$
    
- Evaluate a limit one side only
    
    `limit(1/x, x, 0, **'+'**)` → ∞
    
    `limit(1/x, x, 0, '-')` → −∞
    

### Derivatives

```python
expr = cos(x)
diff(expr, x) # −sin(x)
#OR
expr.diff(x) # −sin(x)
```

- Multiple derivatives at once
    
    ```python
    diff(x**4, x, x, x) # 24x
    #Or
    diff(x**4, x, 3) # 24x
    #Or
    diff(exp(x*y*z), x, y, z)
    ```
    
    $\displaystyle \left(x^{2} y^{2} z^{2} + 3 x y z + 1\right) e^{x y z}$
    
- Unevaluated derivative
    
    ```python
    expr = cos(x)
    deriv = Derivative(expr, x)
    # or assign a symbol as a Function instead of a Symbol
    ```
    
    - deriv
        
        $$
        \frac{d}{d x} \cos{\left(x \right)}
        $$
        
    - Evaluate
    `deriv.doit()`
        
        $$
        \sin{\left(x \right)}
        $$
        
- Solve Differential equation
    
    ```python
    x = Symbol('x')
    f = Function('f')
    Eq(f(x).diff(x, x) - 2*f(x).diff(x) + f(x), sin(x))
    ```
    
    $\displaystyle f{\left(x \right)} - 2 \frac{d}{d x} f{\left(x \right)} + \frac{d^{2}}{d x^{2}} f{\left(x \right)} = \sin{\left(x \right)}$
    
    `dsolve(_)`
    
    $\displaystyle f{\left(x \right)} = \left(C_{1} + C_{2} x\right) e^{x} + \frac{\cos{\left(x \right)}}{2}$
    

### Integral

```python
integrate(cos(x), x) # sin(x)
# Note: SymPy doesn't include the constant of integration
```

- To include the constant
    
    solve as a differential equation
    
    ```jsx
    f = Function('f')
    Eq(f(x).diff(x), cos(x))
    ```
    
    $\displaystyle \frac{d}{d x} f{\left(x \right)} = \cos{\left(x \right)}$
    
    `dsolve(_)`
    
    $\displaystyle f{\left(x \right)} = C_{1} + \sin{\left(x \right)}$
    
- Unevaluated integral
    
    `Integral(exp(-x), (x, 0, oo))`
    
    $\displaystyle \int\limits_{0}^{\infty} e^{- x}\, dx$
    `_.doit()` 
    1
    
- Solve definite integral
    
    $\displaystyle \int\limits_{0}^{\infty} e^{- x}\, dx$
    
    ```python
    integrate(exp(-x), (x, 0, oo)) # 1
    # integrate(_, (integration_variable, lower_limit, upper_limit))
    ```
    
- Multiple integral
    
    `Integral(exp(-x**2-y**2), (x, -oo, oo), (y, -oo, oo))`
    $\displaystyle \int\limits_{-\infty}^{\infty}\int\limits_{-\infty}^{\infty} e^{- x^{2} - y^{2}}\, dx\, dy$
    `integrate(exp(-x**2-y**2), (x, -oo, oo), (y, -oo, oo))`
    $\displaystyle \pi$
    
- When unable to compute integral
    
    `integrate(x**x, x)`
    $\displaystyle \int x^{x}\, dx$
    

### Series Expansion

[Ignorant](https://docs.sympy.org/latest/tutorials/intro-tutorial/calculus.html#series-expansion)

### Finite differences

 [Ignorant](https://docs.sympy.org/latest/tutorials/intro-tutorial/calculus.html#finite-differences)

## Solving algebra

use `solveset` instead of `solve`

`solveset(equation, variable=None, domain=S.Complexes)`

```python
solveset(x**2 - x, x) # {0, 1}
```

### Choose domain

```python
solveset(x**3 -3*x**2 +4*x -2, x)
# {1,1−i,1+i}
solveset(x**3 -3*x**2 +4*x -2, x, **domain=S.Reals**)
# {1}
```

### Linear system of equations

In `solveset` the linear part is solved with `linsolve`

- List of equations form
    
    ```python
    linsolve([x + y + z - 1, x + y + 2*z - 3], (x, y, z))
    ```
    
    $\displaystyle \left\{\left( - y - 1, \  y, \  2\right)\right\}$
    
- Augmented Matrix form
    
    `Matrix(([1, 1, 1, 1], [1, 1, 2, 3]))`
    $\displaystyle \left[\begin{matrix}1 & 1 & 1 & 1\\1 & 1 & 2 & 3\end{matrix}\right]$
    `linsolve(_, (x, y, z))`
    $\displaystyle \left\{\left( - y - 1, \  y, \  2\right)\right\}$
    
- A*x = B form
    
    ```python
    m1 = Matrix(([1, 1, 1],[1, 1, 2]))
    m2 = Matrix([1, 3])
    linsolve((m1, m2), x, y, z)
    ```
    
    $\displaystyle \left\{\left( - y - 1, \  y, \  2\right)\right\}$
    

### Non linear system of equations

In `solveset` the linear part is solved with `nonlinsolve`

```python
nonlinsolve((a**2+a, a-b), (a, b)) # {(−1, −1),(0, 0)}
# a=-1,b=-1 or a=0,b=0
# Gives all combinations of solutions for a and b
```

### use `solve` instead of `solveset`

- LambertW solution
- trigonometric functions

### Get roots

```python
# solveset returns each solution once
solveset((x**3 - 6*x**2 + 9*x), x) # {0,3}
roots((x**3 - 6*x**2 + 9*x), x) # {3: 2, 0: 1}
```

### Complex numbers

`z = 1 + 2*I`

- Conjugate
    
    `z = 1 + 2*I`
    `z.conjugate()`
    $1 - 2 i$
    
- Real and imaginary parts
    
    `real, imag = z.as_real_imag()`
    `real` = 1
    
    `imag` = 2
    
- Magnitude(absolute value)
    
    `abs(z)`
    
- Argument(Phase)
    - Angle it makes with the positive real axis
    
    `arg(z)`
    
- Define symbolically
    
    ```jsx
    x, y = symbols('x y', real=True)
    z = x + y*I
    ```
    

### Get a term of a equation

$\displaystyle x^{2} + 2 x + 3$
`_.as_ordered_terms()[2]`
$3$

## Matrices

### Mutable

Matrices are **mutable**

for immutable matrices, use `ImmutableMatrix`

### Create

```python
Matrix(([1, -1], 
        [3, 4], 
        [0, 2]))
```

$\displaystyle \left[\begin{matrix}1 & -1\\3 & 4\\0 & 2\end{matrix}\right]$

- Column vector
    
    `Matrix([1, -1, 3])`
    $\displaystyle \left[\begin{matrix}1\\-1\\3\end{matrix}\right]$
    
- Row vector
    
    `Matrix([[1, -1, 3]])`
    $\displaystyle \left[\begin{matrix}1 & -1 & 3\end{matrix}\right]$
    

### Basic Operations

- Shape
    
    $\displaystyle \left[\begin{matrix}1 & 2 & 3\\-2 & 0 & 4\end{matrix}\right]$
    
    ```python
    shape(_) # (2, 3)
    ```
    
- Access rows and columns
    
    $\displaystyle \left[\begin{matrix}1 & 2 & 3\\-2 & 0 & 4\end{matrix}\right]$
    `_.row(0)`
    $\displaystyle \left[\begin{matrix}1 & 2 & 3\end{matrix}\right]$
    OR
    `_.col(1)`
    $\displaystyle \left[\begin{matrix}2\\0\end{matrix}\right]$
    
- Delete rows and columns
    
    `M = Matrix([[1, 2, 3], [-2, 0, 4]])`
    $\displaystyle \left[\begin{matrix}1 & 2 & 3\\-2 & 0 & 4\end{matrix}\right]$
    `M.col_del(0)`
    $\displaystyle \left[\begin{matrix}2 & 3\\0 & 4\end{matrix}\right]$
    `M.row_del(1)`
    $\displaystyle \left[\begin{matrix}2 & 3\end{matrix}\right]$
    
- Insert rows and columns
    - These operations **do not** operate in-place
        
        `M = Matrix([[2, 3]])`
        $\displaystyle \left[\begin{matrix}2 & 3\end{matrix}\right]$
        `M.row_insert(1, Matrix([[0, 4]]))`
        $\displaystyle \left[\begin{matrix}2 & 3\\0 & 4\end{matrix}\right]$
        `M`
        $\displaystyle \left[\begin{matrix}2 & 3\end{matrix}\right]$
        
    - Insert rows
        
        M = $\displaystyle \left[\begin{matrix}2 & 3\end{matrix}\right]$
        `M = M.row_insert(1, Matrix([[0, 4]]))`
        $\displaystyle \left[\begin{matrix}2 & 3\\0 & 4\end{matrix}\right]$
        
    - Insert columns
        
        `col_insert`
        
- Methods
    
    **Does not** operate in place
    
    `+, *, **` can be done
    
    - Inverse
        
        to find inverse: `**-1` 
        
        $\displaystyle \left[\begin{matrix}0 & 3\\0 & 7\end{matrix}\right]$
        `_**-1`  # NonInvertibleMatrixError 
        
    - Transpose
        
        $\displaystyle \left[\begin{matrix}1 & 2 & 3\\4 & 5 & 6\end{matrix}\right]$
        `_.T`
        $\displaystyle \left[\begin{matrix}1 & 4\\2 & 5\\3 & 6\end{matrix}\right]$
        
    - Determinant
        
        $\displaystyle \left[\begin{matrix}1 & 0 & 1\\2 & -1 & 3\\4 & 3 & 2\end{matrix}\right]$
        `det(_)`
        $\displaystyle -1$
        
    - Adjoint
        
        ```python
        _.adjugate()
        ```
        
    - RREF
        
        `Matrix([[1, 0, 1, 3], [2, 3, 4, 7], [-1, -3, -3, -4]])`
        $\displaystyle \left[\begin{matrix}1 & 0 & 1 & 3\\2 & 3 & 4 & 7\\-1 & -3 & -3 & -4\end{matrix}\right]$
        `_.rref()`
        $\displaystyle \left( \left[\begin{matrix}1 & 0 & 1 & 3\\0 & 1 & \frac{2}{3} & \frac{1}{3}\\0 & 0 & 0 & 0\end{matrix}\right], \  \left( 0, \  1\right)\right)$
        
    - Null-space
        
        `Matrix([[1, 2, 3, 0, 0], [4, 10, 0, 0, 1]])`
        $\displaystyle \left[\begin{matrix}1 & 2 & 3 & 0 & 0\\4 & 10 & 0 & 0 & 1\end{matrix}\right]$
        `m1.nullspace()`
        $\displaystyle \left[ \left[\begin{matrix}-15\\6\\1\\0\\0\end{matrix}\right], \  \left[\begin{matrix}0\\0\\0\\1\\0\end{matrix}\right], \  \left[\begin{matrix}1\\- \frac{1}{2}\\0\\0\\1\end{matrix}\right]\right]$
        
    - Column-space
        
        $\displaystyle \left[\begin{matrix}1 & 1 & 2\\2 & 1 & 3\\3 & 1 & 4\end{matrix}\right]$
        `_.columnspace()`
        $\displaystyle \left[ \left[\begin{matrix}1\\2\\3\end{matrix}\right], \  \left[\begin{matrix}1\\1\\1\end{matrix}\right]\right]$
        
    - [Eigenvalues, Eigenvectors, and Diagonalization](https://docs.sympy.org/latest/tutorials/intro-tutorial/matrices.html#eigenvalues-eigenvectors-and-diagonalization)
    - [Possible Issues](https://docs.sympy.org/latest/tutorials/intro-tutorial/matrices.html#possible-issues)
        - Zero testing
            
            
- Constructors
    - Identity matrix
        
        `eye(3)`
        $\displaystyle \left[\begin{matrix}1 & 0 & 0\\0 & 1 & 0\\0 & 0 & 1\end{matrix}\right]$
        
    - Zeroes
        
        `zeros(2, 3)`
        $\displaystyle \left[\begin{matrix}0 & 0 & 0\\0 & 0 & 0\end{matrix}\right]$
        
    - Ones
        
        `ones(2, 3)`
        $\displaystyle \left[\begin{matrix}1 & 1 & 1\\1 & 1 & 1\end{matrix}\right]$
        
    - Diagonal
        
        `diag(1, 2, 3)`
        $\displaystyle \left[\begin{matrix}1 & 0 & 0\\0 & 2 & 0\\0 & 0 & 3\end{matrix}\right]$
        
        - More complex
            
            `diag(-1, ones(2, 2), Matrix([5, 7, 5]))`
            $\displaystyle \left[\begin{matrix}-1 & 0 & 0 & 0\\0 & 1 & 1 & 0\\0 & 1 & 1 & 0\\0 & 0 & 0 & 5\\0 & 0 & 0 & 7\\0 & 0 & 0 & 5\end{matrix}\right]$
            

### Split

`Martix[rowRange, columnRange]`

$\displaystyle \left[\begin{matrix}1 & 1 & 1 & 1\\1 & 1 & 2 & 3\end{matrix}\right]$
`_[1:2, 1:3]`
$\displaystyle \left[\begin{matrix}1 & 2\end{matrix}\right]$

`_[1,2]`

---

$\displaystyle \left[\begin{matrix}1 & 1 & 1 & 1\\1 & 1 & 2 & 3\end{matrix}\right]$
`_[1,2]`
2

## Advanced expression manipulation

### `srepr`

$\displaystyle x^{2}$
`srepr(_)`
"Pow(Symbol('x'), Integer(2))”

`Pow(Symbol('x'), Integer(2))` #or `Pow(x, 2)`
$\displaystyle x^{2}$

### `func` and `args`

```python
expr = 3*y**2*x
expr.func # sympy.core.mul.Mul
expr.args # (3, x, y**2)
expr.func(*expr.args) # 3*x*y**2

expr.args[2] # y**2
```

- `args`
    
    $\displaystyle - \frac{1}{\left(3 r + 2\right)^{2}} + \frac{1}{\left(3 r - 1\right)^{2}}$
    `_.args[0]`
    $\displaystyle \frac{1}{\left(3 r - 1\right)^{2}}$
    

### Prevent evaluation

`Add(x, x, evaluate=**False**)`

`sympify("x + x", evaluate=**False**)`
$\displaystyle x + x$

- Keep unevaluated
`x + UnevaluatedExpr(x)`
    
    $\displaystyle x + x$
    `_ + 2*x`
    $\displaystyle 3 x + x$
    `_.doit()`
    $\displaystyle 4 x$
    

## Functions

### Define a function

```python
f, g = symbols('f g', cls = Function)
#OR
f = Function('f')
```

### If `x` depends on `t`, then `x` should be a function of `t` instead of a symbol

```python
t, l = symbols('t, l')
x = **Function**('x')
ø = **Function**('ø')
l*cos(ø(t))-x(t)

#OR

x = Function('x')(t)
ø = Function('ø')(t)
l*cos(ø)-x

#OR
x = symbol('x', cls = Function)
```

Read [Documentation](https://docs.sympy.org/latest/tutorials/intro-tutorial/index.html)→API reference → Functions for more

> 💡 Continue from [AEM](https://docs.sympy.org/latest/tutorials/intro-tutorial/manipulation.html#advanced-expression-manipulation)
