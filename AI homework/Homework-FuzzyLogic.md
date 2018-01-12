### AAI-Homework

---

**(1) Consider two fuzzy subsets of the set X， X = {a, b, c, d,e}. referred to as A and B.                             A={1/a, 0.3/b,0.2/c,0.8/d,0/e} and                                                                                                                                                B = {0.6/a, 0.9/b, 0.1/c, 0.3/d, 0.2/e}**
**Calculate the following : Support, Core, Cardinality, Complement, Union,Intersection, $\alpha A (\alpha =0.5), A^\alpha (\alpha =0.2), \alpha-cut (A_{0.2}, A_{0.3}, A_{0.8}, A_{1})$**

*Sol* 

$supp(A)  = \{a, b, c, d\}$,     $Core(A) = \{a\}$      $card(A) = 1+0.3+0.2+0.8=2.3$ 
$supp(B)  = \{a, b, c, d, e\}$, $Core(B) = \{\}$        $card(B) = 0.6+0.9+0.1+0.3+0.2 = 2.1$
$Comp(A) = \{0/a, 0.7/b, 0.8/c, 0.2/d, 1/e\}$   $Comp(B) = \{0.4/a, 0.1/b, 0.9/c, 0.7/d, 0.8/e\}$

Intersection: $A\bigcap B = \{0.6/a, 0.3/b, 0.1/c, 0.3/d, 0/e\} $

Union: $A\bigcup B = \{1/a,0.9/b,0.2/c,0.8/d,0.2/e\}$

$0.5A = \{ 0.5/a, 0.15/b,0.1/c,0.4/d,0/e\}$ 

$A^{0.2} =\{1/a, 0.786/b,0.725/c,0.956/d,0/e\} $

$A_{0.2} = \{a,b,c,d\}$

$A_{0.3} = \{a,b,d\}$

$A_{0.8} = \{a,d\}$

$A_{1} = \{a\}$



*problem 2 is in the back*

<div style="page-break-before: always;"> </div>

**(2) For**   $A = {0.2/a, 0.4/b, 1/c, 0.8/d, 0/e}$       $B = {0/a, 0.9/b, 0.3/c, 0.2/d, 0.1/e}$

**Draw the Fuzzy Graph of A and B. Then calculate the following**

- **Support, Core, Cardinality, and Complement for A and B independently**
- **Union and Intersection of A and B**
- **the new set C, if C = A2**
- **the new set D, if D = 0.5∙B**
- **the new set E, for an alpha cut at $A_{0.5}$**

*Sol*

$Supp(A) = \{a,b,c,d\}$  $Supp(B) = \{b,c,d,e\}$

$Core(A) = \{c\}$  $Core(B) = \{\}$

$Card(A) = 0.2+0.4+1+0.8=2.4$  $Card(B) = 0+0.9+0.3+0.2+0.1=1.5$

$Comp(A) = \{0.8/a,0.6/b,0/c,0.2/d,1/e\}$  $Comp(B) = \{1/a,0.1/b,0.7/c,0.8/d,0.9/e\}$

Intersection: $A\bigcap B = \{0/a, 0.4/b, 0.3/c, 0.2/d, 0/e\} $

Union: $A\bigcup B = \{0.2/a,0.9/b,1/c,0.8/d,0.1/e\}$

$C = A^2= \{0.04/a,0.16/b,1/c,0.64/d,0/e\}​$

$B = 0.5\cdot B= \{0/a,0.45/b,0.15/c,0.1/d,0.05/e\}$

$E = A_{0.5}= \{c,d\}$



