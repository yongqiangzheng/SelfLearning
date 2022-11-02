# Anaconda
### 创建环境
```
conda create -n <环境名> python=<版本号>
```

### 激活环境

```
conda activate <环境名>
```

### 安装包到当前环境

```
conda install <包名称>=版本号
conda install pytorch -c pytorch-nightly
```

### 从当前环境删除包

```
conda unisntall <包名称>
```

### 退出环境

```
conda deactivate
```

### 删除环境

```
conda env remove --name test
```

### 查看信息

```
conda info
conda info -e #查看所有环境
```

### 显示当前环境的所有包

```
conda list
conda list <包名> #查看某个包的信息
```

### 分享虚拟环境

```
conda env export > environment.yml # 导出当前虚拟环境
conda env create -f environment.yml # 创建保存的虚拟环境
```

### 升级

```
# 升级Anaconda需先升级conda
conda  update  conda
conda  update  anaconda
```

### 批量导出虚拟环境中的所有组件

```
conda list -e > requirements.txt # 导出
conda install --yes --file requirements.txt # 安装

#pip批量导出环境中的所有组件
pip freeze > requirements.txt # 导出
pip install -r requirements.txt # 安装
```

