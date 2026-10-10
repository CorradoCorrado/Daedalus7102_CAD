# Daedalus 7102: 2022 competition robot CAD

CAD for the 2022 competition robot of **FRC Team 7102 Daedalus** (PrepaTec Campus Guadalajara), built for the FIRST Robotics Competition game *Rapid React*. The repository contains the SolidWorks parts and assemblies, DXF cut files, PDF drawings and 3D-print files for most of the robot.

> [!WARNING]
> This repository has been abandoned since September 2022 and is no longer maintained. Use it for reference only.

![Daedalus 7102 2022 FRC competition robot during build](GitFRC_GALLERY/DAEDALUS%202K22%20FRC%20COMP%20BOT.jpg)

## Contents

- [Subsystems](#subsystems)
- [Repository layout](#repository-layout)
- [Software requirements](#software-requirements)
- [Opening the model](#opening-the-model)
- [Manufacturing files](#manufacturing-files)

## Subsystems

| Subsystem | Location | Main parts |
|---|---|---|
| Drivetrain | `GitFRC_CAD/` (root) | AndyMark AM14U5 chassis, long configuration, 6-wheel drive with churro locations. Toughbox Mini gearboxes with CIM motors, 6 in HiGrip wheels. |
| Elevator | `GitFRC_CAD/Elevator/` | 3-stage 57 Sport HD gearbox, 22T and 40T #25 chain sprockets, Rexroth 30 × 30 joint, roller guides, bearing blocks, hooks, stationary stage and sheet-metal base. |
| Elevator base | `GitFRC_CAD/Elevator Basement/` | Motor assembly, bottom support and sheet-metal support. |
| Secondary arms | `GitFRC_CAD/Secondary Arms/` | 57 Sport planetary gearbox with 5:1 stages, 775 RedLine motor, 40T #25 sprocket and hub, sheet-metal plate. |
| Shooter | `GitFRC_CAD/INTAKE & SHOOTER/SHOOTER V4/` | Single-stage 57 Sport gearbox, 6 in wheel. |
| Ball elevator | `GitFRC_CAD/INTAKE & SHOOTER/BALL ELEVATOR V3/` | 2 in compliant wheels, wheel carrier, pulley, motor base. |
| Gussets | `GitFRC_CAD/Elevator/STD_Gussets/` | L, T, pivot, roller and support gussets, each with a DXF in `DXF FILES/`. |
| Electrical | `GitFRC_CAD/` (root) | Electronics base, battery mock-up, robot signal light (`RSL ASSY.SLDASM`), bumper mock-up. |

The final competition robot is `GitFRC_CAD/Bot_ASSY_V2.SLDASM`. `GitFRC_CAD/Bot_ASSY.SLDASM` is the earlier version. Each has a `.SLDDRW` drawing.

Vendor parts (AndyMark, McMaster-Carr) are STEP imports saved as `.STEP.SLDPRT` / `.STEP.SLDASM`. McMaster-Carr part numbers are in the filenames (e.g. `10-32 Nylock Nut 1_90631A411.STEP.SLDPRT`).

## Repository layout

```
Daedalus7102_CAD/
├── GitFRC_CAD/                  # SolidWorks parts, assemblies and drawings
│   ├── Bot_ASSY_V2.SLDASM       # top-level robot assembly (final)
│   ├── Elevator/                # elevator, bearing blocks, hooks, gussets
│   ├── Elevator Basement/       # elevator base and motor mount
│   ├── Secondary Arms/          # secondary arm and gearbox
│   ├── INTAKE & SHOOTER/        # shooter (V4) and ball elevator (V3)
│   ├── InkScape Cad/            # gusset sketches (.svg, .dxf)
│   ├── STLs/                    # 3D-print exports
│   └── *.STEP.SLDPRT            # drivetrain and vendor parts
├── GitFRC_DXF/                  # flat patterns for cutting (gussets, plates, sheet metal)
├── GitFRC_PDF/                  # PDF drawings
└── GitFRC_GALLERY/              # robot photos
```

## Software requirements

| Tool | Purpose |
|---|---|
| SolidWorks 2021 | Parts, assemblies and drawings |
| Any DXF viewer or CAM tool | Reviewing and cutting `GitFRC_DXF/` files |
| Ultimaker Cura 4.13.1 | The committed `.gcode` (Marlin, 0.28 mm layer height) |
| Inkscape | `GitFRC_CAD/InkScape Cad/` gusset sketches |

## Opening the model

1. Clone the repository. Keep the folder structure, since assemblies reference parts by relative path.
2. Open `GitFRC_CAD/Bot_ASSY_V2.SLDASM` in SolidWorks.
3. If SolidWorks asks for missing references, point it at `GitFRC_CAD/` and let it search subfolders.

Close SolidWorks before committing so its `~$*` lock files are released, and don't commit them.

## Manufacturing files

| Folder | Content | Used for |
|---|---|---|
| `GitFRC_DXF/` | 41 flat patterns: gussets, plates, sheet-metal parts, MDF spacers, shooter parts | Router, laser or waterjet cutting |
| `GitFRC_PDF/` | Drawings of the base, elevator, secondary arm, stationary stage and electronics cross member | Machining and assembly |
| `GitFRC_CAD/Elevator/Bearing Block/` | Bearing spacers as `.STL` and `.gcode` | 3D printing |
| `GitFRC_CAD/STLs/` | Long spacer | 3D printing |

Re-export the DXF or PDF after changing a part, and keep the exported filename matching the part.
