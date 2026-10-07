
---

## 📄 docs/EVALUATION.md

```markdown
# Evaluation

## Metrics

| Metric | Formula | Purpose |
|--------|---------|---------|
| Accuracy | (TP+TN)/N | Overall correctness |
| Precision | TP/(TP+FP) | Minimize false positives |
| Recall | TP/(TP+FN) | Minimize false negatives |
| F1-Score | 2·P·R/(P+R) | Balance P & R |
| ROC-AUC | Area under curve | Threshold-independent score |

## Framework Comparison

| Aspect | Keras | PyTorch |
|--------|-------|---------|
| Prototyping speed | Fast | Moderate |
| Debugging | Abstracted | Transparent |
| Flexibility | Moderate | High |
| Deployment | TF Serving, TFLite | TorchScript, ONNX |
| Community | Industry | Research |

## Model Comparison

| Model | Params | Train Time (5 epochs) |
|-------|--------|-----------------------|
| ViT-Base (12 heads, 768 dim, 12 layers) | 85.9M | 19.24s |
| ViT-Small (4 heads, 256 dim, 4 layers) | 3.7M | 11.24s |
| Speedup | — | 1.71× |

## Selection Guide

- **Production, fast deployment** → Keras CNN
- **Research, custom architectures** → PyTorch CNN-ViT
- **Strong global context needed** → Hybrid CNN-ViT
