# 什么是Qt
Qt是一套跨平台的C++框架，用于开发图形用户界面（GUI）和非GUI应用程序。

# 什么是PyQt
PyQt是一个用于创建基于Qt应用程序的Python库。PyQt允许开发者使用Python语言访问Qt的功能，开发桌面应用程序。

# 使用PyQt创建GUI应用程序的基本流程
1. 安装PyQt
2. 使用Qt Designer软件设计应用程序的GUI界面，获得.ui文件
3. 使用Pyuic工具，将.ui文件转换为.py文件
4. 使用Python编程，调用GUI界面的.py文件，编写GUI界面各组件的绑定事件函数

# 安装PtQt工具链
1. pip install PyQt5 
2. pip install PyQt5-tools
3. VsCode中安装PyQt Integration拓展
4. PyQt Integration拓展中Pyqt-integration > Pyuic: Cmd指定绝对路径，一般在path_to_anaconda/envs/你的环境名/bin/pyuic5
5. PyQt Integration拓展中Pyqt-integration > Qtdesigner: Path指定绝对路径，一般在path_to_anaconda/envs/你的环境名/lib/python3.8/site-packages/qt5_applications/Qt/bin/designer
6. 在「Pyqt-integration > Pyuic > Compile: Filepath」指定将 .ui 文件转换成 .py 文件时的保存路径和命名格式
7. 路径报错的话find /home/zhuangpeican/.conda/envs/TCTrack++/ -name "designer"找路径