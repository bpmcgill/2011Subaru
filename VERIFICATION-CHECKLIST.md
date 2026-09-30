# Verified wiring checklist — 2011 Outback Premium/Harman-Kardon navigation amp

Scope: 2011 Subaru Outback Limited 3.6R, factory navigation, Harman/Kardon (HK) premium audio. This is the proof ledger for `hk-amp-speaker-wiring.html`; completed source-derived items are checked, while unresolved factory power/enable details and vehicle-side validation remain open.

## Work items and proof

- [x] Verify manual/system family and the relevant equipment path.
  - Proof: `sources/8-audio-system.pdf`, printed WI-60–WI-64, heading “2. PREMIUM AUDIO”; WI-62 identifies A:R386 as AUDIO AMPLIFIER. This diagram set is distinct from “1. NORMAL AUDIO” (WI-57 onward); Outback/Sedan markers appear in the diagrams.
  - Proof of HK applicability: `sources/ET-18-power-amplifier.pdf`, printed ET-18 says “harman/kardon® audio system only.” Navigation-specific system route checked in `sources/28-navigation-system.pdf`, printed WI-167–WI-169. FSM drawing does not explicitly identify “Limited” trim; physical option/connector verification remains required.

- [x] Verify navigation-unit audio path to factory amp (not high-current power).
  - Proof: `sources/28-navigation-system.pdf`, printed WI-169 / NAVI-03, visually checked. Navigation-unit i144/i131 paths pass via i153/R331 and i196/R385 into R386 A2–A5 and A17/A18/A22/A23. Wire colors and route appear on the drawing.

- [x] Verify premium amplifier speaker output connector IDs and pin/wire/destination routes.
  - Proof: `sources/8-audio-system.pdf`, printed WI-63 (AUDIO(PA)-04) and WI-64 (AUDIO(PA)-05), visually checked. B:R316 is 10-way; C:R317 is 12-way.
  - Corrections after enlarged visual audits: LH tweeter uses R317 C3 (V) / C9 (GY) through R331 pins 14/13 → i158 pins 1/2. RH tweeter uses R317 C1 (Lg) / C2 (Y) through R331 pins 12/11 → i159 pins 1/2. R316 B1/B5 (GW) are tied and continue to AUDIO(PA)-01 A; not tweeter outputs. Front-left door is R316 B4 (G) / B10 (Br); front-right door is R316 B3 (BR) / B9 (WR). See HTML for the traced connector paths and downstream wire color changes.
  - A second visual review found the initial table contained errors; pin-to-wire-to-endpoint paths have since been corrected and are described in the HTML. Verify connector-face numbering at the vehicle before wiring.
  - The HTML includes the OEM diagram pages as embedded snapshots. Confirm harness-side connector keying/orientation before probing. Amp pins are not labelled +/−; polarity must not be guessed from color.

- [x] Verify R386 adapter branch, grounds, and connector identifiers.
  - Proof: WI-62 shows R386 A10–A12 (Or/Y/Br): A10 Or routes through R384 pin 1 to R383 pin 1 BY and GND-06; A11 Y routes via R384 pin 4 / R383 pin 4 GB toward NAVI-01; A12 Br through matching adapter positions. WI-62 also shows a separate BY ground to GND-06.
  - `sources/4-ground-circuit.pdf`, printed WI-30, shows C:R317 C6/C7 black joining GND-07, marked “OA: EXCEPT FOR NORMAL AUDIO MODEL.” `sources/60-rear-harness.pdf`, printed WI-256–WI-260, lists relevant connector pole counts and R383/R384 as the amp adapter cord.

- [x] Verify factory amp removal safety procedure.
  - Proof: `sources/ET-18-power-amplifier.pdf`, ET-18, HK-only procedure: disconnect battery ground; move passenger seat fully forward before disconnecting battery ground due to power seat; disconnect amplifier harness. Installation torque listed: 4.5 N·m (0.46 kgf-m, 3.32 ft-lb).

- [ ] Establish factory R386 high-current battery B+ input suitable for an aftermarket amplifier.
  - Status/proof: not established. AUDIO(PA)-01 WI-60 and NAVI-01 WI-167 show head-unit/navigation supply circuits only (FB-22 fuse 24 ACC; MB-16 fuse 10 B; MB-3 fuse 6 B; navigation also FB-26 fuse 4 IG). They do not establish an R386 high-current amplifier battery feed. Fuse summary WI-22 lists audio/amplifier loads generally, not the amp connector pinout. Do not use an unknown R386 pin or head-unit feed to power the aftermarket amplifier. Provide a separate fused battery cable sized per amplifier manufacturer unless an existing power cable is verified at the vehicle.

- [ ] Confirm dedicated OEM amplifier remote/enable function.
  - Status/proof: no reviewed page labels an R386 terminal “AMP REMOTE,” “AMP ON,” or “amplifier enable.” NAVI-01/NAVI-03 do trace a Yellow conductor from navigation-unit A11 through J/C i166 and i153/R331 pin 9, R383 pin 4 (GB) and R384 pin 4 to R386 A11 (Y). Its electrical function/rating is not stated; do not use it as REM based on color/route alone.
  - Owner context: Ben reports an existing amp turn-on wire already run to the trunk and is comfortable tapping it. This is owner-identified aftermarket wiring, not factory proof. Verify its voltage behavior with a meter during off/ACC/on and ensure it can drive the new amp REM input (or a relay if manufacturer specifies).

- [ ] Confirm vehicle harness against diagram before cutting or repinning.
  - Vehicle proof required: verify premium/nav equipment, connector designations, connector orientation, wire color and continuity at the car. Color alone is insufficient. Keep each speaker output pair isolated and do not common speaker negatives or tie them to chassis unless the new amp manufacturer expressly allows it.

## Build and validation checks

- [x] Downloaded original factory PDF excerpts from user’s SMB share into `sources/`; checked PDF metadata/printed sheet IDs.
- [x] Cross-read original text layer and visually inspected WI-62, WI-63, WI-64 and NAVI-01/NAVI-03; corrected a mistaken first-pass tweeter/R316 B9 interpretation.
- [x] HTML contains five embedded factory diagram snapshots and inline CSS; no remote images, fonts, scripts or stylesheet dependencies detected.
- [ ] Browser render/usability check still needed.
- [ ] Independent public web cross-check unavailable in this run: web search backend repeatedly returned Firecrawl `NoneType.status_code`. No internet-derived pinout is used to fill factory-manual gaps.

## Naming caution

The power-supply load list WI-22 uses the generic label “Audio amplifier (McIntosh),” while the Entertainment manual ET-18 explicitly marks its power-amplifier procedure as Harman/Kardon-only. Do not transfer unrelated McIntosh pinouts based on that generic load-list entry. The premium-audio and navigation diagrams used here are the direct wiring basis.
