# tfrecord
Custom Dataset to tfrecord

## Environment

Apple M1
python 3.10
tensorflow 2.18

## 1. Object Detection Images, Labels(xml) structure change

I used "LabelImg" tool

You should change data structure format like "PASCAL VOC2012"

 Dataset
│   └── VOC2012
│       ├── Annotations
│       │   ├── sample.xml # <filename> tag must same JPEGImages's filename
│       │   └── sample2.xml
│       ├── ImageSets
│       │   └── Main
│       │       ├── Mold_train.txt # change class name into your dataset class information
│       │       └── Mold_val.txt
│       ├── images
│       │   └── JPEGImages
│       │       ├── sample.jpg
│       │       └── sample2.jpg
│       └── label_map.json # label information, check name and number

## 2. run (check date : 24/12/12)

!python functions/create_pascal_tfrecord.py \
  --data_dir="Dataset/VOC2012" \
  --set=train \
  --year=VOC2012 \
  --annotations_dir="Annotations" \
  --output_path="results/results" \
  --num_shards=10 \
  --label_map_json_path="Dataset/VOC2012/label_map.json"

if sucess, results folder have tfrecords and .json file

** functions from https://github.com/google/automl