## 图像的矩阵表示
采样和量化

图像大小 $M\times N$

![](image/2022-01-17-18-14-20.png)

如下图

前者为本书使用的空间坐标约定，后者为工具箱常用约定

![](image/2022-01-17-18-19-22.png)

## 图像的输入/输出和显示
#### imread('filename')

支持多数流行图像格式如 `JPEG` `JPEG 2000` `TIFF`

`>> f = imread('test.jpg');`

结尾处的分号用于抑制输出，若没有分号则该行操作的结果会显示在屏幕上

#### imshow(f)
```m
>> f = imread('test.jpg');
>> imshow(f)
```

如想同时输出多张图片，如下

`>> figure,imshow(g)`

#### imwrite(f,'filename')
1. `imwrite(f,'filename.jpg','quality',q)`
$q\in [0,100]$ (数字越小，劣化越高)

2. `imwrite(f,'filename.tif','compression','parameter',...,'resolution',[colres rowres])`
parameter:
    * none 未压缩
    * packbits 默认用于非二值图像

见 `p9(MATLAB)`

## 类和图像类型
![](image/2022-01-17-18-49-54.png)

工具箱支持 4 中图像类型
* 灰度级图像 Gray-scale images
* 二值图像 Binary images
* 索引图像 Indexed images
* RGB 图像 RGB images

灰度级图像：矩阵的值表示灰度的浓淡

二值图像：只有逻辑值 0 和 1

`islogical(C)` C 是逻辑数组返回 1 ，否则 0

`B = logical(A)` 把 A 转成逻辑数组 B

`B = class_name(A)` 把 A 转为特定类型 `class_name`

其中 `class_name` 可以是 `im2uint8 im2uint16 im2double im2single mat2gray`

`mat2gray` 把一幅图像转化未标定到范围 [0,1] 的 double 类数组

`g = mat2gray(A,[Amin,Amax])`，A 中值小于 Amin 变为 0 ；大于 Amax 变为 1

**自此，我们的图像定义为 `class image_type` 如 `uint8 灰度级图像`**