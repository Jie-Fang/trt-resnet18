# Quick start

1. Extract sampleUffResnet.tar.gz to path/to/TensorRT/samples/
2. Extract resnet.tar.gz to path/to/TensorRT/data
3. Test:
  ```
	 cd path/to/TensorRT/data/resnet
   ./sample_uff_resnet --int8
  ```
  
# File description

## sampleUffResnet

- samleUffResnet.cpp: main source file
- BatchStreamPPM.h: read images function
- frozen_graph.pb: resnet18 freeze graph obtained from your tensorflow model
- frozen_graph.pb.uff: obtained from frozen_graph.pb
- tf_resnet_config.py: some configuration for generating frozen_graph.pb.uff


## resnet

- frozen_graph.pb.uff: copy from sampleUffResnet
- sample_uff_resnet & sample_uff_resnet_debuf: copy from path/to/TensorRT/bin and they are generated from Makefile in sampleUffResnet
- CalibrationTableResnet: for TRT int8 mode, generated from 500 images in the Imagenet folder. Here I place it in the folder, you can delete it, then when running quick test, it will be gennerated automatically.
- Imagenet: stores some proccessed images for testing and calibration.
  
  
# Some commands:

## generate uff file

```
convert-to-uff tensorflow --input-file frozen_graph.pb -p tf_resnet_config.py
```
