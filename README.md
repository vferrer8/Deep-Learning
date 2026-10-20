# Deep Learning: Image Classification for Robotic Picking

Functional prototype of the vision component of a warehouse picking robot. It uses transfer learning on a ResNet18 pretrained on ImageNet, with CIFAR-10 as a proxy dataset for the objects the robot would have to recognise.

Coursework for the MSc in Artificial Intelligence (UTAMED). The project has two parts: a design document (part 1, PDF) and its implementation (part 2, notebook).

## Approach

**Data**
- CIFAR-10 (10 classes), with images resized from 32×32 to 64×64.
- 5,000 training images held out for validation. The official 10,000-image test set is kept blind.
- Augmentation on the training set only: random horizontal flip and colour jitter (brightness, contrast, saturation).
- Normalisation with ImageNet statistics.

**Model**
- `resnet18` with `IMAGENET1K_V1` weights.
- The whole backbone is frozen. Only a new head is trained (`Dropout(0.3)` + `Linear(512, 10)`).
- That leaves **5,130 trainable parameters**.

**Training**
- `CrossEntropyLoss`, Adam (lr = 1e-3), 5 epochs, fixed seeds for reproducibility.

## Results

| Set | Accuracy |
|---|---|
| Validation (epoch 5) | 0.66 |
| **Test (10,000 images)** | **0.65** (macro F1 0.65) |

Per-class F1 on test ranges from about 0.51 to 0.72. Vehicles (ship, truck) score best, and animals that look alike at low resolution score worst. The notebook also includes learning curves, a confusion matrix and sample predictions.

**Reading the result.** The pipeline works end to end and the design is validated, but the accuracy is not yet good enough for a real logistics setting. Training was deliberately limited to 5 epochs with a frozen backbone to keep compute costs low. The natural next steps are:

- Unfreeze the last ResNet blocks and fine-tune them with a lower learning rate.
- Train for more epochs, with early stopping and a learning-rate schedule.
- Train on images from the actual warehouse instead of CIFAR-10.

## Repository contents

```
├── RAA_Parte1_VictorFerrer.pdf     # Part 1: design document (architecture and plan)
└── RAA_Parte2_VictorFerrer.ipynb   # Part 2: implementation, training and evaluation
```

> The notebook text and the design document are in Spanish.

## Tech stack

Python · PyTorch · torchvision · scikit-learn (metrics) · Matplotlib · Seaborn · Jupyter (GPU)

## Author

**Víctor Ferrer**, MSc in Artificial Intelligence, UTAMED
