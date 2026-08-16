---
title: Mechanical Design Analysis Traveller
created: 2026-08-16
type: template
status: blank
tags: [mechanical-engineering, stress-analysis, traveller, design-record]
---

# Mechanical Design Analysis Traveller

> **Copy this file per part.** Rename to `TRAVELLER_<part>__<YYYYMMDD-HHMM>.md`. Fill as you work.
> Guidance for every line lives in [`MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md`](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md) — `guide §N.N` references link into it.
>
> **Conventions used here**
> - `*(one)*` — mutually exclusive, tick exactly one.
> - `*(all that apply)*` — multi-select.
> - `*(all)*` — every box must end up ticked.
> - **`—` = deliberately not applicable.** Leave nothing blank; an empty box is ambiguous, a dash is a decision.
> - Tables use `☐` because Markdown tables cannot hold live checkboxes. Everywhere else uses real checkboxes.

---

## Identification

| | |
|---|---|
| **Part / assembly** | |
| **Part number / rev** | |
| **Project** | |
| **Analyst** | |
| **Date started** | |
| **Date completed** | |
| **Supersedes** | |

*Revision is carried by the filename timestamp — no separate rev field.*

---

## Decision trail — the whole path at a glance

*Fill this last. It is the summary a reviewer reads first.*

| # | Decision | Taken | Guide ref |
|---|---|---|---|
| 1 | Governing code | | [§1.2](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#12-does-a-code-govern) |
| 2 | Limit state(s) to prove | | [§1.3](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#13-what-must-actually-be-proven) |
| 3 | Static / dynamic | | [§2.3](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#23-static-or-dynamic) |
| 4 | Triage: regimes routed out | | [§2.4](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#24-triage-gate-does-a-specialized-regime-govern) |
| 5 | Ductile / brittle | | [§3.1](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#31-ductile-or-brittle-behavior) |
| 6 | Linear / nonlinear | | [§3.2](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#32-linear-elastic-or-nonlinear) |
| 7 | Model idealization | | [§4.1](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#41-dimensional-reduction) |
| 8 | Determinate / indeterminate | | [§4.5](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#45-determinate-or-indeterminate) |
| 9 | Solution method | | [§5.2](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#52-equilibrium-or-energy) |
| 10 | Hand / FEA | | [§5.5](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#55-closed-form-or-fea) |
| 11 | Failure criterion | | [§7.1](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#71-selection-gate) |
| 12 | **Governing mode** | | [§8.4](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#84-margin-of-safety) |
| 13 | **Minimum MS** | | [§8.4](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md#84-margin-of-safety) |
| 14 | Verdict | ☐ pass ☐ fail ☐ conditional | |

---

# 1 · Framing

**Function:** ________________________________________________

**Design life:** ________ yr / ________ cycles → *cycles feed the fatigue screen at [§3](#3---triage-gate--all-nine-answered) #1*

**Consequence of failure** *(one)*

- [ ] Cosmetic
- [ ] Production loss
- [ ] Injury
- [ ] Fatality

**Inspectable in service?** *(one)*

- [ ] Yes
- [ ] No → flaw-tolerant design required

**Load path** *(one)*

- [ ] Redundant
- [ ] Single → raises required margin

- [ ] Consequence assessed for *this part* failing, not the whole machine

**Governing code:** ____________________  **edition:** ________

*(one)*

- [ ] No code governs — theory and factor of safety are my choice, documented below
- [ ] A code governs → failure theory and factor of safety are **decided by it**; comparison at [§5](#criterion-and-margin) skipped

**Limit states to prove** *(all that apply)*

- [ ] Strength
- [ ] Stiffness — limit ________
- [ ] Stability
- [ ] Life
- [ ] Seal / leak-tightness

- [ ] Governing limit state named: ____________________ — **not** assumed to be strength

**Units** *(one)*

- [ ] SI
- [ ] US customary — lbf/lbm and g_c handled

**Sign convention:** ____________________  **Origin / coordinate system:** ____________________

### Shigley 26 — considerations that materially apply

*(all that apply)*

- [ ] 1 Functionality
- [ ] 2 Strength / stress
- [ ] 3 Distortion / deflection / stiffness
- [ ] 4 Wear
- [ ] 5 Corrosion
- [ ] 6 Safety
- [ ] 7 Reliability
- [ ] 8 Manufacturability
- [ ] 9 Utility
- [ ] 10 Cost
- [ ] 11 Friction
- [ ] 12 Weight
- [ ] 13 Life
- [ ] 14 Noise
- [ ] 15 Styling
- [ ] 16 Shape
- [ ] 17 Size
- [ ] 18 Control
- [ ] 19 Thermal properties
- [ ] 20 Surface
- [ ] 21 Lubrication
- [ ] 22 Marketability
- [ ] 23 Maintenance
- [ ] 24 Volume
- [ ] 25 Liability
- [ ] 26 Remanufacturing / resource recovery

- [ ] Ticked items that route **out** of structural analysis have an owner
- [ ] A passing stress analysis was **not** treated as satisfying this list

---

# 2 · Loads

### Load inventory — every row gets a mark

| Load type                         | In  | Value / case | Excluded because |
| --------------------------------- | --- | ------------ | ---------------- |
| Applied service                   | ☐   |              |                  |
| Reactions                         | ☐   |              |                  |
| Self-weight                       | ☐   |              |                  |
| Inertial / transport / shock      | ☐   |              |                  |
| **Thermal**                       | ☐   | ΔT =         |                  |
| **Preload** (bolt, press, shrink) | ☐   |              |                  |
| **Residual** (weld, machine, HT)  | ☐   |              |                  |
| Pressure                          | ☐   |              |                  |
| Environmental (wind/snow/seismic) | ☐   |              |                  |
| Installation / handling           | ☐   |              |                  |
| Fault / abuse                     | ☐   |              |                  |

- [ ] Thermal present **and** structure indeterminate → **this induces real stress** (see [§4](#4--material-and-idealization))
- [ ] Exclusions justified above, not left silent

### Load path

- [ ] FBD drawn — whole body and each internal cut
- [ ] ΣF = 0, ΣM = 0 verified **numerically** from output
- [ ] Critical section at station ____________ because ____________________
- [ ] Checked M/S, not M alone

### Static or dynamic

ω_forcing = ________ Hz · ω_natural = ________ Hz · **ratio = ________**

**Regime** *(one)*

- [ ] Ratio ≲ 1/3 → quasi-static, inertia neglected
- [ ] Ratio > 1/3 → **EXIT vibration** (§3 screen #9)

- [ ] Suddenly applied but non-impacting → factor of 2 applied as a bound

---

# 3 · ⚠ TRIAGE GATE — all nine answered

> **The highest-risk page in this traveller.** A missed screen is a missed failure mode.
> Tick the table only if the regime **applies**. Every tick needs a disposition on the [register](#route-out-register) at the back.

| #   | Regime                                           | Applies | Basis for the answer |
| --- | ------------------------------------------------ | ------- | -------------------- |
| 1   | **Fatigue** — >10³ cycles                        | ☐       |                      |
| 2   | **Fracture** — flaw + thick/low-toughness/cold   | ☐       |                      |
| 3   | **Creep** — T > 0.4·T_melt                       | ☐       |                      |
| 4   | **Contact / wear** — sliding, rolling            | ☐       |                      |
| 5   | **Joints** — bolted/welded in path               | ☐       |                      |
| 6   | **Impact** — high strain rate                    | ☐       |                      |
| 7   | **Corrosion / SCC**                              | ☐       |                      |
| 8   | **Plate/shell buckling** — thin-wall compression | ☐       |                      |
| 9   | **Vibration** — near resonance                   | ☐       |                      |

- [ ] All nine answered — **negatives justified as carefully as positives**
- [ ] #6 positive → **#2 re-checked** (impact + cold = classic brittle fracture)
- [ ] Interactions considered — #1 + #7 = corrosion fatigue, worse than either alone
- [ ] Every positive entered on the [route-out register](#route-out-register)
- [ ] Kt treatment at [§5](#stress-state) updated if #1 is positive

**Outcome** *(one)*

- [ ] All nine negative → proceed to [§4](#4--material-and-idealization)
- [ ] One or more positive → spine continues **and** specialist work is required

---

# 4 · Material and idealization

### Behavior class

**Elongation ________ %**

**Class from test data** *(one)*

- [ ] Ductile — elongation > 5%
- [ ] Brittle — elongation < 5%

**Embrittlement screen** *(all that apply — any tick overrides "Ductile" above)*

- [ ] Service temp ________ °C at or below DBTT
- [ ] Thick or constrained section — triaxial tension
- [ ] Sharp notch / keyway / weld toe at critical section
- [ ] High strain rate

**Class carried forward: ____________________** *(the screened result, not the datasheet value)*

### Linearity

**Nonlinearity screen** *(all that apply — any tick forces nonlinear analysis)*

- [ ] Material — σ ________ vs S_y ________
- [ ] Geometric — δ ________ vs ½t ________ ; rotation ________°
- [ ] Boundary / contact — gaps, contact, follower loads

- [ ] **All clear → linear-elastic assumed** *(re-verified at [§7](#7---assumption-ledger-audit))*

### Material properties

| | |
|---|---|
| Material / condition | |
| Source (standard or cert) | |
| Basis | ☐ typical ☐ min specified ☐ A-basis ☐ B-basis |
| S_y / S_ut / S_uc | |
| E / G / ν | |
| At service temp | ________ °C |

- [ ] Not typical properties paired with a minimum-property safety factor

**Material class** *(one)*

- [ ] Isotropic and homogeneous
- [ ] Anisotropic / composite / AM → **guide §7 does not apply**; build orientation: ________

### Idealization

**Model** *(one)*

- [ ] Bar / truss
- [ ] Beam
- [ ] Plate / shell
- [ ] 2D solid
- [ ] 3D solid

**L/h = ________ · r/t = ________ · a/t = ________**

**Beam theory** *(one — mark `—` if not a beam)*

- [ ] Euler-Bernoulli — L/h ≳ 10
- [ ] Timoshenko — L/h ≲ 10 → **shear energy term added at [§5](#method)**

**2D idealization** *(one)*

- [ ] Plane stress
- [ ] Plane strain → **σ₃ = ν(σ₁+σ₂) = ________ carried forward**
- [ ] Axisymmetric
- [ ] Full 3D

**Boundary conditions:** ____________________

- [ ] Bracketed — analysis run at **both** pinned and fixed bounds

**Bracket outcome** *(one)*

- [ ] Both bounds pass → result robust, uncertainty immaterial
- [ ] Bounds disagree → **joint stiffness is a design driver** — disposition: ____________________

**Determinacy** — r = ________ , 3n or 6n = ________ *(one)*

- [ ] Determinate — statics sufficient
- [ ] Indeterminate — degree ________ ; compatibility mandatory
- [ ] **Unstable — STOP. This is a mechanism, not a structure**

- [ ] Reaction *arrangement* checked, not just the count
- [ ] If indeterminate: thermal / settlement / misfit cases carried from §2
- [ ] Guide §4.6 exclusion zones marked; **fillet radii specified: R ________**

---

# 5 · Method and results

### Method

**Solution approach** *(one)*

- [ ] Vectorial statics
- [ ] Energy — which method: ____________________

**Castigliano validity gate** *(all that apply — any tick means Castigliano is **INVALID** → use unit load)*

- [ ] Thermal load present
- [ ] Support settlement or fabrication misfit present
- [ ] Material or geometric nonlinearity

**Formulation** *(one)*

- [ ] Force / flexibility
- [ ] Displacement / stiffness

- [ ] **Hand estimate: ________ MPa / ________ mm** ← *done before trusting any FE result*
- [ ] FEA used — solver: ____________________

**Uncertainty treatment** *(one)*

- [ ] Deterministic
- [ ] Probabilistic — target p_f ________

### Stress state

| Quantity | Value | Station |
|---|---|---|
| N / V / M / T | | |
| σ_bending | | |
| τ_shear / τ_torsion | | |
| **σ₁ ≥ σ₂ ≥ σ₃** | | |
| **τ_max = (σ₁−σ₃)/2** | | |
| **σ′ (von Mises)** | | |
| **δ_max** | | |

- [ ] **All three principal stresses written, including zeros**
- [ ] τ_max uses σ₁−σ₃ (the extremes), not the in-plane pair
- [ ] Non-circular torsion → J_t used, **not** the polar moment

**Superposition conditions** *(all — required before superposing anything)*

- [ ] Linear-elastic material
- [ ] Small deformation
- [ ] Consistent idealization, axes, and sign convention
- [ ] No P-Δ / buckling interaction

- [ ] **Components superposed, then one σ′ computed** — von Mises values not added

**Stress concentration** *(one)*

- [ ] Exempt — ductile + static, for yielding only
- [ ] Applied — K_t = ________
- [ ] Fatigue — K_t = ________ , q = ________ , **K_f = ________**

### Criterion and margin

**Theory used: ____________________**

**Reference strength** *(one)*

- [ ] Yield — S_y = ________
- [ ] Ultimate — S_ut = ________

| Limit state | Applied | Allowable | n | **MS** |
|---|---|---|---|---|
| Strength | | | | |
| **Deflection** | | limit L/____ = | | |
| Buckling | P = | P_cr = | | |
| | | | | |

- [ ] Deflection checked at **unfactored service loads**
- [ ] Buckling: K = ________ (design value), minimum I used, each axis its own L_e

**Factor of safety n = ________ · basis** *(one)*

- [ ] Code-mandated
- [ ] Consequence-based table
- [ ] Pugsley — A ____ B ____ C ____ → n_sx ____ ; D ____ E ____ → n_sy ____
- [ ] Reliability-based

**Factor applied** *(one)*

- [ ] On strength — ASD / allowable stress
- [ ] On load — LRFD
- [ ] Partial factors — Eurocode

- [ ] Conventions not mixed; factors not applied twice
- [ ] If nonlinear: factor applied to the **load**, analysis run at the factored load
- [ ] **MS ≥ 0 for every limit state** · **MS_min = ________ · governing mode: ____________________**

> If strength passes but deflection governs, that is a normal and expected outcome — and a higher-strength alloy will not fix it.

---

# 6 · ⚠ VERIFICATION

### Independent check

**Method used: ____________________** *(must differ from the primary method)*

Primary ________ vs check ________ → **difference ________ %**

**Agreement** *(one)*

- [ ] Within ~10–20% → accepted
- [ ] Factor of 2+ → **resolved before proceeding, not averaged** — resolution: ____________________

- [ ] Confirmed the check is not a re-run of the same method, nor a review of the same arithmetic

### Sanity checks

*(all)*

- [ ] Units dimensionally consistent throughout
- [ ] Order of magnitude sensible for the material
- [ ] Reactions sum to applied loads — numerically, from output
- [ ] Limiting cases degenerate to known answers
- [ ] Symmetric structure + symmetric load → symmetric result
- [ ] Deflected shape plausible and satisfies intended BCs
- [ ] Signs correct — tension where tension is expected
- [ ] Result sits at a sensible fraction of yield

### FEA — if used

*(all — mark `—` throughout if FEA was not used)*

- [ ] **Mesh convergence demonstrated**
- [ ] Element type / order appropriate
- [ ] Element quality checked in high-stress regions
- [ ] BCs verified — no artificial over-constraint
- [ ] Loads distributed realistically, not applied at points
- [ ] **Reactions = applied loads**
- [ ] Contact converged, not force-terminated
- [ ] No rigid body modes

- [ ] **No stress reported from a singularity.** If refinement kept raising stress at a sharp corner, a real fillet was modelled instead — R = ________

### Sensitivity — conclusion must survive every bound

*(all)*

- [ ] BCs at both bounds
- [ ] Material at minimum specified, at service temperature
- [ ] Loads nominal **and** maximum credible
- [ ] Geometry at tolerance extremes
- [ ] Minimum wall after corrosion allowance
- [ ] Friction / preload across realistic range

**Sensitivity outcome** *(one)*

- [ ] Conclusion unchanged across all ranges → analysis complete
- [ ] Conclusion changes → **design driver: ____________________** · disposition: ____________________

### Empirical — if performed

*(all that apply)*

- [ ] Proof / burst test
- [ ] Strain gauge — predicted ________ vs measured ________
- [ ] Modal test
- [ ] NDT: ____________________
- [ ] First-article dimensional inspection

- [ ] Any discrepancy **explained**, not noted and ignored

---

# 7 · ⚠ ASSUMPTION LEDGER AUDIT

> **The closing of the loop.** Every assumption checked against the computed answer.
> A violated assumption means the result is **invalid**, not merely failing.

| # | Assumed | Evidence | ✅⚠❌ |
|---|---|---|---|
| 1 | Quasi-static | ratio = | |
| 2 | All 9 triage screens still negative for **final** design | | |
| 3 | Ductile behavior — above DBTT, low constraint | | |
| 4 | **Linear-elastic — σ ______ < S_y ______** | | |
| 5 | **Small deflection — δ ______ < ½t ______ ; rot < 5°** | | |
| 6 | Properties at service temp, correct condition/basis | | |
| 7 | Slenderness ratios hold for **final** geometry | | |
| 8 | Shear deformation negligible (if E-B) | L/h = | |
| 9 | σ₃ carried where plane strain applies | | |
| 10 | BCs bracketed, conclusion robust | | |
| 11 | Determinacy still correct after design changes | | |
| 12 | Castigliano U = U\* held (no thermal/settlement/nonlinear) | | |
| 13 | Superposition — all conditions hold | | |
| 14 | Kt treatment matches final behavior + load type | | |

**Key:** ✅ holds · ⚠ marginal, see sensitivity · ❌ **violated — return to that node**

**Audit outcome** *(one)*

- [ ] **All rows ✅** → proceed to [§8](#8--manufacturing-and-close-out)
- [ ] Any ❌ → **result is invalid, not merely failing** — returned to node ________

- [ ] Re-analysis complete *(if any ❌ above)*
- [ ] Confirmed: **no stress above yield is being reported from a model that assumed no yielding**

---

# 8 · Manufacturing and close-out

- [ ] Surface finish specified — critical if the fatigue screen was positive
- [ ] Residual stress considered — weld / machining / forming / heat treat
- [ ] Tolerance stack extremes fed into sensitivity
- [ ] **Every fillet the analysis relies on is dimensioned and toleranced on the drawing**
- [ ] Delivered material condition and orientation verified
- [ ] Assembly effects captured — torque, alignment, shim, forced fit-up

### Route-out register

> **No route-out may be left open.** Detection without disposition is worse than never screening.

| # | Regime | Disposition | Reference / owner | Date |
|---|---|---|---|---|
| | | ☐ analyzed elsewhere ☐ not governing ☐ **open risk** | | |
| | | ☐ analyzed elsewhere ☐ not governing ☐ **open risk** | | |
| | | ☐ analyzed elsewhere ☐ not governing ☐ **open risk** | | |
| | | ☐ analyzed elsewhere ☐ not governing ☐ **open risk** | | |

- [ ] Every [§3](#3---triage-gate--all-nine-answered) positive screen appears above with a disposition

### Open items and limitations

| # | Item | Impact | Owner | Resolved |
|---|---|---|---|---|
| 1 | | | | ☐ |
| 2 | | | | ☐ |
| 3 | | | | ☐ |

### Package completeness

*(all)*

- [ ] Problem statement, scope, what is being proven
- [ ] Code and edition, or explicit statement of none
- [ ] Load cases **including exclusions and why**
- [ ] Triage results — all nine screens
- [ ] Material properties with source, basis, temperature, condition
- [ ] **Completed ledger audit**
- [ ] Model, idealization, and BCs justified
- [ ] Method rationale
- [ ] Results per location / load case / limit state
- [ ] Failure criterion and the reason for it
- [ ] Factor of safety and its basis
- [ ] **Independent check and its result**
- [ ] Mesh convergence evidence, if FEA
- [ ] Sensitivity study
- [ ] Route-out dispositions
- [ ] Conclusion, limitations, conditions of validity

- [ ] **Reproducibility test:** a competent engineer who has never seen this could reproduce the result and identify what would invalidate it

---

## Conclusion

**Verdict** *(one)*

- [ ] Pass
- [ ] Fail
- [ ] Pass with conditions

**Governing limit state:** ____________________ · **MS_min:** ________

**Conditions / limitations of validity:**

_______________________________________________________________

_______________________________________________________________

**This analysis is invalidated if:** *(the assumptions a future reader must re-check)*

_______________________________________________________________

---

## Sign-off

| Role | Name | Signature | Date |
|---|---|---|---|
| **Analyst** | | | |
| **Independent checker** | | | |
| **Approver** | | | |

> The independent checker signs to the [§6 independent check](#independent-check) — a **different method**, not a review of the same arithmetic.

---

*Blank template. Guidance: [`MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md`](MECHANICAL-DESIGN-CHECKLIST__20260816-0939.md)*
