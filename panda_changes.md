# Changes for Pandaset and 2DPASS

#### Requirements

Same as 2DPASS plus:

* json
* gzip
* numpy-quaternion
* pandas

Also specified in requirements.txt

### Usage

    python3 main.py --config config/2DPASS-large-pandaset.yaml --gpu 0 --test --num_vote 1 --checkpoint 2dpass_model/best_model.ckpt --submit_to_server

Set correct configuration file, model checkpoint and --submit_to_server flag in order to save predictions

### Dataloader

* pc_dataset.py
    * add packages gzip, json, pickle, quaternion
    * add getPoses function
    * add absoluteFilePathsLidar function
    * add absoluteFilePathsLabel function
    * remove some lines regarding images since we don't use them in inference
    * add label map from pandaset to kitti format
    * add Pandaset class

* dataset.py
    * remove lines about 2d data loading and augmentation
    * remove images data in data_dict object

* panda-kitti.yaml: label configuration file in pandaset

* 2DPASS-large-pandaset.yaml: configuration file for pandaset dataset

* 2DPASS-pandaset.yaml: configuration file for pandaset dataset

* 2DPASS-semantickitti.yaml: changed dataset path

* 2DPASS-large-semantickitti.yaml: changed dataset path

### Inference

* base_model.py: changed output predictions path

### Other

* metric_util.py: changed metric import