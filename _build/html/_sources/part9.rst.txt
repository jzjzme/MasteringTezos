.. _part9:

*************************
Building your first DApp
*************************

The Contract
================

We will be building a voting smart contract based on https://www.zastrin.com/courses/simple-tezos-dapp/lessons/1-1 from Zastrin and TCF. The purpose of the contract is to pass a list of candidates in an election. The logic in the smart contract will count the votes made for each candidate, while preventing people from voting multiple times.

For the contract development, we recommend using the Liquidity online IDE http://www.liquidity-lang.org/zeronet/. There are several smart contract examples on there to explore, and it also supports testing, deployment and displays the corresponding Michelson code. All smart contracts in liquidity are .liq files.

Let’s get to it!

Declaring the storage
=======================

First let’s outline the storage for the contract. We want to store two things: all the candidates in the election and the amount of votes they have received, as well as voter information so they cannot vote multiple times. These will be stored in the form of a hash or key-value store. So to do this, we will have candidates store their name (string) and votes (int) while voters store their Tezos address (address) and if they voted or not (bool).


::

  [%%version 0.4]

  type storage = {
  		candidates : (string, int) map;
  		voters : (address, bool) map;
  }


The init Function
====================

Let’s create the init function which builds the necessary parts when the contract is first created. When deployed, we need to first get all the candidates’ names and set their respective vote counts to zero. To do this, we will be using Liquidity’s fold function which is an accumulator that applies a function to an array. We will also need to create an empty storage for the voters, as there are none initially when the smart contract is first deployed.

::

  let%init init_candidates (candidate_names : string list) =
  let candidates = List.fold (fun (elt, map) -> Map.add elt 0 map) candidate_names
        		(Map [] : (string, int) map) in
    	{ candidates = candidates; voters = (Map : (address, bool) map); }


The Main Function
===================

Let’s move to the main function of the smart contract and create the logic which will power the contract.

The first parameter is the string, which the caller will pass when voting for a candidate. The first logic we want to add is that when a caller calls the contract and passes the candidate name, the vote count will increment. But first, we need to find the candidate using the map.find function. If the candidate is not found, the failwith function, which is like an error, will show the candidate is not valid. If the candidate is found, we will use the map.add function to increment the vote by one.

::

  let%enty main
  	(parameter : string)
  	(storage : storage) =

    	Map.find parameter storage.candidates with
    		None -> failwith (“Candidate is not valid”, parameter)
    		Some x -> Map.add parameter (x+1) storage.candidates



It is important to know that in Liquidity there are no side effects. This means that when you execute Map.add instead of modifying, it returns a new map. So we will need to catch this using the match keyword. Match is a standard in both OCaml and Liquidity for changing maps by finding the associated values then performing operations.

::

  let%enty main
  	(parameter : string)
  	(storage : storage) =

    	Storage.candidates <- match Map.find parameter storage.candidates with
    		None -> failwith (“Candidate is not valid”, parameter)
    		Some x -> Map.add parameter (x+1) storage.candidates

Let’s also assign our storage variable to our new storage and finish the entry function. Since we do not have any additional operations, we can return an empty list.

::

  let%enty main
  	(parameter : string)
  	(storage : storage) =

  let storage =
  	Storage.candidates <- match Map.find parameter storage.candidates with
  		None -> failwith (“Candidate is not valid”, parameter)
  		Some x -> Map.add parameter (x+1) storage.candidates

  in
    (([] : operation list), storage)

Let’s build the logic for the voters. First we need to derive the address of the voter using Current.source() function. Next, let’s check if the voter has voted before using the match function from earlier. If the address does not match to any address in the map, we can add the voter’s address to our map as the voter has not voted yet. If the address matches, then we can return an error that the voter has voted already. Don’t forget to catch the new map!

::

  let addr = Current.source () in

  let storage =
    storage.voters <-match Map.find addr storage.voters with
    	None -> Map.add addr true storage.voters
    	Some x -> failwith (“Voter has already voted”, addr)
  in


Let’s look at the code as a whole now:

::

  [%%version 0.4]

  type storage = {
  		candidates : (string, int) map;
  		voters : (address, bool) map;
  }

  let%init init_candidates (candidate_names : string list) =
  let candidates = List.fold (fun (elt, map) -> Map.add elt 0 map) candidate_names
        		(Map [] : (string, int) map) in
    	{ candidates = candidates; voters = (Map : (address, bool) map); }

  let%enty main
  	(parameter : string)
  	(storage : storage) =

  	let addr = Current.source () in
  let storage =
  		storage.voters <-match Map.find addr storage.voters with
  			None -> Map.add addr true storage.voters
  			Some x -> failwith (“Voter has already voted”, addr)
  in

  let storage =
      		Storage.candidates <- match Map.find parameter storage.candidates with
     			 None -> failwith (“Candidate is not valid”, parameter)
      			Some x -> Map.add parameter (x+1) storage.candidates
    	in

   	(([] : operation list), storage)

If you decided to compile the contract, there may be a warning for undeclared variable x. This is because x has not been determined yet until user input, but otherwise the contract is complete! Congrats! Let’s get to building the HTML frontend.
