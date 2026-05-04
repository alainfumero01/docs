# Roboflow Annotation Guidelines V1

These guidelines are intended for upload into the Appia-owned Roboflow workspace for Windfix AI.

## Annotation Objective

Create high-consistency YOLO bounding-box annotations for the 15 blade-damage classes defined in `02_Blade_Damage_Taxonomy_V1.md`.

## Annotation Format

- bounding boxes only
- one box per distinct defect instance where feasible
- boxes should be tight around the visible damage extent without excessive background
- if a defect is partially occluded, box only the visible evidence

## General Rules

- annotate only defects visible in the current image
- do not infer hidden damage outside the frame
- do not label pure shadows, glare, or compression artifacts as damage
- use one primary class per defect instance
- when damage spans a large area, create a box around the actual affected zone rather than the entire blade section
- if the same class appears multiple times in one image, annotate each instance separately

## Overlap Rules

- if two distinct defect classes are clearly separate, annotate both
- if one visual region could fit multiple classes, choose the most specific or most operationally useful class
- do not stack duplicate labels on the same exact defect region

## Image Quality Rules

- skip images that are too blurry to support confident labeling
- flag low-quality images for review rather than forcing uncertain labels
- if a defect is probable but not visually confirmable, leave it unlabeled and flag for reviewer decision

## Class-Specific Notes

### Erosion

- `leading_edge_erosion_mild` should capture early or moderate leading-edge wear
- `leading_edge_erosion_severe` should capture substantial deterioration, major substrate exposure, or clearly escalated severity

### Cracks

- `surface_crack` is for broader structural or surface-line cracking
- `gel_coat_cracking` is for fine coating-level crack patterns

### Splits And Separations

- `trailing_edge_split` is reserved for trailing-edge seam opening
- `bond_line_separation` is for other bond-line distress outside the trailing-edge-specific class

### Structural Exposure

- use `fiber_exposure` when reinforcing fibers are visibly exposed
- use `delamination` when layer separation is the dominant visual signal

### Non-Structural Surface Conditions

- use `surface_contamination` only for foreign material or residue, not for actual substrate damage
- use `coating_blister` only for raised or bubbled coating failures

## Review Workflow

- annotators create initial labels
- uncertain cases are flagged for `Windfix AI Reviewer` review
- review queue should be sampled regularly for consistency control
- target inter-annotator agreement should exceed 90%

## Dataset Split Strategy

- train: 80%
- validation: 10%
- test: 10%

Split rules:

- avoid near-duplicate images of the same defect appearing across different splits
- where possible, split by inspection batch or work order to reduce leakage
- preserve class representation across all three splits

## Versioning Rules

- create a new dataset version for any material labeling change, class-definition adjustment, or major image-ingest batch
- record version notes for:
  - image sources added
  - classes affected
  - guideline changes
  - review or QA findings
