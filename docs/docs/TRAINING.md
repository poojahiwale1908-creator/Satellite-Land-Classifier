# Training

## Hyperparameters

| Parameter | Value |
|-----------|-------|
| Optimizer | Adam |
| Learning rate | 1e-3 (CNN) / 1e-4 (ViT) |
| Loss | Binary Cross-Entropy |
| Batch size | 16–32 |
| Epochs | 5–10 |
| Early stopping | Patience 3–5 |
| Checkpoint metric | val_accuracy |

## Training Loop

### Keras

```python
history = model.fit(
    train_generator,
    epochs=10,
    validation_data=validation_generator,
    callbacks=[checkpoint_callback, early_stopping],
    verbose=1
)
