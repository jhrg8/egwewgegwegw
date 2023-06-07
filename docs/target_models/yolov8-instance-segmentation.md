## YOLOv8 Instance Segmentation

[YOLOv8](https://github.com/ultralytics/ultralytics) is an open-source computer vision model by Ultralytics, the creators of YOLOv5 that supports object detection, classification, and instance segmentation. You can use `autodistill` to train a YOLOv8 object detection model on a dataset of labelled images generated by the base models that `autodistill` supports.

This document shows how to train an instance segmentation model using a base model supported by `autodiistill` and YOLOv8's instance segmentation functionality.

View our [YOLOv8](/target-models/yolov8/) page for information on how to train object detectino models.

### Installation

To use the YOLOv8 target model, you will need to install the following dependency:

```bash
pip3 install autodistill-yolov8
```

### Quickstart

```python
from autodistill_yolov8 import YOLOv8
target_model = YOLOv8("yolov8n-seg.pt")

# train model using images in `context_images_labeled` folder for 200 epochs
target_model.train("./context_images_labeled/data.yaml", epochs=200)

# export weights for future use
saved_weights = target_model.export(format="onnx")

# show performance metrics for your model
metrics = target_model.val()

# run inference on the new model
pred = target_model.predict("./context_images_labeled/train/images/dog-7.jpg", conf=0.01)
```