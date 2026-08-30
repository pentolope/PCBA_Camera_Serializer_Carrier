# Dual-Camera High-Speed Carrier

Compact carrier board for two small digital camera modules and a host processor/FPGA connection over a realistic modern camera interface.

This repository holds the design problem for a **compact dual-camera carrier**: two small digital camera modules on one board, linked to a host processor/FPGA connection. The brief fixes the functional skeleton — two cameras, a realistic modern camera interface, camera power rails, clocks/control, ESD where exposed, and a host connector — and it fixes one deliberate hardship: connector placement must be restrictive enough that high-speed lane escape and return paths genuinely constrain the layout. It also conditions part selection on public layout guidance existing for the parts chosen.

Two things the brief leaves deliberately open are easy to misread as closed. First, the interface: MIPI CSI-2 and a serializer/deserializer architecture are given as examples ("such as"), not as an exhaustive pair, so another realistic modern camera link remains admissible. Second, the guidance: the brief says "public layout guidance" and does not say what kind of published source qualifies, nor does it state that the layout rules actually used must be traceable back to it.

Beyond that the brief is low-detail (2/5). Which camera interface to adopt, all specific silicon, connectors and camera modules, board outline and mounting, rail voltages and regulator topology, stackup and impedance targets, what counts as 'exposed' for ESD, and the protection strategy are all left to the design agent.

> **This board has not been designed.** There is no schematic, no layout and no
> part selection here — only the brief, a reading of the brief, and the
> scaffolding a design run needs. That is the intended state of this repository,
> not a gap in it.

## What the brief fixes, and what it leaves open

The brief pins down 13 requirements and deliberately leaves
21 decisions to whoever designs the board. The `Source` column says
which is which: `brief` is quoted from [BRIEF.md](BRIEF.md), `metadata` comes
from the benchmark catalogue, and `open` means the brief does not fix it.

| Aspect | Value | Source |
|---|---|---|
| Board function | Compact carrier for two camera modules plus a host processor/FPGA connection | brief |
| Camera count and type | Two small digital camera modules | brief |
| Camera link architecture | A realistic modern camera interface; the brief names MIPI CSI-2 and a serializer/deserializer architecture as examples ("such as"), not as a closed list | brief |
| Part selection constraint | Parts chosen must have public layout guidance; the brief does not say what kind of published source qualifies | brief |
| Camera power | Camera power rails must be provided on the carrier | brief |
| Clocks and control | Clocks/control for the cameras must be included | brief |
| ESD protection | Required where exposed; the brief does not define what counts as exposed (see OPEN-12) | brief |
| Host interface | A host connector must be present | brief |
| Mechanical connector placement | Deliberately restrictive, so high-speed lane escape and return paths are load-bearing constraints | brief |
| Likely layer count | 6 | metadata |
| Category / difficulty / brief detail | camera-high-speed; difficulty 5/5; detail 2/5 | metadata |
| Primary stressors | MIPI/serializer high-speed lanes; compact connectors; power filtering; lane escape | metadata |
| Board outline, size, mounting and camera spacing | Open — no dimension, mounting scheme or spacing is fixed; the design agent chooses, bounded only by the stated compactness (REQ-01) | open |
| Rail voltages, regulator topology, filtering scheme, specific silicon and connector part numbers | Open — not fixed by the brief; the design agent chooses and documents each | open |

The full split, with the verbatim brief text substantiating every fixed
requirement, is in [board/requirements.md](board/requirements.md) and
machine-readably in [board/requirements.json](board/requirements.json).

**Missing details are design freedom, not permission to fabricate unstated user
requirements.** A choice the brief left open is recorded as a decision, with its
reasoning — never promoted into a requirement.

## Benchmark position

| | |
|---|---|
| Benchmark id | 29 of 32 |
| Category | camera-high-speed |
| Difficulty | 5 / 5 |
| Brief detail | 2 / 5 |
| Likely layer count | 6 |
| Primary stressors | MIPI/serializer high-speed lanes, compact connectors, power filtering, lane escape |

At difficulty 5/5 with only 2/5 brief detail, this board tests whether a design agent can build a credible high-speed camera subsystem from a sparse prompt without inventing user requirements. The metadata stressors — MIPI/serializer high-speed lanes, compact connectors, power filtering, lane escape — are all layout-physics stressors, and the brief deliberately makes connector placement restrictive so that lane escape and return-path integrity cannot be routed around. The "public layout guidance" clause is the benchmark's evidence hook: it conditions part selection on such guidance existing, testing whether the agent grounds its high-speed rules in citable published material instead of asserting them. It is equally a test of restraint in the other direction — the brief's "such as" list of interfaces and its unqualified "public layout guidance" are open, and closing them prematurely is as much a failure as fabricating a number.

This repository is one of thirty-two. The suite, the protocol and the results
live in [PCBA_AutoDesignAndTest_Bench](https://github.com/pentolope/PCBA_AutoDesignAndTest_Bench).

## Repository layout

| Path | Contents |
|---|---|
| `BRIEF.md` | the supplied brief — authoritative, preserved byte for byte, never edited |
| `board/requirements.md` | what the brief fixes, what it leaves open, and where decisions get recorded |
| `board/requirements.json` | the same split, machine-readable, each fixed requirement bound to brief text |
| `board/manifest.template.json` | the toolkit's minimum manifest, pre-filled for this board |
| `board/toolchain.json` | where this board's build finds KiCad and the router |
| `benchmark/metadata.json` | the supplied catalogue entry — category, difficulty, detail, stressors |
| `docs/architecture.md` | the decisions this board must make, as questions, unanswered |
| `docs/sources.md` | the classes of evidence the design will have to cite |
| `docs/status.md` | what exists, what does not, and what is deliberately absent |
| `candidates/` | disposable search output, ignored by Git |
| `.claude/skills/` | the claim-audit and accountability-review skills [CLAUDE.md](CLAUDE.md) requires before a push |
| `tooling/PCBA_AutoDesignAndTest` | the shared verification/routing/release toolkit, as a pinned submodule |

## Getting the repository

The toolkit is a submodule and carries KiCad Routing Tools as a submodule of its
own, so clone recursively:

```bash
git clone --recursive https://github.com/pentolope/PCBA_Camera_Serializer_Carrier.git
```

```bash
git submodule update --init --recursive
```

## Designing the board

Generic verification, routing and release logic is **not** written here. It is
consumed from `tooling/PCBA_AutoDesignAndTest`, which is board-agnostic by
construction and must stay that way; this repository owns the board and nothing
else. Start from
[the toolkit's onboarding guide](tooling/PCBA_AutoDesignAndTest/examples/onboarding.md),
and see [CLAUDE.md](CLAUDE.md) for the rules a design run works under.

```bash
python3 tooling/PCBA_AutoDesignAndTest/run.py preflight
```

## Brief integrity

`BRIEF.md` SHA-256 `8bc219517e0aad84b4b3d8ac46e26e527e13fd4abe6b9193fd96ba6f87ff31d0`

Every quotation in `board/requirements.json` is bound to those exact bytes. If
the brief ever changes, the bindings are stale by construction — which is the
point of recording the digest.
