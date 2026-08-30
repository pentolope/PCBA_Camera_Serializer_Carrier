# PCBA_Camera_Serializer_Carrier — Dual-Camera High-Speed Carrier

**Benchmark ID:** 29  
**Difficulty:** 5/5  
**Brief detail:** 2/5  
**Category:** camera-high-speed  
**Likely layer count:** 6  
**Primary stressors:** MIPI/serializer high-speed lanes, compact connectors, power filtering, lane escape

## Design brief

Design a compact carrier for two small digital camera modules and a host processor/FPGA connection. Use a realistic modern camera interface such as MIPI CSI-2 or a serializer/deserializer architecture, selecting parts with public layout guidance. Include camera power rails, clocks/control, ESD where exposed, and a host connector. Make the mechanical connector placement restrictive enough that high-speed lane escape and return paths matter.

## Benchmark intent

This brief is intentionally one member of a heterogeneous PCBA-autodesign benchmark. Treat stated requirements as authoritative; where the brief leaves choices open, make and document reasonable engineering decisions rather than inventing hidden user requirements. The repository should remain a consumer of the shared `PCBA_AutoDesignAndTest` toolkit rather than accumulating board-specific logic in the toolkit.
