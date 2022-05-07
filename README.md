最近需要在2019年版本的nano SDK上部署模型， 目前只找到了直接推理的方法。
| item | 版本   |
| ---- | ------ |
| CUDA | 10.0.0 |
|tensorrt|5.1.6.1|
|jetpack|4.2.2|
|opencv|3.3.1|
|pytorch|1.3.0|
|torchvision|0.4.1|

pytorch在这里下载whl文件:

https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-10-now-available/72048

## step 1 训练

data.zip数据集是yolo格式:

![title](https://img-blog.csdnimg.cn/d4c1c8dd010b450b8920418d6e96b6b9.png)

之后clone 这个repo 里面有所有用得到的code

```python
git clone -b yolov5 https://github.com/Promethe-us/YoloDeployOnNano
```

然后按照**yolov5s.ipynb教程**进行训练，得到**best.pt**

## step 2 推理(without tensorrt)

- 将 best.pt 放到目录yolov5/下
- 修改detect.py中的模型权重路径

```python3'
!python detect.py --source 0
```

推理结果: FPS=8

![title](https://img-blog.csdnimg.cn/da70659ab36e4081b49b2bea9f98e24d.png#pic_center)
