# Mutual Attestation via Kleene's Second Recursion Theorem

This is the hub repository for the research artifacts accompanying *Bootstrapping Mutual Attestation with Kleene's Second Recursion Theorem*.

## Problem and Goal

In the IETF RATS architecture, an **Attester** produces signed evidence containing measurements of its software and configuration. A **Verifier** authenticates that evidence using endorsements and appraises the measurements against expected measurements or **reference values**, supplied by a Reference Value Provider. The attestation result allows a **Relying Party** to decide whether it can trust the Attester.

In a decentralised architecture that pools attestable computing resources from many independent peers, there may be no central party trusted by every participant. The peers must therefore attest one another, and each node must know the reference values of the nodes it verifies.

Naively hard-coding those values leads to an infinite regress. If nodes embed one another's measurements as reference values, embedding them changes the measured code and therefore changes the measurements. Replacing the embedded values with the new measurements changes the code again, and the process repeats. We call this the **reference-value bootstrapping problem** for mutual attestation.

This project solves that problem using **Kleene's second recursion theorem**. This theorem enables each node to reconstruct the exact source code of its peers and derive their reference values locally **without an external Reference Value Provider**. The reference value must be a deterministic function of the source: when an architecture measures a build artifact rather than the deployed source itself, the source-to-artifact build must therefore be reproducible bit-for-bit.

## Research Artifacts

| Repository | Description |
| ---------- | ----------- |
| [PyReflect](https://github.com/acompany-develop/PyReflect) | A transpiler for mutually-referential reflective programming in Python |
| [mutual-ra-poc](https://github.com/acompany-develop/mutual-ra-poc) | A PoC implementation of mutual attestation for TPM-backed nodes using Kleene's second recursion theorem |
| [NixReflect](https://github.com/acompany-develop/NixReflect) | A Nix transpiler bundled with an AWS Nitro Enclaves PoC in which two enclaves reproducibly rebuild each other's enclave image and derive the corresponding reference PCR0–2 values |

<!--
## How to cite

```bibtex
@inproceedings{...,
  author    = {...},
  title     = {...},
  booktitle = {...},
  year      = {...},
  month     = {...},
  doi       = {...},
}
```
-->

## License

See the individual repositories for their licenses.
