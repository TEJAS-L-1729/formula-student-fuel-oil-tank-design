# Design Decisions & DFM Rationale

This document captures the engineering reasoning behind the fuel and oil tank designs — the *why* behind each choice, not just the final geometry.

## Baffle Design Logic

The fuel tank's baffle system uses two different hole sizes by design, not by accident:

- **Bottom reservoir plate: 6mm holes** — deliberately restrictive, so fuel is retained in the ~450ml anti-starvation reservoir even while the rest of the tank is sloshing under lateral g.
- **Upper baffle plates: 7mm holes** — larger and freer-flowing, since these plates exist primarily to break up bulk fluid motion and add structural stiffness, not to trap fuel.

Baffles were made from **1mm aluminum sheet** — thin enough to minimize added weight and wasted internal volume, while still being rigid enough to survive repeated slosh loading across a full endurance run.

The **fuel return line was routed to discharge directly into the bottom reservoir** rather than the tank's bulk volume — reinforcing the anti-starvation strategy by actively topping up the region the pump draws from.

## Packaging Constraints

The oil tank's width was set to **120mm specifically for improved chassis packaging** — a tighter footprint made it easier to fit alongside the tank's other powertrain and chassis components without conflicting with surrounding hardware.

*(If there are specific Formula Bharat rulebook clauses — e.g. minimum tank clearance from the driver, containment requirements, or mounting rules — that directly shaped this width or the tank's placement, add them here with the rule reference. This is public competition information, so it's safe to cite directly.)*

## Sealing & Connection Design

- The oil tank includes a **flat welding face** specifically for the return and feed line adapters, simplifying a manufacturing step that would otherwise require welding onto a curved surface.
- A **positive-stop opening near the filler cap** was added for catch-can connection, ensuring a repeatable, correctly-seated connection during assembly.

### Sealing Flange & O-Ring Groove

The sealing flange (machined from Aluminium 6061) interfaces directly with the **GSX-R600 fuel pump**, so its bolt pattern, bore diameter, and mounting face dimensions were all derived from the pump's actual mounting geometry rather than a generic fitting.

The O-ring groove itself was sized using the **Parker O-Ring Handbook** — the industry-standard reference for groove width, depth, and squeeze ratio as a function of O-ring cross-section. Following a published reference here (rather than estimating) matters because an undersized groove causes the O-ring to over-compress and take a permanent set, while an oversized groove lets it extrude under pressure — either failure mode risks a fuel leak at the flange. The flange was held to a **0.1mm tolerance** to keep the groove dimensions within the seating range the O-ring needs to seal reliably.

## Material Selection

Both tanks were fabricated from **Aluminium 6061**, confirmed by the manufactured parts (see [README](README.md#manufacturing)) and used for the sealing flange as well. The choice was weighed against the other materials commonly considered for FSAE fuel/oil system components:

| Material | Weight | Weldability | Fuel/Oil Compatibility | Corrosion Resistance | Manufacturability | Verdict |
|---|---|---|---|---|---|---|
| **Aluminium 6061** | Low | Good (TIG-weldable) | Excellent | Good (self-oxidizing layer) | Easy to sheet-form and machine | **Selected** |
| Mild Steel | High | Excellent | Good | Poor — rusts without coating | Easy to weld/form | Rejected — weight and corrosion risk in a fuel/oil environment |
| Stainless Steel (304/316) | High | Good | Excellent | Excellent | Harder to form thin sheet, more expensive | Rejected — unnecessary weight penalty for the corrosion benefit gained |
| PET / Engineering Plastic | Very low | Not weldable (needs bonding/fasteners) | Fuel-dependent — can swell with some fuel blends | Excellent | Easy to mold, hard to seal reliably at joints | Rejected — sealing reliability at tank seams was a bigger risk than the weight saved |
| CFRP / Composite | Low | Not weldable | Good, but resin-dependent | Excellent | Expensive, slow lead time, needs specialized layup | Rejected — cost and lead time not justified for this component |

**Why Aluminium 6061 won:** it hit the best balance of low weight, reliable weldability (critical since both tanks are welded sheet assemblies with baffles), and long-term compatibility with both fuel and oil — without the cost or lead-time penalty of composites, or the corrosion risk of uncoated steel.

### Fuel Sight Tube — PTFE

A **PTFE sight tube** was used on the fuel tank to allow a visual fuel level check. PTFE was chosen specifically because it holds up to prolonged fuel contact without swelling, cracking, or degrading — a common failure mode for cheaper clear plastics exposed to fuel over a full season of use.

## Validation Philosophy

Rather than sizing the fuel tank off a single estimate, consumption was calculated two independent ways — once from real MoTec telemetry, once from simulated lap data — specifically so the final tank volume wasn't resting on one method's assumptions. The **1.55% agreement** between methods was the threshold that gave confidence to proceed with the smaller, better-packaged tank design rather than over-sizing for safety margin alone.
