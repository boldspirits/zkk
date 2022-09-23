---
layout: default
---

<div align="center">
  <h1 align="center">ZKP Knowledge Base</h1>
  <p align="center">An ongoing knowledge base for ZKP domain knowledge.</p>
</div>

## Historical Overview

### Foundations of zkSNARKs

This is an overview of foundational papers relevant to zkSNARKs. It’s mostly based on [presentations](https://twitter.com/stonecoldpat0/status/1017778014841602048/photo/1) by Jens Groth at the IC3 Bootcamp at Cornell University in July 2018 and at the 2nd [ZKProof Standards workshop](https://www.youtube.com/watch?v=X-z3JYlFdzs) in Berkeley, CA in April 2019.

Jens talks about three recurring motifs:

1. Language - what statements can we prove
2. Security - what are our assumptions, unconditional soundness vs. unconditional zero knowledge
3. Efficiency - prover, verifier computation, interaction, setup size, succinctness

The following papers in theoretical computer science/cryptography set the boundaries of what we are working with (note that some papers deal with more than one aspect of ZKPs):

#### Theory

[GMR85] Goldwasser, Micali, Rackoff [[The Knowledge Complexity of Interactive Proof Systems]](https://people.csail.mit.edu/silvio/Selected%20Scientific%20Papers/Proof%20Systems/The_Knowledge_Complexity_Of_Interactive_Proof_Systems.pdf)

- defines zero-knowledge proofs in terms of completeness, soundness, zero-knowledge
- gives an interactive zero-knowledge proof system

#### Language

[GMW91] Goldreich, Micali, Wigderson [[Proofs that Yield Nothing But their Validity or All Languages in NP have Zero-Knowledge Proofs]](https://people.csail.mit.edu/silvio/Selected%20Scientific%20Papers/Zero%20Knowledge/Proofs_That_Yield_Nothing_But_Their_Validity_or_All_Languages_in_NP_Have_Zero-Knowledge_Proof_Systems.pdf)

- look at graph 3-coloring problem
- prove that NP-complete languages have proof systems

#### Security

[GMW91] Goldreich, Micali, Wigderson [[Proofs that Yield Nothing But their Validity or All Languages in NP have Zero-Knowledge Proofs]](https://people.csail.mit.edu/silvio/Selected%20Scientific%20Papers/Zero%20Knowledge/Proofs_That_Yield_Nothing_But_Their_Validity_or_All_Languages_in_NP_Have_Zero-Knowledge_Proof_Systems.pdf)

- one-way functions suffice for computational zero-knowledge

[BC86] Brassard, Crépeau [[All-or-Nothing Disclosure of Secrets]](http://crypto.cs.mcgill.ca/~crepeau/PDF/ASPUBLISHED/BCR86.pdf)

- you can get perfect (unconditional) zero-knowledge as opposed to computational zero-knowledge

[BCC88] Brassard, Chaum, Crépeau [[Minimum Disclosure Proofs of Knowledge]](http://crypto.cs.mcgill.ca/~crepeau/PDF/ASPUBLISHED/BCC88.pdf)

- look at zero-knowledge against unbounded adversaries

#### Efficiency

[BFM88] Blum, de Santis, Micali, Persiano [[Non-interactive Zero-knowledge]](https://people.csail.mit.edu/silvio/Selected%20Scientific%20Papers/Zero%20Knowledge/Noninteractive_Zero-Knowkedge.pdf) 

- CRS (common reference string) for non-interactive ZKPs

[Kilian92] Kilian [[A note on efficient zero-knowledge proofs and arguments]](https://people.csail.mit.edu/vinodv/6892-Fall2013/efficientargs.pdf)

- how to get succinct interactive proofs

#### Pairing-based cryptography

Later on we have some ideas from pairing-based cryptography:

[BGN05] Dan Boneh, Eu-Jin Goh, Kobbi Nissim [[Evaluating 2-DNF Formulas on Ciphertexts]](https://crypto.stanford.edu/~dabo/papers/2dnf.pdf)

- pairing-based double-homomorphic encryption scheme

#### Non-interactive zero-knowledge

From there, we can ask, how to get perfect non-interactive zero-knowledge?

[GOS06] Jens Groth, Rafail Ostrovsky, Amit Sahai [[Perfect Non-Interactive Zero Knowledge for NP]](https://eprint.iacr.org/2005/290.pdf)

- efficient, uses circuit-SAT

[GS08] Jens Groth, Amit Sahai [[Efficient Non-Interactive Proof Systems for Bilinear Groups]](https://eprint.iacr.org/2007/155.pdf)

- efficient, uses a practical language (R1CS)

[Gro10] Jens Groth [[Short pairing-based non-interactive zero-knowledge arguments]](https://www.iacr.org/archive/asiacrypt2010/6477323/6477323.pdf)

- preprocessing zk-SNARKs
- power knowledge of exponent(KoE) assumption
- universal CRS, works for any circuit

#### Succinctness

And then, how to get succinctness?

[GW11] Gentry, Wichs [[Separating Succinct Non-Interactive Arguments From All Falsifiable Assumptions]](https://eprint.iacr.org/2010/610.pdf)

- SNARG = Succinct non-interactive argument
- justifies need for KoE assumption

[BCCT12] Bitansky, Canetti, Chiesa, Tromer [[From extractable collision resistance to succinct non-Interactive arguments of knowledge, and back again]](https://eprint.iacr.org/2011/443.pdf)

- zk-SNARK
- verifier time polynomial in statement size (ease of verification)

[GGPR13] Gennaro, Gentry, Parno, Raykova [[Quadratic Span Programs and Succinct NIZKs without PCPs]](https://eprint.iacr.org/2012/215.pdf)

- quadratic span programs, quadratic arithmetic programs
- specialized CRS, tailored to specific circuit

This is a graph of various constructions in this [video](https://www.youtube.com/watch?v=X-z3JYlFdzs&t=668s) at 34:00

#### Implementations

And at this point we begin to see implementations:

[PHGR13] Parno, Gentry, Howell, Raykova [[Pinocchio: Nearly Verifiable Practical Computation]](https://eprint.iacr.org/2013/279.pdf)

Relating back to the three motifs, Jens talks about the following areas for improvement with regard to each of the three motifs:

1. Language: Pairing-friendly languages, interoperability between languages

2. Security: Setup - multi-crs, mpc-generated, updatable; Formal verification

3. Efficiency: Asymmetric pairings, commit-and-prove

#### Reference Texts:

- Introduction to Modern Cryptography by Katz, Lindell
- Algebra by M. Artin
- Abstract Algebra by Dummit and Foote
- Introduction To Commutative Algebra, by M. Atiyah and I. Macdonald
- Arithmetic of Elliptic Curves by J. Silverman

## Hardware Acceleration

### Leading Problem

- Proof generation is time-consuming, high-latency, and not efficient enough on traditional CPUs
- As L2 rollups and other applications of ZKP grow, we need to consider hardware as a potential breakthrough of performance improvement

### Business Models

- zk-mining: Plug-n-play FPGA accelerator cards (revenue through hardware sale)
- zk-Rollup: public, private and on-premise cloud (revenue through hourly premiere)
- Software auxiliary: SDK for dApps and API (license to program FPGA in developer-friendly way

### 3 Potential Scenarios

1. Permissioned networks, e.g. StarkNet 
2. Permissionless networks where provers compete on cost, e.g. Mina's Snarketplace
3. Permissionless networks where provers compete on latency, e.g. Polygon Hermes & Zero 

### Selection metrics
1. Performance: latency, throughput, and power consumption 
2. Total cost of ownership (capital expenditures and maintenance costs) 
3. NRE cost (non recurring engineering: onboarding difficulties) 
4. Long-term comparative advantage: competitor performance may double in a year with the same MSPR (e.g. Intel, Nvidia GPU) 

### Structure of ZKP Hardware Acceleration
- Current popular structure is to combine CPU and FPGA/GPU to perform proof generation. CPU tackles single-threaded pieces at higher frequency and deal with non-determinism 
- MSM and FFT can be parallelized, but arithmetization and commitments may be single threaded (different from the “embarrassingly parallel” PoW mining structure) 
- Most FPGA design tools are proprietary: FPGAs have higher barrier to enter than GPU accelerations 

## Light Client 

### Leading Problem

- Full node is resource-draining: downloading and verifying the whole chain of blocks takes time and resources
- Not retail friendly to be on mobile and perform quick actions like sending transactions and verifying balances

### Technology Highlight

- Trust-minimized interaction with full nodes and do not interact directly with the blockchain
- Much lighter on resources and storage but require higher network bandwidth
- Linear time based on chain length: verify from the root to the target height (may be from a trusted height, therefore constant length)
- Process overview:
    - retrieve a chain of headers instead of full block
    - verify the signatures of the intermediary signed headers and resolve disputes through checking with full nodes iteratively
- Superlight client: requires downloading only a logarithmic number of block headers while storing only a single block header between executions

### Commit-and-proof Schemes

| Name                                           | Mechanism                                                                     | Prover Complexity | Verifier Complexity | Trusted Setup | Reference                                                                                                                                                  |
| ---------------------------------------------- | ----------------------------------------------------------------------------- | ----------------- | ------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Recursive SNARKs                               | Cycle of elliptic curves                                                      | High              | Low                 | Yes           | [https://minaprotocol.com/wp-content/uploads/technicalWhitepaper.pdf](https://minaprotocol.com/wp-content/uploads/technicalWhitepaper.pdf)                 |
| KVC (Key-Value Commitment)                     | Constant size key-value map                                                   | Med-high          | Medium              | No            | [https://eprint.iacr.org/2020/1161.pdf](https://eprint.iacr.org/2020/1161.pdf)                                                                             |
| AMT (authenticated multipoint evaluation tree) | authenticate a polynomial multipoint evaluation at the first n roots of unity | Medium            | Medium              | No            | [https://people.csail.mit.edu/devadas/pubs/scalable\_thresh.pdf](https://people.csail.mit.edu/devadas/pubs/scalable_thresh.pdf)                            |
| KZG Polynomial Commitment                      | Elliptic curve pairings with BLS12-381                                        | High              | Low                 | Yes           | [https://www.iacr.org/archive/asiacrypt2010/6477178/6477178.pdf](https://www.iacr.org/archive/asiacrypt2010/6477178/6477178.pdf)                           |
| Verkle Tree                                    | (with anonymous revocation)                                                   | High              | Low                 | No            | [https://math.mit.edu/research/highschool/primes/materials/2018/Kuszmaul.pdf](https://math.mit.edu/research/highschool/primes/materials/2018/Kuszmaul.pdf) |
| Vector Commitment                              | RSA and computational Diffie-Hellman over bilinear groups                     | High              | Low                 | Yes           | [https://eprint.iacr.org/2011/495.pdf](https://eprint.iacr.org/2011/495.pdf)                                                                               |
| One-to-many prover VSS                         | Prover batching with sumcheck and Fiat-Shamir                                 | Medium            | Low                 | No            | [https://www.usenix.org/system/files/sec22summer\_zhang-jiaheng.pdf](https://www.usenix.org/system/files/sec22summer_zhang-jiaheng.pdf)                    |


 

## Arithmetic Fields

### Leading Problem

- Proof systems encode computation as a set of polynomial equations defined over a field. Operating on a different field will lead to gigantic circuits.
- For pairing based SNARKs, there is a limited selection of pairing-friendly curves such as BN254 and BLS12-381.
- FFTs require factors of two for the curves in order to make the polynomial computations practical.
- Proof recursions require encoding arithmetic statements of a field into equations over a different field.
- Bridge operators and roll-ups need interoperability with non-pairing friendly and not highly 2-adic curves, such as Bitcoin and Ethereum’s ECDSA over secp256k1. ([BN254 precompiled contract](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-197.md))
- Choosing the field is a tradeoff of speed and security.

### Solutions

- Brute force: decompose elements into limbs and operate on the limbs; Reduce and recompose the elements only when necessary
    - Very expensive: may represent up to 1000X the original constraints in the circuit
    - [xJsnark framework](https://akosba.github.io/papers/xjsnark.pdf)
    - [gnark implementation](https://github.com/ConsenSys/gnark/blob/3d3672148b38c548b6527c5f2cfe1af5ae61a11f/std/math/nonnative/doc.go)
- 2-chains and cycles: use matching base fields to implement one curve inside of the other (assume pairing based schemes)
    - Non-pairing based scheme can use non-pairing friendly or hybrid cycles at a cost, such as using PCS (polynomial commitment scheme) or pasta curves with linear time.
    - [Pasta Curves](https://electriccoin.co/blog/the-pasta-curves-for-halo-2-and-beyond/)
    - [2-chains of elliptic curves](https://eprint.iacr.org/2021/1359.pdf)
- Lower the requirements on the field: Polynomial Commitment Scheme (PCS) may not involve elliptic curves at all to be instantiated on arbitrary fields

### Reference Reading

- [A survey of elliptic curves for proof systems](https://eprint.iacr.org/2022/586.pdf)
- [ECFFT: Fast Polynomial Algorithms over all Finite Fields](https://arxiv.org/abs/2107.08473)

## Efficient Signatures 

### Leading Problems

- Signature verification is a problem that arises in many ZK related projects, from Zcash to zk-rollups
- Different types of signatures depend on different field or curve arithmetic and need different speed-up methods
- Here we will discuss some different options for signature schemes, and strategies for efficient implementations

#### Specialized ZK signatures

- Given a ZKP system, a simple signature scheme can be constructed as follows. The signer generates a random secret key sk, and hashes it to get the associated public key pk. They then prove, in zero knowledge, that they know some sk such that hash(sk) = pk. [Picnic](https://microsoft.github.io/Picnic/) is a variant of this idea, using a block cipher rather than a hash function
- Since the statement being proved involves just a single evaluation of a hash or block cipher, these schemes can be highly efficient, particularly if using arithmetic-friendly primitives such as LowMC or Poseidon
- The caveat here is that the proof must be generated by the user who owns the secret key. If the signature is part of a larger circuit, such as Zcash’s spend circuit, this may be undesirable, as a user cannot outsource proving to another entity without revealing their secret key to that entity

#### Native curves

- If we wish to support delegated proving, it may be best to use a conventional signature scheme such as ECDSA, and include its verification steps in our circuit. This way the user can generate just a signature, and a separate prover can prove that they witnessed a valid signature
- To make this efficient, we can choose an elliptic curve such that the base field of the curve matches the “native” field of our argument system. An example of this is the [Baby Jubjub](https://eips.ethereum.org/EIPS/eip-2494) curve, whose base field matches the scalar field of alt_bn128. If we use an argument system such as Groth16 with alt_bn128 as our curve, Baby Jubjub arithmetic can be done “natively”
- However, using a curve like Baby Jubjub isn’t always an option. Sometimes we need compatibility with existing tools which support conventional curves. Polygon Zero, for example, must support Ethereum’s existing signature scheme, which is ECDSA over secp256k1. In these cases, we must simulate arithmetic in another field using bignum techniques

#### Bignum techniques

- For example, if we use standard multiplication algorithms for ED25519 field multiplication and range check each of the 5x5 limb products, we can reduce the cost by:
- Since 2^255 = 19 mod p_ed25519, you could combine limb products with the same weight mod 255 (in bits). The combined products will have a few more bits but it should be cheaper overall
- If we split each intermediate product into bits and use binary adders, we can minimize the number of splits by adding intermediate products with the same weight "natively" first. For example, if two intermediate products have a weight of 2^51 (the base), we can split the sum into 52 bits, which is just over half the cost of doing two 51-bit splits. When we have an intermediate product with a weight of 2^255 or more, we can change its weight to 1 and multiply it by 19, since 2^255 = 19 mod p_ed25519. That could help to further reduce the number of splits

##### CRT inspired methods

- Alternatively, there's the Aztec approach of having the prover give a purported product, then checking the identity mod p_native (almost free) and then mod, say, 2^306 (can ignore limb products with weights of 306+)
- We're going to publish a couple other methods soon, which should be cheaper than the ones above

##### Other tricks

- These methods can be generalized to arbitrary low-degree formulas rather than simple multiplications. Checking a whole elliptic curve formula directly can be much more efficient
- Finally, we would expect the cost to come down significantly if you used a PLONK or STARK implementation that supported lookup-based range checks, instead of range checking via binary decomposition

#### Edge cases

- We can use incomplete formulae if we’re careful

#### Conventional optimizations

- In the scalar multiplication code, we would suggest looking into windowing
- If we’re checking an ECDSA or EdDSA signature, we can leverage the fact that one of the multiplications has a fixed base, enabling various preprocessing tricks
- Curve-specific: secp256k1 supports the [GLV endomorphism](https://link.springer.com/chapter/10.1007/3-540-44647-8_11), for example, which allows us to split a curve multiplication into two smaller ones, opening the door to multi-scalar multiplication methods such as Yao’s

### Suggestions

1. Use “ZK native” signatures if possible (i.e. [Picnic](https://microsoft.github.io/Picnic/))
2. Use “native” curves if possible (i.e. [JubJub](https://github.com/zkcrypto/jubjub))
3. In non-native curve arithmetic, for example ED25519, combine the limb products with the same weight mod 255 (in bits) 
    1. minimize the number of splits by adding intermediate products with the same weight first. For example, when we have 2 intermediate projects of weight 2^51, we can split the sum into 52 bits 
    2. If we have an intermediate product with weight of 2^255 or more, we can change its weight to 1 and multiply by 19, since 2^255 = 19 mod p_ed25519
4. Use CRT related method like Aztec’s approach to have the prover give a purported product and check the identity mod p_native to ignore large limb products 
5. Use a PLONK or STARK can cut down the cost significantly 
6. Check [windowing](https://en.wikipedia.org/wiki/Elliptic_curve_point_multiplication) in the scalar multiplication code 
7. Leverage the constant generator in one of the multiplications in EdDSA 
8. [GLV Endomorphism](https://link.springer.com/chapter/10.1007/3-540-44647-8_11) can split a curve multiplication into two smaller ones in curves like secp256k1

## Proof Aggregation

### Leading Problem

- Proving n statements individually leads to n proofs. Therefore, in the absence of recursion/aggregation, the verification cost grows linearly with the number of statements proven. This is not ideal for a high-throughput blockchain

### Technology Highlight

- Custom PLONK gates, the bilinearity elliptic curve pairings as used in KZG

### Proof Aggregation Schemes

- Halo uses recursion to include proof number i-1 in proof i for all i and: 
  - amortizes the verification cost of the final proof for all n proofs
  - necessitates sequentialism: proof i cannot be generated until proof i-1 already exists
- Plonky2 uses custom PLONK gates for the Poseidon hash function to succinctly verify FRI proofs
  - recursive proofs on FRI proofs to prove the validity of multiple proofs in one
  - the final recursive proof proves the validity of all tx proofs
- SnarkPack utilizes the KZG10 polynomial commitment schemes together with the Bulletproof trick to aggregate Groth16 proofs into a single proof 
  - can be verified in base-2 logarithmic time (in the number of proofs)

### Current Research Progress

### Reference Reading

- [Proofs for Inner Pairing Products and Applications](https://eprint.iacr.org/2019/1177)
- [SnarkPack: Practical SNARK Aggregation](https://eprint.iacr.org/2021/529)
- [Recursive Proof Composition without a Trusted Setup](https://eprint.iacr.org/2019/1021)
- [Fractal: Post-Quantum and Transparent Recursive Proofs from Holography](https://eprint.iacr.org/2019/1076)
- [Fast Recursive Arguments with PLONK and FRI](https://github.com/mir-protocol/plonky2/blob/main/plonky2/plonky2.pdf) 

## Vulnerabilities

- Zero-knowledge proof systems require the following properties to be defined as a zero-knowledge proof:
  - Completeness: If a statement is true, an honest verifier will be convinced of this by an honest prover
  - Soundness: If a statement is false, then there is a negligible probably that a cheating prover can prove the validity of the statement to an honest verifier
  - Zero-knowledge property: If a statement is true, then the verifier learns nothing about the statement other than the fact that the statement is true

- As such, if one of the above properties are broken, we no longer have a valid zero-knowledge proof system
- This section organizes known vulnerabilities in implementations of zero-knowledge proof systems by the above properties and an additional section mainly pertaining to more general cryptographic vulnerabilities

### Vulnerabilities that break completeness

- Correctness of G_k, generated in the ownership proof, is not enforced in the balance proof in Lelantus
  - [Lelantus Cryptographic Audit](https://firo.org/about/research/papers/lelantus-cryptography-audit-abdk.pdf)

### Vulnerabilities that break soundness

#### The Fiat-Shamir transformation

- Trail of Bits is publicly disclosing critical vulnerabilities that break the soundness of multiple implementations of zero-knowledge proof systems, including PlonK and Bulletproofs
- These vulnerabilities are caused by insecure implementations of the Fiat-Shamir transformation that allow malicious users to forge proofs for random statements
- The vulnerabilities in one of these proof systems, Bulletproofs, stem from a mistake in the [original academic paper](https://eprint.iacr.org/2019/953.pdf), in which the authors recommend an insecure Fiat-Shamir generation
- Addendum: Challenges should also be generated in such a way they are independently random.
   - See [Fiat-Shamir challenges in range_prover are not always independently random](https://github.com/firoorg/firo/issues/890)

##### Affected Parties

- The following repositories were affected:
  - [ZenGo’s zk-paillier](https://github.com/ZenGo-X/zk-paillier)
  - [SECBIT Labs’ ckb-zkp](https://github.com/sec-bit/ckb-zkp)
  - [Adjoint, Inc.’s bulletproofs](https://github.com/adjoint-io/bulletproofs)
  - [Dusk Network’s plonk](https://github.com/dusk-network/plonk)
  - [Iden3’s SnarkJS](https://github.com/iden3/snarkjs)
  - [ConsenSys’ gnark](https://github.com/ConsenSys/gnark)

##### Solution

- The Fiat-Shamir hash computation must include all public values from the zero-knowledge proof statement and all public values computed in the proof (i.e., all random “commitment” values)

##### Reference Reading

- [Serving up zero-knowledge proofs](https://blog.trailofbits.com/2021/02/19/serving-up-zero-knowledge-proofs/)
- [The Frozen Heart vulnerability in PlonK](https://blog.trailofbits.com/2022/04/18/the-frozen-heart-vulnerability-in-plonk/)
- [The Frozen Heart vulnerability in Bulletproofs](https://blog.trailofbits.com/2022/04/15/the-frozen-heart-vulnerability-in-bulletproofs/)
- [The Frozen Heart vulnerability in Girault’s proof of knowledge](https://blog.trailofbits.com/2022/04/14/the-frozen-heart-vulnerability-in-giraults-proof-of-knowledge/)
- [Coordinated disclosure of vulnerabilities affecting Girault, Bulletproofs, and PlonK](https://blog.trailofbits.com/2022/04/13/part-1-coordinated-disclosure-of-vulnerabilities-affecting-girault-bulletproofs-and-plonk/)

#### Creating Fake ZK-SNARK proofs

- In certain ZK-SNARK protocols, a trusted setup ceremony is devised in order to produce parameters for use in the proof generation of a particular statement
- However, there are extra parameters, deemed as toxic waste, that meant to be destroyed after the ceremony has been performed. If  the toxic waste is not properly disposed of, a cheating prover can generate fake proofs and mislead and honest verifier

##### Reference Reading

- [Creating fake ZK-SNARK proofs](https://medium.com/qed-it/how-toxic-is-the-waste-in-a-zksnark-trusted-setup-9b250d59bdb4)
- [Zcash Counterfeit Vulnerability](https://nvd.nist.gov/vuln/detail/cve-2019-7167)

### Vulnerabilities that break the zero-knowledge property

#### Honest verifier zero-knowledge proof

- Honest verifier zero-knowledge proofs (HVZKP) assume an honest verifier. This means that in the presence of malicious verifiers, non-interactive protocols should always be used 
- These also exchange fewer messages between prover and verifier. A malicious verifier can employ different attacks depending on the proof system

##### Reference Reading

- [Using HVZKP in the wrong context](https://www.zkdocs.com/docs/zkdocs/security-of-zkps/when-to-use-hvzk/)
- [UC non-interactive, proactive, threshold ECDSA with identifiable aborts (2020)](https://eprint.iacr.org/2021/060.pdf)

### General Vulnerabilities affecting zero-knowledge enabled systems

#### Reference Reading

- [Disclosure of recent vulnerabilities in Aztec 2.0](https://hackmd.io/@aztec-network/disclosure-of-recent-vulnerabilities)
- [SELFDESTRUCT main via delegatecall in ZkSync](https://docs.zksync.io/dev/security/ZKSYNC1-2021-01/)


## Licensing

| License                              | Permissions                                                         | Conditions                                                                                                                     | Projects                                                                                                                                                                                                                                                                                                    |
| ------------------------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MIT                                  | Commercial use, distribution, modification, private use             | License and copyright notice                                                                                                   | [Scroll](https://github.com/michaelrhodes/scroll/blob/master/LICENSE), [Libsnark](https://github.com/scipr-lab/libsnark/blob/master/LICENSE), [Plonky2](https://github.com/mir-protocol/plonky2/tree/main/insertion)                                                                                                                                                                |
| GNU GPLv3                            | Commercial use, distribution, modification, patent use, private use | Disclose source, license and copyright notice, state changes                                                                   | [Aleo](https://github.com/AleoHQ/aleo/blob/main/LICENSE.md), [Tornado Cash](https://github.com/tornadocash/tornado-core/blob/master/LICENSE). [Aztec](https://github.com/AztecProtocol/AZTEC/blob/develop/LICENSE)                                                                                          |
| Mozilla Public License               | Commercial use, distribution, modification, patent use, private use | Disclose source, license and copyright notice                                                                                  |   /                                                                                                                                                                                                                                                                                                          |
| Apache License                       | Commercial use, distribution, modification, patent use, private use | License and copyright notice, state changes                                                                                    | [O(1) Labs](https://github.com/o1-labs/proof-systems/blob/master/LICENSE), [StarkEx](https://github.com/starkware-libs/starkex-contracts/blob/master/LICENSE), [Halo2](https://github.com/zcash/halo2/blob/main/LICENSE-APACHE), [zkSync](https://github.com/matter-labs/zksync/blob/master/LICENSE-APACHE), [Plonky2](https://github.com/mir-protocol/plonky2/tree/main/insertion) |
| BSD License                          | Commercial use, distribution, modification, patent use, private use | Disclose source, license and copyright notice                                                                                  |                        /                                                                                                                                                                                                                                                                                     |
| BSL                                  | Non-production use, distribution, modification, private use         | Disclose source, license and copyright notice                                                                                  | [Uniswap v3](https://github.com/Uniswap/v3-core/blob/main/LICENSE), Aave                                                                                                                                                                                                                                    |
| BOSL (Bootstrap Open Source License) | Commercial use, distribution, modification, private use             | Open-source the improvements, improvements available under BOSL after 12 months, disclose source, license and copyright notice | Zcash ([halo2’s](https://github.com/zcash/orchard/blob/main/LICENSE-BOSL) initial launch)                                                                                                                                                                                                                   |
| Polaris Prover License               | Non-commercial use                                                  | No transfer of rights, state changes                                                                                           | [StarkWare Prover ](https://starkware.co/starkware-polaris-prover-license/)                                                                                                                                                                                                                                 |

## Verifiable Delay Functions (VDF)

### Leading Problems

1. randomness is hard to generate on chain due to non-determinism, but we still want to be able to verify the randomness 
2. fairness of leader election is hard to ensure as the attacker may manipulate the randomness in election 

### VDF Requirements

1. Anyone has to compute **sequential** steps to distinguish the output. No one can have a speed advantage. 
2. The result has to be **efficiently verifiable** in a short time (typically in log(t))

### Techniques

- injective rational maps (First attempt in [original VDF paper](https://eprint.iacr.org/2018/601.pdf)): “weak VDF” requires large parallel processing
- Finite group of unknown order ([Pietrazak](https://eprint.iacr.org/2018/627.pdf) and [Wesolowski](https://eprint.iacr.org/2018/623.pdf)): use a trapdoor or Rivest-Shamir-Wagner time-lock puzzle

### Applications

- Chia blockchain: use VDF for consensus algorithms
- Protocol Labs + Ethereum Foundation: co-funding grants for research of viability of building optimized ASICs for running a VDF

### Great Resources

- [https://vdfresearch.org/](https://vdfresearch.org/)
- [https://blog.trailofbits.com/2018/10/12/introduction-to-verifiable-delay-functions-vdfs/](https://blog.trailofbits.com/2018/10/12/introduction-to-verifiable-delay-functions-vdfs/)

## Formal Verification

### Leading Problem

- How do we formally verify that a set of constraints used by a zero knowledge proof system has the desired characteristics, such as soundness, completeness, functional correctness, and zero knowledge?

- Zero knowledge proof systems often use a mathematical constraint system such as R1CS or AIR to encode a computation. The zero knowledge proof is a probabilistic cryptographic proof that the computation was done correctly

- Formal verification of a constraint system used in a zero knowledge proof requires 
   - (1) a formal specification of the computation that the constraint system is intended to encode
   - (2) a formal model of the semantics of the constraint system
   - (3) the specific set of constraints representing the computation
   - (4) the theorem prover, and
   - (5) the mechanized proof of a theorem relating (1) and (3)

### Techniques

- To prove a general statement with certainty, it must be a purely mathematical statement which can be known to be true by reasoning alone, without needing to perform any tests. The reasoning must start from consistent assumptions (axioms) and proceed by truth-preserving inferences
   - Example: given that a bachelor is defined as an unmarried man, and a married man by definition has a spouse, it can be proven with certainty that no bachelor has a spouse.

- A proof theory codifies a consistent set of rules for performing truth-preserving inference. Proof theories can be used to construct proofs manually, with pencil and paper
   - Example: [sequent calculus for classical logic](http://logitext.mit.edu/logitext.fcgi/tutorial)

- Computer programs called proof assistants reduce labor and mitigate the risk of human error by helping the user to construct machine-checkable proofs
   - Examples: [Coq](https://coq.inria.fr/), [Agda](https://agda.readthedocs.io/en/v2.6.0.1/getting-started/what-is-agda.html), [Coq](https://coq.inria.fr/), [Agda](https://agda.readthedocs.io/en/v2.6.0.1/getting-started/what-is-agda.html), [Isabelle](https://isabelle.in.tum.de/), [ACL2](https://www.cs.utexas.edu/users/moore/acl2/manuals/latest/?topic=ACL2____TOP), [PVS](https://pvs.csl.sri.com/), [Imandra](https://docs.imandra.ai/imandra-docs/), and [Lean](https://leanprover.github.io/)

#### Using a proof assistant

- To use a proof assistant to prove a statement about a program, there are two main approaches:

  - (1) Write the program in the proof assistant language and apply the proving facilities to the program directly
  - (2) Use a transpiler to turn a program written in another language into an object which the proof assistant can reason about

- Of these approaches, (1) seems preferable for the greater confidence provided by the proof being about exactly the (source) program being executed, as opposed to output of a transpiler which is assumed to have the same meaning as the source program
- What motivates approach (2) is when (for whatever reason) the proof assistant language is not suitable as a language for developing the application in

#### Without using a proof assistant

- There are also ways to prove a statement about a program without (directly) using a proof assistant:

  - Use a verified compiler (e.g. [CompCert](https://compcert.org/)), which turns a source program into an object program which provably has certain properties by virtue of (proven) facts about the verified compiler
     - Note that there is a distinction between a verified compiler and a verifying compiler.  CompCert itself is proved to generate binary that will always be semantically equivalent to the C input.  A verifying compiler generates a binary along with a proof of correctness that the binary is semantically equivalent to the source.
     - When a program is compiled by a verifying or verified compiler, we say that the compiler output is correct by construction (provided that the input is correct).
  - Use an automatic proof search algorithm, which takes as input statements to be proven and outputs proofs of those statements if those statements are true and the proof search algorithm finds proofs
  - Use a static analyzer, which takes as input a program and automatically checks for various kinds of issues using predetermined algorithms

- Both of these approaches have limitations:

  - A verified compiler is limited in what statements it can prove about the resulting program: typically, just that the resulting program has the same meaning or behavior as the source program

  - An automatic proof search algorithm is limited in what statements it can prove by the sophistication of the algorithm and the computational power applied to it. Also, due to Gödel's incompleteness theorem, there cannot exist a proof search algorithm which would find a proof of any given true statement

  - A static analyzer is generally not capable of reasoning about the meaning of a program to see if it’s correct; it is only able to recognize patterns which always or often indicate some kind of issue

### Formal Verification for ZK Circuits

- Formal verification for probabilistic proof systems, inclusive of ZK proof systems, encompasses two main problem spaces:

  1. Proving the intended properties of a general-purpose proving system, such as soundness, completeness, and zero knowledge (E.g., Bulletproofs, Halo 2, etc.)
  2. Proving the intended properties of a circuit, namely that it correctly encodes the intended relation

- Problem (1) is generally considered a very difficult problem and has not been done for any significant proving system

- Problem (2) can be done with a formal specification of the relation and a model of thcircuit semantics.  Usually it requires proving functional correctness of functions defined within the relation as well as the existence of witness variables for every argument to the function


#### Denotational design

- Denotational design provides a helpful way of thinking about both problem spaces (general and application-specific). The circuit denotes a set: namely, the set of public inputs for which the circuit is satisfiable

- The goal of application specific circuit verification is to prove that the circuit denotes the intended relation
- The goal of general purpose proving system verification is to prove that it has the intended properties with respect to the denotational semantics of circuits:

  1. Soundness means that if the verifier accepts a proof, then with high probability, the public input used to generate the proof (i.e., the statement being proven) is in the set denoted by the circuit (i.e., the statement is true)
  2. Completeness means that if a public input (i.e., a statement) is in the set denoted by the circuit (i.e., the statement is true), then the proving algorithm successfully outputs a proof which the verifier accepts

 - Example: consider a ZK proving system which one would use to show that one has a solution to a Sudoku puzzle, without revealing the solution
   - The statements to be proven are of the form "X (a Sudoku puzzle) is solvable"
   - The relation we intend is the set of solvable Sudoku puzzles
   - Soundness means that if the verifier accepts a proof that X is solvable, then with high probability, X is solvable
   - Completeness means that if X is solvable, then the prover creates a proof that X is solvable which the verifier accepts
   - Zero knowledge means that having a proof that X is solvable does not reduce the computational difficulty of finding a solution to X
   - To see this example worked out more formally, see [the OSL whitepaper](https://eprint.iacr.org/2022/1003).

- If you know that your circuit denotes the relation you intend, and you know that your general purpose proof system is sound and complete in the above senses, then you know that your application-specific proving system (i.e., the circuit plus the general proof system) has the intended soundness and completeness properties for that application

- This suggests that, given a formally verified general-purpose proving system, and a verifying compiler from statements to circuits, one can solve the problem of proving correctness of application-specific proving systems without application-specific correctness proofs

- Suppose that 

  1. one can write the statement to be expressed by a circuit in a machine-readable, human-readable notation, where it is self-evident that the statement being written has the intended meaning or denotation
  2. one has a verifying compiler which turns that statement into a circuit which provably has the same denotation as the source statement
  3. circuit can be executed on a formally verified general-purpose probabilistic proving system

- Then one can generate formally verified application-specific probabilistic proving systems without any additional proof writing for an additional application. This seems like a promising way forward towards a sustainable and cost effective approach to formal verification for ZK circuits

### Synthesizing formally verified programs

- Here is a summary of some of the ways in which the ecosystem supports efficient execution of verified code:

  - The proof assistants [Coq](https://coq.inria.fr/) and [Agda](https://github.com/agda/agda/) do not provide for compilation of programs written in those languages to an efficiently executable form
  - The language [ATS](http://www.ats-lang.org/) provides proof facilities and purports to allow for programming with the efficiency of C and C++
  - There are various means for transpiling code written in a mainstream language such as C or Haskell into a proof assistant, which allows for theorems to be proven about the extracted model of the source program
  - You can synthesize an efficient binary program using Coq (e.g., using [Fiat](https://github.com/mit-plv/fiat-crypto))
  - The proof assistant ACL2 defines a subset of Common Lisp with a full formal logic.  When a definition is executable, it can be compiled into efficient code, and because the language is a formal logic, you can define and prove theorems about the code
  - There is a verifying compiler project, [ATC](https://kestrel.edu/research/atc), from ACL2 to C
  - Imandra defines a subset of OCaml with a full formal logic and a theorem prover


#### Current limitations of formal methods on modern hardware

- In the context of modern computing, most computationally intensive tasks deal with vector math and other embarassingly parallel problems which are done most efficiently on specialized hardware such as GPUs, FPGAs, and ASICs
- This is generally true of the problem of constructing proofs in probabilistic proof systems. Provers for these proof systems would be most efficient if implemented on specialized hardware, but in practice, they are usually implemented on CPUs, due to the greater ease of programming on CPUs and the greater availability of those skill sets in the labor market
- For creating a formally verified implementation of a probabilistic proof system which executes efficiently, it seems that the right goal is not to optimize for speed of execution on a CPU, but to target specialized hardware such as FPGAs, GPUs, or ASICs
- Unfortunately, tools for compiling formally verified programs to run on FPGAs, GPUs, or ASICs are more or less nonexistent as far as we know

### The State of Current Progress

- Decades of research exists on formal verification strategies for arithmetic circuits in the context of hardware verification
   - See, e.g., [Drechsler et al (2022)](https://link.springer.com/chapter/10.1007/978-981-16-7182-1_36) and [Yu et al (2016)](https://ieeexplore.ieee.org/document/7442835)
   - This work has limited industral applications, e.g., the AAMP5 (see [Kern and Greenstreet (1997), page 43](https://cse.usf.edu/~haozheng/lib/verification/general/survey-FV.pdf))
   - This line of research is not directly applicable to formal verification of arithmetic circuits for zk-SNARKs, because 
     arithmetic circuits in hardware and arithmetic circuits in zk-SNARKs are not quite the same things
- Orbis Labs is working on:
   - A [verifying Halo 2 circuit compiler](https://github.com/Orbis-Tertius/coq-arithmetization) for [Σ¹₁ formulas](https://eprint.iacr.org/2022/777)
      - Expected to be working in Q4 2022 or Q1 2023
   - [Orbis Specification Language (OSL)](https://eprint.iacr.org/2022/1003/), which provides a high level spec language which we can compile to Σ¹₁ formulas
   - A toolchain (Miya) for developing formally verified, hardware accelerated probabilistic proof systems
      - A theory of interaction combinator arithmetization, towards compiling
        formally verified code into circuits
      - No timeline on this; still in basic research
- [Kestrel Institute](https://www.kestrel.edu) is a research lab that has proved functional correctness of a number of R1CS gadgets using the ACL2 theorem prover.  (Kestrel also does a lot of other FV work, including on Yul, Solidity, Ethereum, and Bitcoin)
   - They [formalized and proved](https://www.cs.utexas.edu/users/moore/acl2/manuals/latest/index.html?topic=ZKSEMAPHORE____SEMAPHORE) the functional correctness of parts of the Ethereum Semaphore R1CS
   - They [formalized and proved](https://www.cs.utexas.edu/users/moore/acl2/manuals/latest/index.html?topic=ZCASH____ZCASH) the functional correctness of parts of the Zcash Sapling protocol.  An overview of the process:
     - Used the [ACL2](https://www.cs.utexas.edu/users/moore/acl2/) proof assistant to formalize specs of parts of the Zcash Sapling protocol
     - Formalized rank 1 constraint systems [(R1CS) in ACL2](https://www.cs.utexas.edu/users/moore/acl2/manuals/latest/index.html?topic=R1CS____R1CS)
     - Used an extraction tool to fetch the R1CS gadgets from the Bellman implementation, and then used the [Axe](https://www.kestrel.edu/research/axe/) toolkit to lift the R1CS into logic
     - Proved in ACL2 that those R1CS gadgets are semantically equivalent to their specs, implying soundness and completeness
- [Aleo](https://www.aleo.org/) is developing programming languages such as [Leo](https://leo-lang.org/) that compile to constraint systems such as R1CS
     - Aleo aims to create a verifying compiler for Leo, with theorems of correct compilation generated and checked using the ACL2 theorem prover
     - Aleo has also done post-hoc verification of R1CS gadgets using Kestrel Institute's [Axe](https://www.kestrel.edu/research/axe/) toolkit
- [Nomadic Labs](https://www.nomadic-labs.com/) is a consulting firm that does a lot of work on Tezos and they built the Zcash Sapling protocol for shielded transactions into the Tezos blockchain as of the Edo upgrade.   Kestrel Institute formally verified some of the R1CSes used in that protocol. (Nomadic Labs also does a lot of other FV work)
- Anoma team is working on the [Juvix language](https://github.com/anoma/juvix) as a first step toward creating more robust and reliable alternatives for formally verified smart contracts than existing languages
- Andrew Miller and Bolton Bailey are working on a [formal verification of a variety of SNARK proof systems](https://github.com/BoltonBailey/formal-snarks-project), using the Lean Theorem Prover, in the Algebraic Group Model
- [Alex Ozdemir](https://cs.stanford.edu/~aozdemir/research/) from Stanford is working on adding a [finite field solver](https://github.com/alex-ozdemir/CVC4/tree/ff) in cvc5 SMT Solver
- Lucas Clemente Vella and Leonardo Alt are working on [SMT solver](https://github.com/lvella/polynomial-solver/blob/master/docs/SMT-2022-extended-abstract/full-text.pdf) of polynomial equations over finite fields
- Veridise is working on:
    - [Medjai](https://github.com/Veridise/Medjai), a symbolic evaluator for Cairo, intended for use in automatic proof search
    - [Picus](https://github.com/Veridise/Picus), a symbolic VM for R1CS, intended for use in automatic proof search
    - [V](https://github.com/Veridise/V), a specification language intended for use in expressing statements to be proven
      by automatic proof search
- [Ecne](https://0xparc.org/blog/ecne) is a special-purpose automatic proof search tool which can prove
  that an R1CS constraint system defines a function (total or partial)
   - In other words, it proves that for any input values on which the system is satisfiable, there
     is a unique combination of output values on which the system is satisfied
   - This proves, for an R1CS which is intended to be satisfiable on all possible inputs (denoting a function
     as opposed to a partial function), that there are enough constraints, in the sense that adding constraints
     could not change the denotation of the circuit if the denotation remains a partial function
   - This does not imply soundness
   - This approach has been proven to be useful in flushing out bugs in circuits
- [Starkware](https://starkware.co/) is writing [Lean](https://leanprover.github.io/)
  [proofs](https://github.com/starkware-libs/formal-proofs) to check that
  circuits expressed as Cairo programs conform to their specs

### How to analyze each research effort / development project

- You could analyze each research effort / development project in terms of
   - the language used for specification
   - the language used to model the constraint system
   - which theorem prover they are using
   - what sorts of theorems are they proving, like soundness, completeness, functional completeness, and zero knowledge
- Other interesting attributes of project concerning FV for constraint systems are:
   - whether the tooling and the formal verification are open source.  It is hard to have confidence in a theorem when the components that went into proving that theorem are not available for inspection
   - what is the trusted core, i.e., what software in the stack is not formally verified, and what are the possible consequences if it has bugs

### Future Research Directions

 - A lot of work needs to be done. There is not enough emphasis placed on formal verification in the security industry
 - Based on the observations and arguments presented in this blog post, we think the following will be some interesting directions for future research and development:
   - Build foundations for formally verifying zero knowledge proof systems:
   - Generalizable proof techniques for proving the desired properties formally
   - Reusable verified abstractions for proof systems, e.g., a polynomial commitment scheme library
- Can we formally verify systems that are designed to automatically make ZK circuits more efficient? 
   - For example: systems that choose a different circuit so that the setup MPC is more parallelizable or that allow a prover who learns part of the witness in advance to partially evaluate a circuit and use this information to compute proofs faster
- Improved specification languages and verified translators between specification languages
- Understand how to create formally verified programs to run on vectorized hardware, e.g., FPGAs, GPUs, and/or ASICs

### Terminology

- There are different ways to axiomatize a problem to prove it.  Some categories are denotational semantics, axiomatic semantics, and operational semantics.  Operational semantics is particularly useful for proving things about programs
- If you write a specification of a computation in a high-level formal language and compile it to a constraint system using a verified or verifying compiler, that is called correct by construction.  If you take an existing constraint system and you try to prove properties about it (up to and including soundness and completeness) with respect to a specification in a high-level formal language, that is called post-hoc verification

## Proof Systems

### Background - Commitment Schemes
- Allows one party to commit to some data by publishing a commitment
- Later they can reveal the data and convince anyone it is the same as what they committed to.
- Ideally, a commitment scheme should be:
    - **Hiding** - It does not reveal the input that is committed
    - **Binding** - It is impossible (or impractically difficult) to open a commitment to a different value that it was created with

#### Pedersen Commitments
- Let $$G$$ and $$H$$ be two public generators for a large group where the discrete log is hard.
- For an input, $$x$$, and hidden random value, $$r$$, the Pedersen commitment is $$comm(x) = xG + rH$$
- The commitment is opened by revealing $$x$$ and $$r$$
- These have some cool properties compared with hash commitments:
    - **Additively Homomorphic:** $$comm(a) + comm(b) = comm(a+b)$$
    - **Batchable:** $$x_1G_1 + x_2G_2 + ... + rH = \vec{x}\vec{G} + rH$$
- Low-level tech: discrete log group
- Assumptions: discrete log
- Resources:
    - Lecture by Dan Boneh: [https://youtu.be/IkNZWJFcfcU](https://youtu.be/IkNZWJFcfcU)
    - Overview by Bill Buchanan: [https://youtu.be/J9SOk9dIOCk](https://youtu.be/J9SOk9dIOCk)

#### Kate Commitments (KZG)
- A type of polynomial commitment scheme that employs structured reference string (SRS) and require trusted setup, thus producing toxic waste
- The verifier asks "what is the value of the polynomial at z"
- The prover responds with $$y$$ and a proof $$h(s)$$ using:
    - the polynomial $$f()$$
    - the commitment - $$f(s)$$ where $$s$$ is a secret point (toxic waste)
    - the proof - $$h(s)$$
    - the coordinates $$z$$, $$y$$
- The verifier is able to convince themselves this is true even if they don’t know $$f()$$
- Require pairing-friendly curves to multiple elliptic curve points
- Low-level tech: pairing group
- Assumptions: discrete log + secure bilinear pairing
- Used for:
    - zk-SNARKs
    - [Data Availability Sampling](https://ethresear.ch/t/an-alternative-low-degreeness-proof-using-polynomial-commitment-schemes/6649)
- Libraries:
    - [https://github.com/proxima-one/kzg](https://github.com/proxima-one/kzg) (Rust)
    - [https://github.com/sifraitech/kzg](https://github.com/sifraitech/kzg) (Rust)
    - [https://github.com/protolambda/go-kzg](https://github.com/protolambda/go-kzg) (Go)
    - [https://github.com/benjaminion/c-kzg](https://github.com/benjaminion/c-kzg) (C)
    - [https://github.com/mratsim/constantine/tree/master/research/kzg_poly_commit](https://github.com/mratsim/constantine/tree/master/research/kzg_poly_commit) (Nim)
    - [https://github.com/Nashatyrev/jc-kzg](https://github.com/Nashatyrev/jc-kzg) (Java)
- Resources:
    - General overview: [https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html](https://dankradfeist.de/ethereum/2020/06/16/kate-polynomial-commitments.html)
    - Trusted setup:
        - [https://vitalik.ca/general/2022/03/14/trustedsetup.html](https://vitalik.ca/general/2022/03/14/trustedsetup.html)
        - [https://github.com/ethereum/kzg-ceremony-specs](https://github.com/ethereum/kzg-ceremony-specs)
    - Math simply put: [https://twitter.com/bkiepuszewski/status/1518163771788824576](https://twitter.com/bkiepuszewski/status/1518163771788824576)

#### Inner Product Arguments (IPA)
- A modification of Pedersen commitments to allow polynomial commitments
- Does not require trusted setup and pairing-friendly curves
- Larger proof size compared with KZG
- Low-level tech: discrete log group
- Assumptions: discrete log
- Used for:
    - Halo2
    - [Kimchi](https://o1-labs.github.io/proof-systems/plonk/inner_product.html)
- Libraries:
    - [https://github.com/arnaucube/ipa-rs](https://github.com/arnaucube/ipa-rs) (Rust)
    - [https://github.com/arkworks-rs/poly-commit/tree/master/src/ipa_pc](https://github.com/arkworks-rs/poly-commit/tree/master/src/ipa_pc) (Rust)
- Resources:
    - General overview: [https://dankradfeist.de/ethereum/2021/07/27/inner-product-arguments.html](https://dankradfeist.de/ethereum/2021/07/27/inner-product-arguments.html)
    - Talk: [https://youtu.be/dD_0Vn4BhmI](https://youtu.be/dD_0Vn4BhmI)

#### Fast Reed-Solomon Interactive Oracle Proof of Proximity (FRI)
- Based around [Reed-Solomon](https://youtu.be/1pQJkt7-R4Q) erasure coding
- Only requires hash-based (symmetrical) cryptography (quantum-resistant)
- No need for a trusted setup
- Much larger proof sizes
- Used for:
    - STARKs
    - Plonky2
- Resources:
    - General overview: [https://aszepieniec.github.io/stark-anatomy/fri.html](https://aszepieniec.github.io/stark-anatomy/fri.html)
    - Vitalik's deep dive: [https://vitalik.ca/general/2017/11/22/starks_part_2.html](https://vitalik.ca/general/2017/11/22/starks_part_2.html)
- Assumptions: collision-resistant hash function

#### Diophantine Arguments of Knowledge (DARK)
- Based on unknown order groups
- Requires trusted setup if using RSA groups, not if using Class Groups
- Much slower verification time compared with others (O(n))
- Resources:
    - Paper: [https://eprint.iacr.org/2019/1229.pdf](https://eprint.iacr.org/2019/1229.pdf)


#### Commitment Schemes Comparison

| Scheme         | Pedersen                                         | KZG                                                                                                     | IPA                                                         | FRI                                    | DARK                                                            |
|----------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|----------------------------------------|-----------------------------------------------------------------|
| Type           | Scalar                                           | Polynomial                                                                                              | Polynomial                                                  | Polynomial                             | Polynomial                                                      |
| Low-level tech | Discrete log group                               | Pairing group                                                                                           | Discrete log group                                          | Hash function                          | Unknown order group                                             |
| Setup          | $$G,H$$ generator points and random scalar $$r$$ | $$G1$$, $$G2$$ groups, $$g1$$, $$g2$$ generators, $$e$$ pairing function, $$s_k$$ secret value in $$F$$ | $$G$$ elliptic curve, $$g^n$$ independent elements in $$G$$ | $$H$$ hash function, $$w$$ unity root  | $$N$$ unknown order, $$g$$ random in $$N$$, $$q$$ large integer |
| Commitment     | $$aG+rH$$                                        | $$(a_0s^0+...a_ns^n)g_1$$                                                                               | $$a_0g_0+...+a_ng_n$$                                       | $$H(f(w^0), ..., f(w^n))$$             | $$(a_0q^0+...a_nq^n)g$$                                         |
| Proof size     | $$O(N)$$                                         | $$O(1)$$                                                                                                | $$O(log(N))$$                                               | $$O(log^2(N))$$                        | $$O(log(N))$$                                                   |
| Verify time    | $$O(N)$$                                         | $$O(1)$$                                                                                                | $$O(log(N))$$                                               | $$O(log^2(N))$$                        | $$O(N)$$                                                        |
| Prove time     | $$O(N)$$                                         | $$O(N)$$                                                                                                | $$O(N)$$                                                    | $$O(N*log^2(N))$$                      | $$O(N)$$                                                        |

### Bulletproofs
- Short NIZK that requires no trusted setup.
- Low-level tech: Pedersen commitments.
- Uses its own constraint system, which is easily convertible to R1CS.
- Assumptions: discrete log.

#### Performance:
- Prover time: $$O(N * log(N))$$
- Verifier time: $$O(N)$$
- Proof size: $$O(log(N))$$
- Works best with `dalek` curve having a Ristretto group (a compressed group of Ed25519 points).

#### Application scope:
- Range proofs (take only 600 bytes)
- Inner product proofs
- Verifiable secret shuffle
- Intermediary checks in MPC protocols
- Aggregated and distributed (with many private inputs) proofs

#### Used in:
- Confidential TX for Bitcoin:
    - [https://elementsproject.org/features/confidential-transactions](https://elementsproject.org/features/confidential-transactions)
- Monero
    - [https://medium.com/digitalassetresearch/monero-becomes-bulletproof-f98c6408babf](https://medium.com/digitalassetresearch/monero-becomes-bulletproof-f98c6408babf)
- Stellar Shielded Tx (Cloak)
    - [https://github.com/stellar/slingshot/blob/main/spacesuit/spec.md](https://github.com/stellar/slingshot/blob/main/spacesuit/spec.md)

#### Implementations:
- [https://github.com/dalek-cryptography/bulletproofs](https://github.com/dalek-cryptography/bulletproofs) (Rust)
- [https://github.com/adjoint-io/bulletproofs](https://github.com/adjoint-io/bulletproofs) (Haskell)
- [https://github.com/bbuenz/BulletProofLib](https://github.com/bbuenz/BulletProofLib) (Java)

#### Examples:
- [https://github.com/lovesh/bulletproofs-r1cs-gadgets](https://github.com/lovesh/bulletproofs-r1cs-gadgets)
- [https://github.com/MarcKloter/bulletproofs_gadgets](https://github.com/MarcKloter/bulletproofs_gadgets)

#### Resources:
- [https://crypto.stanford.edu/bulletproofs/](https://crypto.stanford.edu/bulletproofs/)
- [https://youtu.be/gZjDKgR4dw8?t=1045](https://youtu.be/gZjDKgR4dw8?t=1045)


### Maurer (sigma) Proofs
- Short proof that needs no trusted setup.
- Dlog-based variant of the interactive Sigma protocols.
- Require a constant number (3) of public-key operations.
- Can be made non-interactive using Fiat-Shamir transform.
- Generalize Schnorr proofs to arbitrary linear functions.
- Multiple Sigma proofs can be combined to form a new proof (composition):
    - if you have two Sigma protocols for proving statements `A` and `B` you can compose them into a protocol for proving `A or B`, `A and B`, `eq(A,B)`, `all(n,A)`, `eq-all(n,A)`;
    - `n` must be known at compile time.
- Assumptions:
    - discrete log,
    - honest verifier or Fiat-Shamir.

#### Application scope
- Discrete log (dlog) proofs, prove knowledge of x such that g^x = y for publicly known values g, y.
- One-of-many dlogs, discrete log equality (dleq).
- Range proofs.
- Knowledge of message and randomness in a Pedersen commitment, equality of message in 2 Pedersen commitments.
- Pedersen commitment and ciphertext ([twisted ElGamal](https://github.com/yuchen1024/Twisted_ElGamal_PKE/blob/master/doc/Twisted_ElGamal_Report.pdf)) holds the same message.

#### Used in:
- Verifiable Random Functions
    - [https://medium.com/asecuritysite-when-bob-met-alice/verifiable-random-functions-4563d6eb17ab](https://medium.com/asecuritysite-when-bob-met-alice/verifiable-random-functions-4563d6eb17ab)
- Signal [Algebraic MACs](https://smeiklej.com/files/ccs14.pdf) for or group chats:
    - [https://signal.org/blog/signal-private-group-system/](https://signal.org/blog/signal-private-group-system/)
- Dleq proofs in the adaptor signatures
    - [https://github.com/LLFourn/one-time-VES/blob/master/main.pdf](https://github.com/LLFourn/one-time-VES/blob/master/main.pdf)
- ElGamal encryption in the [Cryptography for #metoo](https://petsymposium.org/2019/files/papers/issue3/popets-2019-0054.pdf)

#### Libraries:
- [https://github.com/LLFourn/secp256kfun/tree/master/sigma_fun](https://github.com/LLFourn/secp256kfun/tree/master/sigma_fun) (Rust)
- [https://docs.rs/zkp/0.7.0/zkp](https://docs.rs/zkp/0.7.0/zkp) (Rust)
- [https://github.com/xlab-si/emmy](https://github.com/xlab-si/emmy) (Go)
- [https://pkg.go.dev/go.dedis.ch/kyber/v4/proof](https://pkg.go.dev/go.dedis.ch/kyber/v4/proof) (Go)
- [https://github.com/cryptobiu/libscapi](https://github.com/cryptobiu/libscapi) (C++)
- [https://github.com/spring-epfl/zksk](https://github.com/spring-epfl/zksk) (Python)

#### Resources
- Overview: [https://medium.com/@loveshharchandani/zero-knowledge-proofs-with-sigma-protocols-91e94858a1fb](https://medium.com/@loveshharchandani/zero-knowledge-proofs-with-sigma-protocols-91e94858a1fb)
- Blog post about Maurer generalization of dlog-based Sigma protocols: [https://cronokirby.com/posts/2022/08/the-paper-that-keeps-showing-up/](https://cronokirby.com/posts/2022/08/the-paper-that-keeps-showing-up/)
- Math: [https://www.win.tue.nl/~berry/CryptographicProtocols/LectureNotes.pdf](https://www.win.tue.nl/~berry/CryptographicProtocols/LectureNotes.pdf) (pp. 47-61)
- Forum discussion: [https://community.zkproof.org/t/standardizing-sigma-protocols/471](https://community.zkproof.org/t/standardizing-sigma-protocols/471)


### Halo 2
- Combines an efficient accumulation scheme with [PLONKish](https://twitter.com/feministPLT/status/1413815927704014850) arithmetization and needs no trusted setup.
- Superchargable with pre-computed lookup tables and custom gates.
- Flourishing developer ecosystem actively developed tooling.
- Low-level tech: IPA commitments.
- Assumptions: discrete log.

#### Performance:
- Allows to choose (codewords rate):
    - fewer rows => fast prover,
    - fewer columns and constraints => fast verifier.
- Prover time: $$O(N * log(N))$$
- Verifier time: $$O(1)$$ > PLONK+KZG > Groth'16
- Proof size: $$O(log(N)$$

#### Application scope:
- Arbitrary verifiable computation;
- Recursive proof composition;
- Circuit-optimized hashing based on lookup-based [Sinsemilla](https://zcash.github.io/halo2/design/gadgets/sinsemilla.html) hash function.

#### Used in:
- [Zcash Orchard Shielded Protocol](https://electriccoin.co/blog/announcing-zip-224-bringing-halo-2-to-zcash/) [\[ZIP 224\]](https://github.com/zcash/zips/issues/435)
- [Scroll zkEVM](https://scroll.io/blog/zkEVM#zkEVM_Design_highlight_111)
- [Orbis ZK-Rollup](https://github.com/Orbis-Tertius) on Cardano
- [Dark Fi L1](https://dark.fi/)

#### Libraries:
- [https://github.com/zcash/halo2](https://github.com/zcash/halo2) - original (IPA)
- [privacy-scaling-explorations/halo2wrong](https://github.com/privacy-scaling-explorations/halo2wrong) - replaces IPA to KZG
- [https://github.com/Orbis-Tertius/halo2](https://github.com/Orbis-Tertius/halo2) - replaces IPA to FRI (WIP)

#### Examples:
- [https://github.com/nikkolasg/halo2-circuits](https://github.com/nikkolasg/halo2-circuits)
- [https://github.com/icemelon/halo2-tutorial](https://github.com/icemelon/halo2-tutorial)
- [https://github.com/weijiekoh/halo2_circuits](https://github.com/weijiekoh/halo2_circuits)
- [https://github.com/akinovak/halo2-semaphore](https://github.com/akinovak/halo2-semaphore)
- [https://github.com/timoth-y/halo2-encryption](https://github.com/timoth-y/halo2-encryption)

#### Resources:

- General overview: [https://electriccoin.co/blog/explaining-halo-2/](https://electriccoin.co/blog/explaining-halo-2/)
- Talk: [https://youtu.be/KdkVTEHUxgo?t=399](https://youtu.be/KdkVTEHUxgo?t=399)
- Math: [https://vitalik.ca/general/2021/11/05/halo.html](https://vitalik.ca/general/2021/11/05/halo.html)
- Awesome: [https://github.com/adria0/awesome-halo2](https://github.com/adria0/awesome-halo2)
- Ecosystem showcase: [https://youtu.be/JJi2TT2Ahp0](https://youtu.be/JJi2TT2Ahp0)

### Plonky2

- Combines FRI with PLONKish arithmetization and needs *no trusted setup*
- Extensively optimized for modern processors (both x86-64 and ARM64) using:
    - [Ed448-Goldilocks](https://eprint.iacr.org/2015/625.pdf), whose modulus allows working on 64-bit fields
    - [SIMD](http://ftp.cvut.cz/kernel/people/geoff/cell/ps3-linux-docs/CellProgrammingTutorial/BasicsOfSIMDProgramming.html) operations for efficient sponge hashing
- Leverages custom gates to significantly optimize non-native arithmetic (e.g. field division)
- Uses Poseidon sponge as the underlying hash function. Supports GMiMC, which will result in more efficiency, but might be less secure
- Assumptions: collision-resistant hash function

#### Performance:

- Prover time: $$O(log^2(N))$$ - 300ms/20s (depending on the codewords rate)
- Verifier time: $$O(log^2(N))$$
- Proof size: $$O(N*log^2(N))$$ - 500kb/43kb (depending on the codewords rate)

#### Application scope:

- Recursive proof composition
- Circuit optimization using TurboPLONK's custom gates

#### Used in:

- [Polygon Zero](https://blog.polygon.technology/introducing-plonky2)
- [Maru Network](https://proxima-one.github.io/maru/introduction.html)

#### Libraries
- [https://github.com/mir-protocol/plonky2](https://github.com/mir-protocol/plonky2)

#### Examples:

- [https://github.com/qope/plonky2-examples](https://github.com/qope/plonky2-examples)
- [https://github.com/recmo/proto-ecdsa-plonky2](https://github.com/recmo/proto-ecdsa-plonky2)
- [https://github.com/mir-protocol/plonky2-semaphore](https://github.com/mir-protocol/plonky2-semaphore)
- [https://github.com/timoth-y/plonky2-encryption](https://github.com/timoth-y/plonky2-encryption)

#### Resources

- [https://github.com/mir-protocol/plonky2/blob/main/plonky2/plonky2.pdf](https://github.com/mir-protocol/plonky2/blob/main/plonky2/plonky2.pdf)
- [https://proxima-one.github.io/maru/background-knowledge/plonky2.html](https://proxima-one.github.io/maru/background-knowledge/plonky2.html)


### MPC-in-the-head

#### Background - MPC:
- MPC enables parties to carry out distributed computation on their private inputs.
- each party produces a computation transcript (its own view).
- **Important observation #1:** if the final result of MPC is wrong, then there's an inconsistent views somewhere.

#### Background - Secret Sharing:
- Secret Sharing allows splitting some secret among multiple parties, such that all of them need to cooperate for using it.
- **Important observation #2:** if only a subset of shares is revealed, then the secret remains unknown.

#### Overview:
- The prover simulates an MPC protocol "in their head", which computes $$f(x)$$ on a private input $$x$$ shared among $$n$$ virtual parties.
- The verifier can then ask to reveal a subset of views, which isn't enough to recover private inputs, but gives some confidence that the probability of not seeing the inconsistency is small.
- It's not small enough, so we need to repeat this interaction multiple times (~300).
- This can then be made non-interactive by doing this in parallel and applying Fiat-Shamir transform.
- The underlying MPC protocol used for proof generation isn't important, only views are;
- This allows treating simulated MPC as a black box and skip computing, thus avoiding a lot of overhead.
- Can be efficiently applied for boolean circuits, unlike most other NIZKs that are only feasible with arithmetic circuits.
- Can be extended with RAM - shared memory with private addresses ([paper](https://eprint.iacr.org/2022/313.pdf))
- Above innovations allow to easily compile arbitrary program into the verifiably computation circuit.

#### Performance:
- Prover time: $$O(n)$$ - much less than with SNARKs
- Verifier time: $$O(n)$$
- Proof size: $$O(n)$$
- The overhead of doing computation verifiably is much lower ($$1/{n_{reps}*n_{parties}}$$ => ~1/600) than that of SNARKs (~1/millions).
- Additions are free, but multiplications needed to be simulated many times.
- With pre-processing it's possible to reduce size and verifier complexity at the prover's expense.

#### Application scope:
- Complex programs that are poorly translatable to arithmetic circuits, e.g. SHA hashes.
- ML and other types of approximate calculations, that do floating point arithmetic (can be done bit-by-bit in boolean circuits).
- Delegated proving:
    - You want to create a SNARK of some statement, but don't want to compute it yourself nor to reveal the witness to a third party.
    - One thing you could do is create a MPCith proof and then the delegated party would create a new proof which verifies this one.
- Optimized confidential transactions using delegated proving
    - The idea being that you would minimize latency for the transaction creator, where they create the proof as fast as possible, and then another entity could compress the proof with other techniques.

#### Libraries:
- [https://github.com/trailofbits/reverie/tree/stacked-ikos](https://github.com/trailofbits/reverie/tree/stacked-ikos) (Rust)
- [https://github.com/cronokirby/boo-hoo](https://github.com/cronokirby/boo-hoo) (Rust)
- [https://github.com/cronokirby/Rem-Boo](https://github.com/cronokirby/Rem-Boo) (Rust)

#### Resources:
- Podcast episodes:
    - [https://cronokirby.substack.com/p/mpc-in-the-head-special](https://cronokirby.substack.com/p/mpc-in-the-head-special)
    - [https://cronokirby.substack.com/p/mpc-in-the-head-2-thoughts-about](https://cronokirby.substack.com/p/mpc-in-the-head-2-thoughts-about)
- Great intro paper (ZKBoo): [https://eprint.iacr.org/2016/163.pdf](https://eprint.iacr.org/2016/163.pdf)
- Security analysis: [https://eprint.iacr.org/2021/437.pdf](https://eprint.iacr.org/2021/437.pdf)
