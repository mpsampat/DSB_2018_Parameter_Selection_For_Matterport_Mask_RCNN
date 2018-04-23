#### Overview

1. This document compares the Matterport Mask_RCNN parameters used by various contestants for the 2018 DSB. 
2. Note that since Waleed made new updates to Mask_RCNN there are two code bases used by the contestants. These are listed below.
   1. Type 1: Older Mask_RCNN_code from here: [https://github.com/killthekitten/kaggle-ds-bowl-2018-baseline](https://github.com/killthekitten/kaggle-ds-bowl-2018-baseline)
   2. Type 2: latest Mask_RCNN_code from here: https://github.com/matterport/Mask_RCNN

#### Comparison of Matterport Mask_RCNN parameters

| PARAMETERS                          | Mehul                    | Zheng          | Waleed              | Avi                   | Yueqi                 | Brian                  |
| ----------------------------------- | ------------------------ | -------------- | ------------------- | --------------------- | ----------------------|------------------------|
| Public_LB Score                     | 0.472                    | 0.489          | 0.476               | **0.532**             | 0.464                 | 0.449                  |
| Private_LB Score                    | 0.472                    | **0.590**      | 0.433               | **0.560**             | 0.534 (late)          | 0.499                  |
| Private_LB Score (with stage1 test) | 0.489                    | ?              | ?                   | ?                     |                       | 0.520 (late) *         |
| CodeBase                            | Type-2                   | Type-1         | Type2               | Type 1?               | Type-1                | Type-1                 |
| MEAN_PIXEL                          | [0 0 0]                  | [0 0 0]        | [43.53 39.56 48.22] | [123.7, 116,8, 103,9] | [123.7, 116,8, 103,9] | [42.18, 38.22, 46.82]  |
| LEARNING_RATE                       | 1e-03                    | 1e-03          | 1e-03               | 1e-02                 | 1e-03                 | 1e-04 / 1e-04          |
| LEARNING_SCHEDULE                   | 8 epochs                 |                | ?                   |                       | 60                    | 60 heads / 40 all      |
| RPN_ANCHOR_RATIOS                   | [0.5, 1, 2]              | [0.5, 1, 2]    | [0.5, 1, 2]         | [0.5, 1, 2]           | [0.5, 1, 2]           | [0.5, 1, 2]            |
| USE_MINI_MASK                       | True                     | True           | True                | **False**             | True                  | True                   |
| MINI_MASK_SHAPE                     | (56,56)                  | (56,56)        | (56,56)             | ?                     | (56,56)               | (56,56)                |
| GPU_COUNT                           | 1                        | 1              | ?                   | ?                     | 1                     | 8                      |
| IMAGES_PER_GPU                      | 2                        | 1              | 6                   | ?                     | 1                     | 2                      |
| STEPS_PER_EPOCH                     | 312                      | 598            | ?                   | ?                     | 200                   | 56 **                  |
| VALIDATION_STEPS                    | 35                       | 66             | ?                   | ?                     | 25                    | 9                      |
| BACKBONE                            | resnet101                | resnet101      | resnet50            | ?                     | resnet101             | resnet101              |
| NUM_CLASSES                         | 1+1                      | 1+1            | 1+1                 | 1+1                   | 1+1                   | 1+1                    |
| IMAGE_MIN_DIM                       | 512                      | 512            | 512                 | 512                   | 1024                  | 512 ***                |            |
| IMAGE_MAX_DIM                       | 1024                     | 512            | 512                 | 1024                  | 1024                  | 512                    |
| IMAGE_PADDING                       | True                     | True           | Removed             |                       | True                  | True                   |
| RPN_ANCHOR_SCALES                   | 8,16,32,64,128           | 8,16,32,64,128 | 8,16,32,64,128      |                       | 16, 32, 64, 128, 256  | 4, 8, 16, 32, 64       |
| RPN_ANCHOR_STRIDE                   |                          |                |                     | 1                     | 1                     | 1                      |
| BACKBONE_STRIDES                    | 4,8,16,32,64             | 4,8,16,32,64   |                     |                       | 4, 8, 16, 32, 64      | 4, 8, 16, 32, 64, 128  |
| RPN_TRAIN_ANCHORS_PER_IMAGE         | 320                      | 320            | **64**              | 250                   | 256                   | 320                    |
| IMAGE_MIN_SCALE                     | 0                        | NA             | **2**               |                       | NA                    | NA                     |
| IMAGE_RESIZE_MODE                   | square                   | NA             | crop                | NA                    | NA                    | NA                     |
| RPN_NMS_THRESHOLD                   | ?                        | 0.7            |                     |                       | 0.7                   | 0.7                    |
| DETECTION_MIN_CONFIDENCE            | ?                        | 0.7            |                     | 0.8                   | 0.85                  | 0.5                    |
| DETECTION_NMS_THRESHOLD             | ?                        | 0.7            |                     | 0.3                   | 0.3                   | 0.3                    |
| TRAIN_ROIS_PER_IMAGE                | ?                        | 600            |                     |                       | 512                   | 512                    |
| DETECTION_MAX_INSTANCES             |                          | ?              | ?                   | 500                   | 400                   | 1000                   |
| MAX_GT_INSTANCES                    |                          | ?              | ?                   | 500                   | 200                   | 512                    |
| init_with                           | coco                     | coco           | ?                   |                       | coco                  | coco                   |
| DATA_AUGMENTATION                   | flip-lr + gaussian noise |                | flip-lr + flip-up   | rotate zoom, noise    | flip-lr + crop +      | random augs 10% of time|
|                                     |                          |                |                     |                       |  gaussian noise +     | fliplr, gray(3ch stack)|
|                                     |                          |                |                     |                       |color style transfer   | random hsv color shift,|
|                                     |                          |                |                     |                       |                       | random noise (1 ch),   |
|                                     |                          |                |                     |                       |                       | blur with 5,5 kernel   |

Additional Notes
* My official Private LB score was 0.485 trained as noted with stage1 test and the weebly external data, without the weebly data
  (which I unfortunately did not choose for the contest) was 0.499, my late submission of 0.520 is same training regime but drops 
  masks that are < 15% of the average size of the masks for that image.  I had this code in my submission but turned it off at some
  point and never turned it back on.  I realized after stage1 but felt it would be cheating to turn it on again given I had uploaded
  my code with it turned off.  Leaving it on would have put me in medal territory.  (Live and learn!)
  
** I had 894 images in my final train set.  For images that scored badly or for which my kmeans clustering showed there were few of
   I repeated the same image multiple times in the train set.  So that the optimizer would see it more often.  Could have caused
   overfitting but didn't seem to.
   
*** My approach on image size was to train on the whole image so long as it fit inside the 512x512 box.  If the image was larger, then
    I took a random crop.  Resizing seemed to cause a lot of FP on small nuclei, so I wanted to avoid same.  I also took Waleed's
    suggestion to reduce the threshold in utils.unmold_mask() from 0.5 to 0.4
    
