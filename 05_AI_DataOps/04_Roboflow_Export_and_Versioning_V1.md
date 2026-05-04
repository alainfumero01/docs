# Roboflow Export And Versioning V1

This document defines the target workspace configuration for dataset export and version control.

## Workspace Intent

- provisional workspace owner until Appia onboarding: `alain.fumero@aidasolutionsgroup.com`
- target long-term workspace owner: Appia Wind Services
- target billing owner: Appia
- AIDA AI team access: annotator or reviewer roles only unless higher access is explicitly needed

## Live Workspace Status

- verified workspace id: `project-onyx`
- live project id: `project-onyx/blade-damage-detection`
- live project name: `Blade Damage Detection`
- dataset version initialized: `v1-baseline` as version `1`
- YOLO export confirmed as available on version `1` with `yolov11`

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

- configure or lock the 15 labels in the live Roboflow project settings
- upload the annotation guidelines into the workspace
- add AIDA AI team members with annotator access
- transfer or add ownership to Appia after the Appia onboarding meeting
