# DeSTSeg+

Official PyTorch implementation of [DeSTSeg+](https://www.engineeringvillage.com/app/doc/?docid=cpx_78d9dd0419ae8242edfM7a3d1017816338&pageSize=25&index=1&searchId=894a3dc7530e41108d4ff44baba65ee8&resultsCount=1&usageZone=resultslist&usageOrigin=searchresults&searchType=Quick) - ICIC-2025
## Datasets

We use the MVTec AD dataset for experiments. To simulate anomalous image, the Describable Textures Dataset (DTD) is also adopted in our work. 

## Installation

Please install the dependency packages using the following command by **pip**:

```
pip install -r requirements.txt
```

## Training and Testing

To get started, users can run the following command to train the model on all categories of MVTec AD dataset:

```
python train_old.py --gpu_id 0 --num_workers 16
```

Users can also customize some default training parameters by resetting arguments like `--bs`, `--lr_DeST`, `--lr_res`, `--lr_seghead`, `--steps`, `--DeST_steps`, `--eval_per_steps`, `--log_per_steps`, `--gamma` and `--T`.

To specify the training categories and the corresponding data augmentation strategies, please add the argument `--custom_training_category` and then add the categories after the arguments `--no_rotation_category`, `--slight_rotation_category` and `--rotation_category`. For example, to train the `screw` category and the `tile` category with no data augmentation strategy, just run the following command:

```
python train_old.py --gpu_id 0 --num_workers 16 --custom_training_category --no_rotation_category screw tile
```

To test the performance of the model, users can run the following command:

```
python eval_new.py --gpu_id 0 --num_workers 16
```

## Pretrained Checkpoints

Download pretrained checkpoints [谷歌云盘](https://drive.google.com/drive/folders/1MqI-MTH8VyIVoDj33SrRNAfVbaCQ8Kbp?hl=zh-cn) and put the checkpoints under `<project_dir>/saved_model/`.

## Acknowledgements

This project is developed based on and inspired by the excellent work of the authors of [ml-destseg](https://github.com/apple/ml-destseg.git).  
We would like to sincerely thank the authors for open-sourcing their codebase, which provided an important foundation for this work.  
On top of their implementation, we further extended and improved the method to develop **DeSTSeg+**.


