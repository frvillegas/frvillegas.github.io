? heymantr1(p)=hgm(4/5,[-1/4,3/4],[1/2,1],p)

? forprime(p=7,500,if(p%20==1,print(p,"  ",recognizep(heymantr1(p)))))

41  2
61  2
101  2
181  2
241  2
281  2
401  2
421  2
461  2

? quartchar(p)=pv=[1,3,7,9,11,13,17,19];cv=[1,I,-I,-1,-1,-I,I,1];cv[memb(p%20,pv)]

? forprime(p=7,100,print(p,"  ",recognizep(heymantr1(p))*quartchar(p)))
7  0
11  2
13  0
17  0
19  2
23  0
29  2
31  2
37  0
41  2
43  0
47  0
53  0
59  2
61  2
67  0
71  2
73  0
79  2
83  0
89  2
97  0
