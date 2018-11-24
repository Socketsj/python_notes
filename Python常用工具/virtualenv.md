# virtualenv的基本使用

### 1. 安装 virtualenv

    $ pip install virtualenv

### 2. 进入到项目目录下，创建一个名为 **venv** 的独立的Python环境

    $ cd demeter
    $ virtualenv --no-site-packages venv

### 3. 激活使用虚拟环境

    $ source venv/bin/activate
    (venv)$

**注意**：命令提示符前面有个 **(venv)** 前缀，表示当前处于名为 **venv** 的Python环境下

### 4.安装第三方库到虚拟环境中(系统Python环境不受任何影响)

    (venv)$ pip install django

### 5. 退出虚拟环境，回到系统环境下

    (venv)$ deactivate
    $ 

### 6. 删除虚拟环境

    $ rm -rf venv

