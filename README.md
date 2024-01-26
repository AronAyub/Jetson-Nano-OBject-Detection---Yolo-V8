# Jetson Nano OBject Detection - Yolo V8
 Object Detection using Yolo V8

## Steps

- We have to install python3.8 to be able to install ultralytics YOLO v8

* Steps for python 3.8 installation:

```
sudo apt update
sudo apt upgrade
sudo apt install build-essential libssl-dev zlib1g-dev libncurses5-dev libncursesw5-dev libreadline-dev libsqlite3-dev libgdbm-dev libdb5.3-dev libbz2-dev libexpat1-dev liblzma-dev libffi-dev libc6-dev
```

```
Download the Python source code for version 3.8 from the official Python website. You can use the following command to download it directly to your Jetson Nano:
	wget https://www.python.org/ftp/python/3.8.12/Python-3.8.12.tar.xz

Extract the downloaded archive by running the following command:
tar -xf Python-3.8.12.tar.xz
cd Python-3.8.12
```

```
Configure the build process:
	./configure --enable-optimizations
	 
Build Python:
make -j4

```

```
Once the compilation is complete, you can install Python by running the following command:
	sudo make altinstall
	python3.8 --version
```

- Now come out from python3.8 folder and create a separate environment using python 3.8

```
python3.8 -m venv myenv                                                
source myenv/bin/activate
```
## Installing Ultralytics

```
pip install ultralytics
```
- show ultralytics version
```
pip show ultralytics
```

**We have to downgrade the torch and tourchvision packages to avoid errors**

 - [Pytorch Site][def2]
- First uninstall torch by

```
pip uninstall  torch
#then install this version
pip install torch==1.11
```
- Uninstall the current torchvision by
```
pip unistall torchvision
```
- Install the right torchvision

```
pip install torchvision 1.11
```

- *This process will analyze the images using YOLV8 in CPU and not GPU*

- To test the code, i am using VS code.

## Installing VS code
[check this online.][def]
- CLTR + SHIFT + P select compiler.

- then run the code below.

### For images

```
rom ultralytics import YOLO
model = YOLO("yolov8.pt")
results = model("directory/image.jpg", save = True)

```

### For the video

```
from ultralytics import YOLO
model = YOLO("yolov8.pt")
results = model("directory/video.mp4", save =True)
```

- Future Challage

- Try live feed on your camera,
-Do object counting, 
- The code is provided in this repositoty.



[def]: https://jetsonhacks.com/2019/10/01/jetson-nano-visual-studio-code-python/
[def2]: https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048