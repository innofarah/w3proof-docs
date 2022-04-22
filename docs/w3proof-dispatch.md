# w3proof-dispatch

## Motivation

Basically, we can consider a formal proof to be some **'asset'** that is considered an evidence for the validity of some statement. These 'assets' are usually produced by [theorem provers](https://en.wikipedia.org/wiki/Automated_theorem_proving) and [proof assistants](https://en.wikipedia.org/wiki/Proof_assistant#:~:text=In%20computer%20science%20and%20mathematical,proofs%20by%20human%2Dmachine%20collaboration.). To trust a statement 'on the web' means to 'assert'/'declare' this trust and transmit the **'assertion'** through the web. So, as we are considering formal proofs to be the source of trust, what needs to be transmitted and exchanged as the embodiement of this trust are formal proofs themselves, and thus the 'assets' referring to them.

As a result, it makes sense to start the exploration by experimenting with how these 'assets' can be presented, shared, and distributed through the web, regardless, for now, of how different and diverse their forms can be, and what problems will arise from this fact. This diversity is due to the existence of several producers of such 'assets' (theorem provers and proof assistants), which differ in both aspects of their implementation as well as the logical foundations they stand upon, which makes the process of normalizing the form of these 'assets' to exchange them in a distributed and transparent manner non-trivial.

But again, this is not the first thing to address, as before worrying about wanting to plant various kinds of trees in a garden, maybe to make it colorful, one first needs to know how to plant a tree in the first place. Hence, the [w3proof-dispatch](https://github.com/innofarah/w3proof-dispatch) tool is a first attempt to explore the potential possibilities.

## Entry Goal

The main goal of this tool is to address the idea of sharing formal proofs as produced by the [Abella](https://abella-prover.org) proof assistant, and the idea of sharing 'assertions' of the validity of some 'asset', according to some specific producer. What is meant by this?

## Components Involved

To make things simple at the beginning, only one producer of 'assets' (proof assistant) is considered for experimenting. This producer is the [Abella](https://abella-prover.org/) proof assistant. The other component within this experiment is the [IPFS](https://ipfs.io/)/[IPLD](https://ipld.io/) model.
