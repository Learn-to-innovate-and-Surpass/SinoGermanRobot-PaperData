# Simulating your own six axis robot

[中文](README.md) · Repository: **https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot**

The aim is to **start with a few seed actions, generate many candidates for the same task through constrained random perturbations, and screen them through batch simulation and task review**. This can reduce repeated waypoint teaching and build more useful data. The intended progression is less repetitive programming → checked, reusable data → later VLA training and evaluation. Contributions are welcome: robot documentation, simulation adaptations, candidate augmentation methods, reproducible failures, sequence constraints, and data collection interfaces.

The current implementation targets the **six-axis AUBO-i5**, with i5H CAD used as an appearance reference. It connects browser simulation, action-file review, and an independent execution interface. Supporting another six-axis robot requires developer changes and validation. There is currently no automatic adaptation from uploaded photographs or a DH table. This guide starts with preparation and simulation in a separate copy; it does not claim generic hardware control or completed VLA training.

The long-term goal is to organize robot work around tasks and constraints, reusing data and skills to reduce the need for a separate fixed program for every variation. Models and tool-using agents can be replaceable components for document interpretation, modeling, candidate augmentation, simulation checks, and data organization. Users should spend less effort switching between tools while consequential choices, validation results, and execution authorization remain visible. The architecture should accommodate future algorithms rather than assume a single dominant approach. Greater autonomy, usability, and lower adaptation cost are objectives to evaluate on concrete tasks.

## 1. Prepare the inputs

Write **unknown / unmeasured** when information is unavailable. Ask the AI what evidence is needed. Record the source, exact model, document revision, and page for each parameter; keep original manufacturer URLs.

| Input | What to provide |
| --- | --- |
| Robot identity | Manufacturer, exact model, order and type of the six joints, nameplate photograph; record the controller model separately. |
| Kinematics | DH or modified-DH table and frame diagram; convention, transform multiplication order, indexing, angular/length units, joint zero offsets, and positive directions. A table without its convention is insufficient. |
| Geometry and photographs | Authorized STEP, URDF, STL, or other model resources; front, side, top, tool, and mounting photographs, with measured dimensions and the pose associated with each photograph. Without CAD, begin with an explicitly approximate shape. |
| Frames and end effector | Origins and axes for robot base, workbench, flange, tool TCP, and cameras; state the direction of every transform. Unmeasured TCP, hand–eye transform, and mounting offsets stay unmeasured. |
| Limits and exclusion zones | Per-joint position/velocity limits and manufacturer evidence; tool/cable envelopes; each zone's frame, minimum/maximum corners, units, source, and measurement status. Do not present unsupported acceleration values as manufacturer limits. |
| Task and acceptance criteria | Task description, source actions, start/end conditions, required poses/key points/gripper events, and tolerances; distinguish process requirements, measurements, and provisional rules. |

**Photographs help describe appearance and layout; they do not replace metric measurement or frame calibration.** DH/MDH and CAD do not establish controller zero positions, joint signs, or the tool TCP by themselves. Preserve the units and notation supplied by the manufacturer; the [official Universal Robots DH tables](https://www.universal-robots.com/articles/ur/application-installation/dh-parameters-for-calculations-of-kinematics-and-dynamics/) illustrate documentation structure, not parameters for other models.

## 2. Begin with one small task

1. Follow the repository's root instructions and explore the third browser view, the action editor. With Python 3.11 installed, run `py -3.11 -B simulation/launcher.py start` from the repository root. The web service uses local loopback interfaces and does not require the robot SDK.
2. Preserve the original AUBO-i5 version and create a separate copy or branch for your model. Give the AI your inputs and obtain a parameter comparison, missing-information list, and implementation plan first.
3. Check zero configuration, positive/negative single-joint changes, and multiple combined poses. Compare position and orientation with independent manufacturer kinematics or existing trustworthy pose records, and compare browser and Python results. Define justified tolerances. Without independent evidence, report internal consistency only; do not claim hardware calibration.
4. Add the workbench and exclusion zones. The current checker approximates links/tools with capsules and obstacles with axis-aligned boxes. For a rotated obstacle, explicitly choose a conservative box or extend the algorithm. Maintain visual and collision geometry separately: an invisible wall must still participate in collision checks. The [official ROS URDF example](https://github.com/ros/urdf_tutorial/blob/ros2/urdf/07-physics.urdf) also defines `visual` and `collision` separately; this project does not automatically import arbitrary URDFs.
5. Reuse and modify a few known actions for one well-defined task. Check poses, adjacent transitions, and the repeat transition, then evaluate the task criteria. Passing a geometric proxy can still change the task. Increasing the allowed joint correction must not conceal task failure.

The proposed extension is **seed actions → constrained random perturbation/interpolation → multiple same-task candidates → batch simulation screening and rollouts → task review → data collection**. Define variable joints, perturbation bounds, and task phases first; preserve frozen joints, grasp/release events, TCP position/orientation tolerances, ordering, and start/end conditions. Check the initial-to-first, adjacent, and repeat transitions for every candidate, and record source lineage, random seeds, and filtering outcomes. **This complete batch pipeline is a development direction. The present browser's candidate search and repair are not a completed batch dataset generator or a learned generative model.** Assess task validity, coverage, and redundancy alongside candidate counts.

## 3. Reusable prompt for an AI assistant

Replace the bracketed fields with your own information. You can start with partial inputs and mark the rest unknown.

```text
Help me adapt SinoGermanRobot to my six-axis robot in a separate copy/branch.
This round is simulation and offline validation only. Preserve the AUBO-i5
baseline. Do not connect to or operate physical devices.
Goals, in order: reduce repetitive waypoint programming; collect reusable,
traceable data; integrate VLA training later.
Specific goal: use constrained random perturbation/interpolation of a few
seed actions to create many same-task candidates for batch screening and
rollouts. Identify existing capabilities and batch interfaces still to develop.

Robot and task: [manufacturer/model/joint order/types/task description]
Original documentation: [URLs, revisions, pages, permissions or provenance]
DH/MDH: [table, convention, multiplication order, indexing, units,
         zero offsets, positive joint directions]
Photographs/CAD: [paths or attachments, views, measured dimensions,
                  joint pose associated with the photographs]
Frames: [base/workbench/flange/TCP/camera definitions and transform directions;
         mark unknown items unmeasured]
Limits: [per-joint position/velocity/acceleration with evidence;
         cable/tool envelopes; unmeasured items]
Exclusion zones: [name, frame, min/max, units, collision-only flag,
                  evidence and measurement status]
Task preservation: [key points/TCP position and orientation tolerances/gripper
                    events/order/start and end conditions/justification]
Seed actions: [format, units, provenance, variable joints, frozen joints,
               perturbation bounds; or none]

Work in this order:
1. Identify conflicts and missing inputs. Ask at most three high-priority
   questions first, explaining why each matters. Never infer measured joint
   parameters, zeros, speed limits, or calibration from photographs.
2. Compare the current i5-specific implementation with the target model.
   List file-level changes for Python/browser kinematics, appearance,
   collision envelopes, joint limits, and model versioning. Renaming or
   uniformly scaling the old robot does not complete adaptation.
3. Implement simulation in the separate copy, preserving baseline tests.
   Add independent reference-pose checks for the target robot. Make
   radian/degree, metre/millimetre, and WXYZ/other orientation conversions explicit.
4. Validate augmentation rules on a few candidates before scaling up.
   Check initial, adjacent, and repeat transitions and task preservation.
   Record source seed actions, random seeds, perturbation settings,
   rejection reasons, and correction magnitude. Preserve required frozen
   joints; do not move key task events merely to pass collision checks.
   Keep original and revised actions separate; preserve unknown metadata;
   do not fabricate review or execution records.
5. Report verified results, simulation assumptions, and unmeasured items,
   together with reproduction steps. An approximate appearance model is
   acceptable when clearly labelled; it is not validated kinematics or control.
6. Keep legacy real_motion_enabled=false and workspace_limits.validated=false.
   Do not enable the ReviewedActionGate hardware path for the new model
   in this round. Do not start up, home, or move a robot automatically.
```

## 4. Locations a developer must inspect

These are current implementation locations, **not an existing generic robot-plugin API**. Paths are relative to the repository root.

| Location | Adaptation concern |
| --- | --- |
| `src/robot_model.py` | `load_scene()`, `pose_matrices()`, `controller_pose()`; six-joint assumptions, axes/origins, controller-to-visual signs, base registration, flange orientation. |
| `simulation/static/editor-kinematics.mjs` | `controllerPoseData()` still contains six-joint assumptions, i5 signs, and a `-0.0235 m` offset. Keep browser and Python changes consistent. |
| `assets/robot_models/i5h_scene.json`, `tools/cad_conversion/` | Current model-loading path and CAD conversion/build pipeline. Renaming the model requires updating loaders and version binding. Adding a URDF alone does not replace this model. |
| `src/tool_geometry.py`, `src/workbench_frame.py` | Tool mounting/collision capsules and workbench-to-base transform. Do not reuse the existing workbench rotation without justification. |
| `simulation/action_editor_engine.py` | `CAPSULES`, `TABLE_OBSTACLES`, `LIMIT_DEG`, `options()`, `segment_check()`, `repair()`; reassess the existing uniform ±175° limit and other bounds. |
| `simulation/static/action-editor.js`, `action-editor.html`; `src/aubo_show_gui.py`, `real_show_gui.py` | Six-joint controls, numeric limits, and model labels. Other demonstration scenes also contain original task poses that require adaptation. |
| `src/action_review.py` | `model_revision()`, `validate_reviewed_action()`, `ReviewedActionGate`; bind the new model/constraint versions and invalidate prior reviews. |
| `tests/` | Preserve the i5 baseline; add independent kinematic references, frontend/backend consistency, collision/sequence/task checks, and offline blocking tests for the target model. |

**Hardware adaptation is a separate later development stage.** The current execution path targets AUBO-i5. For another model, a developer must also inspect `src/real_robot_worker.py`, `src/real_action_core.py`, `src/robot_diagnostics.py`, `src/execution_speed.py`, and the relevant `config/` files, and implement controller interfaces, state/stop semantics, manufacturer speed evidence, file-review gates, and actual starting-pose checks. Changing an IP address, replacing CAD, or selecting a model name does not complete hardware adaptation. This guide provides no gate-bypass procedure.

## 5. Accumulate useful data

Retain a traceable chain of **original candidate → revised candidate → geometric check → task review → reviewed version**. Record rejection, simulation acceptance, task-review outcome, and whether physical execution occurred, each with evidence. The current `execution_review` binds a file and scene; it does not establish task semantics, physical calibration, or training quality. Add task-specific criteria and checks.

The following is a **proposed future data design**, not output already supplied by the existing action JSON:

| Content | Suggested records |
| --- | --- |
| Vision and language | Image/video frame references, camera identity, task text, and task phase. |
| State and action | Measured joint/gripper state separately from commanded actions; specify absolute position, delta, or other action meaning, units, frame, and joint order. |
| Time | Separate timestamps for frames, states, and commands; clock domains, synchronization method, sampling rate, dropped frames, and latency. |
| Provenance and labels | Episode/step IDs, seed action IDs/hashes, random seeds and perturbation settings, robot/tool/scene/calibration/code versions, revisions/reviews, success/failure/interruption, and simulation/real origin. |

A future simulation collector can synchronize rendered RGB observations with states, actions, language, and time. Present browser playback and the paper's data package should not be labelled a training-ready dataset. The [official LeRobot dataset documentation](https://huggingface.co/docs/lerobot/en/lerobot-dataset-v3) is a reference for organizing states, actions, timestamps, videos, and metadata. Integration still requires field conversion, time alignment, quality filtering, and training/evaluation splits that prevent variants of the same source trajectory from leaking across sets. Adding a language sentence to joint JSON alone does not produce a complete VLA dataset.

When contributing an Issue/PR at **https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot**, include the model, source documentation, adaptation scope, reproducible input, version, and actual validation results. Reproducible augmentation/failure cases, task-preservation criteria, and data interfaces are especially useful. Respect separate permissions for photographs, manufacturer materials, and third-party models; the repository-root license defines its scope for self-authored code. Reduced teaching effort and more valid data are expected benefits. Existing small-sample programming timings apply only to their recorded tasks and completion criteria; batch augmentation efficiency and VLA training benefits require separate evaluation.
