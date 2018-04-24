# 基于tensorflow1.7.0 + object detection API 实现视频识别、语言识别、文本识别功能
 
前言：在搭建环境的时候，如果采用源码安装，到处都是坑，估计2天时间都未必能弄好，
 
所以，建议尽量不采用源码安装。 
 
一 、TensorFlow 环境搭建（为了保证本项目运行成功）请严格按照下面步骤按照

python3.5(3.5或以上 ,其中pip3 需要升级到 10.1)
Protobuf 3.3 (官方说的2.6 在用protoc编译时出错 )
Python-tk
Pillow 1.0
lxml
tf Slim (which is included in the "tensorflow/models/research/" checkout)
Jupyter notebook
Matplotlib
Tensorflow
Cython
cocoapi
 
二、ubuntu16.4下安装
#For CPU
pip install tensorflow
# For GPU
pip install tensorflow-gpu （如果安装gpu）
 
三、依赖包安装( 下面仅仅举例，包括第一点所说的所有软件包都需要安装)
sudo apt-get install protobuf-compiler python-pil python-lxml python-tk
sudo pip install Cython
sudo pip install jupyter
sudo pip install matplotlib
sudo pip .....
 
直接用download方式从 github.com/tensorflow/models 下载models包，大概470M，如果用git 太慢。
 
四、COCO API 安装
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
make 
cp -r pycocotools <path_to_tensorflow>/models/research/

五、Protobuf 编译(非常重要，编译不成功，后面无法执行)
# From tensorflow/models/research/
protoc object_detection/protos/*.proto --python_out=.

六、设置PYTHONPATH路径 （非常重要)
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim

七、测试安装
python object_detection/builders/model_builder_test.py
不报错，则表示安装成功
 
八、运行 jupyter
在 ~/tensorflow/models/research 目录下运行 jupyter 
nohup jupyter notebook --ip=* --no-browser --allow-root 2>&1 > my.log &
然后 在浏览器输入 http://xxx.xxx.xxx.xxxx:8888/ ,其中xxx.xxx.xxx.xxx表示安装jupyter的IP地址，8888表示端口
 
九 、在浏览器中运行 object_detection_tutorial.ipynb ，这个demo是图片识别,但需要改进！有些
 识别不出来。 
 

 
 
