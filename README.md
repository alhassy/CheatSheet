<h1> Easily Making CheatSheets with Org-mode </h1>

Pretty cheat sheets, or “reference cards”, obtainable from Org-mode files. See section [4](#getting-started) below to get started making your own cheat sheets!

**The listing sheet, as PDF, can be found
 [here](<https://github.com/alhassy/CheatSheet/blob/master/CheatSheet.pdf>)**,
 while below is an unruly html rendition.

This reference sheet is built around the system
<https://github.com/alhassy/CheatSheet>.

**The listing sheet, as PDF, can be found
[here](<https://github.com/alhassy/CheatSheet/blob/master/CheatSheet.pdf>)**,
while below is an unruly html rendition.


# Table of Contents

1.  [Hello, World!](#org810628d)
2.  [CheatSheet Examples](#orgc296bbb)
3.  [Why Learn & Relearn?](#org8dc463b)
4.  [Getting Started](#getting-started)
5.  [What if it's not good enough?](#org3b46ef7)
6.  [Org-mode Basics](#orgc12889e)
7.  [Basic Equational Support](#orga4d2ba6)
8.  [What if I want 3 columns?](#orgeebf7c2)
9.  [Parallel Environment](#org4277d51)













<a id="org810628d"></a>

# Hello, World!

-   **Pretty PDF:** Enter `M-x compile` to produce a nice looking PDF of your reference sheet.
    -   I've bound this command to `C-c C-m` in [my Emacs setup](https://github.com/alhassy/emacs.d) ;-)

	My Emacs configuration also documents how I utilise ‘minted’
	to obtain colourful source code blocks.

-   **Section Headers:** A usual Org header, say `* my section`, results in the boxed headers
    used in this cheat sheet.

-   **Parallel Environments:** The LaTeX matter here supports an org-enviornment
    named `parallel` for producing text side-by-side.

    The column break is automatic, but as
    this is sugar for a `minipage` containing a `multicolum` we can force a column
    separation with `\columnbreak`: This command, in Org, necessities newlines between
    the items being separated.

To learn more, manipulating this source is the way to go!

Also, opening this file produces a `README.md` ;-)
Which can then be regenerated on-demand with `f11`.


<a id="orgc296bbb"></a>

# CheatSheet Examples

Reference sheets created from this project include,

-   **[ElispCheatSheet](https://github.com/alhassy/ElispCheatSheet):** Quick reference to the core language of Emacs
    &#x2014;Editor MACroS.

-   **[Islam](https://github.com/alhassy/islam):** Important figures in the faith.

-   **[PrologCheatSheet](https://github.com/alhassy/PrologCheatSheet):** Program where everything is a relation &#x2014;i.e., a database table.

-   **[CatsCheatSheet](https://github.com/alhassy/CatsCheatSheet):** Listing of common theorems in elementary category theory.

-   **[LatticesCheatSheet](https://github.com/alhassy/LatticesCheatSheet):** Reference sheet for definitions and results in Lattice Theory.

-   **[OCamlCheatSheet](https://github.com/alhassy/OCamlCheatSheet):** Basics of OCaml, “the best imperative language”.

-   **[CoqCheatSheet](https://github.com/alhassy/CoqCheatSheet):** Reference sheet for the Coq language.

-   **[GojuRyuCheatSheet](https://github.com/alhassy/GojuRyuCheatSheet):** A quick cheat sheet for common terms in Goju Ryu Karate
    &#x2014;the hard-soft style of karate.

<div class="org-center">
*If you use this org-setup to produce a neat cheat sheet, please let me know!*
</div>


<a id="org8dc463b"></a>

# Why Learn & Relearn?

*The world of ideas is not revealed to us in one stroke;*
*we must both permanently and unceasingly recreate it in*
*our consciousness.* &#x2014;Rene Thom

\newpage


<a id="getting-started"></a>

# Getting Started

The steps to utilising this git project for your own cheat sheet may be:

1.  Go to the repo where you want to make a cheat sheet.

2.  Add this project as a submodule then copy its core to where you're working:

	git submodule add https://github.com/alhassy/CheatSheet.git
	; cp CheatSheet/CheatSheet.org .
	; cp CheatSheet/README.org .

3.  Open `CheatSheet.org` and locate `#+INCLUDE: CheatSheetSetup.org`
    then rewrite `CheatSheetSetup.org → CheatSheet/CheatSheetSetup.org`.

I don't think this is difficult to automate, so I will likely get
to doing it. Indeed, just copy-paste the following into, say the
`*scratch*` buffer then `C-x C-e` after the final closing parenthesis.

    (let ((your-repo "~/example") ;; Alter this location!
	  (enable-local-variables :all))
	  ;; Look at my “local variables” below; ensure nothing malicious.
	  ;; So no need to be queried about loading them.

     ;; Obtain the submodule then make a /copy/ of this cheatsheet.
     (eshell-command (concat
       "  cd " your-repo
       "; git submodule add https://github.com/alhassy/CheatSheet.git"
       "; cp CheatSheet/CheatSheet.org ."
      ))

     ;; Make your cheat sheet refer to the submodule's setup file.
     (find-file-other-window (concat your-repo "/CheatSheet.org"))
     (beginning-of-buffer)
     (re-search-forward "INCLUDE: CheatSheetSetup.org" nil t)
     (replace-match "INCLUDE: CheatSheet/CheatSheetSetup.org")
     (beginning-of-buffer)
    )

    ;; To remove a submodule:
    ;; git submodule deinit ⟪path_to_submodule⟫ ; git rm ⟪path_to_submodule⟫

For the `README.md` to be generated as desired, fill in the macros `URL` and `blurb`
at the top of this org file to point to your repository and provide a description
of what the cheatsheet serves to accomplish.


<a id="org3b46ef7"></a>

# What if it's not good enough?

*“The person who thinks of doing something, is usually passed by the person doing it.”*

*The more that you read, the more things you will know.*
*The more that you learn, the more places you'll go.*
&#x2014;Dr. Seuss

\newpage


<a id="orgc12889e"></a>

# Org-mode Basics

Read [Org-mode for beginners](https://orgmode.org/worg/org-tutorials/org4beginners.html) for a refresher!

-   For more see [The Compact Org-mode Guide](https://orgmode.org/orgguide.pdf).

-   **Reloading:** To reload a file with updated org settings, press
    `C-c C-c` on a settings line &#x2013;i.e., one beginning with a `#+`, to reset the
     temporary file cache.

-   **Inclusion:** During export, you can include the content of another file.
    -   Syntax: `#+INCLUDE: "⟨fileName⟩" [⟨markup⟩ [⟨language⟩]]`
	-   `markup ::= src | example`
	-   `language ::= C | haskell | emacs-lisp | ⋯`
	-   If the markup is not given, the text will be assumed to be in
	    Org mode format and will be processed normally; c.f., [Setup files](https://orgmode.org/manual/In_002dbuffer-settings.html).

    -   To visit the file, `C-c '` while the cursor is on the line with the file name.

    -   Include only portions of a file by appending with `:lines "x-y"` where `x` is the first
	line and `y` is the second-to-last line. Also `"-y"` for upto but not including line `y`,
	and `"x-"` for taking line `x` until the end of the file.


<a id="orga4d2ba6"></a>

# Basic Equational Support

Basic name-formula equational support. `\eqn{name}{formula}`
yields a displayed equation with `formula` left aligned and `name` right aligned:

\eqn{name}{formula}

Moreover, we can refer to such a formula by invoking `\ref{name}` &#x2013;e.g., \ref{Functoriality} and \ref{name}.
However, if `name` involves unicode symbols, then this may cause problems.

See the [CatsCheatSheet](https://github.com/alhassy/CatsCheatSheet) for examples of this kind.


<a id="orgeebf7c2"></a>

# What if I want 3 columns?

At the top, say after the `#+INCLUDE: CheatSheet/CheatSheetSetup.org` line, add a new
section:

    * begin multicols  :ignore:
    #+latex: \begin{multicols}{3}

Then at the very bottom, add a section to close this multicol:

    * end multicols   :ignore:
    #+latex: \end{multicols}

Having three narrow columns is useful for term-heavy or formula heavy sheets.

\newpage


<a id="org4277d51"></a>

# Parallel Environment

Cheat sheets should not waste space, so the setup provides
a `parallel` LaTeX enviornment that takes an optional parameter
indicating how many columns are desired &#x2014;two by default.
Importantly, we use this environment as if it were any normal org-block:

<div class="parallel">
    ,#
    #+begin_parallel org
    ???content here???
    #+end_parallel

The initial new line is important, otherwise the parallel environment
occurs in-line, which may not be the intended behaviour.

</div>

Below we demonstrate that [loops implement finite quantifications](https://frama-c.com/)
by showing how the specification of a loop is implemented, unsurprisingly,
using a loop. [I tend to use a lot of unicode.](https://github.com/alhassy/MyUnicodeSymbols)

A finite quantification can be defined axiomatically
by the empty-range rule and split-off term rules.
Together these form a recursive definition which can be phrased as a loop.

<div class="parallel">
    // For _⊕_ : 𝑻 → 𝑻 → 𝑻,
    // fold(A,a,b) ≈ (⊕ x : a..b-1 • A[x])
    /*@ axiomatic Fold {
      @
      @ logic 𝑻
      @   fold{L}(𝑻 *A, ℤ a, ℤ b)
      @   reads a,b,A, A[..] ;
      @
      @ axiom foldEmptyRange{L} :
      @   ∀ 𝑻 *A, ℤ a, b; a ≥ b
      @   =⇒  fold(A,a,b) == identity(⊕);
      @
      @ axiom foldSplitOffTerm{L} :
      @   ∀ 𝑻 *A, ℤ a, b; a ≤ b
      @   =⇒      fold(A, a, b+1)
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

`parallelNB` produces a side-by-side rendition with ‘N’o ‘B’ar:

<div class="parallelNB">
left \newline left \newline left

\columnbreak
right \newline right \newline right

</div>

Here is an example with four columns:

<div class="parallel">
left \newline left \newline left

\columnbreak
middle \newline middle \newline middle

\columnbreak
middle \newline middle \newline middle

\columnbreak
right \newline right \newline right

</div>

Here is an example with three columns and ‘n’o ‘b’ar:

<div class="parallel3NB">
left \newline left \newline left

\columnbreak
middle \newline middle \newline middle

\columnbreak
right \newline right \newline right

</div>

\newpage
