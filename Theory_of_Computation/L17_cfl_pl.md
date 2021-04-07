---
geometry: margin=2cm
--- 

\title{Pumping Lemma for Context-Free Languages}
\maketitle

# Outline 

- Idea and Definition
- Examples

# Context-Free Pumping Lemma Idea

Context-Free Pumping Lemma Idea: 

- Pumping Lemma is used to prove a language is **NOT** context-free
- There are two pumps now
    - Pumps on two cycles in the PDA to match stack pushes/pops

## Theorem: Pumping Lemma for CFLs 

If L is a context-free language, there is a number p (the pumping length) where if: 

- $\sigma$ $\in$ L 
- |$\sigma$| $\ge$ p 

Then we can divide $\sigma$ into five pieces $\sigma$ = uvxyz such that: 

- |vy| > 0
- |vxy| $\le$ p 
- for each i $\ge$ 0, uv^i^xy^i^z $\in$ L

## Proving a Language is NOT Context-Free Using Pumping Lemma

1. Assume L is context-free
2. Show that some string can be pumped
3. Show when pumped its not valid
4. PROOF BY CONTRADICTION




