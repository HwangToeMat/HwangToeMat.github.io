---
title: Football play detection with Tensorflow API
image: https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/result3.png?raw=true
description: >
 We used ssdlite_mobilenet_v2_coco[Download Link] to analyze soccer games in real time because we need fast computing speed. But as you can see in the image below, our model(Left) performs very well even though it is a lightweight model.
author: author1
order: 3
layout: post
---

<a href="https://github.com/HwangToeMat/Tensorflow-API-HTM/tree/master/2.object_detection">[main code]</a>
## Data Download
 
**EasyDownloader <a href="https://github.com/HwangToeMat/Open-Images_EasyDownload">[GitHub Link]</a>**

Download images that have both 'football category' and 'personal category' in each image with the code below.
```
python ../0.Open-Images_EasyDownload/EasyDownloader.py 
    --category "Football" 
    --category "Person" 
    --type "inter
```
**tf_record**

Create tf_record file with Football_label_map.pbtxt and create_Football_tf_record.py

**label_map**
```
item {
  name: "/m/01226z"
  id: 1
  display_name: "Football"
}
item {
  name: "/m/01g317"
  id: 2
  display_name: "Person"
}
```
**usage**
```
python create_Football_tf_record.py
    --data_dir=../0.Open-Images_EasyDownload/train_data/images
    --output_dir=./Football_tf_record
    --label_map_path=./Football_label_map.pbtxt
```
## Train
### model

| Model name        | Speed (ms)          | COCO mAP|
| ------------- |:-------------:| -----:|
| mask_rcnn_resnet101_atrous_coco      | 470      | 33 |
| faster_rcnn_resnet101_coco      | 106      | 32 |
| ssd_mobilenet_v2_coco      | 31      | 22 |
| **ssdlite_mobilenet_v2_coco**      | **27**      | **22** |

We used **ssdlite_mobilenet_v2_coco<a href="http://download.tensorflow.org/models/object_detection/ssdlite_mobilenet_v2_coco_2018_05_09.tar.gz">[Download Link]</a>** to analyze soccer games in real time because we *need fast computing speed.*

## Result
### graph
**DetectionBoxes_Precision**

<img src="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/DetectionBoxes_Precision.png?raw=true" style="max-width:100%;">

**DetectionBoxes_Recall**

<img src="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/DetectionBoxes_Recall.png?raw=true" style="max-width:100%;">

### Image(Left : our model / Right : ground truth )

<img src="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/result1.png?raw=true" alt="result1" style="max-width:100%;">
<img src="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/result2.png?raw=true" alt="result2" style="max-width:100%;">
<img src="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/result3.png?raw=true" alt="result3" style="max-width:100%;">

## Conclusion
**As you can see in the image of the result, ground truth recognizes people as one, but in our model, we see one by one.**
