# python环境配置
建议使用Anaconda。先下载并安装Anaconda。然后创建一个python环境。我使用的是python3.8
具体操作如下：
安装好Anaconda后，在开始菜单中搜索 anaconda prompt 打开，逐行输入下列命令。
```
conda create --name stereo-realsense python=3.8
conda activate stereo-realsense
pip install -r requirements.txt
```

配置环境只需要执行一次。如果关闭后 anaconda prompt，下次采集的时候，重新打开 anconda prompt后，只需要输入
```
conda activate stereo-realsense
```
就可以了。