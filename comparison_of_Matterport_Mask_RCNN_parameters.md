#### Overview

1. This document compares the Matterport Mask_RCNN parameters used by various contestants for the 2018 DSB. 
2. Note that since Waleed made new updates to Mask_RCNN there are two code bases used by the contestants. These are listed below.
   1. Type 1: Older Mask_RCNN_code from here: [https://github.com/killthekitten/kaggle-ds-bowl-2018-baseline](https://github.com/killthekitten/kaggle-ds-bowl-2018-baseline)
   2. Type 2: latest Mask_RCNN_code from here: https://github.com/matterport/Mask_RCNN

#### Comparison of Matterport Mask_RCNN parameters

| PARAMETERS                          | Mehul                    | Zheng          | Waleed              | Avi                   |
| ----------------------------------- | ------------------------ | -------------- | ------------------- | --------------------- |
| Public_LB Score                     | 0.472                    | 0.489          | 0.476               | **0.532**             |
| Private_LB Score                    | 0.472                    | **0.590**      | 0.433               | **0.560**             |
| Private_LB Score (with stage1 test) | 0.489                    | ?              | ?                   | ?                     |
| CodeBase                            | Type-2                   | Type-1         | Type2               | Type 1?               |
| MEAN_PIXEL                          | [0 0 0]                  | [0 0 0]        | [43.53 39.56 48.22] | [123.7, 116,8, 103,9] |
| LEARNING_RATE                       | 1e-03                    | 1e-03          | 1e-03               | 1e-02                 |
| LEARNING_SCHEDULE                   | 8 epochs                 |                | ?                   |                       |
| RPN_ANCHOR_RATIOS                   | [0.5, 1, 2]              | [0.5, 1, 2]    | [0.5, 1, 2]         | [0.5, 1, 2]           |
| USE_MINI_MASK                       | True                     | True           | True                | **False**             |
| MINI_MASK_SHAPE                     | (56,56)                  | (56,56)        | (56,56)             | ?                     |
| GPU_COUNT                           | 1                        | 1              | ?                   | ?                     |
| IMAGES_PER_GPU                      | 2                        | 1              | 6                   | ?                     |
| STEPS_PER_EPOCH                     | 312                      | 598            | ?                   | ?                     |
| VALIDATION_STEPS                    | 35                       | 66             | ?                   | ?                     |
| BACKBONE                            | resnet101                | resnet101      | resnet50            | ?                     |
| NUM_CLASSES                         | 1+1                      | 1+1            | 1+1                 | 1+1                   |
| IMAGE_MIN_DIM                       | 512                      | 512            | 512                 | 512                   |
| IMAGE_MAX_DIM                       | 1024                     | 512            | 512                 | 1024                  |
| IMAGE_PADDING                       | True                     | True           | Removed             |                       |
| RPN_ANCHOR_SCALES                   | 8,16,32,64,128           | 8,16,32,64,128 | 8,16,32,64,128      |                       |
| RPN_ANCHOR_STRIDE                   |                          |                |                     | 1                     |
| BACKBONE_STRIDES                    | 4,8,16,32,64             | 4,8,16,32,64   |                     |                       |
| RPN_TRAIN_ANCHORS_PER_IMAGE         | 320                      | 320            | **64**              | 250                   |
| IMAGE_MIN_SCALE                     | 0                        | NA             | **2**               |                       |
| IMAGE_RESIZE_MODE                   | square                   | NA             | crop                | NA                    |
| RPN_NMS_THRESHOLD                   | ?                        | 0.7            |                     |                       |
| DETECTION_MIN_CONFIDENCE            | ?                        | 0.7            |                     | 0.8                   |
| DETECTION_NMS_THRESHOLD             | ?                        | 0.7            |                     | 0.3                   |
| TRAIN_ROIS_PER_IMAGE                | ?                        | 600            |                     |                       |
| DETECTION_MAX_INSTANCES             |                          | ?              | ?                   | 500                   |
| MAX_GT_INSTANCES                    |                          | ?              | ?                   | 500                   |
| init_with                           | coco                     | coco           | ?                   |                       |
| DATA_AUGMENTATION                   | flip-lr + gaussian noise |                | flip-lr + flip-up   | rotate zoom, noise    |