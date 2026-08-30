# Benchmark entry — board 29 of 32

[metadata.json](metadata.json) is the supplied catalogue entry for this board,
preserved byte for byte from the seed pack. It is the same record that appears
in `boards_index.json` in
[PCBA_AutoDesignAndTest_Bench](https://github.com/pentolope/PCBA_AutoDesignAndTest_Bench), and the two must agree.

| | |
|---|---|
| Repository | `PCBA_Camera_Serializer_Carrier` |
| Board id | `camera_serializer_carrier` |
| Category | camera-high-speed |
| Difficulty | 5 / 5 |
| Brief detail | 2 / 5 |
| Likely layer count | 6 |
| Primary stressors | MIPI/serializer high-speed lanes, compact connectors, power filtering, lane escape |

`difficulty` is how hard the board is. `detail` is how much of it the brief
states — and a low `detail` is not a low bar. A detail-1 brief leaves the
architecture open on purpose, and an agent that fills the silence with invented
user requirements has failed the board more thoroughly than one that designs it
badly.

At difficulty 5/5 with only 2/5 brief detail, this board tests whether a design agent can build a credible high-speed camera subsystem from a sparse prompt without inventing user requirements. The metadata stressors — MIPI/serializer high-speed lanes, compact connectors, power filtering, lane escape — are all layout-physics stressors, and the brief deliberately makes connector placement restrictive so that lane escape and return-path integrity cannot be routed around. The "public layout guidance" clause is the benchmark's evidence hook: it conditions part selection on such guidance existing, testing whether the agent grounds its high-speed rules in citable published material instead of asserting them. It is equally a test of restraint in the other direction — the brief's "such as" list of interfaces and its unqualified "public layout guidance" are open, and closing them prematurely is as much a failure as fabricating a number.

## What goes here

Compact results only: metrics, verdicts, and the commit each was measured at.
The evidence for a result is the artefact the toolkit recomputes, not a summary
of it.

Routing search output, candidate pools, build trees and field-solver dumps do
**not** go here. They are ignored by [.gitignore](../.gitignore) and are
regenerated from what is committed. Thirty-two repositories share one benchmark
clone; weight here is paid thirty-two times.

## Protocol

The attempt protocol is defined once, in the umbrella repository, so that
thirty-two boards cannot drift into thirty-two protocols. See
[PCBA_AutoDesignAndTest_Bench/BENCHMARK.md](https://github.com/pentolope/PCBA_AutoDesignAndTest_Bench/blob/main/BENCHMARK.md).
