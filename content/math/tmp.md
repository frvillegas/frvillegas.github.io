---
type:
- project
kind:
- Math
project:
- HGM
title: Special parameters
tags:
categories:
date: 2024-10-26
lastMod: 2024-10-26
---
type:: note
kind:: Math
title:: Special parameters, work of Woldemar Heymann 1
author:: Fernando Rodriguez Villegas
project:: HGM
tags:: 
date:: Oct 8th, 2024


  + An old paper

([Über hypergeometrische Funktionen, deren letztes Element speziell ist.](https://gdz.sub.uni-goettingen.de/download/pdf/PPN599415665_0044/LOG_0039.pdf)) (from a talk by Wadym Zudilin) discusses the value of an ${}_2F_1$ at special $t$'s. He does $t=-1/3,1/4,1/5$ and mentions Gauss for $t=1,-1,1/2$ and Kummer for $t=-1/8,1/9,8/9$.

$$
F_h = F \left( -\frac{h}{2}, -\frac{h}{2} + \frac{1}{2}, h + \frac{3}{2}, -\frac{1}{3} \right)
= \frac{2}{3} \cdot \left( \frac{8}{9} \right)^h \cdot \frac{\Gamma \left( \frac{1}{3} \right) \cdot \Gamma \left( h + \frac{3}{2} \right)}{\sqrt{\pi} \cdot \Gamma \left( h + \frac{4}{3} \right)}
$$
If we take $h=1/2$ we get an HGM defined over $\mathbb Q$ with gamma vector $[-4,1,1,2]$ and corresponding Weierstrass model
$$
y^2+xy=x^3+\frac t{64}x.
$$
For $t=-1/3$ we get a curve with $j$-invariant $j(\sqrt{-3})=54000$ and the Frobenius traces match. We recognize the rhs as a Jacobi motive twisted by ${\mathbb Q}(\sqrt{2})$.

  + With MAGMA 
```
> J:=JacobiMotive([1/3],[1/2,1/2+1/3]);
ORDER_IS_SUBFIELD: special root
> J:=TateTwist(J,-1);
ORDER_IS_SUBFIELD: special root
> pv:=PrimesInInterval(5,100);
> [EulerFactor(J,p): p in pv];
[
    5*x^2 + 1,
    7*x^2 - 4*x + 1,
    11*x^2 + 1,
    13*x^2 - 2*x + 1,
    17*x^2 + 1,
    19*x^2 + 8*x + 1,
    23*x^2 + 1,
    29*x^2 + 1,
    31*x^2 - 4*x + 1,
    37*x^2 + 10*x + 1,
    41*x^2 + 1,
    43*x^2 + 8*x + 1,
    47*x^2 + 1,
    53*x^2 + 1,
    59*x^2 + 1,
    61*x^2 - 14*x + 1,
    67*x^2 - 16*x + 1,
    71*x^2 + 1,
    73*x^2 + 10*x + 1,
    79*x^2 - 4*x + 1,
    83*x^2 + 1,
    89*x^2 + 1,
    97*x^2 - 14*x + 1
]
```

  + With GP
```
? heymantr(p,h)=hgm(-1/3,[-h/2,-h/2+1/2],[h+3/2,1],p)
? forprime(p=5,100,print(p,"  ",recognizep(heymantr(p,1/2)*kronecker(2,p))))
5  0
7  4
11  0
13  2
17  0
19  -8
23  0
29  0
31  4
37  -10
41  0
43  -8
47  0
53  0
59  0
61  14
67  16
71  0
73  -10
79  4
83  0
89  0
97  14
```

  + For $t=4/5$ Woldemar Heymann has
    + In MAGMA
 ```
 > J:=JacobiMotive([1/2+1/3,1/2+2/3],[1/2+2/5,1/2+3/5]);
 > pv:=PrimesInInterval(7,100);
 > p,EulerFactor(J,p)]: p in pv];
 [
     [
         7,
         -T^2 + 1
     ],
     [
         11,
         T^2 - 2*T + 1
     ],
     [
         13,
         -T^2 + 1
     ],
     [
         17,
         -T^2 + 1
     ],
     [
         19,
         T^2 - 2*T + 1
     ],
     [
         23,
         -T^2 + 1
     ],
     [
         29,
         T^2 - 2*T + 1
     ],
     [
         31,
         T^2 - 2*T + 1
     ],
     [
         37,
         -T^2 + 1
     ],
     [
         41,
         T^2 - 2*T + 1
     ],
     [
         43,
         -T^2 + 1
     ],
     [
         47,
         -T^2 + 1
     ],
     [
         53,
         -T^2 + 1
     ],
     [
         59,
         T^2 - 2*T + 1
     ],
     [
         61,
         T^2 - 2*T + 1
     ],
     [
         67,
         -T^2 + 1
     ],
     [
         71,
         T^2 - 2*T + 1
     ],
     [
         73,
         -T^2 + 1
     ],
     [
         79,
         T^2 - 2*T + 1
     ],
     [
         83,
         -T^2 + 1
     ],
     [
         89,
         T^2 - 2*T + 1
     ],
     [
         97,
         -T^2 + 1
     ]
 ]
 ```
 BTW, we get exactly the same Euler factors if we take the conjugate motive (with parameters
 $$
 1/2+1/3,1/2+2/3],[1/2+1/5,1/2+4/5
 $$
 )

  + With GP
  + We can compute the constant $k$ numerically.
type:: note
kind:: Math
title:: Special parameters, work of Woldemar Heymann 2
author:: Fernando Rodriguez Villegas
project:: HGM
tags:: Wiman sextic, Robert Fricke, Kummer, Leonid Lachtin
date:: Oct 11th, 2024


  + One thing that Woldemar Heymann doesn't make clear is whether the constants $k,k'$  in his [formula](logseq://graph/FRV-Math?block-id=67065195-717e-4c2c-a158-e0bf0ad15abd) depend on $h$. Earlier he computes it by setting $h=0$ so as suggested it probably does not. (see [note](logseq://graph/FRV-Math?block-id=670f44bc-c29d-4c50-9acc-d552113fa69f))
  + The cases of HGM of rank two have really only two options: weight $0$ (Artin motives) or weight $1$ (curves).

  + Talking to Ariel Pacetti yesterday makes me think again about Edouard Goursat's book on Kummer non-linear differential equation and how to understand it arithmetically. I.e. can one formulate the condition of taking a hypergeometric local system to another in terms of equalities of  traces of motives?

  + Ariel Pacetti's argument I think is that if we have the equality of geometric monodromy then arithmetically the two corresponding motives can only differ by a twist by a rank one motive. Recovering the Galois representation from a geometric one  is some version of a refined Riemman-Hilbert correspondence.

  + Very interesting (and readable) papers by Leonid Lachtin on the  group of order $360$  (isomorphic to $A_6 $) and a degree six equation. 

@The differential resolvent of a degree six equation with a group of order 360
@Differential resolvent for the degree six equation of Anders Wiman of genus $10$.

Lachtin says this (translated by ChatGPT from screenshot)

> *The results obtained by Valentiner and Wiman led me to the idea that there exists an equation of the 6th degree with the group of order 360, whose roots are rational functions of the integrals of a certain linear differential equation of the third order with three singular points. I believe that the key to solving equations of the 6th degree should be sought here, analogous to the solution of equations of the 5th degree, as was provided by Prof. Klein. I intend to elaborate on the results I have found so far and hope to address this question in more detail in the future.*

and in a footnote adds:

> *The present work was already completed when I learned from a letter by Prof. Klein about the existence of an earlier report by Prof. Fricke, which appeared in Volume V of the Annual Report of the German Mathematical Society. At the end of this report, Prof. Fricke discusses almost exactly the same equation of the 6th degree, which I had found a little later. Prof. Fricke mainly addressed the transcendental nature of this problem, without touching on the differential resolvent and some other characteristics of the task. Therefore, I believe that the current communication might still have some value for the mathematical literature.*


He gives an order three differential equation with the Valentiner group ST27 as monodromy group (see section 2 of the first paper):


Using ChatGPT to convert into TeX we get
$$
x^2 (x - 1)^2 \frac{d^3 v}{dx^3} + (6x - 3) x (x - 1) \frac{d^2 v}{dx^2} + 
\left\{ \frac{518}{75} x^2 - \frac{8513}{1200} x + \frac{15}{16} \right\} \frac{dv}{dx} +
\left\{ \frac{616}{675} x - \frac{4389}{4320} \right\} v = 0
$$
Then again ChatGPT to convert to GP code
```
? L=x^2*(x-1)^2*y^3+(6*x-3)*x*(x-1)*y^2+((518/75)*x^2-(8513/1200)*x+15/16)*y+((616/675)*x-4389/4320);
? \r goursat/modular-units-diff-eqn.gp
? diffexponstd(L)
-1/4, 0, 1/4], [-1/2, 0, 1/2], [11/15, 14/15, 4/3
``` 
These exponents match what Leonid Lachtin finds:
((67090411-ca14-4afd-8ac2-40dddb94a266))
And checking against  Beukers-Heckman  @Algebraic hypergeometrric funtions this is a quadratic twist of a twist of BH8.
((6708e349-70c8-420d-a076-8b48c61992f3))

  + Felix Klein kind of puts Leonid Lachtin down in comments (*...in a voluminous work...*)


The Paul Gordan paper Klein mentions should be this one: @On the differential equation of the Valentiner group

Leonid Lachtin ends with an ABC-type polynomial  (giving a Belyi cover)
  + The cover given by both Robert Fricke and Leonid Lachtin look the same. Here's Robert Fricke's
$$
J : J - 1 : 1 =\\
 (\tau - 5)^4 \left( \tau - \frac{5}{2}
\left( 11 \pm 3 \sqrt{-15} \right) \right)^2:\\ 
 \left( \tau^2 - (40 \pm 6 \sqrt{-15}) \tau + 5^4 \right)
\cdot \left( \tau^2 - \left( \frac{35 \pm 9 \sqrt{-15}}{2} \right) \tau \\
- \left( \frac{55 \pm 15\sqrt{-15}}{2} \right)^2 \right):\\
 -\pm 2^8 \cdot 3^4 \cdot 5^2  \sqrt{-15} \tau .
$$

  + The connection between the groups is that the center of the Valentiner group is of order $6$ and the quotient by the center is isomorphic to $A_6$. Both Leonid Lachtin and Robert Fricke start with a sextic curve (not the  Wiman sextic?)


$$
10x^3y^3 + 9z(x^5 + y^5) - 45x^2y^2z^2 - 135xyz^4 + 27z^6
$$
This is the same equation as in Robert Fricke (1), who says:
> *The group of these substitutions reduces modulo 3 to a finite G, which is abstractly identical to the above-mentioned. This definition of G simultaneously provides in the $\zeta$-plane a network of 2.360 triangles of the type (2,4,5) which, when combined, form a Riemann surface of genus 10 with 360 transformations. The corresponding algebraic structure is none other than that represented by equation (1). An advantage of the transcendental approach associated with equation (2) is that the understanding of the structure of  G is particularly easy to achieve from this standpoint. Moreover, the transcendental approach makes it effortlessly possible to explicitly establish both of the resolvents of the sixth degree associated with G, whose existence also plays an important role in Wiman's developments. The form of these resolvents is given as:*

  + 

type:: note
kind:: Math
title:: Special parameters, work of Woldemar Heymann 3
author:: Fernando Rodriguez Villegas
project:: HGM
tags:: Robert Fricke, Ernst Kummer, Leonid Lachtin, monodromy, complex reflection group
date:: Oct 12th, 2024


  + Compute the monodromy representation of the polynomial $F_6$.
GP
```
? f=(x - 5)^4 * (x - 5*(11 + 3*a)/2)^2+t*2^8 * 3^4 * 5^2 * a * x;
? f=f*Mod(1,a^2+15);
? lift(f*conj(f))
x^12 - 150*x^11 + 11325*x^10 - 509000*x^9 + 14771250*x^8 - 274162500*x^7 +
 (-233280000*t + 3316031250)*x^6 + (11080800000*t - 26758125000)*x^5 + 
(-163296000000*t + 145592578125)*x^4 + (1078920000000*t - 528933593750)*x^3
 + (4031078400000*t^2 - 3353400000000*t + 1232431640625)*x^2 + 
(4009500000000*t - 1668750000000)*x + 1000000000000
```

MAGMA
```
> r<y>:=PolynomialRing(Rationals());
> K<a>:=NumberField(y^2+15);        
> f:=x^12 - 150*x^11 + 11325*x^10 - 509000*x^9 + 14771250*x^8 - 274162500*x^7 + (-233280000*t + 3316031250)*x^6 + (11080800000*t - 26758125000)*x^5 + (-163 296000000*t + 145592578125)*x^4 + (1078920000000*t - 528933593750)*x^3 + (4031 078400000*t^2 - 3353400000000*t + 1232431640625)*x^2 + (4009500000000*t - 1668 750000000)*x + 1000000000000;
> M,H,V,D,hv,fv:=monodr(f,K);
> #H;
360
> IdentifyGroup(H);
<360, 118>
> IsIsomorphic(H,AlternatingGroup(6));
true Homomorphism of GrpPerm: H, Degree 12, Order 2^3 * 3^2 * 5 into GrpPerm: $,
Degree 6, Order 2^3 * 3^2 * 5 induced by
    (1, 5)(2, 6)(3, 11)(4, 12) |--> (1, 3)(2, 4)
    (1, 5, 7, 12)(2, 6, 3, 8)(4, 10)(9, 11) |--> (1, 3, 4, 5)(2, 6)
    (1, 4, 10, 12, 7)(2, 8, 11, 9, 3) |--> (1, 5, 2, 6, 4)
> D;
[
    GModule of dimension 1 over K,
    GModule of dimension 1 over K,
    GModule of dimension 5 over K,
    GModule of dimension 5 over K
]
> 
> M;
[
    Closed chain consisting of 4 paths starting at 52.97070910 around 
    1.000000000
    Permutation: (1, 5)(2, 6)(3, 11)(4, 12)
    ,
    Closed chain consisting of 11 paths starting at 52.97070910 around 
    0.0000000000
    Permutation: (1, 5, 7, 12)(2, 6, 3, 8)(4, 10)(9, 11)
    ,
    Closed chain consisting of 15 paths starting at 52.97070910 around Infinity
    Permutation: (1, 4, 10, 12, 7)(2, 8, 11, 9, 3)

]
> fv[2];
[
    [
        <$.1 - 1, 1>
    ],
    [
        <$.1 - 1, 1>
    ],
    [
        <$.1 - 1, 1>
    ]
]
> fv[3];
[
    [
        <$.1 - 1, 3>,
        <$.1 + 1, 2>
    ],
    [
        <$.1 - 1, 1>,
        <$.1 + 1, 2>,
        <$.1^2 + 1, 1>
    ],
    [
        <$.1 - 1, 1>,
        <$.1^4 + $.1^3 + $.1^2 + $.1 + 1, 1>
    ]
]

> hv[3];
[
    [ 0 -1  1  0  0]
    [ 0 -1  0  0  0]
    [ 1 -1  0  0  0]
    [ 0 -1  0  1  0]
    [ 0 -1  0  0  1],

    [-1  0  1  0  0]
    [-1  0  0  0  1]
    [-1  0  0  1  0]
    [-1  0  0  0  0]
    [-1  1  0  0  0],

    [ 0  1  0 -1  0]
    [ 0  0  0 -1  1]
    [ 0  0  1 -1  0]
    [ 1  0  0 -1  0]
    [ 0  0  0 -1  0]
]

```
 In GP (again using ChatGPT with help) we have
```
hv3 = [
    [0, -1, 1, 0, 0; 
     0, -1, 0, 0, 0; 
     1, -1, 0, 0, 0; 
     0, -1, 0, 1, 0; 
     0, -1, 0, 0, 1],

    [-1, 0, 1, 0, 0; 
     -1, 0, 0, 0, 1; 
     -1, 0, 0, 1, 0; 
     -1, 0, 0, 0, 0; 
     -1, 1, 0, 0, 0],

    [0, 1, 0, -1, 0; 
     0, 0, 0, -1, 1; 
     0, 0, 1, -1, 0; 
     1, 0, 0, -1, 0; 
     0, 0, 0, -1, 0]
];

? checkrealroot(3,2],[2,1,1,1],[1,1,1,1,1)
2, 2], [1, 1, 1, 1], [1, 1, 1, 1
```
So we have a real root of $\tilde E_7$.

  + It all has to do with solving the degree six equation along the lines of what Felix Klein did for the quintic. For example we have this paper of Francesco Brioschi: @Sur l'équation du sixième degré (the two cubics form a factorization of the sextic, this is related to the Humbert surface of degree three? i.e. to degree three maps to elliptic curves from the genus two curve determined by the sextic)
  + What I think Leonid Lachtin and Robert Fricke are doing is computing with the Valentiner group as a complex reflection group in rank three. Lachtin describes the (known) invariant ring and finds the differential equation satisfied by the corresponding transcendence degree three extension (polynomial ring over fixed ring). What I didn't know is that there is a system of PDE's for this as well. This is described somewhere. There are five cases of complex reflection groups in rank three. Their smallest degree invariants are: $2,4,6,6,6$. These determine interesting curves with a large symmetry group. The most famous one is of course the degree four Klein curve for $PSL_2({\mathbb F}_7)$. Would be interesting to do the same computations for all cases in all ranks. Why did they expect a cover ramified only at $t=0,1,\infty$? Lachtin affirms it on p. 466 and refers to a previous paper (in Russian). But it seems the guide is always Klein's work, in turn a generalization of Schwartz's work.

id:: 670bd3f6-aaea-46b6-9a52-7a3b81cb49f8
type:: note
kind:: Math
title:: Valentiner group
author:: Fernando Rodriguez Villegas
project:: HGM
tags:: Robert Fricke, Belyi cover, Valentiner, ABC polynomial, Artin motives
date:: Oct 13th, 2024


  + Robert Fricke's book: @Lehrbuch der Algebra (Band 2). Fricke expands on the short [note](logseq://graph/FRV-Math?block-id=670a0b27-9c5e-4f67-8587-d8d5125d8834) above and shows how to compute the Belyi cover  in an interesting way.
  + Tried the simpler case BH5 with monodromy group $A_5$ (=ST23).

GP
```
? hgmmonodr([1/6,5/6,1/2],[1/5,4/5,0])
[31, -12, 1, 0, 12, 0, 1, 1, 0, 0], [-1, 0, 0, -12, 1, 0, 12, 0, 1], [0, 0, -1, 1, 0, 0, 0, 1, 0]
``` 

MAGMA
```
> W:=MatrixGroup<3,GF(31)|-12, 1, 0, 12, 0, 1, 1, 0, 0], [-1, 0, 0, -12, 1, 0, 12, 0, 1], [0, 0, -\
1, 1, 0, 0, 0, 1, 0>;
> W1:=W/Center(W);
> z,phi:=IsIsomorphic(W1,AlternatingGroup(5));
> z;                                          
true
> phi(W1.1);
(1, 3, 4, 2, 5)
> phi(W1.2);
(2, 5)(3, 4)
> phi(W1.3);
(1, 5, 4)
```
From LMFDB: [cover](https://beta.lmfdb.org/Belyi/5T4/5/2.2.1/3.1.1/a/) (adjust singularities to  $t=0,1,\infty$ and replace $x$ by $1/x$)
MAGMA 
```
> R<t,x>:=PolynomialRing(Rationals(),2);
> f:=x^5 - 5*x^4 + 40*x^3 + 1728*t;
> M,H,V,D,hv,fv:=monodr(f,Rationals());
> D;
[
    GModule of dimension 1 over Rational Field,
    GModule of dimension 4 over Rational Field
]
> fv[2];
[
    [
        <x - 1, 2>,
        <x + 1, 2>
    ],
    [
        <x - 1, 2>,
        <x^2 + x + 1, 1>
    ],
    [
        <x^4 + x^3 + x^2 + x + 1, 1>
    ]
]
> CharacterTable(H);

Character Table of Group H
--------------------------
Class |   1  2  3    4    5
Size  |   1 15 20   12   12
Order |   1  2  3    5    5
---------------------------
p  =  2   1  1  3    5    4
p  =  3   1  2  1    5    4
p  =  5   1  2  3    1    1
---------------------------
X.1   +   1  1  1    1    1
X.2   +   3 -1  0   Z1 Z1#2
X.3   +   3 -1  0 Z1#2   Z1
X.4   +   4  0  1   -1   -1
X.5   +   5  1 -1    0    0
```
We can read-off the character values of the $3$-dimensional representations (up to conjugation) from those of the standard representation (of dimension $4$) that we have from the cover. This is an example of a Edouard Goursat G-II rigid local system; it is #2 in Table 1 of our paper with Danylo Radchenko 
 GP
 ```
? f=x^5 - 5*x^4 + 40*x^3 + 1728*t;
? d=poldisc(f);
? factor(content(d))
[2 24]
[3 12]
[5  5]
?  factor(d)
[t - 1 2]
[    t 2]
```
So there is a twist by ${\mathbb Q}(\sqrt 5)$. But the $\pm 1$ factor in the monodromy seems to include $\sqrt{1-t}$.  More precisely, we want $\pm\epsilon(p)$, where $\epsilon$ is the character of ${\mathbb Q}(\sqrt{1-t})$ and $p\equiv \pm1 \bmod 5$.

Checking Euler factors: 
GP
```
? fu(t,p)= z=polrecognizep(hgmfrob(t,[1/6,5/6,1/2],[1/5,4/5,0],p)*hgmfrob(t,[1/6,5/6,1/2],[2/5,3/5,0],p));polexpon(z)
? gu(t,p)=polfacttype(x^5 - 5*x^4 + 40*x^3 + 1728*t,p);

? for(t=2,10,print(t,"  ",kronecker(1-t,11),"  ",fu(t,11),"   ",gu(1/t,11)))
2  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
3  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
4  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
5  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
6  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
7  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
8  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
9  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
10  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]

? for(t=2,18,print(t,"  ",-kronecker(1-t,19),"  ",fu(t,19),"   ",gu(1/t,19)))
2  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
3  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
4  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
5  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
6  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
7  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
8  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
9  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
10  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
11  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
12  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
13  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
14  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
15  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
16  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
17  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
18  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]

? for(t=2,28,print(t,"  ",-kronecker(1-t,29),"  ",fu(t,29),"   ",gu(1/t,29)))
2  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
3  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
4  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
5  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
6  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
7  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
8  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
9  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
10  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
11  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
12  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
13  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
14  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
15  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
16  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
17  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
18  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
19  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
20  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
21  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
22  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
23  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
24  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
25  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
26  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
27  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
28  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]

? for(t=2,30,print(t,"  ",kronecker(1-t,31),"  ",fu(t,31),"   ",gu(1/t,31)))
2  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
3  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
4  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
5  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
6  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
7  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
8  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
9  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
10  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
11  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
12  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
13  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
14  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
15  -1  [1/6, 1/6, 1/2, 1/2, 5/6, 5/6]   [3, 1, 1]
16  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
17  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
18  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
19  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
20  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
21  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
22  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
23  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
24  1  [0, 0, 1/3, 1/3, 2/3, 2/3]   [3, 1, 1]
25  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
26  -1  [1/10, 3/10, 1/2, 1/2, 7/10, 9/10]   [5]
27  1  [0, 0, 1/2, 1/2, 1/2, 1/2]   [2, 2, 1]
28  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
29  -1  [0, 0, 0, 0, 1/2, 1/2]   [2, 2, 1]
30  1  [0, 0, 1/5, 2/5, 3/5, 4/5]   [5]
```

type:: note
kind:: Math
title:: Constant in Woldemar Heymann's identity
author:: Fernando Rodriguez Villegas
project:: HGM
date:: Oct 16th, 2024


  + Computing numerically the constant $k$ (see [note1](logseq://graph/FRV-Math?block-id=670f472a-95cb-4cf1-b16f-4187c93c89f4) and [note2](logseq://graph/FRV-Math?block-id=670e00fd-413d-4eff-93d7-897bbaf75ea8))
  + We try check the identity of motives from Woldemar Heymann for $h=1/3$. The HGM parameters are 
$[1/6,2/3],[1,1]$ and corresponding curve exponents
```
? hgmcurveexpon(1/6,2/3,1)
[1/3, 2/3, 1/6, 5/6]
```
The corresponding new part of the Euler curve is of dimension two.
```
> A<x,y>:=AffineSpace(Rationals(),2);
> C6:=Curve(A,y^6-x^4*(x-1)^2*(x-4/5));
> C3:=Curve(A,y^3-x^4*(x-1)^2*(x-4/5));
> Genus(C6);
4
> Genus(C3);
2
```
Computing the Euler factors of the HGM 
```
? fu(p)=polrecognizep(hgmfrob(4/5,[1/6,2/3],[1,1],p)*hgmfrob(4/5,-[1/6,2/3],[1,1],p))

? forprime(p=5,100,if(p%3==1,z=fu(p);if(p%5==1||p%5==4,print(p"  ",z,"  ",nfdisc(z)),print(p,"   ",z))))
7   49*x^4 + 7*x^2 + 1
13   169*x^4 - 26*x^2 + 1
19  361*x^4 - 76*x^3 - 3*x^2 - 4*x + 1  225
31  961*x^4 + 248*x^3 + 33*x^2 + 8*x + 1  225
37   1369*x^4 + 37*x^2 + 1
43   1849*x^4 + 43*x^2 + 1
61  3721*x^4 + 122*x^3 - 57*x^2 + 2*x + 1  225
67   4489*x^4 - 134*x^2 + 1
73   5329*x^4 + 73*x^2 + 1
79  6241*x^4 - 1264*x^3 + 177*x^2 - 16*x + 1  225
97   9409*x^4 + 97*x^2 + 1
```
For $p\equiv \pm 1 \bmod 5$ we get Euler factors defining the field ${\mathbb Q}(\zeta_{15})^+$. Compare to the right hand side.
```
? gu(p)=
{	
	teichmuller(27/25+O(p^20))^(-(p-1)/3)
	*gamma(frac(1/3+1/3)+O(p^20))
	*gamma(frac(1/3+2/3)+O(p^20))
	/gamma(frac0(1/3+2/5)+O(p^20))
	/gamma(frac0(1/3+3/5)+O(p^20))
	*gamma(1/3+O(p^20))
	*gamma(2/3+O(p^20))
	/gamma(2/5+O(p^20))
	/gamma(3/5+O(p^20))
;}

? forprime(p=5,100,if(p%3==1 &&(p%5==1||p%5==4),print(p"  ",algdep(gu(p),4))))
19  x^4 + 4*x^3 - 3*x^2 + 76*x + 361
31  x^4 - 8*x^3 + 33*x^2 - 248*x + 961
61  x^4 - 2*x^3 - 57*x^2 - 122*x + 3721
79  x^4 + 16*x^3 + 177*x^2 + 1264*x + 6241
```
There seems to just be a global sign difference.
```
> J:=JacobiMotive([1/3,2/3,1/3+1/3,1/3+2/3],[2/5,3/5,1/3+2/5,1/3+3/5]); J:=TateTwist(J,-1);
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root

> pv:=[19, 31, 61, 79, 109, 139, 151, 181, 199];
> [EulerFactor(J,p): p in pv];                  
[
    361*T^4 - 76*T^3 - 3*T^2 - 4*T + 1,
    961*T^4 + 248*T^3 + 33*T^2 + 8*T + 1,
    3721*T^4 + 122*T^3 - 57*T^2 + 2*T + 1,
    6241*T^4 - 1264*T^3 + 177*T^2 - 16*T + 1,
    11881*T^4 + 1526*T^3 + 87*T^2 + 14*T + 1,
    19321*T^4 - 556*T^3 - 123*T^2 - 4*T + 1,
    22801*T^4 + 1208*T^3 - 87*T^2 + 8*T + 1,
    32761*T^4 + 7964*T^3 + 846*T^2 + 44*T + 1,
    39601*T^4 + 6368*T^3 + 654*T^2 + 32*T + 1
]

```
Confirms the HGM traces. The cubic character does not play a role? Somehow it is incorporated in the Jacobi motive.
```
? forprime(p=5,200,if(p%3==<1 &&(p%5==1||p%5==4),z=fu(p);print(p"  ",z)))
19  361*x^4 - 76*x^3 - 3*x^2 - 4*x + 1
31  961*x^4 + 248*x^3 + 33*x^2 + 8*x + 1
61  3721*x^4 + 122*x^3 - 57*x^2 + 2*x + 1
79  6241*x^4 - 1264*x^3 + 177*x^2 - 16*x + 1
109  11881*x^4 + 1526*x^3 + 87*x^2 + 14*x + 1
139  19321*x^4 - 556*x^3 - 123*x^2 - 4*x + 1
151  22801*x^4 + 1208*x^3 - 87*x^2 + 8*x + 1
181  32761*x^4 + 7964*x^3 + 846*x^2 + 44*x + 1
199  39601*x^4 + 6368*x^3 + 654*x^2 + 32*x + 1
```
It works for the other primes as well (here $p\equiv 1 \bmod 3$)
```
> pv:=[7, 13, 19, 31, 37, 43, 61, 67, 73, 79, 97];
> [EulerFactor(J,p): p in pv];                    
[
    49*T^4 + 7*T^2 + 1,
    169*T^4 - 26*T^2 + 1,
    361*T^4 - 76*T^3 - 3*T^2 - 4*T + 1,
    961*T^4 + 248*T^3 + 33*T^2 + 8*T + 1,
    1369*T^4 + 37*T^2 + 1,
    1849*T^4 + 43*T^2 + 1,
    3721*T^4 + 122*T^3 - 57*T^2 + 2*T + 1,
    4489*T^4 - 134*T^2 + 1,
    5329*T^4 + 73*T^2 + 1,
    6241*T^4 - 1264*T^3 + 177*T^2 - 16*T + 1,
    9409*T^4 + 97*T^2 + 1
]
```
and
```
? forprime(p=5,100,if(p%3==1,z=fu(p);print(p"  ",z)))
7  49*x^4 + 7*x^2 + 1
13  169*x^4 - 26*x^2 + 1
19  361*x^4 - 76*x^3 - 3*x^2 - 4*x + 1
31  961*x^4 + 248*x^3 + 33*x^2 + 8*x + 1
37  1369*x^4 + 37*x^2 + 1
43  1849*x^4 + 43*x^2 + 1
61  3721*x^4 + 122*x^3 - 57*x^2 + 2*x + 1
67  4489*x^4 - 134*x^2 + 1
73  5329*x^4 + 73*x^2 + 1
79  6241*x^4 - 1264*x^3 + 177*x^2 - 16*x + 1
97  9409*x^4 + 97*x^2 + 1
```

  + For $h=1/6$ we get the HGM  $[1/12,7/12],[1/2,1]$ with Hodge numbers $[2],[2]$. The geometric monodromy group is $(72,30)$ with center of order $6$. The hypergeometric series satisfies
```
? ff=hypseries([1/12,7/12],[1/2,1],500);
? ff6=ff^6;
? F=seralgdep(subst(ff6,x,y),6,6)
(1073741824*y^6 - 6442450944*y^5 + 16106127360*y^4 - 21474836480*y^3 + 16106127360*y^2 - 6442450944*y + 1073741824)*x^6 + (201326592*y^5 - 1006632960*y^4 + 2013265920*y^3 - 2013265920*y^2 + 1006632960*y - 201326592)*x^5 + (725090304*y^5 - 3609722880*y^4 + 7187988480*y^3 - 7156531200*y^2 + 3562536960*y - 709361664)*x^4 + (-168148992*y^4 + 673251328*y^3 - 1010860032*y^2 + 674562048*y - 168804352)*x^3 + (11067456*y^4 - 38984448*y^3 + 50563968*y^2 - 28444416*y + 5797440)*x^2 + (24816*y^3 - 96096*y^2 + 117936*y - 46656)*x + y^3
? F=substvec(F,[x,y],[x^6,t])
(1073741824*t^6 - 6442450944*t^5 + 16106127360*t^4 - 21474836480*t^3 + 16106127360*t^2 - 6442450944*t + 1073741824)*x^36 + (201326592*t^5 - 1006632960*t^4 + 2013265920*t^3 - 2013265920*t^2 + 1006632960*t - 201326592)*x^30 + (725090304*t^5 - 3609722880*t^4 + 7187988480*t^3 - 7156531200*t^2 + 3562536960*t - 709361664)*x^24 + (-168148992*t^4 + 673251328*t^3 - 1010860032*t^2 + 674562048*t - 168804352)*x^18 + (11067456*t^4 - 38984448*t^3 + 50563968*t^2 - 28444416*t + 5797440)*x^12 + (24816*t^3 - 96096*t^2 + 117936*t - 46656)*x^6 + t^3
```
The Galois group is for $t=19$ (generic value, apply `polredbest`) the [group](https://people.maths.bris.ac.uk/~matyd/GroupNames/129/Dic3sD6.html)
```
> f:=x^36 - 12*x^30 + 49848*x^24 + 738776*x^18 + 57515748*x^12 - 7650912*x^6 + 438976;
> G:=GaloisGroup(f);                                                           
> #G;                                                                          
144
> IdentifyGroup(G);
<144, 154>
```
For $t=4/5$ instead we get (apply `polredbest`) the [group](https://people.maths.bris.ac.uk/~matyd/GroupNames/1/C4xS3.html)
```
> h:=x^36 - 60*x^30 - 12330*x^24 - 1046300*x^18 - 5849775*x^12 - 17232000*x^6 + 512000;
> G:=GaloisGroup(h);                                                           
> #G;                                                                          
24
> IdentifyGroup(G);                                                            
<24, 5>
```
 
Evaluating $F$ at $t=4/5$ and comparing Euler factors we have
```
? h=x^36 - 60*x^30 - 12330*x^24 - 1046300*x^18 - 5849775*x^12 - 17232000*x^6 + 512000;
? fu1(p,f=1)=polrecognizep(hgmfrob(4/5,[1/12,7/12],[1/2,1],p,f)*hgmfrob(4/5,-[1/12,7/12],[1/2,1],p,f))

? forprime(p=5,200,if(p%3==1,z=fu1(p);print(p"  ",polexpon(z),"  ",polfacttype(h,p))))
7  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
13  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4, 4, 4, 4, 4, 4, 4]
19  [1/3, 1/3, 2/3, 2/3]  []
31  [1/6, 1/6, 5/6, 5/6]  []
37  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
43  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
61  [1/3, 1/3, 2/3, 2/3]  []
67  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4, 4, 4, 4, 4, 4, 4]
73  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
79  [1/3, 1/3, 2/3, 2/3]  [3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3]
97  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
103  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
109  [1/6, 1/6, 5/6, 5/6]  [6, 6, 6, 6, 6, 6]
127  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4, 4, 4, 4, 4, 4, 4]
139  [1/3, 1/3, 2/3, 2/3]  [3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3]
151  [1/6, 1/6, 5/6, 5/6]  [6, 6, 6, 6, 6, 6]
157  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
163  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4, 4, 4, 4, 4, 4, 4]
181  [0, 0, 0, 0]  [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
193  [1/12, 5/12, 7/12, 11/12]  [12, 12, 12]
199  [0, 0, 0, 0]  [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```
Actually $h$ is reducible!
```
? factor(h)
[                              x^12 - 170*x^6 + 5 1]
[x^24 + 110*x^18 + 6365*x^12 + 35200*x^6 + 102400 1]
```
Let these factors be $h1,h2$. They both have the same Galois closure , in fact $h1$ determines a subfield of that determined by $h2$.
```
? forprime(p=5,100,if(p%3==1,z=fu1(p);print(p"  ",polexpon(z),"  ",polfacttype(h1,p))))
7  [1/12, 5/12, 7/12, 11/12]  [12]
13  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4]
19  [1/3, 1/3, 2/3, 2/3]  []
31  [1/6, 1/6, 5/6, 5/6]  [6, 6]
37  [1/12, 5/12, 7/12, 11/12]  [12]
43  [1/12, 5/12, 7/12, 11/12]  [12]
61  [1/3, 1/3, 2/3, 2/3]  [3, 3, 3, 3]
67  [1/4, 1/4, 3/4, 3/4]  [4, 4, 4]
73  [1/12, 5/12, 7/12, 11/12]  [12]
79  [1/3, 1/3, 2/3, 2/3]  [3, 3, 3, 3]
97  [1/12, 5/12, 7/12, 11/12]  [12]
```
Note that the degree polynomial $x^4 - 170x^2 + 5$ has Galois group $C_4$ .
```
? polgalois(x^4 - 170*x^2 + 5)
[4, -1, 1, "C(4) = 4"]
```

  + The Jacobi motive is 

$$
[1/3,2/3,1/2,5/6], [2/5,3/5,17/30,23/30]
$$
With GP get the exponents of the roots
```
7  -1  [1/12, 5/12, 7/12, 11/12]
13  1  [1/4, 1/4, 3/4, 3/4]
19  -1  [1/6, 1/6, 5/6, 5/6]
31  -1  [1/3, 1/3, 2/3, 2/3]
37  1  [1/12, 5/12, 7/12, 11/12]
43  -1  [1/12, 5/12, 7/12, 11/12]
61  1  [1/3, 1/3, 2/3, 2/3]
67  -1  [1/4, 1/4, 3/4, 3/4]
73  1  [1/12, 5/12, 7/12, 11/12]
79  -1  [1/6, 1/6, 5/6, 5/6]
97  1  [1/12, 5/12, 7/12, 11/12]
103  -1  [1/12, 5/12, 7/12, 11/12]
109  1  [1/6, 1/6, 5/6, 5/6]
127  -1  [1/4, 1/4, 3/4, 3/4]
139  -1  [1/6, 1/6, 5/6, 5/6]
151  -1  [1/3, 1/3, 2/3, 2/3]
157  1  [1/12, 5/12, 7/12, 11/12]
163  -1  [1/4, 1/4, 3/4, 3/4]
181  1  [0, 0, 0, 0]
193  1  [1/12, 5/12, 7/12, 11/12]
199  -1  [1/2, 1/2, 1/2, 1/2]
```
We are off by the Kronecker symbol at $-4$.

```
> J:=JacobiMotive([1/3,2/3,1/2,5/6],[2/5,3/5,17/30,23/30]);
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root
ORDER_IS_SUBFIELD: special root
> pv:=PrimesInInterval(7,200);
> p,EulerFactor(J,p)]: p in pv];
[
    [
        7,
        T^4 - T^2 + 1
    ],
    [
        11,
        T^4 - 2*T^2 + 1
    ],
    [
        13,
        T^4 + 2*T^2 + 1
    ],
    [
        17,
        T^4 + 2*T^2 + 1
    ],
    [
        19,
        T^4 - 2*T^3 + 3*T^2 - 2*T + 1
    ],
    [
        23,
        T^4 + 2*T^2 + 1
    ],
    [
        29,
        T^4 - 2*T^2 + 1
    ],
    [
        31,
        T^4 + 2*T^3 + 3*T^2 + 2*T + 1
    ],
    [
        37,
        T^4 - T^2 + 1
    ],
    [
        41,
        T^4 - 2*T^2 + 1
    ],
    [
        43,
        T^4 - T^2 + 1
    ],
    [
        47,
        T^4 + 2*T^2 + 1
    ],
    [
        53,
        T^4 + 2*T^2 + 1
    ],
    [
        59,
        T^4 - 2*T^2 + 1
    ],
    [
        61,
        T^4 + 2*T^3 + 3*T^2 + 2*T + 1
    ],
    [
        67,
        T^4 + 2*T^2 + 1
    ],
    [
        71,
        T^4 - 2*T^2 + 1
    ],
    [
        73,
        T^4 - T^2 + 1
    ],
    [
        79,
        T^4 - 2*T^3 + 3*T^2 - 2*T + 1
    ],
    [
        83,
        T^4 + 2*T^2 + 1
    ],
    [
        89,
        T^4 - 2*T^2 + 1
    ],
    [
        97,
        T^4 - T^2 + 1
    ],
    [
        101,
        T^4 - 2*T^2 + 1
    ],
    [
        103,
        T^4 - T^2 + 1
    ],
    [
        107,
        T^4 + 2*T^2 + 1
    ],
    [
        109,
        T^4 - 2*T^3 + 3*T^2 - 2*T + 1
    ],
    [
        113,
        T^4 + 2*T^2 + 1
    ],
    [
        127,
        T^4 + 2*T^2 + 1
    ],
    [
        131,
        T^4 - 2*T^2 + 1
    ],
    [
        137,
        T^4 + 2*T^2 + 1
    ],
    [
        139,
        T^4 - 2*T^3 + 3*T^2 - 2*T + 1
    ],
    [
        149,
        T^4 - 2*T^2 + 1
    ],
    [
        151,
        T^4 + 2*T^3 + 3*T^2 + 2*T + 1
    ],
    [
        157,
        T^4 - T^2 + 1
    ],
    [
        163,
        T^4 + 2*T^2 + 1
    ],
    [
        167,
        T^4 + 2*T^2 + 1
    ],
    [
        173,
        T^4 + 2*T^2 + 1
    ],
    [
        179,
        T^4 - 2*T^2 + 1
    ],
    [
        181,
        T^4 - 4*T^3 + 6*T^2 - 4*T + 1
    ],
    [
        191,
        T^4 - 2*T^2 + 1
    ],
    [
        193,
        T^4 - T^2 + 1
    ],
    [
        197,
        T^4 + 2*T^2 + 1
    ],
    [
        199,
        T^4 + 4*T^3 + 6*T^2 + 4*T + 1
    ]
]
```
