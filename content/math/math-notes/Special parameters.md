---
title: "Special parameters"
omit_header_text: true
tags: ["Math", "HGM"]
featured_image: '/images/heymann.png'
categories: ["Math Notes"]
date: 2024-10-08
lastMod: 2024-10-08
---
  + An old paper ([Über hypergeometrische Funktionen, deren letztes
  Element speziell
  ist](https://gdz.sub.uni-goettingen.de/download/pdf/PPN599415665_0044/LOG_0039.pdf))
  by W. Heymann (from a talk by Wadim Zudilin) discusses the value of
  an ${}_2F_1$ at special $t$'s. He does $t=-1/3,1/4,1/5$ and related values and mentions Gauss for $t=1,-1,1/2$ and Kummer for $t=-1/8,1/9,8/9$.

  + For example we have this identity
$$
F_h = F \left( -\frac{h}{2}, -\frac{h}{2} + \frac{1}{2}, h + \frac{3}{2}, -\frac{1}{3} \right)
= \frac{2}{3} \cdot \left( \frac{8}{9} \right)^h \cdot \frac{\Gamma \left( \frac{1}{3} \right) \cdot \Gamma \left( h + \frac{3}{2} \right)}{\sqrt{\pi} \cdot \Gamma \left( h + \frac{4}{3} \right)}
$$
If we take $h=1/2$ we get an HGM defined over $\mathbb Q$, we get the gamma vector $[-4,1,1,2]$ and corresponding Weierstrass model
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
? heymanntr(p,h)=hgm(-1/3,[-h/2,-h/2+1/2],[h+3/2,1],p)
? forprime(p=5,100,print(p,"  ",recognizep(heymanntr(p,1/2)*kronecker(2,p))))
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

  + For $t=4/5$ Heymann has
$$
F\left( \frac{h}{2}, \frac{h}{2} + \frac{1}{2}, 3h, \frac{4}{5} \right) 
= k \cdot \left( \frac{27}{25} \right)^h \cdot \frac{\Gamma \left( h + \frac{1}{3} \right) \Gamma \left( h + \frac{2}{3} \right)}{\Gamma \left( h + \frac{2}{5} \right) \Gamma \left( h + \frac{3}{5} \right)},
\qquad 
h + \frac{1}{3} > 0,
$$
$$
F\left( \frac{h}{2}, \frac{h}{2} + \frac{1}{2}, 3h - 1, \frac{4}{5} \right) 
= k' \cdot \left( \frac{27}{25} \right)^h \cdot \frac{\Gamma \left( h - \frac{1}{3} \right) \Gamma \left( h + \frac{1}{3} \right)}{\Gamma \left( h - \frac{1}{5} \right) \Gamma \left( h + \frac{1}{5} \right)},
\qquad
h - \frac{1}{3} > 0.
$$
For $h=1/2$ we get the Artin HGM $[[1/4,3/4],[1/2,1]]$ with gamma vector $[-4,2,2]$, which has geometric model the Belyi equation
$$
x^2(1-x)^2-2^2\cdot2^2/4^4t.
$$
For $t=4/5$ we get the polynomial
$$
x^4 - 2x^3 + x^2 - 1/20
$$
which gives the cyclotomic field ${\mathbb Q}(\zeta_{20})^+$ with Galois group cyclic of order four. The rhs of the formula corresponds to the Jacobi motive 
$$
[[1/2+1/3,1/2+2/3],[1/2+2/5,1/2+3/5]]
$$
twisted by the quadratic character of ${\mathbb Q}(\sqrt 3)$, times possibly a contribution from the unspecified constant $k$ in the formula (we compute it below).

  + In MAGMA
 ```
 > J:=JacobiMotive([1/2+1/3,1/2+2/3],[1/2+2/5,1/2+3/5]);
 > pv:=PrimesInInterval(7,100);
 > [[p,EulerFactor(J,p)]: p in pv];
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
 BTW, we get exactly the same Euler factors if we take the conjugate
 motive (with parameters $[[1/2+1/3,1/2+2/3],[1/2+1/5,1/2+4/5]]$) 

  + With GP
 ```
? heymantr1(p)=hgm(4/5,[-1/4,1/4],[1/2,1],p)
? forprime(p=7,100,print(p,"  ",recognizep(heymantr1(p))))

  7  0
 11  -2
 13  0
 17  0
 19  2
 23  0
 29  -2
 31  -2
 37  0
 41  2
 43  0
 47  0
 53  0
 59  2
 61  2
 67  0
 71  -2
 73  0
 79  2
 83  0
 89  -2
 97  0
 ```
 The traces agree up to a sign, which does not seem to be a character.
 
 Checking directly against the number field in GP
 ```
 ? f=x^4 - 2*x^3 + x^2 - 1/20
 ? nf=nfinit(f);
   *** nfinit: Warning: nonmonic polynomial. Result of the form [nf,c].
 ? forprime(p=7,100,print(p,"   ",nfeulerfactor(nf,p)/(1-x)/(1-kronecker(20,p)*x)))
 7   x^2 + 1
 11   x^2 + 2*x + 1
 13   x^2 + 1
 17   x^2 + 1
 19   x^2 - 2*x + 1
 23   x^2 + 1
 29   x^2 + 2*x + 1
 31   x^2 + 2*x + 1
 37   x^2 + 1
 41   x^2 - 2*x + 1
 43   x^2 + 1
 47   x^2 + 1
 53   x^2 + 1
 59   x^2 - 2*x + 1
 61   x^2 - 2*x + 1
 67   x^2 + 1
 71   x^2 + 2*x + 1
 73   x^2 + 1
 79   x^2 - 2*x + 1
 83   x^2 + 1
 89   x^2 + 2*x + 1
 97   x^2 + 1
 ```
 This matches the HGM trace.
 
 We can compute the constant $k$ numerically.
 ```
 ? ff=hypseries([1/4,3/4],[1/2,1],500);
 ? a=subst(truncate(ff),x,4/5.)
 1.9021130325903071442328786667587642868
 ? b=gamma(1/2+1/3)*gamma(1/2+2/3)/gamma(1/2+2/5)/gamma(1/2+3/5)
 1.0300566479164914136743113906093968629
 ? c=a/b
 1.8466101223051520415421743456221458944
 ? algdep(c*5/3,4)
 x^4 - 10*x^2 + 5
 ```
 This constant is in the same field ${\mathbb Q}(\zeta_{20})^+$.
 
 Actually the other constants are also algebraic in the same field.
 ```
 ? algdep(a,4)
 x^4 - 5*x^2 + 5
 ? algdep(b*3/5,2)
 x^2 + x - 1
 ```
