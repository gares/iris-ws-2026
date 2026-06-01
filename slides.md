---
# You can also start simply with 'default'
theme: neversink
color: rocq
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: "Elpi: manipulating Rocq syntax made easy"
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
layout: cover
image: logo.png
transition: fade
level: 2
hideInToc: true
---

# Elpi: manipulating Rocq syntax made easy

<div style="width:330px;margin-left:auto;margin-right:auto">

![Elpi logo](/logo.png "Logo")

</div>
<div style="text-align: right !important;">Iris WS 10/6/2026</div>



---
layout: center
level: 2
---

# This talk
<br/>

<Toc minDepth="1" maxDepth="1" />




---
layout: section
color: rocq
---

# The language in a nutshell

---
layout: two-cols-header
level: 2
---

# Elpi: Hello World!

::left::

Simply typed $\lambda$-calculus in $\lambda$-tree syntax (HOAS)

<<< @/snippets/stlc.elpi#types elpi

Typing


````md magic-move

<<< @/snippets/stlc.elpi#of elpi
<<< @/snippets/stlc.elpi#of1 elpi
<<< @/snippets/stlc.elpi#of2 elpi
<<< @/snippets/stlc.elpi#of elpi


````

<br/>
<br/>
<br/>

::right::

````md magic-move {at:1}

```elpi
goal> of (lam x\ lam y\ x) TyFst.
```

```elpi
goal> of (lam x\ lam y\ x) (arr S0 T0).
goal> of        (lam y\ c) T0.
```

```elpi
goal> of (lam x\ lam y\ x) (arr S0 (arr S1 T1)).
goal> of        (lam y\ c) (arr S1 T1).
goal> of                c  T1.
```

```elpi
goal> of (lam x\ lam y\ x) TyFst.

Success:
  TyFst = arr S0 (arr S1 S0)
```

```elpi
goal> of (app H A) T.

Failure.
```

````

---
layout: two-cols-header
level: 2
---

# Elpi = $\lambda$Prolog + CHR

::left::

Typing (as before)

<<< @/snippets/stlc.elpi#of elpi

Holes & constraints

<<< @/snippets/stlc.elpi#cst elpi

<v-click at="6">
Constraint Handling Rules

<<< @/snippets/stlc.elpi#chr elpi
</v-click>

<br/>
<br/>
<br/>


::right::

````md magic-move
```elpi
goal> of (app H A) T.
```

```elpi
goal> of (app H A) T.

Success:

Constraints:
  of A S  /* suspended on A */
  of H (arr S T)  /* suspended on H */
```

```elpi
goal> of (app H A) T, H = (lam x\ x).

Success:

Constraints:
  of A T  /* suspended on A */
```

```elpi
goal> of (app (lam x\ x) A) T.

Success:

Constraints:
  of A T  /* suspended on A */
```

```elpi
goal> of (app D D) T.
```

```elpi
goal> of (app D D) T.

Success:

Constraints:
  of D S  /* suspended on D */
  of D (arr S T)  /* suspended on D */
```

```elpi
goal> of (app D D) T.

Failure
```
````


---
layout: image
image: chr.png
level: 2
backgroundSize: 50%
---

# Elpi = $\lambda$Prolog + CHR

---
layout: section
color: rocq
---

# The integration in Rocq

---
layout: image-right
image: onion.png
backgroundSize: 80%
transition: fade
level: 2
---

# The plan

- first commands
- then tactics
- then elaboration


---
layout: image-right
image: readme.png
backgroundSize: 80%
transition: fade
level: 2
---

# Notable features

- HOAS for Gallina
- quotations and anti-quotations

  ![Quotations](/quote.png "quote")

- Databases of rules
- Extensive API
  * Binding OCaml is easy
  * Rocq vernacular like APIs
  * Json/XML (for fun)

  ![API example](/api.png "api")


---
layout: two-cols-header
level: 2
---

# Commands

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Derive

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# NES

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Tactics

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Algebra tactics

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Trocq

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```


---
layout: two-cols-header
level: 2
---

# Elaboration

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```


---
layout: two-cols-header
level: 2
---

# Coercion

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Canonical Structures

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Type Classes

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: two-cols-header
level: 2
---

# Record Builder

<div class="authors">

![proux01](/avatars/proux01.jpg)


</div>

DSL to declare a hierarchy of interfaces

:: left ::

* xxxx


:: right ::

```coq
xxx
```

---
layout: section
color: rocq
---

# The good company

https://github.com/rocq-community/metaprogramming-rosetta-stone

---
transition: fade
zoom: 0.75
level: 2
---

# Comparison

<table>

<thead>
<tr style="border-bottom-width: 4px"> <th></th> <th>Elpi</th> <th>Ltac2</th> <th>MetaRocq</th> </tr>
</thead>
<tbody>

<tr> <td>Gallina</td>
  <td>
    <icon-park-twotone-pie-seven/>
    <br/><small>no mutual fix/ind</small>
  </td>
  <td>
    <icon-park-twotone-round/>
  </td>
  <td>
    <icon-park-twotone-round/>
  </td>
</tr>

<tr> <td>Bound Variables</td>
  <td>
    <icon-park-twotone-round/>
  </td>
  <td>
    <icon-park-twotone-pie-three/>
    <br/><small>quotations</small>

  </td>
  <td>
    <icon-park-twotone-pie-one/>
    <br/><small>toplevel quotation</small>
  </td>
</tr>

<tr style="border-bottom-width: 4px"> <td>Holes</td>
  <td>
    <icon-park-twotone-round/>
  </td>
  <td>
    <icon-park-twotone-pie-five/>
    <br/><small>tactic monad</small>

  </td>
  <td>
    <icon-park-twotone-pie-one/>
    <br/><small>only AST</small>
  </td>
</tr>

<tr> <td>Proof API</td>
  <td>
    <icon-park-twotone-pie-four/>
    <br/><small>weak ltac1 bridge</small>
  </td>
  <td>
    <icon-park-twotone-round/>
    <br/><small>(sufficiently close)</small>
  </td>
  <td>
    <icon-park-twotone-pie-one/>
    <br/><small>only TC search, obligations</small>
  </td>
</tr>

<tr style="border-bottom-width: 4px"> <td>Vernacular API</td>
  <td>
    <icon-park-twotone-pie-seven/>
    <br/><small>no notations, obligations</small>
  </td>
  <td>
    <material-symbols-circle-outline/>
  </td>
  <td>
    <icon-park-twotone-pie-three/>
    <br/><small>only env, obligations</small>
  </td>
</tr>

<tr style="border-bottom-width: 4px"> <td>Elaborator API</td>
  <td>
    <icon-park-twotone-pie-six/>
    <br/><small>no error locations</small>
  </td>
  <td>
    <material-symbols-circle-outline/>
  </td>
  <td>
    <material-symbols-circle-outline/>
  </td>
</tr>


<tr style="border-bottom-width: 4px"> <td>Reasoning logic</td>
  <td>
    <icon-park-twotone-pie-one/>
    <br/><small>Abella</small>
  </td>
  <td>
    <material-symbols-circle-outline/>
  </td>
  <td>
    <icon-park-twotone-pie-six/>
    <br/><small>no holes, unif</small>
  </td>
</tr>

</tbody>
</table>

To the best of my knowledge, on 1/1/2026 {style="text-align:center"}


---
layout: section
color: rocq
---

# What makes me proud


---
layout: two-cols-header
level: 2
---

# Hierarchy Builder

<div class="authors">

![CohenCyril](/avatars/CohenCyril.jpg)
![pi8027](/avatars/pi8027.jpg)
![gares](/avatars/gares.jpg)
![proux01](/avatars/proux01.jpg)
![ThomasPortet](/avatars/ThomasPortet.jpg)
![affeldt-aist](/avatars/affeldt-aist.jpg)
<!--
![FissoreD](/avatars/FissoreD.jpg)
![SkySkimmer](/avatars/SkySkimmer.jpg)
![thery](/avatars/thery.jpg)
![Tvallejos](/avatars/Tvallejos.jpg)
![VojtechStep](/avatars/VojtechStep.jpg)
![ybertot](/avatars/ybertot.jpg)
-->

</div>

DSL to declare a hierarchy of interfaces

:: left ::

* generates boilerplate via Elpi's API: modules, implicit arguments, canonical structures, ... 
* used by the Mathematical Components library and other ~20 libraries
* makes "packed classes" easy

  ![MC](/hb_intf.png "number of interfaces"){style="width: 80%"}

  2017
  <span style="width:8em; display:inline-block"/>
  2022
  <span style="width:2em; display:inline-block"/>
  2024

:: right ::

```coq
From HB Require Import structures.

HB.mixin Record IsAddComoid A := {
  zero : A;
  add : A -> A -> A;
  addrA : forall x y z, add x (add y z) = add (add x y) z;
  addrC : forall x y, add x y = add y x;
  add0r : forall x, add zero x = x;
}.

HB.structure Definition AddComoid := { A of IsAddComoid A }.

Notation "0" := zero.
Infix "+" := add.

Check forall (M : AddComoid.type) (x : M), x + x = 0.
```

<!--
this is the command / this is the argument

uses the APIs to declare modules, coercions, implicit arguments

--
layout: two-cols-header
level: 2
--

# Trocq

<div class="authors">

![ecranceMERCE](/avatars/ecranceMERCE.jpg)
![amahboubi](/avatars/amahboubi.jpg)
![CohenCyril](/avatars/CohenCyril.jpg)
<!-- ![palmskog](/avatars/palmskog.jpg) -- >

</div>

Proof transfer via parametricity (with or without univalence).

:: left ::

<div style="padding-right: 3em">


- Registers in Elpi Databases translation rules
- Synthesizes transfer proofs minimizing the axioms required

</div>

:: right :: 

<div style="transform: scale(1.2)">

```coq 
From Trocq Require Import Trocq.

Definition RN : (N <=> nat)%P := ...
Trocq Use RN.

Lemma RN0 : RN 0%N 0%nat. ...
Lemma RNS m n : RN m n -> RN (N.succ m) (S n). ...
Trocq Use RN0 RNS.

Lemma N_Srec : ∀P : N -> Type, P 0%N ->
    (∀n, P n -> P (N.succ n)) -> ∀n, P n.
Proof.
trocq. (* replaces N by nat in the goal *)
exact nat_rect.
Qed.
```

</div>

--
layout: two-cols-header
level: 2
--

# Derive

<div class="authors">

![gares](/avatars/gares.jpg)
![CohenCyril](/avatars/CohenCyril.jpg)
![bgregoir](/avatars/bgregoir.jpg)
![eponier](/avatars/eponier.jpg)
![Blaisorblade](/avatars/Blaisorblade.jpg)
![rlepigre](/avatars/rlepigre.jpg)
![dwarfmaster](/avatars/dwarfmaster.jpg)
<!--
![artagnon](/avatars/artagnon.jpg)
![ecranceMERCE](/avatars/ecranceMERCE.jpg)
![ejgallego](/avatars/ejgallego.jpg)
![FissoreD](/avatars/FissoreD.jpg)
![herbelin](/avatars/herbelin.jpg)
![jfehrle](/avatars/jfehrle.jpg)
![maximedenes](/avatars/maximedenes.jpg)
![pedrotst](/avatars/pedrotst.jpg)
![phikal](/avatars/phikal.jpg)
![pi8027](/avatars/pi8027.jpg)
![ppedrot](/avatars/ppedrot.jpg)
![proux01](/avatars/proux01.jpg)
![robblanco](/avatars/robblanco.jpg)
![SimonBoulier](/avatars/SimonBoulier.jpg)
![SkySkimmer](/avatars/SkySkimmer.jpg)
![Tragicus](/avatars/Tragicus.jpg)
![vbgl](/avatars/vbgl.jpg)
![VojtechStep](/avatars/VojtechStep.jpg)
![wdeweijer](/avatars/wdeweijer.jpg)
![whonore](/avatars/whonore.jpg)
![ybertot](/avatars/ybertot.jpg)
![yoichi-at-bedrock](/avatars/yoichi-at-bedrock.jpg)
![Zimmi48](/avatars/Zimmi48.jpg)
- ->

</div>

Framework for type driven code synthesis

:: left ::

<div style="padding-right: 3em">

Derivations:
- parametricity
- deep induction
- equality tests and proofs
- lenses (record update syntax)
- a few more...

</div>

:: right :: 

<div style="transform: scale(1.2)">

```coq
From elpi.apps Require Import derive.std lens.

#[only(lens_laws, eqb), module] derive
Record Box A := { contents : A; tag : nat }.

About Box. (* Notation Box := Box.t *)

Check Box.eqb :
  ∀A, (A -> A -> bool) -> Box A -> Box A -> bool.

(* the Lens for the second field *)
Check @Box._tag : ∀A, Lens (Box A) (Box A) nat nat.

(* a Lens law *)
Check Box._tag_set_set : ∀A (r : Box A) y x,
  set Box._tag x (set Box._tag y r) = set Box._tag x r.
```

</div>


--
layout: two-cols-header
level: 2
--

# Algebra Tactics

<div class="authors">

![pi8027](/avatars/pi8027.jpg)
![proux01](/avatars/proux01.jpg)
![amahboubi](/avatars/amahboubi.jpg)
<!-- ![CohenCyril](/avatars/CohenCyril.jpg)
![gares](/avatars/gares.jpg) -- >

</div>

`ring`, `field`, `lra`, `nra`, and `psatz` tactics for the Mathematical Components library. 

:: left ::

- works with any instance of the structure: concrete, abstract and mixed
  like `int * R` where `R` is a variable
- automatically push down ring morphisms and additive functions to
  leaves of the expression
- reification up to instance unification in Elpi


:: right ::

```coq
From mathcomp Require Import all_ssreflect.
From mathcomp Require Import all_algebra.
From mathcomp Require Import ring lra.

Lemma test (F : realFieldType) (x y : F) :
  x + 2 * y <= 3 ->
  2 * x + y <= 3 ->
    x + y <= 2.
Proof. lra. Qed.

Variables (R : unitRingType) (x1 x2 x3 y1 y2 y3 : R).
Definition f1 : R := ...
Definition f2 : R := ...
Definition f3 : R := ...

(* 500 lines of polynomials later... *)

Lemma example_from_Sander : f1 * f2 = f3.
Proof. rewrite /f1 /f2 /f3. ring. Qed.
```


--
layout: section
color: rocq
--

# Elpi in a nutshell

https://github.com/LPCIC/elpi/

--
layout: two-cols-header
image: vespa.png
backgroundSize: 80%
level: 2
--

# Rules, rules, rules!{style="text-align:center"}


:: left ::


## Roots

- Elpi is a constraint logic programming language
- Elpi is a dialect of λProlog and CHR
- backtracking is not the point

<br/>

## What really matters

- Code is organized in rules
- Rule application is guided by a pattern
- Rules can be added statically and dynamically



:: right ::

## <icon-park-twotone-caution/> Vintage syntax ahead

<ul>
<li><p>variables are capitals
<force-inline>
```elpi
X
```
</force-inline>
</p></li>

<li><p> λx.t  is written
<force-inline>
```elpi
x\ t
```
</force-inline>
</p></li>

<li><p>rules are written
<force-inline>
```elpi
goal :- subgoal1, subgoal2...
```
</force-inline>
</p></li>

</ul>



--
layout: section
color: rocq
transition: fade
--

# Integration in Rocq

https://github.com/LPCIC/coq-elpi/
-->


---
layout: section
color: rocq
---

# Conclusion

---
layout: default
level: 2
---

# Elpi: take home

<br/>

## Extension language
  - Use a language (ony) when it is a good fit
  
## Rule-based is a good fit for
  - HOAS (binders and local context)
  - prover logical environment (global context)
  - (meta) meta programming (homoiconicity)


---
layout: default
level: 2
---

# In the pipes

- Full gallina (mfix and minductive)
- More hooks
  - printing (box language already bound)
  - unification
  - elaborator
- Better syntax
- Memoization (tabling via SLG)
  - no good public benchmark, but BedRock/BlueRock/SkyLabs-AI needs it
  - loop detection could help beginners

---
layout: default
backgroundSize: 80%
level: 2
title: Thanks
---

# Thanks for contributing code! {style="text-align:center"}

<div style="text-align:center">

https://github.com/LPCIC/coq-elpi/

</div>


<div class="vauthors">


<br/>
<br/>

![Armael](/avatars/Armael.jpg)
![Blaisorblade](/avatars/Blaisorblade.jpg)
![CohenCyril](/avatars/CohenCyril.jpg)
![FissoreD](/avatars/FissoreD.jpg)
![JasonGross](/avatars/JasonGross.jpg)
![MSoegtropIMC](/avatars/MSoegtropIMC.jpg)
![SimonBoulier](/avatars/SimonBoulier.jpg)
![SkySkimmer](/avatars/SkySkimmer.jpg)
![ThomasPortet](/avatars/ThomasPortet.jpg)
![Tragicus](/avatars/Tragicus.jpg)
![Tvallejos](/avatars/Tvallejos.jpg)
![Villetaneuse](/avatars/Villetaneuse.jpg)
![VojtechStep](/avatars/VojtechStep.jpg)
![XVilka](/avatars/XVilka.jpg)
![Zimmi48](/avatars/Zimmi48.jpg)
![affeldt-aist](/avatars/affeldt-aist.jpg)
![agontard](/avatars/agontard.jpg)
![amahboubi](/avatars/amahboubi.jpg)
![artagnon](/avatars/artagnon.jpg)
![bgregoir](/avatars/bgregoir.jpg)
![cdunchev](/avatars/cdunchev.jpg)
![dwarfmaster](/avatars/dwarfmaster.jpg)
![ebmoon](/avatars/ebmoon.jpg)
![ecranceMERCE](/avatars/ecranceMERCE.jpg)
![ejgallego](/avatars/ejgallego.jpg)
![eponier](/avatars/eponier.jpg)
![gares](/avatars/gares.jpg)
![gdufrc](/avatars/gdufrc.jpg)
![herbelin](/avatars/herbelin.jpg)
![jfehrle](/avatars/jfehrle.jpg)
![jwintz](/avatars/jwintz.jpg)
![kit-ty-kate](/avatars/kit-ty-kate.jpg)
![lthls](/avatars/lthls.jpg)
![lukovdm](/avatars/lukovdm.jpg)
![mattam82](/avatars/mattam82.jpg)
![maximedenes](/avatars/maximedenes.jpg)
![mb64](/avatars/mb64.jpg)
![palmskog](/avatars/palmskog.jpg)
![patrick-nicodemus](/avatars/patrick-nicodemus.jpg)
![patricoferris](/avatars/patricoferris.jpg)
![pedrotst](/avatars/pedrotst.jpg)
![phikal](/avatars/phikal.jpg)
![pi8027](/avatars/pi8027.jpg)
![ppedrot](/avatars/ppedrot.jpg)
![proux01](/avatars/proux01.jpg)
![rgrinberg](/avatars/rgrinberg.jpg)
![rlepigre](/avatars/rlepigre.jpg)
![robblanco](/avatars/robblanco.jpg)
![sacerdot](/avatars/sacerdot.jpg)
![shonfeder](/avatars/shonfeder.jpg)
![smuenzel](/avatars/smuenzel.jpg)
![thery](/avatars/thery.jpg)
![thomas-lamiaux](/avatars/thomas-lamiaux.jpg)
![vbgl](/avatars/vbgl.jpg)
![voodoos](/avatars/voodoos.jpg)
![wdeweijer](/avatars/wdeweijer.jpg)
![whonore](/avatars/whonore.jpg)
![ybertot](/avatars/ybertot.jpg)
![yoichi-at-bedrock](/avatars/yoichi-at-bedrock.jpg)

</div>

---
layout: image-right
backgroundSize: 80%
level: 2
title: Thanks
---

# Thanks for listening! {style="text-align:center"}


