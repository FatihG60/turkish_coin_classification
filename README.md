# Detection of Turkish Coins using YOLOv5

The problem is to detect turkish coins and count the coin in each image accurately.<br>

There are 5 Turkish coins labeled from 0 to 4. Here are the classes<br>

* 0 is 5 kuruş <br>
* 1 is 10 kuruş <br>
* 2 is 25 kuruş <br>
* 3 is 50 kuruş <br>
* 4 is 1 lira <br>

## Data Collecting 
First, we took pictures of different numbers of coins and from different angles to detect the coins. <br>
After we used [LabelImg](https://github.com/heartexlabs/labelImg) and yolo format to label each image. <br>
We added few examples of images that we took. All the images and annotations can be found under [data](https://github.com/ynsgkturk/CoinDetectionProject/tree/main/data) folder. <br>

<p float="left">
  <img src="/data/train/images/IMG_000086.jpg" width="300" />
  <img src="/data/train/images/IMG_000178.jpg" width="300" /> 
  <img src="/data/train/images/IMG_000587.jpg" width="300" />
</p>

## Training the YOLOv5 Model Using PyTorch

[Yolov5](https://github.com/ultralytics/yolov5) is a higly efficient and accurate model among the other object detection models. 

| Algorithm     |  Inference Time(sec) | mAP |
| ------------- | ------------- | --------- |
| DETR-DC5 | 0.097  | 49.5 |
| YOLOv5x6  | 0.045  | 55 |
| Faster R-CNN | ~0.2 | 48.1 | 

Table 1. Comparison of Object Detection Models ([YoloV5](https://pytorch.org/hub/ultralytics_yolov5/), [Faster R-CNN](https://github.com/ShaoqingRen/faster_rcnn), [DETR](https://github.com/facebookresearch/detr))

To train the model with our dataset we used original documentation. [Train Custom Data](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data)

## Data Augmentation with Albumentations

[Albumentations](https://albumentations.ai/) is a computer vision tool that boosts the performance of deep convolutional neural networks.<br>

We used few data augmentation methods to enlarge our dataset.
* Random Brightness Contrast
* Gauss Noise 
* ISO Noise

For more detail you can check the [augmentaiton file](https://github.com/ynsgkturk/CoinDetectionProject/blob/main/data_augmentation.py) and [Bounding Box Augmentation documentation](https://albumentations.ai/docs/getting_started/bounding_boxes_augmentation/).

## Contributors ✨
Thanks go to these people.

<a href="https://github.com/FatihGovtas/turkish_coin_classification/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=ynsgkturk/CoinDetectionProject" />
</a>

Made with [contrib.rocks](https://contrib.rocks).


# turkish_coin_classification
**-->** Türk madeni paralarının tanınması (5, 10, 25, 50 kuruş ve 1 tl) için YOLOV5 ağı kullanıldı.
### Proje Aşamaları	
1)	Veri seti oluşturulması: Çeşitli açılardan para fotoğrafları çekildi(1147). 
2)	Etiketleme: Etiketleme için labelImg programı kullanılarak veriler etiketlendi.
3)	Eğitim: Verilerin %80 eğitim (917) %20 test(230) olacak şekilde ayrıldı. Colab üzerinden ağ eğitimini gerçekleştirildi. Eğitim 30 epoch olarak gerçekleştirildi.
### Model Sonuçları
<img src="https://user-images.githubusercontent.com/74897177/181749841-b2f463a3-5533-4cf5-ba12-7703f7cd0087.png" width=300 height=400>                                <img src="https://user-images.githubusercontent.com/74897177/181750751-b34bd613-bc96-47e8-808a-4f70e9da2dc2.png" width=300 height=400>
