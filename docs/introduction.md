# Introduction & Components

## Where to Start?

### Higher-Level Goal

At the higher level, this project attempts to address the notion of providing **trust**, or *an additional layer of trust* on the web by exploiting [formal proofs](https://en.wikipedia.org/wiki/Formal_verification#:~:text=In%20the%20context%20of%20hardware,using%20formal%20methods%20of%20mathematics.), in contrast to the usual scene where trust in a *statement* is provided only through trusting the entity claiming that *statement*, usually by the [public key infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure) model or by the [web of trust](https://en.wikipedia.org/wiki/Web_of_trust) model.

**Trust** here could be relevant to many **themes**, including for example trust in *software components*, trust in *produced scientific results*, and trust within *journalism and news platforms*. **Trust on the web** within the context of these themes means that the *data to be trusted*, whatever that might be, is exchanged through the web, and thus the intended source of trust as well needs to be addressed and exchanged within the realm of the web. Naturally, before thinking about how to achieve this wide-range goal itself, the **foundations, utilities, or steps** needed to achieve it need to be **investigated** thoroughly. As **formal proofs** are the driving force and the essence of what the source of trust is desired to be, the sharing and usage of formal proofs within the realm of the web needs to be addressed.

### Primary Idea

Basically, we can consider a formal proof to be an **asset** that is considered an evidence of the validity of some statement. Such an **asset** is usually produced by [theorem provers](https://en.wikipedia.org/wiki/Automated_theorem_proving) and [proof assistants](https://en.wikipedia.org/wiki/Proof_assistant). The intended idea here is that in addition to providing a **formal proof asset** as evidence, the asset could be *signed* by some entity and provided as an **assertion**. The reason behind the definition of these two notions of an **asset** and an **assertion** is that in the existing theorem proving world, a proof is always rechecked when desired to be reused. This process often requires time and resources; it might be necessary in some cases, but not so in others. However, by allowing the notion of an entity *asserting* a proof of some theorem, and another entity willing to trust the producing entity, a theorem could be reused **without rechecking**. You might say here that, well, we are still believing a theorem/statement by trusting the entity through the signature and not by the proof itself. This is true, at first thought. However, the idea here that the formal proof is still available for rechecking if desired; for example, two different entities might choose to do two different things. Anyway, this is just the foundational idea to start with, and much is to emerge further.

### First Step

As a result, it makes sense to start the investigation by experimenting with how these **assets** and **assertions** can be *presented*, *shared*, and *distributed* through the web, regardless for now, of how different and diverse the forms of **assets** can be, and what problems will arise from this fact. This diversity is due to the existence of several producers of such assets (theorem provers and proof assistants), which differ in both aspects of their implementation as well as the logical foundations they stand upon, which makes the process of normalizing the form of these assets to exchange them in a distributed and transparent manner non-trivial.

But again, this is not the first thing to address, as before worrying about wanting to plant various kinds of trees in a garden, maybe to make it colorful, one first needs to know how to plant a tree in the first place. Hence, **we start the W3Proof project by developing a first exploratory tool** that is intended **to work with one kind of asset producer** [and consumer] &rarr; [w3proof-dispatch](./w3proof-dispatch.md): a first attempt to explore potential possibilities.

However, before introducing and illustrating the core idea and functionalities of [w3proof-dispatch](./w3proof-dispatch.md), let us first present an overview of the **main components** at the base of this project and the main motivations behind using them.

---

## Components Involved

### Abella: the Proof Assistant

To quote [Abella's official website](https://abella-prover.org):

> Abella is an interactive theorem prover based on lambda-tree syntax. This means that Abella is well-suited for reasoning about the meta-theory of programming languages and other logical systems which manipulate objects with binding.

Alright, what we really need to say about Abella right now is not something related to the above quotation. Of course it is important, but what we need to deal with currently is **what does this tool produce as assets for us to use**.

Basically, producing a proof for a theorem in Abella consists of introducing in a file for example, some axioms and relevant definitions for the theorem, maybe introducing/proving some other theorems (lemmas) preceding it to be used in its proof, writing the formula of the theorem itself, and then writing the **proof steps** that will help the proof assistant to complete the proof; the proof steps are usually called **proof tactics**, and a grouping of them is called a **proof script**. For you dear reader, this process might look quite familiar, as it is similar to most other software of this type. If it's not, consider the following **example**:

```apache
% Definition of natural numbers %
Kind nat type.
Type z nat.
Type s nat -> nat.

Define nat : nat -> prop by
  nat z;
  nat (s N) := nat N.

% Some theorem : the successor of a natural number, %
%                according to the above definition of natural numbers, %
%                is also a natural number. %

Theorem succ_nat : forall A, nat A -> nat (s A).

% the proof steps: %

induction on 1. intros. case H1.
search. apply IH to H2. search.

>> Proof completed. [after execution]
  
```

This is an example of what is called a ***theorem* file in Abella**, with the `.thm` extension.

The above example as displayed is contained in a single file, however, it could exist differently: in two files `nats.thm` and `some_theorems.thm`, one of them **Importing** the other:

```apache
% in file "nats.thm" %
Kind nat type.
Type z nat.
Type s nat -> nat.

Define nat : nat -> prop by
  nat z;
  nat (s N) := nat N.
```

```apache
% in file "some_theorems.thm" %

Import "nats".

Theorem succ_nat : forall A, nat A -> nat (s A).
induction on 1. intros. case H1.
search. apply IH to H2. search.
```

### JSON: Data Formatting

### Signatures: Trust Bridge

### IPLD: Content-Addressing

### IPFS: Our Agent to the Web
