# Anime And Stylized Character Profile

Use this profile when the target is anime, manga-inspired, or otherwise deliberately stylized. The reference and user brief define the style; this document supplies a review structure, not a universal anime formula.

## Parameters To Record

- **Global proportion**: total height `H`, head height `h`, head-to-body ratio, shoulder/hip widths, torso length, limb lengths, hand/foot scale, stance, and deliberate asymmetry.
- **Head and face**: skull/jaw silhouette, eye-line height, eye spacing and slant, iris/pupil scale, brow, nose simplification, mouth position/width, ear position, hairline, and expression.
- **Hair**: overall outer contour, front/side/back mass, parting, major clump directions, tip shapes, length landmarks, and how hair clears the face, shoulders, and clothing.
- **Clothing**: major silhouette, layering order, hem/cuff/collar landmarks, thickness/clearance, rigid versus flexible pieces, and identity-critical motifs.
- **Pose and view**: head/body orientation, limb gesture, camera projection, required comparison views, and whether foreshortening is present.
- **Budget**: base and evaluated faces by body, face, hair, clothing, and accessories; triangle count if real-time; deformation-driven density exceptions.

Use reference measurements where possible. If the view is oblique or foreshortened, record an interval or confidence note rather than claiming exact depth from pixels.

## Silhouette-First Build

1. Match the complete body contour and pose with a low-density proxy.
2. Add head shape and large hair masses; verify recognizable contour in front, side, and three-quarter views.
3. Add clothing masses and only the accessories that materially affect recognition or construction.
4. Validate face landmark placement in the reference camera before refining eyelids, iris layers, mouth, or small features.
5. Add local topology only where it supports contour, shading, or required expression/deformation.

Hair should be organized into primary masses and secondary clumps. Avoid many thin spikes as a substitute for the reference's large-scale hair design. Clothing should preserve the graphic silhouette and layered construction; folds are secondary to garment fit and contour.

## Evaluation Rubric

Score each category from 0 to 4: `0` missing/contradictory, `1` major mismatch, `2` recognizable but visibly off, `3` close with localized differences, `4` matches the approved evidence. Record evidence and largest discrepancy for every score.

| Category | Weight | What to compare |
|---|---:|---|
| Reference projection and pose | 20% | Camera/view alignment, body orientation, gesture, foreshortening |
| Body proportions and contour | 20% | Head/body ratio, widths, limb lengths, stance, outer silhouette |
| Face identity | 20% | Head/jaw, eye placement/shape, expression, nose/mouth treatment |
| Hair silhouette | 15% | Outer contour, mass balance, length, parting and major clump flow |
| Clothing and accessories | 15% | Layer order, major forms, fit, characteristic details |
| Cross-view volume and construction | 10% | Plausible depth, attachment, no single-view-only geometry |

Weighted result is for local comparison evidence only. It does not replace the Router's reference gate or stage decision. Do not average away a critical identity mismatch: report any category below `2` as a local blocker even if the total is high.

## Anime Character Regression Cases

Maintain three fixed cases with stable reference images and camera overlays:

1. **Front-view full-body standing character**: checks proportion landmarks, body contour, face placement, hair mass, and clothing blocks.
2. **Single three-quarter reference with occluded/backside regions**: checks uncertainty handling and whether unseen features remain explicitly provisional.
3. **Pose-capable character with layered clothing and long hair**: checks shoulder/elbow/hip/knee deformation, garment clearance, hair intersections, and per-region topology budget.

Each case records reference files and provenance, required views, parameter sheet, accepted assumptions, body/face/hair/clothing evaluated density, scoring evidence, fit defects, and local repair ownership. A regression passes only when no critical category is below `2`, there are no unreported visible intersections, and stated technical budgets are met. Compare like-for-like reference views; pixel overlays support but do not replace shape review.

## Common Failure Diagnosis

- **Looks unlike the character**: check camera/projection, pose, head/body ratio, face landmarks, and hair/clothing silhouette in that order before adding detail.
- **Only matches the front**: revisit head and torso depth, hair volume, garment layering, and hidden-side assumptions.
- **Looks generic despite high density**: restore stylized landmarks and exaggerations from reference; density is not an identity feature.
- **Clothing or hair penetrates**: identify static fit versus pose deformation, then inspect object boundary, clearance, bone placement, weights, or required simulation.
- **Pinching or faceting**: inspect local topology and evaluated modifier result; add density only where silhouette, shading, or deformation needs it.
