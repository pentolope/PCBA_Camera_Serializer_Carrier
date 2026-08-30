# Sources — Dual-Camera High-Speed Carrier

The evidence this board's design will have to cite. **Classes of document, not
documents:** the specific parts are not chosen yet, so naming a datasheet here
would be choosing one.

A number that reaches the board carries its provenance: source, document id or
URL, retrieval date, units, and the condition it applies under. A number without
that is not evidence, and no live network lookup may change a validation or
release result.

| Kind of source | What the design needs from it |
|---|---|
| Camera-interface silicon datasheet for the link architecture chosen (serializer/deserializer, CSI bridge, aggregator, or the equivalent for another modern camera interface) | Lane counts, supported data rates, termination, supply rails and power sequencing all come from the chosen device, which the brief does not name. |
| Public layout guidance for the chosen high-speed parts — device-vendor layout or application note, standards-body layout guidance, fabricator design rules, or a published reference design | The brief conditions part selection on public layout guidance existing (REQ-05), so this class has to be located for each candidate part; the brief does not restrict which kind of published source qualifies, so the admissible source is itself a documented choice (OPEN-21). |
| Specification for the camera link actually chosen (e.g. MIPI CSI-2 / D-PHY, a SerDes link specification, or the specification of whichever modern camera interface is adopted) | Sets the differential signalling rules, impedance targets, skew and length-matching budgets that the escape routing must satisfy. |
| Camera module datasheet and mechanical drawing | Fixes the module pinout, rail voltages and currents, clock and control requirements, and the mating geometry that drives placement. |
| Connector datasheets and mating/mechanical drawings (camera-side and host-side) | Pitch, pad geometry, ground-pin distribution and mating orientation determine whether the restrictive placement of REQ-10 is escapable at all. |
| PCB fabricator capability and stackup documentation | The likely 6-layer stackup, dielectric constants, copper weights, minimum trace/space and via classes must be checked against a real process before impedance and escape geometry can be claimed. |
| Controlled-impedance calculation or field-solver output for the chosen stackup | Impedance targets asserted without a solved geometry are exactly the kind of unsubstantiated claim this board is designed to expose. |
| ESD protection device datasheets | Clamping level, dynamic resistance and — critically — line capacitance versus the link's data rate determine whether protection is compatible with the high-speed lanes. |
| Regulator datasheets with noise, PSRR and load-transient data, for whichever regulator topology is chosen | Camera analog and PLL rails are noise-sensitive; rail quality claims need the chosen device's own noise and PSRR curves behind them. |
| Clock source datasheet with phase-noise / jitter specification | If clocks are generated on-board, the jitter budget for the camera and link must be traceable to a measured device spec. |
| Decoupling and power-integrity reference material for the chosen silicon | Target-impedance and decoupling schemes for the camera rails need a published basis, since the brief specifies only that filtering matters. |
| Assembly and DFM guidance for fine-pitch compact connectors | Compactness plus fine-pitch connectors puts the design near process limits; solderability and rework access need a documented process basis. |

## Recording a source, once one is chosen

Replace the class with the actual document — manufacturer, part number, revision
and date — and state the fact taken from it, in the units the document uses.
Keep the class row: it says why the document was needed.

JLCPCB-wide process limits are **not** recorded here. They live in the toolkit's
`profiles/jlcpcb/`, with their own provenance; this board records only its own
tighter targets and its own selected options. A limit copied into two places is
a rival threshold, and the toolkit has a gate that says so.
