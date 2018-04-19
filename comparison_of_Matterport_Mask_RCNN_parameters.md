| Parameter | Mehul | Zheng |
| LEARNING_RATE | 1e-3 | 1e-3 |
| RPN_ANCHOR_RATIOS | [0.5, 1, 2] |  same | 
| USE_MINI_MASK     | True | same |
| MINI_MASK_SHAPE   | (56,56) | same |
| GPU_COUNT         | 1 | 1 |
| IMAGES_PER_GPU    | 2 | 1 |
| STEPS_PER_EPOCH   | 312 |  598 |
| VALIDATION_STEPS  | 35 | 66 |
| BACKBONE          | resnet101 | resnet101 |
| NUM_CLASSES       | (1+1) | 1+1  |
| IMAGE_MIN_DIM     | 512   | 512  |
| IMAGE_MAX_DIM     |  512  | 512  |
| IMAGE_PADDING     | True  | True |
| RPN_ANCHOR_SCALES | 8,16,32,64,128 | same |
| BACKBONE_STRIDES  | 4,8,16,32,64   |  same |
RPN_TRAIN_ANCHORS_PER_IMAGE | 320 | same |
