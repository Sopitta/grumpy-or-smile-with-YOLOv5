# Grumpy or smiley face detection with YOLOv5

This project applies YOLOv5 from https://github.com/ultralytics/yolov5 to detect wheter a face (especially my face :D) is grumpy or smiley. 
The code follows and adapts from https://www.youtube.com/watch?v=tFNJGim3FXw by Nicholas Renotte.
## Pretrianed model

clone YOLOv5 repo and download the model which is readily available in pytorch 

```bash
git clone https://github.com/ultralytics/yolov5
```


## Collect a dataset

Follow create_dataset.ipynb

## Label the images

Before continue, make sure that the folder /data/labels exists.
1. Clone labelImg repo

    ```bash
    git clone https://github.com/tzutalin/labelImg

    cd labelImg

    pyrcc5 -o libs/resources.py resources.qrc
    ```
2. Open cmd in the project directory. 
3. run the command

    ```bash
    cd labelIMG
    python labelIMG.py
    ```
4. labelImg window will pop up, label all the images in data/images ans saved the labels to data/labels. make sure to save labels in yolo format.
    
## Label the images

![LabelImg](https://github.com/Sopitta/grumpy-or-smile-with-YOLOv5/blob/main/image/labelImg.PNG)

1. Set Open Dir to be the /data/images
2. Change save dir to /data/labels
3. Change the labelling for mat on the left panel to YOLO format.

## Train the model on custom dataset

```bash
cd yolov5 #go to yolov5 directory
python train.py --img 320 --batch 16 --epochs 500 --data dataset.yaml --weights yolov5s.pt --workers 1
```

## Results

Testing the trained model with unseen live webcame

![Grumpy face](https://github.com/Sopitta/grumpy-or-smile-with-YOLOv5/blob/main/image/grumpy_test.PNG)

![Smiley face](https://github.com/Sopitta/grumpy-or-smile-with-YOLOv5/blob/main/image/smile_test.PNG)
