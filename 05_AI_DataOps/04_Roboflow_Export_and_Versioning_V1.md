# Roboflow Export And Versioning V1

This document defines the target workspace configuration for dataset export and version control.

## Workspace Intent

- workspace owner: Appia Wind Services
- billing owner: Appia
- AIDA AI team access: annotator or reviewer roles only unless higher access is explicitly needed

## Dataset Export Standard

- export format: `YOLOv11`
- annotation type: object detection bounding boxes
- normalized train/val/test directory structure expected from Roboflow export

## Dataset Split Strategy

- train: `80%`
- validation: `10%`
- test: `10%`

## Versioning Strategy

Create a new dataset version when any of the following occur:

- a new labeled image batch is added
- class definitions change
- annotation guidelines change in a way that affects labels
- large correction passes are completed
- augmentation settings materially change

## Version Notes Template

Each Roboflow dataset version should include:

- version name
- creation date
- image count
- class distribution summary
- data sources added
- QA notes
- split configuration confirmation
- export format confirmation

## Recommended Naming

- workspace: `appia-windfix-ai`
- project: `blade-damage-detection`
- versions: `v1-baseline`, `v2-historical-batch-a`, `v3-qc-corrections`, etc.

## QA Checks Before Export

- all 15 classes present in the dataset
- minimum class coverage thresholds tracked
- no empty-class export
- split percentages verified
- random image spot-check completed
- reviewer queue cleared for release version

## External Actions Still Required

These items require direct Roboflow access and are not completed in this repository alone:

- create or verify the Appia-owned workspace
- configure the 15 labels in Roboflow
- upload the annotation guidelines into the workspace
- add AIDA AI team members with annotator access
- confirm the Roboflow export target is configured for YOLOv11
- enable dataset versioning in the live workspace
