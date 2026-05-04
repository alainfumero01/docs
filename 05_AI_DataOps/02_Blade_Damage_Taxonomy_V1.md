# Blade Damage Taxonomy V1

This taxonomy defines the 15 YOLO annotation classes for the Windfix AI training dataset.

## Class List

1. `leading_edge_erosion_mild`
2. `leading_edge_erosion_severe`
3. `surface_crack`
4. `delamination`
5. `pit_cavity`
6. `trailing_edge_split`
7. `lightning_strike_mark`
8. `vortex_generator_damage`
9. `coating_blister`
10. `bond_line_separation`
11. `fiber_exposure`
12. `impact_damage`
13. `tip_damage`
14. `surface_contamination`
15. `gel_coat_cracking`

## Class Definitions

### `leading_edge_erosion_mild`

Visible leading-edge wear with superficial material loss, coating wear, or roughening that does not yet indicate major structural exposure.

### `leading_edge_erosion_severe`

Advanced leading-edge damage with substantial material loss, deeper substrate exposure, or clear aerodynamic degradation risk.

### `surface_crack`

Linear crack visible on the blade surface that appears distinct from gel-coat-only craze cracking and may indicate substrate involvement.

### `delamination`

Separation between material layers or skin-laminate regions, typically visible as lifting, hollowed areas, bulging, or exposed layered structure.

### `pit_cavity`

Localized cavity, gouge, or pitted material-loss zone that is deeper than ordinary abrasion and visually bounded in a compact region.

### `trailing_edge_split`

Opening, seam failure, or split visible along the trailing edge.

### `lightning_strike_mark`

Burning, scorching, puncture, branching discoloration, receptor-area damage, or other visual evidence consistent with a lightning event.

### `vortex_generator_damage`

Detached, broken, bent, missing, or visibly compromised vortex generator components or surrounding attachment damage.

### `coating_blister`

Raised, bubbled, or blistered coating region where the surface finish is lifting from the underlying material.

### `bond_line_separation`

Visible separation, opening, or distress along a bonded seam or bond line outside the specific trailing-edge split condition.

### `fiber_exposure`

Visible structural fibers or reinforcement exposed due to coating or laminate loss.

### `impact_damage`

Discrete impact zone such as denting, chipping, puncture, crushing, or foreign-object strike damage not better classified elsewhere.

### `tip_damage`

Damage concentrated at or immediately adjacent to the blade tip, including breaks, deformation, material loss, or tip-edge compromise.

### `surface_contamination`

Non-structural surface fouling such as residue, buildup, staining, oil, biological matter, or debris obscuring the blade surface.

### `gel_coat_cracking`

Fine surface-level crazing or gel-coat crack networks that appear confined to the coating layer.

## Labeling Notes

- choose the most specific class available
- avoid dual-labeling the same defect instance unless distinct defects are visibly separate
- when uncertainty exists between `surface_crack` and `gel_coat_cracking`, default to `gel_coat_cracking` unless substrate involvement is visually indicated
- use `leading_edge_erosion_severe` only when the severity is clearly beyond superficial wear
