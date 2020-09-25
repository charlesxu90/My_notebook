# 环境操作

## 创建环境

```plain
$ conda create --name python36-env python=3.6 pip=20.0
```
## 激活环境

```plain
$ conda activate basic-scipy-env
```
## 关闭环境

```plain
(basic-scipy-env) $ conda deactivate
```
## 在当前目录下创建并激活环境

```plain
$ conda create --prefix ./env ipython=7.13 matplotlib=3.1 pandas=1.0 python=3.6
$ conda activate ./env
```
## 列出已有环境

```plain
$ conda env list
```
## 删除环境

```plain
$ conda remove --name my-first-conda-env --all
$ conda remove --prefix /path/to/conda-env/ --all
```
# 包操作

## 搜索包

```plain
$ conda search scikit-learn
```
## 安装包

```plain
(basic-scipy-env) $ conda install scikit-learn=0.22
```
## 使用 pip 在 conda 环境中安装包

```plain
(basic-scipy-env) $ conda install pandas
```
## 列出环境中的包

```plain
$ conda list --name basic-conda-env
$ conda list --prefix /path/to/conda-env
```
# 分享环境

## 创建environment.yml文件

### 示例 environment.yml 文件：

```plain
name: machine-learning-env
dependencies:
  - ipython
  - matplotlib
  - pandas
  - pip
  - python
  - scikit-learn
```
* 如果要用于在当前目录下创建./env 文件夹，需要将 name 的值设为 null。
## 使用 environment.yml 文件

* 通过 environment.yml 文件来对环境做版本控制，如将其添加到 git 中。
```plain
$ cd project-dir
$ conda env create --prefix ./env --file environment.yml
$ conda activate ./env
```
## 导出当前环境

```plain
$ conda env export --name machine-learning-env --no-builds
```
## 更新环境：

```plain
$ conda env update --prefix ./env --file environment.yml  --prune
```
## 重新创建环境：

```plain
$ conda env create --prefix ./env --file environment.yml --force
```
## Jupyter 与 Conda 环境的同步

JupyterLab 和 Jupyter Notebooks 会默认确保 IPython kernel 可用。但如果有使用某一版本的 IPython kernel，则需要在 environment.yml 文件中添加相应的信息。

```plain
name: xgboost-env
dependencies:
  - ipykernel=5.3
  - ipython=7.13
  - matplotlib=3.1
  - pandas=1.0
  - pip=20.0
  - python=3.6
  - scikit-learn=0.22
  - xgboost=1.0
```
# Conda 安装源 (channels)

## 命令行中使用

```plain
$ conda install scipy=1.3 --channel conda-forge --name my-first-conda-env
```
## 添加其他 channel

### 命令行添加

```plain
$ conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
$ conda config --set show_channel_urls yes
```
### environment.yml 文件中添加

```plain
dependencies:
- chanelname::modulename=X.Y.Z
```
## 无法找到源，使用 pip 安装

在 channel 中都没找到时，可以使用 pip 安装。

```plain
name: null
dependencies:
 - jupyterlab=1.0
 - matplotlib=3.1
 - pandas=0.24
 - scikit-learn=0.21
 - pip=19.1
 - pip:
   - kaggle=1.5
   - yellowbrick=0.9
```
# Conda 安装过程

![图片](https://uploader.shimo.im/f/3Oc4driVCfP272BY.png!thumbnail)

其他：[使用 conda 管理 GPU 依赖包](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/05-managing-cuda-dependencies/index.html);[Conda常用操作记录（for Mac）](https://zhuanlan.zhihu.com/p/81611615)。

## 



