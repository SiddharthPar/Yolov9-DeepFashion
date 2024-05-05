## Training
Data Preparation

-Creating smaller dataset of 500 images in 7:2:1 split


``` shell
python3 /mnt/DATA/EE22M204/Desktop/yolov9-main/deep_fashion/annotations/data.py
```
-Seperating out images in the json files
``` shell
python3 /mnt/DATA/EE22M204/Desktop/yolov9-main/deep_fashion/annotations/image_fold.py
```
-Converting data to yolo format
```shell
python3 /mnt/DATA/EE22M204/Desktop/yolov9-main/deep_fashion/annotations/seg_data.py
```


Multi-GPU Training 

``` shell
python segment/train_dual.py --workers 8 --device 1,2 --batch 8  --data /mnt/DATA/EE22M204/Desktop/sidharth_data/deep_fashion/coco.yaml --img 640 --cfg /mnt/DATA/EE22M204/Desktop/yolov9-main/data/yolov9-c-dseg.yaml --weights '' --name yolov9-c-dseg --hyp hyp.scratch-high.yaml --no-overlap --epochs 50 --close-mosaic 10
```
Training Results

<div align="center">
    <a href="./">
        <img src="yolov9-main/runs/train-seg/yolov9-c-dseg30/val_batch2_labels.jpg" width="49%"/>
    </a>
</div>


| Box_loss | Seg_loss | obj_loss | cls_loss | mAP_0.5(B) | mAP_0.5:0.95(B) | precision(B) | recall(B) | mAP_0.5(B)) | mAP_0.5:0.95(B) |
|----------|----------|----------|----------|------------|-----------------|--------------|-----------|-------------|-----------------|
| 2.8349   | 1.5734   | 4.4038   | 3.7451   | 0.789      | 0.456           |  0.16666     |  0.12483  | 0.11159     | 0.036629        |

