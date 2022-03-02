# Pretrained TF to Pytorch

[Official TF Repo](https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet)
[Official TF Repo Snapshot](https://github.com/mingxingtan/efficientnet)

## Usage

1. Download TF checkpoint

```
export MODEL=efficientnet-b0
wget https://storage.googleapis.com/cloud-tpu-checkpoints/efficientnet/${MODEL}.tar.gz

tar zxf ${MODEL}.tar.gz

wget https://upload.wikimedia.org/wikipedia/commons/f/fe/Giant_Panda_in_Beijing_Zoo_1.JPG -O panda.jpg
wget https://storage.googleapis.com/cloud-tpu-checkpoints/efficientnet/eval_data/labels_map.txt

python eval_ckpt_main.py --model_name=$MODEL --ckpt_dir=$MODEL --example_img=panda.jpg --labels_map_file=labels_map.txt
```


Please refer to the following colab for more instructions on how to obtain and use those checkpoints.

  * [`eval_ckpt_example.ipynb`](eval_ckpt_example.ipynb): A colab example to load
 EfficientNet pretrained checkpoints files and use the restored model to classify images.


#     
2. Run `convert.py`

```
python3 convert.py -h
usage: convert.py [-h] [--model MODEL] --tf_weight TF_WEIGHT
                  [--pth_weight PTH_WEIGHT]

TF EfficientNet to Pytorch EfficientNet

optional arguments:
  -h, --help            show this help message and exit
  --model MODEL
  --tf_weight TF_WEIGHT
                        Directory name to save the TF chekpoint
  --pth_weight PTH_WEIGHT
                        output PyTorch model file name
```

Example
```
python3 convert.py --model efficientnet-b0 --tf efficientnet-b0 --pth b0

# if custom model
python3 convert_custom.py --model efficientnet-b0 --tf efficientnet-b0 --pth b0
```
