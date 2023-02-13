# 双目摄像机和realsense数据采集

## python环境配置
首先确认按照[python环境配置](../python_env/contents.md)进行python环境的准备

## 相机id确定
接着将双目摄像头模组和realsense接连上电脑，在该电脑上运行下get_cam_id.py确认下左右摄像头的id号

打开anaconda prompt终端，移动到你放置代码的文件夹，运行下面的指令进行相机id确认
```
python stereo_and_realsense_capture.py
```
运行该脚本后（有可能启动比较慢）会出现可视化窗口，在窗口响应的情况下（可以通过鼠标移到窗口内点击一下，保证窗口响应）可以通过键盘进行操作。点击`p`可以显示当前对应的相机ID（在anconda prompt的窗口中显示）用以确认。根据窗口中的图像判断当前的图像是来自哪个相机（realsense，左目还是右目）。按键盘上的数字0到9可以切换到相应的设备号上（切换的过程有可能比较慢，因为相机要初始化，请耐心等待）。可以从1开始，直到分别确认了左右目的相机id。比如左目的id是3，右目是2。按`q`可以退出程序。


## 采集数据
```
python stereo_and_realsense_capture.py $save_path $left_cam_id $right_cam_id
```
运行上面代码，$save_path是要保存采集图像的路径 $left_cam_id 和 $right_cam_id 分别是上一步中确认的左右目id
例如：
```
python stereo_and_realsense_capture.py stereo_and_realsense 2 3
```
启动和准备时间较长，耐心等待...
当出现可视化窗口后，按键盘`s`可以保存窗口中显示的当前帧图片，按`q`退出。和上面步骤一样，所有的键盘操作必须在窗口响应下进行。

采集完成后，所采集的图片会保存在所指定的 $save_path 中。

 **注意**：
 如果按`q`退出后，进行新一次采集的时候，命令行键入的存贮路径没有改变，原本采集的图片将被同名的新采集图片覆盖。解决办法有指定新的保存路径，或者将原来采集的文件重新命名为其他格式。上述代码保存的文件命名格式为:
 双目模组左图：`left_{frame_id}.png`, 双目模组右图：`right_{frame_id}.png`, realsense rgb图：`color_{frame_id}.png`, realsense 深度图：`depth_{frame_id}.npy`, realsense 深度放缩系数：`depth_scale.txt`, realsense rgb内参矩阵`color_camera_matrix.npy`。
 进行新一轮采集时，建议采用指定新的保存路径方式。
