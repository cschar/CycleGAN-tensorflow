<!-- <img src='imgs/horse2zebra.gif' align="right" width=384> 

<br><br><br>
-->

## basic flow
```


#Train first
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=horse2zebra --continue_train=True --print_freq=50

#turn to frames
youtube-dl <video_with_horses> -o test.mp4
ffmpeg -i test.mp4 -f image2 out%06d.jpg 
ffmpeg -i myvideo.avi -ss 00:00:10 -vf fps=1/60 img%03d.jpg   # frame every minute, strating at 10 s

#Optional scaling 256x256,  not sure training images need this...
# but other datasets already were scaled down to 256
ffmpeg -i youtube_out.mp4 -f image2 -vf scale=256:256 out_%06d.jpg

backup horse2zebra/testA
copy frames to horse2zebra/testA

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=horse2zebra --phase=test --test_dir=./test5

#STich together in blender or ffmpeg
cd test5
ffmpeg -i BtoA_image%06d.jpg out.mp4  #make sure no '-' character in name


#voila, watch cycle GAN video



Grab video time slice
ffmpeg -ss 3:59:10 -i $(youtube-dl -f 22 -g 'https://www.youtube.com/watch?v=XXXXXXXX') \
-t 3:06:00

```

#train with different image size output
```
#get frames larger than 512

#put in /datasets/your_dataset/   folders trainA trainB testA testB

CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=your_dataset --load_size=514 --fine_size=512

ffmpeg -i $(youtube-dl -f 22 -g 'https://www.youtube.com/watch?v=hONkNECf6aE
') rubgy_out.mp4
```


# CycleGAN

Tensorflow implementation for learning an image-to-image translation **without** input-output pairs.
The method is proposed by [Jun-Yan Zhu](https://people.eecs.berkeley.edu/~junyanz/) in 
[Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networkssee](https://arxiv.org/pdf/1703.10593.pdf). 
For example in paper:

<img src="imgs/teaser.jpg" width="1000px"/>

<!--
## Applications
### Monet Paintings to Photos
<img src="imgs/painting2photo.jpg" width="1000px"/>

### Collection Style Transfer
<img src="imgs/photo2painting.jpg" width="1000px"/>

### Object Transfiguration
<img src="imgs/objects.jpg" width="1000px"/>

### Season Transfer
<img src="imgs/season.jpg" width="1000px"/>

### Photo Enhancement: iPhone photo to DSLR photo
<img src="imgs/photo_enhancement.jpg" width="1000px"/>

-->

## Update Results
The results of this implementation:

- Horses -> Zebras <br>
<img src="imgs/n02381460_510.jpg" width="200px"/> <img src="imgs/AtoB_n02381460_510.jpg" width="200px"/> <img src="imgs/n02381460_4530.jpg" width="200px"/> <img src="imgs/AtoB_n02381460_4530.jpg" width="200px"/> <img src="imgs/n02381460_4660.jpg" width="200px"/> <img src="imgs/AtoB_n02381460_4660.jpg" width="200px"/> <img src="imgs/n02381460_8980.jpg" width="200px"/> <img src="imgs/AtoB_n02381460_8980.jpg" width="200px"/>

- Zebras -> Horses <br>
<img src="imgs/n02391049_1760.jpg" width="200px"/> <img src="imgs/BtoA_n02391049_1760.jpg" width="200px"/> <img src="imgs/n02391049_3070.jpg" width="200px"/> <img src="imgs/BtoA_n02391049_3070.jpg" width="200px"/> <img src="imgs/n02391049_5100.jpg" width="200px"/> <img src="imgs/BtoA_n02391049_5100.jpg" width="200px"/> <img src="imgs/n02391049_7150.jpg" width="200px"/> <img src="imgs/BtoA_n02391049_7150.jpg" width="200px"/>

You can download the pretrained model from [this url](https://1drv.ms/u/s!AroAdu0uts_gj5tA93GnwyfRpvBIDA)
and extract the rar file to `./checkpoint/`.


## Prerequisites
- tensorflow r1.1
- numpy 1.11.0
- scipy 0.17.0
- pillow 3.3.0

## Getting Started
### Installation
- Install tensorflow from https://github.com/tensorflow/tensorflow
- Clone this repo:
```bash
git clone https://github.com/xhujoy/CycleGAN-tensorflow
cd CycleGAN-tensorflow
```

### Train
- Download a dataset (e.g. zebra and horse images from ImageNet):
```bash
bash ./download_dataset.sh horse2zebra
```
- Train a model:
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=horse2zebra
```
- Use tensorboard to visualize the training details:
```bash
tensorboard --logdir=./logs
```

### Test
- Finally, test the model:
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=horse2zebra --phase=test --which_direction=AtoB
```

## Training and Test Details
To train a model,  
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=/path/to/data/ 
```
Models are saved to `./checkpoints/` (can be changed by passing `--checkpoint_dir=your_dir`).  

To test the model,
```bash
CUDA_VISIBLE_DEVICES=0 python main.py --dataset_dir=/path/to/data/ --phase=test --which_direction=AtoB/BtoA
```

## Datasets
Download the datasets using the following script:
```bash
bash ./download_dataset.sh dataset_name
```
- `facades`: 400 images from the [CMP Facades dataset](http://cmp.felk.cvut.cz/~tylecr1/facade/).
- `cityscapes`: 2975 images from the [Cityscapes training set](https://www.cityscapes-dataset.com/).
- `maps`: 1096 training images scraped from Google Maps.
- `horse2zebra`: 939 horse images and 1177 zebra images downloaded from [ImageNet](http://www.image-net.org/) using keywords `wild horse` and `zebra`.
- `apple2orange`: 996 apple images and 1020 orange images downloaded from [ImageNet](http://www.image-net.org/) using keywords `apple` and `navel orange`.
- `summer2winter_yosemite`: 1273 summer Yosemite images and 854 winter Yosemite images were downloaded using Flickr API. See more details in our paper.
- `monet2photo`, `vangogh2photo`, `ukiyoe2photo`, `cezanne2photo`: The art images were downloaded from [Wikiart](https://www.wikiart.org/). The real photos are downloaded from Flickr using combination of tags *landscape* and *landscapephotography*. The training set size of each class is Monet:1074, Cezanne:584, Van Gogh:401, Ukiyo-e:1433, Photographs:6853.
- `iphone2dslr_flower`: both classe of images were downlaoded from Flickr. The training set size of each class is iPhone:1813, DSLR:3316. See more details in our paper.


## Reference
- The torch implementation of CycleGAN, https://github.com/junyanz/CycleGAN
- The tensorflow implementation of pix2pix, https://github.com/yenchenlin/pix2pix-tensorflow
