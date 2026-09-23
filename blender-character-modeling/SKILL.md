---
name: blender-character-modeling
description: Plan and guide human or humanoid character modeling in Blender, including reference analysis handoff, stylized/anime proportions, silhouette-first blockout, region-based topology budgets, hair and clothing construction boundaries, and fit/deformation checks. Use alongside the Router and direct surface modeling for character creation or reference-guided character reconstruction; load rigging and surfacing specialists only when those deliverables are required.
---

# Blender Character Modeling

Build a recognizable, coherent character from the declared reference and use case. Treat proportions, silhouette, pose, topology, clothing fit, and face readability as separate decisions. More polygons do not correct a wrong camera hypothesis or silhouette.

## Authority Boundary

- The `blender-production-router` owns routing, production stages, retry budgets, rollback targets, visual pauses, and final gate decisions.
- This skill owns character-specific analysis and construction guidance: character proportions, visual landmarks, silhouette priorities, topology and density planning, hair/clothing boundaries, and local fit evidence.
- `blender-reference-reconstruction` owns reference evidence and uncertainty when images define the target. Do not turn an unseen back/side into a claimed observation.
- `blender-direct-surface-modeling` owns mesh construction and topology operations; this skill provides character requirements and checks.
- `blender-deformation-rigging` owns armatures, weights, shape keys, and deformation implementation. `blender-material-surfacing` owns material construction. `blender-geometry-validation` reports technical validation evidence.
- Do not mutate Router state, select a replacement production route, advance stages, consume retries, or request project deletion.

Read the Router's production protocol, topology-first contract, and artifact contract before task work. For image-defined characters, use reference reconstruction before formal modeling.

## Required Character Brief

Record only decisions that affect the route, build, gate, or handoff:

- Deliverable: static display, animation, real-time/game asset, print, or other.
- Style profile: anime/stylized, realistic, chibi, or user-defined; preserve user-specific deviations.
- References and views: front, side, back, three-quarter, face close-up, detail images; note projection, crop, pose, and occlusion.
- Pose, camera/view requirements, intended viewing distance, and whether the model must work from multiple views.
- Body, face, hair, clothing, accessory, expression, rigging, and material scope.
- Technical constraints: evaluated face/triangle budgets, texture/material limits, target platform, export needs.
- Unknowns and assumptions, especially hidden surfaces, garment construction, and unseen anatomy.

If information is missing, mark it as an assumption and keep the corresponding Blockout reversible. Do not invent a fixed universal head-to-body ratio.

## Reference And Proportion Pass

1. Ask reference reconstruction to map image views, visible landmarks, occlusions, projection uncertainty, identity cues, and unobserved regions.
2. Establish a character scale using total height `H` or head height `h`. Record measured ratios rather than relying on memory or generic anatomy.
3. Capture landmarks appropriate to the design: crown, chin, eye line, shoulder line, chest/waist/hip lines, elbows, wrists, crotch, knees, ankles, and sole. For face work, record head silhouette, eye centers, brow, nose, mouth, jaw, ear, and hairline.
4. Separate identity-critical features from support details. Typical anime priorities are head/body ratio, face silhouette, eye placement/shape, hair mass silhouette, pose, and major clothing color/form blocks; the actual reference decides their order.
5. Use the supplied camera/projection for comparisons. A single image can establish a view match, not unseen depth or backside truth.

## Character Production Stages

Follow Router stages and gates; this local sequence does not advance global state.

1. **Analysis**: declare purpose, style profile, references, proportions, identity cues, body/clothing/hair part graph, deformation scope, budgets, uncertainty, and required views.
2. **Blockout**: use low-density proxies for head, torso, pelvis, limbs, feet, major clothing, and hair masses. Match the reference's pose and outer contour before facial microfeatures or folds. Preserve camera and cross-view checks.
3. **Primary form**: establish recognizable head/body proportions, face planes, limbs, clothing masses, and hair silhouette. Do not hide an incorrect shape with color, lighting, or accessories.
4. **Topology construction**: direct modeling specialist selects construction and topology. Specify control loops near eyes/mouth when expressive facial deformation is required, and around shoulders, elbows, wrists, hips, knees, and ankles when those joints must deform. Static models may use simpler topology if the target view and shading allow it.
5. **Hair and clothing**: model major hair clumps and garment shells according to visible silhouette and construction. Declare whether an item is a separate shell/object, body surface, rigid accessory, or deforming garment, with its reason. Record intended clearances and overlaps.
6. **Rigging (conditional)**: load rigging specialist only when animation, posing, or deformation is requested. Test representative poses before fine surface detail.
7. **Surfacing (conditional)**: after form gates, assign skin, hair, eye, fabric, and accessory materials with style-appropriate response.
8. **Final validation**: obtain required views, evaluated density evidence, fit checks, pose checks if rigged, and task-specific technical validation before Router gate review.

## Face Count And Density Budget

Never prescribe one universal polygon count. Record a budget by deliverable and region, including base mesh and evaluated modifier result; for real-time targets also record final triangle count. At minimum separate body, head/face, hair, clothing, and accessories.

Use the lowest density that supports the approved silhouette, shading, and required deformation. Add density locally where it changes silhouette, supports facial expression or joint deformation, or fixes visible faceting. Do not uniformly subdivide the character to compensate for weak proportion or topology planning. Distinguish viewport/blockout density from final evaluated density, including Subdivision and hair/garment objects.

Suggested review fields:

```text
deliverable / target platform:
viewing distance and required views:
base faces by region:
evaluated faces by region:
final triangles (when applicable):
deformation regions and required poses:
reason for any budget exception:
```

Numeric values are task budgets, not style rules. Resolve them from the target and evidence before formal production.

## Anime / Stylized Profile

Use `references/anime-character-profile.md`. Preserve deliberate exaggeration and asymmetry from the reference. Do not normalize large eyes, head shape, limb proportions, hand/foot simplification, or hair masses to realistic anatomy. Compare both the complete contour and identity-critical facial/hair landmarks. Separate eye geometry, iris/pupil layers, and hair clumps only when needed by style, material, deformation, or silhouette control; do not turn every color patch into an object.

## Low-Poly Real-Time Game Profile

For low-poly real-time characters, including user-referenced visual targets such as R.E.P.O. or Lethal Company, use `references/low-poly-game-character-profile.md`. Treat game names as visual references only: derive proportions, facets, palette, and detail from supplied images and the target project's constraints. Do not infer a game's internal topology, polygon count, rendering pipeline, or implementation from its appearance.

## Fit And Deformation Checks

- Static fit: inspect garment/body and hair/face intersections in neutral pose from front, side, and three-quarter views. Record intended contacts, hidden overlaps, and clearance assumptions.
- Pose fit: when rigged, inspect at least shoulder lift, elbow bend, hip lift, knee bend, torso twist, and any action specific to the character. Include extreme poses only if required by the deliverable.
- Diagnose visible penetration by owner: reference/proportion, mesh silhouette, object boundary, garment clearance, armature placement, weight distribution, or collision/simulation. Propose a local repair target; do not restart unrelated analysis.
- Shrinkwrap or surface conformity may help fit a shell to a base body, but must be inspected for offsets, folds, thickness, and deformed poses; it is not proof of collision-free clothing.
- A successful render or one matching camera is not proof of valid topology, depth, or deformation.

## Handoff

Provide the Router with the accepted reference assumptions, character parameter/landmark sheet, approved Blockout views, per-region mesh budget, part/object boundaries, fit/deformation evidence, unresolved local defects, and recommended repair owner. The Router decides whether a gate passes or work rolls back.
