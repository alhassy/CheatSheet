<h1> CheatSheet </h1>

Pretty cheat sheets, or \`\`reference cards'', obtainable from Org files.

**The listing sheet, as PDF, can be found [here](https://github.com/alhassy/CheatSheet/blob/master/CheatSheet.pdf)**, while below is a quick-n-dirty html rendition.

<object width="600" height="400" data="CheatSheet.pdf"></object>


# Table of Contents

1.  [Hello, World!](#orgaa44d92)
2.  [Propositional Calculus](#org858e046)
3.  [Loops implement finite quantifications](#orgf0758a5)












<a id="orgaa44d92"></a>

# Hello, World!

-   **Pretty PDF:** Enter `M-x compile` to produce a nice looking PDF of your reference sheet.
    -   I've bound this command to `C-c C-m` in my Emacs setup ;-)

-   **Section Headers:** A usual Org header, say `* my section`, results in the boxed headers
    used in this cheat sheet.

-   **Parallel Environments:** The sequence `<p TAB` produces a \`parallel' environment for
    producing text side-by-side. The column break is automatic, but as 
    this is sugar for a `minipage` containing a `multicolum` we can force a column
    separation with `\columnbreak`: This command, in Org, necessities newlines between
    the items being separated.

\vspace{1em}
To learn more, manipulating this source is the way to go!


<a id="org858e046"></a>

# Propositional Calculus

-   **Metatheorem:** Any two theorems are equivalent; \` \(\true\) ' is a theorem.

[<span class="underline">Equivales</span>](https://ac.els-cdn.com/S0020019000002052/1-s2.0-S0020019000002052-main.pdf?_tid=35e86bb2-edb0-11e7-b1fe-00000aab0f26&acdnat=1514672861_56b3d86466d284cbc76cc2641c47af86) is an equivalence relation that is associative &#x2014; \(((p \equiv q) \equiv r)\equivs(p \equiv (q \equiv r))\) &#x2014;
and has identity \(\true\).

\underline{Discrepancy} \` \(\not\equiv\) ' is symmetric, associative, has identity \` \(\false\) ',
mutually associates with equivales &#x2014; \(((p \not\equiv q) \equiv r) \equivs (p \not\equiv (q \equiv r))\) &#x2014;
and mutually interchanges with it as well
&#x2014; \(p \not\equiv q \equiv r \equivs    p \equiv q \not\equiv r\) &#x2014;.

\vspace{1ex}

\underline{Implication} has the alternative definition \(p \implies q \;\equiv\; \lnot p \lor q\),
has \(\true\) as left identity and \(\false\) as right zero,
distributes over \(\equiv\) in the second argument, and is self-distributive;
and has the properties

<div class="parallelNB">
-   **Shunting:** \invisible{hi}\vspace{-0.5em}
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    </colgroup>
    <tbody>
    <tr>
    <td class="org-left">$ p &and; q \implies r \equivS  p \implies (q \implies r)$</td>
    </tr>
    </tbody>
    </table>

-   **Contrapositive:** \invisible{hi}\vspace{-0.5em}
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    </colgroup>
    <tbody>
    <tr>
    <td class="org-left">$ p \implies q \quad&equiv;\quad \lnot q \implies \lnot p$</td>
    </tr>
    </tbody>
    </table>

\columnbreak

-   **Modus Ponens:** \invisible{hi}\vspace{-2em}    
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    
    <col  class="org-left" />
    
    <col  class="org-left" />
    </colgroup>
    <tbody>
    <tr>
    <td class="org-left">\(p \land (p \implies q)\)</td>
    <td class="org-left">&equiv;</td>
    <td class="org-left">\(p \land q\)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">\(p \land (q \implies p)\)</td>
    <td class="org-left">&equiv;</td>
    <td class="org-left">\(p\)</td>
    </tr>
    
    
    <tr>
    <td class="org-left">\(p \land (p \implies q)\)</td>
    <td class="org-left">\implies</td>
    <td class="org-left">\(q\)</td>
    </tr>
    </tbody>
    </table>

</div>

Moreover it has the useful property \`\`(3.62)'': 
 \(p \implies (q \equiv r) \equivS p \land q    \equivs    p \land r\).

\vspace{1ex}
\underline{Conjunction and disjunction} distribute over one another,
\(\lor\) distributes over \(\equiv\),
\(\land\) distributes over \(\equiv-\equiv\)
in that \(p \land (q \equiv r \equiv s) \equivS p \land q \equivs p \land r  \equivs p \land s\),
and they satisfy,

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">**Excluded Middle**</td>
<td class="org-left">**Contradiction**</td>
<td class="org-left">**Absorption**</td>
<td class="org-left">**De Morgan**</td>
</tr>


<tr>
<td class="org-left">\(p \lor \lnot p\)</td>
<td class="org-left">\(p \land \lnot p \equiv~\false\)</td>
<td class="org-left">\(p \land (\lnot p \lor q) \equiv p \land q\)</td>
<td class="org-left">\(\lnot (p \land q) \equiv \lnot p \lor  \lnot q\)</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
<td class="org-left">\(p \lor (\lnot p \land q) \equiv p \lor  q\)</td>
<td class="org-left">\(\lnot (p \lor q)  \equiv \lnot p \land \lnot q\)</td>
</tr>
</tbody>
</table>


<a id="orgf0758a5"></a>

# [Loops implement finite quantifications](https://frama-c.com/)

A finite quantification can be defined axiomatically
by the empty-range rule and split-off term rules.
Together these form a recursive definition which can be phrased as a loop.

<div class="parallel">


    // For -⊕- : 𝑻 → 𝑻 → 𝑻,
    // fold(A,a,b) ≈ (⊕ x : a..b-1 • A[x]) 
    /*@ axiomatic Fold { 
      @   
      @ logic 𝑻
      @   fold{L}(𝑻 *A, integer a, integer b)
      @   reads a,b,A, A[..] ;
      @
      @ axiom foldEmptyRange{L} :
      @   \forall 𝑻 *A, integer a, b; a >= b
      @   ==>  fold(A,a,b) == identity(⊕);
      @
      @ axiom foldSplitOffTerm{L} :
      @   \forall 𝑻 *A, integer a, b; a <= b
      @   ==>     fold(A, a, b+1) 
      @        == fold(A, a, b  ) ⊕ A[b];
      @ }
      @*/

\columnbreak

    /*@ requires \valid(A+(0..N-1));
      @ assigns \nothing;
      @ ensures \result == fold(A,0,N);
      @*/
    𝑻 fold(int N, 𝑻* A) {
    
        𝑻 total = identity(⊕);
        
        /*@ loop invariant 0 <= n <= N;
          @ loop invariant total == fold(A,0,n);
          @ loop assigns n, total;
          @ loop variant N-n;
        */
        for(int n = 0; n != N; n++)
            total = total ⊕ A[n];
        return total;
    }

</div>

This pseudo-code is reified by giving concrete values
for `(𝑻, ⊕, identity)` such as `(int, +, 0)` or `(bool, ||, false)`.
Any [monoid](https://en.wikipedia.org/wiki/Monoid) will do.

