# TP-YOLO: A Lightweight Attention-based Architecture for Tiny Pest Detection 

Submitted to ICIP2023 and under reviewing.

## Dependencies
```sh
pip install .
```

## Inference
```sh
yolo task=detect mode=predict model=weights/tp-yolo_kb.pt source=input/images save=True
```
<img src="https://github.com/Ericdiii/TP-YOLO/blob/main/figure/demo.png?raw=true" height="390"/>


## Training

```sh
yolo task=detect mode=train model=cfg/tp-yolo.yaml data=datasets/pestdata.yaml epochs=450 batch=4
```
| Dataset       | Paper | Class # | Image # | Instance # | Download |  
|:-------------:| ----- |:-------:|:-------:|:----------:| ---------|
| Khapra beetle | [ICIP2023]() | 3 | 1,600 | 4,885 | [Google Drive](https://drive.google.com/drive/folders/1d5AAjAsaas2aZZ5UGqI30eBaoaMEmU02?usp=drive_link) | 
| Pest24        | [CEA2020](https://www.sciencedirect.com/science/article/abs/pii/S0168169919324123)| 24 | 25,378 | 192,422 | [Google Drive](https://drive.google.com/drive/folders/18_YlUiLW15HndTIUs9BoKWd4C8bdRS_E?usp=drive_link) | 
 

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
