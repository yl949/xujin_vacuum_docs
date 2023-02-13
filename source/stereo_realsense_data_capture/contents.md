# 双目摄像机和realsense数据采集

## 相机id确定
接着将双目摄像头模组和realsense接连上电脑，在该电脑上运行下get_cam_id.py确认下左右摄像头的id号

在anaconda prompt下移动到你放置代码的文件夹，运行下面的指令进行相机id确认
```
python stereo_and_realsense_capture.py
```
运行该脚本后（有可能启动比较慢）会出现可视化窗口，在窗口响应的情况下可以通过键盘进行操作（鼠标移到窗口内点击一下就可以）。点击`p`可以显示当前对应的相机ID（在anconda prompt的窗口中显示）用以确认。根据窗口中的图像判断当前的图像是来自哪个相机（realsense，左目还是右目）。按键盘上的数字0到9可以切换到相应的设备号上（切换的过程有可能比较慢，因为相机要初始化，请耐心等待）。可以从1开始，直到分别确认了左右目的相机id。比如左目的id是3，右目是2。按`q`可以退出程序。


## 采集数据
```
python stereo_and_realsense_capture.py $save_path $left_cam_id $right_cam_id
```
运行上面代码，$save_path是要保存采集图像的路径 $left_cam_id 和 $right_cam_id 分别是上一步中确认的左右目id
例如：python stereo_and_realsense_capture.py stereo_and_realsense 2 3
启动和准备时间较长，耐心等待...
当出现可视化窗口后，期间，按键盘`s`进行当前帧图片采集，按`q`退出。和上面步骤一样，所有的键盘操作必须在窗口响应下进行。

采集完成后，所采集的图片会保存在所指定的 $save_path 中。
 **注意：
 如果按`q`退出后，下次进行采集，如果存贮的路径没有改变，之前采集的图片将被覆盖。解决办法有指定新的保存路径，或者将原来采集的文件重新命名为其他格式。上述代码保存的图片为:
 `left_{frame_id}.png`, `right_{frame_id}.png`, `color_{frame_id}.png`, `depth_{frame_id}.npy`, `depth_scale.txt`, `color_camera_matrix.npy`。
 这边建议指定新的保存路径。
