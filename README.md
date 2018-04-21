# MinGW编译OpenCV

直接下载 

```shell
git clone https://github.com/0xl2oot/OpenCV-MinGW.git
```

MinGW 版本 tdm64-gcc-5.1.0
OpenCV-3.4.1
opencv_contrib-3.4.1
CMake 3.11.0

cmake 参数

```
source-code opencv-3.4.1
build-dir 自己新建的文件夹
```

先 Configure 一下，再 Generate

```c
OPENCV_EXTRA_MODULES_PATH opencv_contrib-3.4.1/modules 
// 这个参数是因为 OpenCV3 之后有些算法的库被放在 opencv_contrib 里了，因此编译的时候需要这个参数，比如 surf 算法，提取图像特征

CMAKE_BUILD_TYPE Debug

ENABLE_CXX11 true 
// 因为 OpenCV 的源码中使用的是 C++11的语法，因此必须使用这个参数

BUILD_opencv_world false 
// 这个我没有看懂是什么，总之这个如果不关掉，麻烦会很大

OPENCV_VS_VERSIONINFO_SKIP true 
//就是因为这个选项，卡了我好几遍，不检查 VS 版本就好了
```

再一次，先 Configure 再 Generate

执行 


```shell
mingw32-make && mingw32-make install 
```

编译完成之后生成的库文件在 install 文件夹中