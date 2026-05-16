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

# 多线程
1. 默认的线程在Qt中称之为窗口线程，也叫主线程，负责窗口事件处理或者窗口控件数据的更新
2. 子线程负责后台的业务逻辑处理，子线程中不能对窗口对象做任何操作
3. 主线程和子线程之间的数据传递通过Qt中的信号与槽机制
4. 线程入口

# Qt线程启动逻辑--调用thread.start()时
1. QThread通过Qt框架调用系统线程API创建线程
2. 操作系统为该线程分配线程栈、寄存器上下文等资源
3. 新线程进入就绪态，等待CPU调度
4. 当线程获得CPU时间片后，Qt内部线程入口函数开始执行
5. Qt在线程入口函数中调用QThread.run()
5. 用户重写的run() 方法开始执行

# 线程入口函数、start、run的区别
1. 线程入口函数本质是操作系统调用的Qt内部静态/私有函数，新线程中执行，不能重写
2. start是公共接口函数，用户代码调用，不能重写，原线程中执行
3. run是虚函数，线程入口函数调用，在新线程中执行，可以重写