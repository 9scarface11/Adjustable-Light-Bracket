# Adjustable Light Bracket — 5-DOF Positioning Mechanism


---

## Overview

A 5-DOF adjustable bracket for positioning a bar light in a machine vision 
inspection system. The bracket allows a technician to manually position the 
light at any desired pose within the workspace and lock it in place — without 
complex mechanisms or lead screws.

The design prioritizes:
- Minimum part count
- Tool-free or single-tool adjustment
- Rigid arrest at any set position
- Fit within a constrained envelope

---

## Degrees of Freedom

| DOF | Type | Range | Joint Used |
|-----|------|--------|------------|
| X Translation | Prismatic | 200mm | Friction Prismatic Joint |
| Y Translation | Revolute (2-link arm) | 40mm workspace | Fastening Revolute Joint |
| Z Translation | Revolute (2-link arm) | 80mm workspace | Fastening Revolute Joint |
| Roll | Revolute | >300° | Friction Revolute Joint |
| Yaw | Revolute | >300° | Fastening Revolute Joint |

---

## Kinematic Chain

GROUND (Base Rod)
│
│ ← Friction Prismatic Joint (X, 200mm travel)
│
[Connecting Link]
│
│ ← Fastening Revolute Joint (Z component)
│
[Link 1 — 45mm]
│
│ ← Fastening Revolute Joint (Y component)
│
[Link 2 — 45mm]
│
│ ← Friction Revolute Joint (Roll, >300°)
│
[Light End Effector]

**Gruebler's Formula (DOF Verification):**

L = 6 links (including ground)
J1 = 5 (1 prismatic + 4 revolute)
J2 = 0

M = 3(L-1) - 2J1 - J2
M = 3(6-1) - 2(5) - 0
M = 15 - 10 = 5 (Target)

---

## Joint Designs

### 1. Friction Prismatic Joint (X-axis)
Enables tool-free sliding along the X-axis (200mm travel).

**Working principle:**
- Two spring-loaded rubber buttons press against the walls of the 
  base sliding groove from both sides
- The spring force keeps the buttons engaged, creating friction that 
  arrests the slider at any position
- To slide: press both buttons inward simultaneously — this disengages 
  the rubber contact surfaces, freeing the slider
- To lock: release the buttons — springs push rubber surfaces back into 
  contact, arresting position instantly
- No tools required for adjustment

<img width="455" height="227" alt="Screenshot 2026-07-15 011922" src="https://github.com/user-attachments/assets/52d1c083-5e98-44cf-9aed-004cc3c3e679" />

### 2. Friction Revolute Joint (Roll axis)
Enables tool-free rotation of the light about its own axis (>300°).

**Working principle:**
- The light connector link has a rubber-coated contact surface
- A spring holds this surface in axial compression against a mating 
  face, generating friction that holds any rotational position
- To rotate: press the light axially inward — this compresses the spring 
  further and disengages the rubber contact surfaces, freeing rotation
- Rotate to desired angle, then release — surfaces re-engage under 
  spring force, arresting the new position
- No tools required for adjustment

### 3. Fastening Revolute Joints (Y, Z, Yaw axes)
Three joints use M5 bolt + nut fastening for rigid obstructive arrest.

**Working principle:**
- M5 Socket Head Shoulder Screw passes through a clearance hole
- Tightening the M5 Nut clamps the links together rigidly
- Loosening allows free rotation to new position
- Allen key (4mm) required for adjustment

---

## Link Sizing

The 2-link revolute arm (Link1 + Link2) handles Y-Z workspace positioning.

**Required workspace:** 80mm (Z) × 40mm (Y)  
**Maximum reach required:**
r_max = √(80² + 40²) = √8000 ≈ 90mm

**Link lengths (equal for symmetric workspace):**
L1 = L2 = 45mm
Total reach = 90mm ✓

Equal link lengths chosen to maximize workspace coverage and simplify 
manufacturing. Nominal operating angle set at ~70° between links to 
avoid singularity at full extension.

---

## Parts List

| Part | Qty | Type | Notes |
|------|-----|------|-------|
| Base Sliding Groove | 1 | Custom | X-axis prismatic rail, 200mm |
| Rubber Button | 2 | Custom | Spring-loaded, friction contact |
| Spring (prismatic) | 1 | Custom | Preloads rubber buttons |
| Connecting Link | 1 | Custom | Base to kinematic arm |
| Link 1 | 1 | Custom | 45mm revolute arm |
| Link 2 | 1 | Custom | 45mm revolute arm |
| Connecting Link 2 | 1 | Custom | Arm to light interface |
| Pushback Rotation Button | 1 | Custom | Friction revolute joint body |
| Spring (revolute) | 1 | Custom | Preloads friction surface |
| M5 Socket Head Screw | 3 | Custom modeled | Standard M5 pitch & diameter |
| M5 Nut | 3 | Custom modeled | Standard M5 pitch & diameter |
| M3 Bolt | 1 | Custom modeled | Light attachment |
| Light | 1 | End effector | Bar light (provided) |

**Total: 13 parts**

---

## Fastener Specifications

| Fastener | Standard Dims | Custom |
|----------|--------------|--------|
| M5 SHCS | Pitch 0.8mm, Dia 5mm | Length 15mm |
| M5 Nut | Pitch 0.8mm, Dia 5mm | Head 5mm |
| M3 Bolt | Pitch 0.5mm, Dia 3mm | Custom length |

All fasteners conform to ISO thread standards. Head geometry 
adapted for envelope constraints.  
Clearance holes: **5.5mm** (M5), **3.3mm** (M3).

---

## Manufacturability

- All structural links are flat extruded profiles — laser cuttable
- No undercuts, no complex geometries
- Single tool for all fastening joints (4mm allen key)
- Rubber buttons and coatings are the only non-metal components
- Spring plungers are standard purchased components

## Serviceability

- Friction joints require zero tools — press and adjust
- Fastening joints require only a 4mm allen key
- Each DOF is independently adjustable without disturbing others
- Any single part replaceable without full disassembly
- All fasteners are standard M5 — available at any hardware store

---

## Repository Structure
adjustable-light-bracket-5DOF/
├── CAD/
│ ├── assembly.SLDASM
│ ├── parts/

│ └── STEP/
│ └── bracket_assembly.stp ← AP214
├── docs/
│ └── Light_Bracket.pdf
└── README.md

---

## Tools Used

- SolidWorks 2025 SP1.2
- STEP export: AP214


