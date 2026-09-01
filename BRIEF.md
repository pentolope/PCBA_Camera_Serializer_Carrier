# PCBA_Camera_Serializer_Carrier — Dual-Camera High-Speed Carrier
## Design brief

Design a compact carrier for two small digital camera modules and a host processor/FPGA connection. Use a realistic modern camera interface such as MIPI CSI-2 or a serializer/deserializer architecture, selecting parts with public layout guidance. Include camera power rails, clocks/control, ESD where exposed, and a host connector. Make the mechanical connector placement restrictive enough that high-speed lane escape and return paths matter.

## Functional requirements

- The link and rails shall be sized for both cameras streaming concurrently at their configured resolution and frame rate.
- Each camera shall be independently resettable, configurable and addressable even if both modules ship with one fixed address.
- Each camera's reference clock shall meet its module's frequency, duty-cycle and jitter limits.

## Power and rails

- Every rail the chosen modules, link devices and clock source need shall be supplied at their stated voltage, tolerance and sequencing.
- Rails shall carry peak draw with both cameras streaming at worst-case input and temperature, with supply noise inside each module's limit.

## Connectors and placement

- All image data, control and any shared trigger shall pass through the single host connector, keyed against reversed mating.
- Connector positions and orientations shall be fixed by a mechanical drawing that is an input to layout, and shall force at least one lane group onto an indirect escape.
- The two optical axes shall hold a fixed, repeatable relationship to each other and to the board datum, to a stated tolerance.

## Signal integrity and return paths

- An unbroken reference plane shall sit adjacent to every high-speed layer; stackup and layer count follow from the impedance the chosen link's guidance requires.
- Every high-speed conductor shall have an adjacent return through the connector and its mate, and no pair shall cross a plane split or void.
- Every layer transition shall have adjacent stitching vias, minimised per lane, with no stubs or probe spurs left on these nets.
- Pair matching and end-to-end loss shall meet the chosen device's guidance; one camera streaming while the other is reset shall be an analysed crosstalk case.

## Protection and robustness

- Every conductor reaching an exposed connector shall have ESD protection there, control, clock, reset and power pins included.
- Lane protection capacitance and its pair mismatch shall keep the link inside the chosen standard's limits; mis-insertion shall not cause latch-up or damage.

## Test and bring-up access

- Each board-generated rail shall have a measurement point with a nearby ground reference, the control channel shall be reachable by an analyser without unmating the host connector, and the board shall operate with one camera fitted.

## Open choices

- Link architecture — direct camera interface or serializer/deserializer — and its silicon; the parts chosen must have published layout guidance sufficient for the requirements above.
- Camera modules and their mating interface, lane count and data rate; host connector family and its mate.
- Whether camera rails and the reference clock come from the carrier or the host, and whether the cameras are frame-synchronised.
