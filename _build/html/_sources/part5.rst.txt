.. _part5:

***************
Part 4: Introduction to Tezos Development
***************
Developing on Tezos is no different than building on other blockchains. Michelson and Liquidity are the languages used for smart contract development, and can interact with HTML and Javascript frontends. Tokens on the Tezos blockchain is known as “tez” and can be stored in Tezos wallets. There are multiple networks used for Tezos Development: the Mainnet, Alphanet and Zeronet.

Mainnet
=============================
The Tezos network is the current incarnation of the Tezos blockchain. It runs with real tez that have been allocated to the donors of July 2017 ICO. The Tezos network has been live and open since June 30th 2018.

Alphanet
=============================
Tezos Alphanet is a test network for the Tezos blockchain with a faucet to obtain free tez [http://tezos.gitlab.io/mainnet/introduction/howtouse.html#faucet ] (see Get free tez). It is updated and rebooted rarely and it is running the same code as the Mainnet. It is the reference network for developers wanting to test their software before going to beta and for users who want to familiarize themselves with Tezos before using their real tez. The Tezos Alpha (test) network has been live and open since February 2017.

Zeronet
=============================
possibly several times a day. This network is mostly used internally by the Tezos developers and may have different constants that Alphanet or Mainnet, for example it has shorter cycles and a shorter interval between blocks. Tezos offers no support for the Zeronet.

***************
The Languages
***************

Michelson
=============================
Michelson is the language used for programming Tezos Smart Contracts. The language is stack based, with high level data types and primitives and strict static type checking. Its design cherry picks traits from several language families.

A Michelson program is a series of instructions that are run in sequence: each instruction receives as input the stack resulting of the previous instruction, and rewrites it for the next one. The stack contains both immediate values and heap allocated structures. All values are immutable and garbage collected.

A Michelson program receives as input a single element stack containing an input value and the contents of a storage space. It must return a single element stack containing aa output value a list of internal operations, and the new contents of the storage space. Alternatively, a Michelson program can fail, explicitly using a specific opcode, or because something went wrong that could not be caught by the type system (e.g. division by zero, gas exhaustion).

The types of the input, output and storage are fixed and monomorphic, and the program is typechecked before being introduced into the system. No smart contract execution can fail because an instruction has been executed on a stack of unexpected length or contents.
This specification gives the complete instruction set, type system and semantics of the language. For the purpose of Tezos Capstone we will be focused on development in the Liquidity language in Section 2.

OCaml
=============================
OCaml (previously known as objective caml) was created in 1996, and is an object-oriented implementation of Caml. It is a functional, imperative and object-oriented language, allowing development to be versatile. Different paradigms can be used, allowing object-oriented structure and imperative functions to be used when needed. Originating from academia, OCaml is extremely efficient and fast, comparable to C, despite it being a high-level and type-safe language.

OCaml is used throughout industry by companies such as Facebook, Docker and Jane Street. It serves as the base syntax for Liquidity.

Liquidity
=============================
Although Michelson can be used directly for the creation of Smart Contracts, the lack of variables and the use of stack-based instructions make it hard to write, and harder to read. Early in the life of Tezos, there was a need for a higher-level language for easier development. The Liquidity prototype was born in June 2017 at OCamlPro, and officially released in February 2018 on the Alphanet network of Tezos.

Liquidity follows Michelson type-system, but implemented on a subset of the OCaml syntax. It comes with a compiler to Michelson, and a decompiler that can translate Michelson contracts to Liquidity, for auditing purpose. We will be focused on Liquidity development in Section 2 of Tezos Capstone.

Additional Reading
=============================

`Michelson White Paper <http://tezos.gitlab.io/mainnet/whitedoc/michelson.html/>`_

`Jane Street explanation on why Ocaml <https://www.youtube.com/watch?v=v1CmGbOGb2I/>`_

`Liquidity <http://www.liquidity-lang.org/doc/index.html/>`_
