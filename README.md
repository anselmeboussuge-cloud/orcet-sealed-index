# Orcet sealed cohort: deposit index and timestamp proofs

This repository publishes the **index of every prediction deposit** made for the sealed prospective evaluation of Orcet, a model of individual roll-call votes in the French National Assembly, together with the **OpenTimestamps proofs** that anchor each deposited file in the Bitcoin blockchain.

Archived on Zenodo: [doi:10.5281/zenodo.23974906](https://doi.org/10.5281/zenodo.23974906).

It accompanies the working paper *Sealed, Timestamped Prospective Evaluation of Parliamentary Vote Prediction* (Anselme Boussuge, Hémicycle, ORCID [0009-0009-8260-2681](https://orcid.org/0009-0009-8260-2681)).

## Why publish the index now

A timestamp proves that a file existed at a given time. It does not prove that the authors did not make other deposits and report only the favourable ones. Publishing the complete list of deposits while the cohort is still running closes that gap: every file that will be scored is listed here, with its hash, before the scores are known.

The prediction files themselves are not published yet. They will be released, with the protocol's scorer and the labels, after the cohort closes (17 November 2026, 23:59:59 Paris time).

## Contents

- `index-depots/`: one JSON index per deposit (schema `orcet-index-v1`). For each prediction file: its path, size, SHA-256 of the deposited file, SHA-256 of the uncompressed JSON, Git blob, production time, model commit, and the identifiers of the deputies (Assembly `PA` identifiers) and amendments covered.
- `predictions/*.ots`: the OpenTimestamps proof of each indexed file (63 files at the time of publication).
- `PROTOCOLE_COHORTE.md`: the evaluation protocol of the cohort, in French, as committed before the votes.

## How to verify

Install the OpenTimestamps client (`pip install opentimestamps-client`). For any indexed file, take its `sha256` from the index and run:

```
ots verify -d <sha256> predictions/<file>.ots
```

The client checks the proof against the Bitcoin blockchain and prints the block time. Under the protocol, a prediction enters the main score only if its proof predates the official opening of the roll call it predicts; when the official opening time is unknown, the proof must predate the start of the sitting day, Paris time. Deposits that do not meet this bound are reported in a separate category. Once the prediction files are released, `sha256sum <file>` must return the indexed hash.

## Licence

Index and proofs: CC BY 4.0.
