---
geometry: margin=2cm
---

\title{Decision Properties of Regular Languages}
\maketitle

# Introduction

Decision Property

- A decision property is a (Boolean) question about a language
    - Is the language empty? 
    - Is the language a subset of another language?
- Algorithm on a representation 
- Applications in verification

Decision properties:

- A boolean operation on a language
    - Unary: F : S &rarr; $\mathbb{B}$
    - Binary: T : S $\times$ S &rarr; $\mathbb{B}$

# Outline

- Membership
- Empty Set and Empty String
- Equivalence and Subset
- Language Size

# Membership

Input: String w and the language as Finite Automaton A

Output: Is w in the language of A?

> w $\in$ *L*(A) ?

Solution:

1. Simulate A on w
2. If A accepts w, then w $\in$ *L*(A)
3. Otherwise, A does not accept w, so w $\not\in$ *L*(A)

\newpage

# Empty Set and Empty String

## Emptiness

Input: Finite Automaton A

Output: Is the language of A empty?

> *L*(A) = $\emptyset$?

Solution:

1. Search nodes reachable from the start state q~0~ 
2. If an accept state q $\in$ F is reachable, *L*(A) is not empty
3. Otherwise, no accept states are reachable, so the language is empty

## Empty String

Input: Finite Automaton A

Output: Is the empty string in language of A?

> $\epsilon$ $\in$ *L*(A)

Solution: 

1. Search nodes reachable from the start state q~o~ following only $\epsilon$ transitions
2. If an accept state q $\in$ F is reachable using only $\epsilon$ transitions, then the empty string $\epsilon$ is in *L*(A)
3. Otherwise, no accept states are reachable on $\epsilon$, so the $\epsilon$ is not in *L*(A)

## Empty Set VS Empty String

Empty Set:

- Set with zero members
- $\emptyset$ = {}
- |$\emptyset$| = 0
- $\emptyset$ $\not$= 0
- *L*($\emptyset$)  = $\emptyset$ = {}

Empty String

- String of length zero
- $\epsilon$ = ()
- |$\epsilon$| = 0
- $\epsilon$ $\not$= 0 and $\epsilon$ $\not$= $\emptyset$ and $\epsilon$ $\not$= e
- *L*($\epsilon$) = {$\epsilon$} = {()}

\newpage

# Equivalence and Subset

Input: Finite Automata L and M 

Output: Do L and M recognize the same language?

> *L*(L) = *L*(M)

Solution: Is there a string accepted by only one of L or M

- Idea: run L and M in "parallel" 
- But: we don't want to actually simulate on both DFA (What if we are comparing *L*(aa\*) and *L*(a\*a)?)
- Instead: Compute the Product DFA of L and M 

## Product DFA

Input: Finite Automata

> L = (Q~L~, $\Sigma$, $\delta$~L~, q~0L~, F~L~)

> M = (Q~M~, $\Sigma$, $\delta$~M~, q~0M~, F~M~)

Output: Product Automaton P = (Q~P~, $\Sigma$, $\delta$~P~, q~0P~, F~P~)
 
Solution

- States: Q~P~ = Q~L~ $\times$ Q~M~
- Start State: q~0P~ = (q~0L~, q~0M~)
- Transition Function $\delta$~p~((*l*,m),$\sigma$) = ($\delta$~L~(*l*,$\sigma$),$\delta$~M~(m,$\sigma$))
- Accept States: depend on usage

Transition, basically for each pair for a given sigma, see what the first item goes to, see what the second item goes to, and then the two items it transitions to is the new pair state you transition to. 

Example:

\
![prod](images/proddfa.png)

\newpage

## Solution to Equivalence

For 2 languages L and M, after using the product DFA of both: 

- Accept only when one of L and M accept:

> F~P~ = \{(*l*, m) | (*l* $\in$ F~L~) $\oplus$ (m $\in$ F~M~) \}
    
> - (*l*, m) = Product state

> - (*l* $\in$ F~L~) = L accepts

> - (m $\in$ F~M~) = M accepts

- Equivalent when product DFA is empty:

> (*L*(L) = *L*(M) $\leftrightarrow$ ($\emptyset$ = *L*(P))

## Subset

Input: Finite Automata

> L = (Q~L~, $\Sigma$, $\delta$~L~, q~0L~, F~L~)

> M = (Q~M~, $\Sigma$, $\delta$~M~, q~0M~, F~M~)

Output: *L*(L) $\subseteq$ *L*(M)

Solution: Product DFA

- P = L $\times$ M
- F~P~= {(*l* $\in$ Q~L~, m $\in$ Q~M~)|(*l* $\in$ F~L~) $\wedge$ (m $\not\in$ F~M~)}

> - (*l* $\in$ Q~L~, m $\in$ Q~M~) = product state
> - (*l* $\in$ F~L~) = accepted by L 
> - (m $\not\in$ F~M~) = not accepted by M 

- (*L*(L) $\subseteq$ *L*(M)) $\equiv$ ($\emptyset$ = *L*(P))
- equivalent: (*L*(L) $\subseteq$ *L*(M)) $\equiv$ ($\emptyset$ = *L*(L) $\cap$ *L*(M))

## Strict Subset

Strict subset (*L*(L) $\in$ *L*(M)) is a decidable property of regular languages

Proof by construction: 

- Input: Finite Automata 
- Output: *L*(L) $\subset$ *L*(M)


\newpage

# Language Size

Given DFA A and string $\sigma$ $\in$ *L*(A)

If the string is larger than the number of transitions, what does this tell us about the language? (INFINITE HEHE)

## Infiniteness

Input: Finite Automaton A

Output: Is the language of A infinite?

> |*L*(A)| = $\infty$ ?

Solution: Doe the transition graph contain a cycle that:

- Is reachable from the start state
- Can reach an accept state
- Contains a non-epsilon transition
