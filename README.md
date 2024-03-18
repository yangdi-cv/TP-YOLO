# TP-YOLO: A Lightweight Attention-based Architecture for Tiny Pest Detection 
By Y. Di, S. L. Phung, J. Berg, J. Clissold and A. Bouzerdoum.

<img src="https://github.com/Ericdiii/TP-YOLO/blob/main/figure/TP-YOLO_framework.png?raw=true" height="180"/>

This repository is an official PyTorch implementation of [TP-YOLO](https://ieeexplore.ieee.org/document/10222202), published by ICIP 2023.

## Dependencies
```sh
pip install .
```

## Inference
```sh
yolo task=detect mode=predict model=weights/tp-yolo_kb.pt source=input/images save=True
```
<img src="https://github.com/Ericdiii/TP-YOLO/blob/main/figure/demo.png?raw=true" height="330"/>


## Training

Hyperparameters:
- Epochs: 450
- Batch size: 4
- Pre-train: None
</br>

Dataset:
| Dataset       | Paper | Class # | Image # | Instance # | 
|:-------------:| ----- |:-------:|:-------:|:----------:|
| Khapra beetle | [ICIP2023](https://ieeexplore.ieee.org/document/10222202) | 3 | 1,600 | 4,885 | 
| Pest24        | [CEA2020](https://www.sciencedirect.com/science/article/abs/pii/S0168169919324123)| 24 | 25,378 | 192,422 | 
</br>

Command:
```sh
yolo task=detect mode=train model=cfg/tp-yolo.yaml data=datasets/pestdata.yaml epochs=450 batch=4
```
</br>

 <img src="https://github.com/Ericdiii/TP-YOLO/blob/main/figure/curve.png?raw=true" height="440"/>

## Evaluation
```sh
yolo task=detect mode=val model=weights/tp-yolo_kb.pt data=datasets/pestdata_val.yaml
```

| Class                  | P    | R    | AP<sub>50 | AP   | 
| ----------------------:|:----:|:----:|:---------:|:----:|
| Khapra beetle (larvae) | 98.2 | 90.4 | 98.2      | 73.4 | 
| Khapra beetle (adult)  | 99.4 | 99.5 | 99.5      | 85.0 |
| Khapra beetle (skin)   | 99.0 | 97.2 | 99.2      | 75.7 |
| All                    | 98.8 | 95.7 | 98.9      | 78.0 |


## Citation
```
@inproceedings{tpyolo,
    title={TP-YOLO: A Lightweight Attention-based Architecture for Tiny Pest Detection},
    author={Yang Di and Son Lam Phung and Julian van den Berg and Jason Clissold and Abdesselam Bouzerdoum},
    booktitle={IEEE International Conference on Image Processing (ICIP)},
    pages={3394-3398},
    year={2023}
}
```
