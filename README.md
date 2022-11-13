# bicubic-image-resize

使用双三次插值法对图像进行缩放。

## 构建与运行

使用cmake进行构建
```shell
mkdir build
cd build
cmake ..
make
```
## 使用与说明


第一个参数传入图像路径，会在图像的同目录下生成一张放大5倍的图像

```shell
./resize $IMAGE_PATH
```


功能类似于如下python伪代码
```python
from PIL import Image
image = Image.open($IMAGE_PATH)
resize_image = image.resize(5 * image.width, 5 * image.height)
image.save($RESIZE_IMAGE_PATH)

```


## 结构

- `resize.hpp` 图像缩放处理
- `image.hpp` 读写封装
- `utils.hpp` 辅助类
- `stb/` stb图像读写库

## 任务说明

### 计时

读写不计入程序总时间。计时部分仅有`resize.hpp`中的`ResizeImage`函数，也仅需要优化此部分。

### 编译与构建

baseline默认编译优化等级为O3，应当在此基础上进行优化。

可以自己重新编写构建脚本，但编译优化等级应该设置为O3。

### 测试

在`images/`目录下给出了若干图片用于测试与计时。最终提交时，也会使用此目录下的图片进行评测程序性能。

注意：要求优化后的程序能够正确缩放图片。虽然不要求用diff test进行评测，但是起码保证图片缩放的效果比较好。建议不要改动总的计算逻辑。
