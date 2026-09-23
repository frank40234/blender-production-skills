# Low-Poly Real-Time Game Character Profile

Use this profile for characters intended to read as low-poly or deliberately simple in a real-time game. R.E.P.O. and Lethal Company may be used as user-selected visual reference labels; they do not define a universal polygon budget or prove any production method. Analyze supplied screenshots or approved reference images and the target project's technical limits.

## Goals

- Preserve character identity through silhouette, proportions, pose, large color regions, and a small number of distinctive features.
- Keep the model readable at the intended camera distance, display size, and lighting conditions.
- Spend geometry where it changes the contour, silhouette shading, articulation, or recognizable feature; use materials only for details that do not need geometric relief.
- Meet an explicit real-time budget without hiding an incorrect shape through flat shading, darkness, fog, or camera angle.

## Required Brief And Budget

Record before formal topology:

```text
target engine/platform and character role:
camera type, typical distance, smallest on-screen size:
static / animated / networked / first-person view requirements:
reference images, views, projection, and unresolved assumptions:
identity-critical silhouette and landmarks:
body, clothing, hair, and accessory part boundaries:
triangle budget by character and by region:
material slots and texture resolution/budget:
deformation bones / poses / animation requirements:
LOD or impostor requirements, if any:
performance or draw-call constraints:
```

Do not substitute a memorized face or triangle count for the target project's budget. Keep base faces, evaluated modifier faces, and final triangulated count distinct. Include all visible clothing, hair, and equipment in the character total. State whether the budget applies to one character, one LOD, or all LODs.

## Visual Construction Rules

1. Begin with a low-density body, clothing, and hair blockout. Match pose, overall contour, head/body proportion, and major negative spaces before surface details.
2. Inspect front, side, and gameplay camera views. If gameplay uses a fixed third-person camera, validate that view while retaining enough volume for other required angles.
3. Establish large masses and readable planes. Deliberate facets should follow form changes; do not make every surface uniformly angular by indiscriminate decimation.
4. Preserve asymmetry and unusual proportions when they identify the character. Do not normalize a stylized design to realistic anatomy.
5. Keep details that affect silhouette, occlusion, collision, or animation as geometry. Use texture/material detail for small, non-silhouette markings when supported by the art direction and platform.
6. Avoid thin, fragile pieces that vanish at target screen size or produce unstable silhouettes. Test appendages, hair tips, straps, and accessories at the smallest required display size.
7. Use flat or smooth shading, normal treatment, and material faceting only as deliberate style choices validated against the reference; none can replace a correct silhouette.

## Topology And Performance Planning

- Allocate triangles per region based on projected size, curvature, articulation, and identity importance. Record why any region exceeds its budget.
- Reserve enough edge flow and deformation loops for joints that must animate. A static showcase budget is not automatically valid for a deforming game character.
- Inspect triangulated evaluated output, not only the editable quad cage. Confirm triangulation does not flip important facets or distort deformation.
- Minimize unnecessary material slots and separate objects, while preserving meaningful boundaries for deformation, equipment, visibility, and reuse.
- Use LOD only when the game needs it; each LOD must retain the silhouette and key identity features at its target distance.
- If decimation or remeshing is considered, compare the result against approved silhouettes and articulation. Repair lost shape before accepting the lower count.

## Fit, Rig, And Collision Checks

For an animated character, test the neutral pose plus representative movement: shoulder lift, elbow bend, hip lift, knee bend, torso turn, and any signature action. Inspect clothing, hair, and gear intersections at each pose. For gameplay collision, separately declare the collision proxy and test clearance through expected movement; visual mesh overlap is not collision validation.

Classify each visible penetration as static garment fit, object boundary, bone placement, weight distribution, collision proxy, or pose-specific deformation. Assign the local repair to modeling, rigging, or collision setup instead of increasing polygon density by default.

## Low-Poly Game Evaluation

Use a 0–4 score per category and include screenshots or measured evidence. A strong score in one category does not cancel a critical failure in another.

| Category | Weight | Evidence |
|---|---:|---|
| Gameplay-view readability | 20% | Silhouette and identity at the minimum intended on-screen size |
| Reference silhouette and proportion | 20% | Fixed-view overlay or landmark comparison; front/side where available |
| Low-poly form and shading | 15% | Facet direction, plane breaks, shading stability against references |
| Identity features and palette | 15% | Face or head cues, major color blocks, signature equipment |
| Budget and runtime fit | 15% | Final triangles, region budget, material slots, LOD and target constraints |
| Fit and deformation | 15% | Clothing/hair intersections, pose tests, collision proxy if required |

Any critical category below `2`, visible unintended penetration, failed target budget, or unreadable silhouette at target size blocks acceptance and needs a local repair. This score supports review; it does not replace Router gates or technical validation.

## Regression Cases

Maintain stable references and target camera settings for these cases:

1. **Single-view low-poly character**: checks silhouette, proportion, palette, facet placement, and minimum display size.
2. **Multiple-view character with asymmetric equipment**: checks that one view is not a flat camera-facing approximation and that equipment remains attached/readable.
3. **Animated character with clothing or hair**: checks region budgets, triangulated result, representative pose deformation, and intersections.

Record reference provenance, camera distance/screen size, accepted assumptions, per-region base/evaluated/final triangle counts, material slots, pose evidence, and largest discrepancy. A regression passes only when all critical categories are at least `2`, the target budget is met, and no unintended visible intersection remains.

## Failure Diagnosis

- **Looks unlike the reference**: fix projection, pose, proportions, or silhouette before topology density or materials.
- **Looks too smooth or too angular**: adjust plane placement and facet size intentionally; do not rely on global decimation or shading toggles alone.
- **Readable only in close-up**: simplify small details and strengthen the major contour and value/color grouping at actual gameplay scale.
- **Budget passes but animation fails**: allocate topology where deformation occurs, revise weights or joint placement, then recount triangulated output.
- **Budget fails**: identify the regions with low screen-space or identity value; simplify those first and recheck all approved views.
- **Clothing or equipment clips**: repair fit, part boundary, rigging, or collision proxy according to the failure owner; polygon reduction is not a fix.
