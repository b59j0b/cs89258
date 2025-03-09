java c
MACM 401/MATH 801
Assignment 4, Spring 2025.
Due Tuesday March 11th at 11pm. Late Penalty: −10% for each hour late.
Question 1: P-adic Lifting (20 marks)
Reference: Section 6.2 and 6.3.
(a) By hand, determine the p-adic representation of the integer u = 116 for p = 5, first using the positive representation, then using the symmetric representation for Z5.
(b) Theorem 2: Let u, p ∈ Z with p > 2. For simplicity assume p is odd.
If −   < u <      there exist unique integers u0, u1, . . . , un−1 such that u = u0 + u1p + · · · + un−1pn−1 and −   < ui < .
Prove uniqueness.
(c) Determine the cube-root, if it exists, of the following polynomials
a(x) = x6 − 531x5 + 94137x4 − 5598333x3 + 4706850x2 − 1327500x + 125000,
b(x) = x6 − 406 x5 + 94262 x4 − 5598208 x3 + 4706975 x2 − 1327375 x + 125125
using reduction mod 5 and linear p-adic lifting. You will need to derivive the update formula by modifying the update formula for computing the √a(x).
Factor the polynomials so you know what the answers are. Express your the answer in the p-adic representation. To calculate the initial solution u0 = 3√a mod 5 use any method. Use Maple to do all the calculations.
Question 2: Hensel lifting (15 marks)
Reference: Section 6.4 and 6.5.
(a) Given
a(x) = x4 − 2x3 − 233x2 − 214 x + 85
and image polynomials
u0(x) = x2 − 3x − 2 and w0(x) = x2 + x + 3,
satisfying a ≡ u0 w0 (mod 7), lift the image polynomials using Hensel lifting to find (if there exist) u and w in Z[x] such that a = uw.
(b) Given
b(x) = 48x4 − 22x3 + 47x2 + 144
and an image polynomials
u0(x) = x2 + 4x + 2 and w0 = x2 + 4x + 5
satisfying b ≡ 6 u0 w0 (mod 7), lift the image polynomials using Hensel lifting to find (if there exist) u and w in Z[x] such that b = uw.
Question 3: Determinants (25 marks)
Consider the following 3 by 3 matrix A of polynomials in Z[x] and its determinant d.
> P := () -> randpoly(x,degree=2,dense):
> A := Matrix(3,3,P);

> d := LinearAlgebra[Determinant](A);
d := −224262 − 455486x2 + 55203x − 539985x4 + 937816x3 + 463520x6 − 75964x5
(a) (15 marks) Let A by an n by n matrix of polynomials in Z[x] and let d = det(A). Develop a modular algorithm for computing d = det(A) ∈ Z[x]. Your algorithm will compute determi-nants of A modulo a sequence of primes and apply the CRT. For each prime p it will compute the determinant in Zp[x] by evaluation and interpolation. In this way we reduce computation of a determinant of a matrix over Z[x] to many computations of determinants of matrices over Zp, a field, for which ordinary Gaussian elimination, which does O(n3) arithmetic operations in Zp, may be used.
You will need bounds for deg d and ||d||∞. Use primes p = [101, 103, 107, ...] and use Maple to do Chinese remaindering代 写MACM 401/MATH 801 Assignment 4, Spring 2025.Java
代做程序编程语言. Use x = 1, 2, 3, ... for the evaluation points and use Maple for the interpolations.
Present your algorithm as a homomorphism diagram.
Implement your algorithm in Maple and test it on the above example.
To reduce the coefficients of the polynomials in A modulo p in Maple use
> B := A mod p;
To evaluate the polynomials in B at x = α modulo p in Maple use
> C := Eval(B,x=alpha) mod p;
To compute the determinant of a matrix C over Zp in Maple use
> Det(C) mod p;
(b) (10 marks) Suppose A is an n by n matrix over Z[x] and      and |ai,j,k| < Bm. That is A is an n by n matrix of polynomials of degree at most d with coefficients at most m base B digits long. Assume the primes satisfy B < p < 2B and that arithmetic in Zp costs O(1). Estimate the time complexity of your algorithm in big O notation as a function of n, m and d. Make reasonable simplifying assumptions such as n < B and d < B as necessary. State your assumptions. Also helpful is
ln n! < n ln n for n > 1.
Question 4: Lagrange Interpolation (20 marks)
In class we stated the following theorem for polynomial interpolation.
Theorem: Let F be a field. Let (x1, y1),(x2, y2), . . . ,(xn, yn) be n points in F2. If the xi are distinct there exists a unique polynomial f(z) in F[z] satisfying deg(f) ≤ n−1 and f(xi) = yi for 1 ≤ i ≤ n.
Lagrange interpolation is an O(n2) algorithm for computing f(z). It does
1. Expand the product M(z) =   (z − xi).
2. Set Li(z) = M(z)/(z − xi) for 1 ≤ i ≤ n.
3. Set αi = Li(xi) for 1 ≤ i ≤ n.
4. Set βi = yi· αi−1for 1 ≤ i ≤ n.
5. Set f =   βiLi(z).
(a) For F = Z7, x = [1, 2, 3, 4] and y = [0, 5, 5, 0], use Maple’s Interp(x,y,z) mod p; command to find f(z). Now, using Maple as a calculator, execute Steps 1 to 5 to find the interpolating polynomial f(z). I suggest you use Arrays for L, α and β.
(b) Write a Maple procedure INTERP(x,y,z,p) that uses Lagrange interpolation to interpolate f(z) for the field F = Zp, that is, for the integers modulo p. Please print out the Li polyno-mials. Test your Maple procedure on the example in part (a).
(c) Show that Steps 1,2,3, and 5 do O(n2) multiplications in F. Since Step 4 does n multiplica-tions and n inverses in F, conclude that Lagrange interpolation does O(n2) multiplications in F. Please note the following. An obvious way to code Step 1 in Maple for F = Z7
> M := z-x[1] mod 7;
> for i from 2 to n do M := Expand((z-x[i])*M) mod 7; od;
In the loop, at step i, this multiplies (z−xi) by M where    for some coefficients bk ∈ F. This multiplication is special because the factors (z − xk) and M are both monic. To minimize the number of multiplications in F we can use

which needs only i − 1 multiplications xk · bk.







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
