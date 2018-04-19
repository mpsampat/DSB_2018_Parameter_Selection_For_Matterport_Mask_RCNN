|                             |                |                |      |      |
| --------------------------- | -------------- | -------------- | ---- | ---- |
| LEARNING_RATE               | 1e-03          | 1e-03          |      |      |
| RPN_ANCHOR_RATIOS           | [0.5, 1, 2]    | [0.5, 1, 2]    |      |      |
| USE_MINI_MASK               | True           | True           |      |      |
| MINI_MASK_SHAPE             | (56,56)        | (56,56)        |      |      |
| GPU_COUNT                   | 1              | 1              |      |      |
| IMAGES_PER_GPU              | 2              | 1              |      |      |
| STEPS_PER_EPOCH             | 312            | 598            |      |      |
| VALIDATION_STEPS            | 35             | 66             |      |      |
| BACKBONE                    | resnet101      | resnet101      |      |      |
| NUM_CLASSES                 | 1+1            | 1+1            |      |      |
| IMAGE_MIN_DIM               | 512            | 512            |      |      |
| IMAGE_MAX_DIM               | 512            | 512            |      |      |
| IMAGE_PADDING               | True           | True           |      |      |
| RPN_ANCHOR_SCALES           | 8,16,32,64,128 | 8,16,32,64,128 |      |      |
| BACKBONE_STRIDES            | 4,8,16,32,64   | 4,8,16,32,64   |      |      |
| RPN_TRAIN_ANCHORS_PER_IMAGE | 320            | 320            |      |      |