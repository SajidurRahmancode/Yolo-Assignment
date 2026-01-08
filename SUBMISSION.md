# Submission Package — Bangladeshi Taka Detection & Recognition

This document enumerates the deliverables for item 16, with concrete locations in this project.

---

## 1) Trained Model Weights

- Detector (YOLOv11s, fine-tuned)
  - Best weights: `/home/meow/Yolo Assignment/runs_bdt/yolo11s_bdt_detection/weights/best.pt`
  - Last weights: `/home/meow/Yolo Assignment/runs_bdt/yolo11s_bdt_detection/weights/last.pt`
  - Training artifacts (metrics, args):
    - `/home/meow/Yolo Assignment/runs_bdt/yolo11s_bdt_detection/`

- Denomination Classifier (ResNet18)
  - Best checkpoint: `/home/meow/Yolo Assignment/runs_bdt/recognition/best_cls.pt`
  - Contains: model state dict and class list.

> Note: If you trained additional runs, they appear under `/home/meow/Yolo Assignment/runs_bdt/` as `yolo11n_bdt_detection*` (older experiments).

---

## 2) Sample Inference Images with Bounding Boxes

- Ultralytics validation visualizations (with detections overlaid):
  - `/home/meow/Yolo Assignment/runs/detect/val/`
  - `/home/meow/Yolo Assignment/runs/detect/val2/`

- Two-stage detection + denomination overlays (produced from the notebook visualization):
  - Generated inline in the notebook (see Assignment.ipynb, two-stage inference cell).
  - If saved during runs, they will appear under a `runs/detect/predict*` folder. For permanent copies, export from the notebook or run `model.predict(..., save=True, project="runs/detect", name="predict_denominations")`.

---

## 3) GitHub or Zipped Project Folder Contents

### Dataset Structure

- Detection (YOLO format):
  - Root: `/home/meow/Yolo Assignment/BDT images/Detection/`
  - Config: `/home/meow/Yolo Assignment/BDT images/Detection/data.yaml`
  - Splits:
    - Train images: `/home/meow/Yolo Assignment/BDT images/Detection/train/images/`
    - Train labels: `/home/meow/Yolo Assignment/BDT images/Detection/train/labels/`
    - Val images: `/home/meow/Yolo Assignment/BDT images/Detection/validation/images/`
    - Val labels: `/home/meow/Yolo Assignment/BDT images/Detection/validation/labels/`
    - Test images: `/home/meow/Yolo Assignment/BDT images/Detection/test/images/`
    - Test labels: `/home/meow/Yolo Assignment/BDT images/Detection/test/labels/`

- Recognition (image classification):
  - Root: `/home/meow/Yolo Assignment/BDT images/Recognition/`
  - Splits (class-subfoldered):
    - Train: `/home/meow/Yolo Assignment/BDT images/Recognition/train/`
    - Val: `/home/meow/Yolo Assignment/BDT images/Recognition/validation/`
    - Test: `/home/meow/Yolo Assignment/BDT images/Recognition/test/`

### Annotation Files

- YOLO labels (`.txt`, normalized `cls cx cy w h`) under:
  - Train labels: `/home/meow/Yolo Assignment/BDT images/Detection/train/labels/`
  - Val labels: `/home/meow/Yolo Assignment/BDT images/Detection/validation/labels/`
  - Test labels: `/home/meow/Yolo Assignment/BDT images/Detection/test/labels/`

### Training and Evaluation Scripts

- Primary notebook (setup, EDA, training, evaluation, two-stage pipeline):
  - `/home/meow/Yolo Assignment/Assignment.ipynb`

- Detector training run directory (Ultralytics artifacts):
  - `/home/meow/Yolo Assignment/runs_bdt/yolo11s_bdt_detection/`
    - `weights/best.pt`, `weights/last.pt`
    - training logs, results, args/configs

- Classifier checkpoint directory:
  - `/home/meow/Yolo Assignment/runs_bdt/recognition/best_cls.pt`

---

## Optional Reproduction Notes

- Activate environment:
  ```bash
  source "/home/meow/.venv/bin/activate"
  ```
- Open the notebook and run cells in order to reproduce training and evaluation.
- For batch export of two-stage predictions to disk, set `save=True` in `model.predict()` and specify `project`/`name`.
