## conda / pip 的依赖库安装

Oct. 10, 2022



今天捣鼓了一下午，想要安装最近很火的stable diffusion



> ## Requirements
>
> A suitable [conda](https://conda.io/) environment named `ldm` can be created and activated with:
>
> ```
> conda env create -f environment.yaml
> conda activate ldm
> ```





在第一步的时候我就碰到了问题。似乎cuda已经不支持macOS了，我稍微尝试了一下就转到windows上尝试。

一开始是不了解conda的这些东西是什么意思的，弄了半天已经有点明白了

```
conda env create (...)
conda env update (...)
conda env remove -n (...)

conda activate (...)
```

**我还有一个问题是conda在不同的环境之中是库里在本地有一份拷贝，在环境里拷贝进去？还是每一份环境的库都是不同的。是则本地环境空间开销太大；否则每次安装新的环境是都要大费周章。**



yaml原来是一个类似的文件标记语言。

```
###environment.yaml

name: ldm
channels:
  - pytorch
  - defaults
dependencies:
  - python=3.8.5
  - pip=20.3
  - cudatoolkit=11.3
  - pytorch=1.11.0
  - torchvision=0.12.0
  - numpy=1.19.2
  - pip:
    - albumentations==0.4.3
    - diffusers
    - opencv-python==4.1.2.30
    - pudb==2019.2
    - invisible-watermark
    - imageio==2.9.0
    - imageio-ffmpeg==0.4.2
    - pytorch-lightning==1.4.2
    - omegaconf==2.1.1
    - test-tube>=0.7.5
    - streamlit>=0.73.1
    - einops==0.3.0
    - torch-fidelity==0.3.0
    - transformers==4.19.2
    - torchmetrics==0.6.0
    - kornia==0.6
    - -e git+https://github.com/CompVis/taming-transformers.git@master#egg=taming-transformers
    - -e git+https://github.com/openai/CLIP.git@main#egg=clip
    - -e .
```

我一直搞不定这个。

##### 问题1

​	conda的源，改用清华的镜像源。

​	但是pip的源也要改。

**问题2**

​	在win上很难弄，我的程序进入了一个一直在转的字符中，没有输出——后来我发现他可能在正常装只是时间太长了——但是当我躺了十几分钟还没成功之后我觉得可能不太对。想了半天我这样子弄：





```
#requirements.txt


    - albumentations==0.4.3
    - diffusers
    - opencv-python==4.1.2.30
    - pudb==2019.2
    - invisible-watermark
    - imageio==2.9.0
    - imageio-ffmpeg==0.4.2
    - pytorch-lightning==1.4.2
    - omegaconf==2.1.1
    - test-tube>=0.7.5
    - streamlit>=0.73.1
    - einops==0.3.0
    - torch-fidelity==0.3.0
    - transformers==4.19.2
    - torchmetrics==0.6.0
    - kornia==0.6
    
    
pip install -r requirements.txt
```

意思是我已经进入了这个环境之后再通过pip批量安装环境。大概是这样







```
pip install -e git+git@github.com:CompVis/taming-transformers.git@master#egg=taming-transformers
```

```
Could not detect requirement name for 'git+https://gitlab.com/jame/clientapp.git', please specify one with #egg=your_package_name
```

python的包有以egg命名的，意思是蛇蛋

Python的第一个主流打包格式是.egg文件。

现在大家庭中又有了一个叫做Wheel(*.whl)的新成员。

wheel“被设计成包含PEP 376兼容安装(一种非常接近于磁盘上的格式)的所有文件”。





百度源速度飞快

pip install -r requirements.txt -i [https://mirror.baidu.com/pypi/simple](https://links.jianshu.com/go?to=https%3A%2F%2Fmirror.baidu.com%2Fpypi%2Fsimple)







nohup ./run.sh >output.log 2>&1 & 

kill -9 PID

