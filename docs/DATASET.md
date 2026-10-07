
## Details

| Property | Value |
|----------|-------|
| Total images | 600 |
| Classes | 2 (binary) |
| Images per class | 300 |
| Resolution | 64 × 64 |
| Channels | RGB (3) |
| Format | JPEG |

## Class Definitions

- **class_0_non_agri** — Urban, barren, water, industrial land
- **class_1_agri** — Crops, vegetation, farmland, orchards

## Preprocessing

- Resize to 64 × 64
- Normalize with ImageNet statistics: `mean=[0.485, 0.456, 0.406]`, `std=[0.229, 0.224, 0.225]`
- Convert to tensor / float array

## Augmentation (training only)

- Random horizontal flip (p=0.5)
- Random vertical flip (p=0.2)
- Random rotation (±45°)
- Color jitter (brightness, contrast, saturation ±20%)

## Loading Strategies

### Sequential (chosen)
- File paths stored in a list
- Batches loaded on demand
- Parallel workers mitigate disk I/O
- Memory usage scales with batch size, not dataset size

### Bulk (alternative)
- All images loaded into RAM at start
- Fastest random access
- Memory scales with dataset size — impractical at scale
