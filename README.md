# Azuli — Sealed Records Registry

Byte-identical mirror of the sealed artifacts published by the RTTP & IQA dual-pillar project (canonical host: `iqa.org`), maintained as an append-only backup of record and for availability during infrastructure maintenance windows.

**Operator disclosure**: this registry is operated by the RTTP & IQA Organization (Lee / Aicent Stack) — the same organization that publishes the sealed artifacts. It is a mirror and backup of record, not an independent third party; verification never trusts this copy — it verifies digests.

## What this is

- **Canonical ledger**: `https://iqa.org/attestations/release-attestations.json` — the append-only release ledger (143 records as of this snapshot, ledger file sha256 `f639bd2d58db45ba7ae1a860e67805c80716f22be66e27dcd7e9c13ff07b1de4`). A byte-identical snapshot is mirrored at [`ledger/release-attestations.json`](ledger/release-attestations.json).
- **Verification**: every artifact tarball in this repository has its sha256 recorded in the ledger. `SHA256SUMS` covers all 166 mirrored files:

  ```
  sha256sum -c SHA256SUMS
  ```

- **Mirroring alters no seal**: artifacts are content-addressed; a byte-identical copy carries the same digest as the sealed value. The canonical host remains `iqa.org`; this mirror never replaces it and is refreshed append-only (new seals are added, existing files are never modified).

## Layout

| Path | Contents |
|---|---|
| `ledger/` | `release-attestations.json` (site release ledger) · `blog-seals.json` (blog article ledger) |
| `records/conformance/` | runner sealed artifacts (lra-runner, aae-runner, icam-runner) + sidecar digests |
| `records/iqa-seal/` · `records/rttp-seal/` | site-freeze tarballs of sealed pages (conformance family pages, report pages, brief, whitepaper, URI references, factsheet) |
| `records/sites/` | sealed site tarballs of the pillar sites (epoekie, aicent, rpki, zcmk, gtiot, aicent-net, bewho, cmtn, sascar, itsun, moloon, dioon, picsi, maxcap, azuli) |
| `records/downloads/` | published release packages (rttp, iqa-org, iqa-mcp across ecosystems) + sidecar digests |

## Provenance

Snapshot taken 2026-11-10 from a byte-verified full-server backup (16,531 members, archive sha256 `075c00b0e23a2d3f412d45e8d890f618fefb2e3b5d598b79335f1dd9a57eb04a`); every extracted artifact was cross-checked against the ledger before commit. This repository contains public artifacts only.

---
RTTP & IQA Organization · Sites: https://rttp.com · https://iqa.org · Blog: https://blog.aicent.com
