# Requirements — Dual-Camera High-Speed Carrier

Two lists. The difference between them is the whole point of this file.

A **fixed requirement** is something [BRIEF.md](../BRIEF.md) asks for. Each one
below quotes the brief text that substantiates it; if a statement cannot be
quoted, it is not a requirement here. An **open decision** is a choice the brief
deliberately left to whoever designs this board.

> Missing details are design freedom, not permission to fabricate unstated user
> requirements.

Promoting a decision into a requirement is the failure this file exists to
prevent. Record a choice under the decision it answers, with the reasoning that
made it — never by adding it to the list above.

Bound to `BRIEF.md` SHA-256 `8bc219517e0aad84b4b3d8ac46e26e527e13fd4abe6b9193fd96ba6f87ff31d0`.

## Fixed by the brief

### REQ-01 — The board is a compact carrier — compactness is a stated property of the design, not an optional goal.

Brief text:

> Design a compact carrier for two small digital camera modules

### REQ-02 — The carrier hosts two small digital camera modules.

Brief text:

> Design a compact carrier for two small digital camera modules and a host processor/FPGA connection.

### REQ-03 — The carrier provides a connection to a host processor or FPGA.

Brief text:

> two small digital camera modules and a host processor/FPGA connection

### REQ-04 — The camera interface must be a realistic modern one. The brief offers MIPI CSI-2 and a serializer/deserializer architecture as examples ("such as"), so either satisfies it, but the list is not closed and another realistic modern camera interface is equally admissible.

Brief text:

> Use a realistic modern camera interface such as MIPI CSI-2 or a serializer/deserializer architecture

### REQ-05 — Parts must be selected such that public layout guidance exists for them — a device with no public layout guidance is excluded by the brief's own selection criterion.

Brief text:

> serializer/deserializer architecture, selecting parts with public layout guidance

### REQ-06 — The board must include camera power rails.

Brief text:

> Include camera power rails, clocks/control, ESD where exposed, and a host connector.

### REQ-07 — The board must include clocks and control signalling for the cameras.

Brief text:

> Include camera power rails, clocks/control, ESD where exposed

### REQ-08 — ESD protection must be included where exposed. The brief states the obligation but not the exposure boundary, which is left open (OPEN-12).

Brief text:

> clocks/control, ESD where exposed, and a host connector.

### REQ-09 — The board must include a host connector.

Brief text:

> ESD where exposed, and a host connector. Make the mechanical connector placement restrictive enough

### REQ-10 — Mechanical connector placement must be restrictive enough that high-speed lane escape and return paths are genuinely constrained — the design must not relieve this difficulty by spreading connectors out.

Brief text:

> Make the mechanical connector placement restrictive enough that high-speed lane escape and return paths matter.

### REQ-11 — Where the brief is silent, the design agent must make and document reasonable engineering decisions rather than invent hidden user requirements.

Brief text:

> make and document reasonable engineering decisions rather than inventing hidden user requirements

### REQ-12 — Stated brief requirements are authoritative and must not be overridden by later design convenience.

Brief text:

> Treat stated requirements as authoritative; where the brief leaves choices open

### REQ-13 — The repository stays a consumer of the shared PCBA_AutoDesignAndTest toolkit; board-specific logic must not be pushed into the toolkit.

Brief text:

> The repository should remain a consumer of the shared `PCBA_AutoDesignAndTest` toolkit rather than accumulating board-specific logic in the toolkit.

## Open — the design agent decides

### OPEN-01 — Which realistic modern camera interface to adopt: direct MIPI CSI-2 from the cameras to the host, a serializer/deserializer architecture between them, or another realistic modern camera link — and, once chosen, whether it is applied uniformly to both cameras.

The brief names MIPI CSI-2 and SerDes only as examples ('such as') of a 'realistic modern camera interface'; it neither chooses between them nor restricts the choice to those two.

*Decision:* **not yet made.**

### OPEN-02 — Which camera-interface silicon (serializer, deserializer, CSI bridge, aggregator or repeater, if any) to use, and how many of them.

The brief constrains only that the chosen parts have public layout guidance; it names no device, vendor or family.

*Decision:* **not yet made.**

### OPEN-03 — Which camera modules to target, their pinout, and how the two cameras are aggregated or presented to the host (independent links, shared link, or combined).

The brief says 'two small digital camera modules' and nothing about the module family, its interface width, or how the two streams reach the host.

*Decision:* **not yet made.**

### OPEN-04 — Lane count, data rate and per-link bandwidth budget for the camera and host links.

The brief states no resolution, frame rate, pixel depth or bit rate; the entire bandwidth budget is unfixed.

*Decision:* **not yet made.**

### OPEN-05 — Camera-side and host-side connector selection: type, pitch, mating orientation, retention, and pin assignment.

The brief requires 'a host connector' and treats connectors as compact and restrictively placed, but names no connector type and gives no pinout.

*Decision:* **not yet made.**

### OPEN-06 — Board outline, overall dimensions, camera-to-camera spacing and baseline, mounting hole pattern, keepouts and any enclosure interface.

The brief says only that the carrier is 'compact'; it states no dimension, mounting scheme or mechanical envelope.

*Decision:* **not yet made.**

### OPEN-07 — The exact stackup: dielectric materials and thicknesses, copper weights, reference-plane assignment per signal layer, and the actual layer count.

Metadata gives 6 as a *likely* layer count, not a requirement, and neither the brief nor metadata specifies materials, thicknesses or plane assignment.

*Decision:* **not yet made.**

### OPEN-08 — Target differential and single-ended impedances, tolerance, and whether impedance is controlled by the fabricator.

The brief states no impedance target; it only makes return paths matter. The number has to come from the interface and stackup eventually chosen, not from the brief.

*Decision:* **not yet made.**

### OPEN-09 — Intra-pair skew, inter-pair skew and total length-matching budgets, and how they are apportioned across the link.

The brief is silent on timing budgets; these follow from the interface and silicon eventually chosen.

*Decision:* **not yet made.**

### OPEN-10 — Power architecture: input rail(s) and where power enters, number of rails, rail voltages, regulator topology (switching, linear, or pass-through), sequencing, and current budget.

The brief requires 'camera power rails' but names no voltage, no current, no source and no regulator type.

*Decision:* **not yet made.**

### OPEN-11 — Power-filtering strategy: decoupling scheme, ferrite/pi filtering on camera analog and PLL supplies, plane splits, and how filtering is verified.

'Power filtering' is a benchmark stressor, not a specified solution; the brief prescribes no filter topology or component values.

*Decision:* **not yet made.**

### OPEN-12 — Which nets count as 'exposed' for ESD purposes, and what protection strategy is applied to each (device type, placement, and the capacitance budget it must respect on high-speed lanes).

The brief requires 'ESD where exposed' without defining the exposure boundary, the stress level, or any protection component.

*Decision:* **not yet made.**

### OPEN-13 — Clock architecture: whether cameras are clocked from an on-board source, from the host, or recovered from the link; and the jitter budget for that source.

The brief requires 'clocks/control' but does not say where clocks originate or what jitter performance is needed.

*Decision:* **not yet made.**

### OPEN-14 — Camera control plane: which control bus is used, addressing/muxing for two cameras, and reset/power-down/strobe/sync signalling.

The brief groups control with clocks in one phrase and specifies no bus, no address scheme and no sideband signals.

*Decision:* **not yet made.**

### OPEN-15 — Where exactly the restrictive connector placement is applied — which edge or face each connector sits on, and which routing hardship that placement is chosen to create.

The brief mandates that placement be restrictive enough to make lane escape and return paths matter, but leaves the specific geometry that produces this to the design agent.

*Decision:* **not yet made.**

### OPEN-16 — Via strategy for lane escape: via type (through, blind/buried, microvia), stitching-via placement around escapes and layer transitions, the fabrication class this implies, and the cost/capability policy used to weigh it.

The brief is silent on fabrication class and on cost; this follows from the chosen connector pitch and stackup and from the agent's own justification policy.

*Decision:* **not yet made.**

### OPEN-17 — Multi-camera synchronisation: whether the two cameras must be frame-synchronised, and if so by what mechanism.

The brief states two cameras on one carrier but says nothing about synchronisation between them.

*Decision:* **not yet made.**

### OPEN-18 — Test, bring-up and manufacturing-test provisions: test points, probe access on high-speed lanes, programming/debug access, fiducials, and the bring-up sequence itself.

The brief does not mention test or bring-up access at all, and prescribes no order in which the board is brought up.

*Decision:* **not yet made.**

### OPEN-19 — Fabricator and assembly process targets, and the resulting minimum trace/space, annular ring and component-placement rules.

Neither the brief nor the metadata names a fabricator or process class.

*Decision:* **not yet made.**

### OPEN-20 — Thermal handling for the interface silicon and regulators, including copper area, via arrays and any airflow assumption.

The brief states no thermal, ambient or power-dissipation requirement; compactness raises the question but does not answer it.

*Decision:* **not yet made.**

### OPEN-21 — What kind of published source counts as 'public layout guidance' for the chosen parts (device-vendor layout or application note, standards-body document, fabricator design rules, published reference design), and how far the layout rules actually used are traced and cited back to it.

The brief conditions part selection on public layout guidance existing but qualifies the guidance in no way and never states that the rules used must be traceable to it; both the admissible source class and the citation discipline are the agent's call.

*Decision:* **not yet made.**

## Where a decision gets recorded

1. Set `chosen` and `rationale` on the matching entry in
   [requirements.json](requirements.json). **That file is the authoritative
   record**, and the only one the benchmark's scripts read: a decision written
   only in prose is invisible to `board_status.py` and to any result that
   counts how many decisions an attempt actually made.
2. Answer it under its `OPEN-nn` heading here as well, with the reasoning and
   the evidence that made the choice. This file is the readable copy; where the
   two disagree, the JSON is what happened.
3. Cite the datasheet or standard in [docs/sources.md](../docs/sources.md).

A choice recorded this way stays visibly a choice. That is what lets a later
reader tell this board's engineering apart from its brief.

## Where this board is most likely to be faked

Places where a design run would be tempted to assert something it cannot
substantiate:

- Impedance, skew and length-matching numbers asserted with no solved stackup behind them. Writing a differential impedance target and a tolerance costs nothing; producing the dielectric, trace geometry and solver result that justify it is the actual work.
- Quietly relaxing REQ-10. The brief mandates connector placement restrictive enough that lane escape and return paths matter; the easiest way to 'succeed' is to spread the connectors out and route comfortably, which defeats the board's entire purpose.
- Picking silicon without checking that public layout guidance exists. The brief conditions part selection on that guidance existing, but it is easy to select a plausible-sounding device and then paraphrase generic high-speed advice as if it were guidance published for that part.
- Escape routing shown at block level only. Lane escape from a fine-pitch connector either closes with real pad, via and trace geometry or it does not; a diagram with arrows is not a demonstration that the pairs fit.
- Return paths described in prose rather than drawn. Layer transitions, stitching vias and plane-split crossings are checkable objects in the layout; a claim of 'continuous reference' with no stitching strategy is unsupported.
- Reading the brief's open choices as closed ones. 'Such as MIPI CSI-2 or a serializer/deserializer architecture' is an example list, not a menu of two; 'public layout guidance' is not restricted to any one kind of publisher; and 'ESD where exposed' names no exposure boundary, stress level, standard or protection device. Narrowing any of these silently hands the design agent a decision it was meant to make, and stating one as if the brief required it fabricates a requirement.
- Power-rail voltages and currents stated as facts. The brief names no rail voltage and no current; any number must be derived from the chosen camera modules and silicon and cited as such, not assumed.
- Filtering treated as a checkbox. 'Power filtering' is a stressor to be answered with a target-impedance argument and physical placement, not with a scattering of decoupling capacitors and a claim of adequacy.
