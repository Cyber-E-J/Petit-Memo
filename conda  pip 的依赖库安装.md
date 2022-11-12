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

```
pip install -r requirements.txt -i https://mirror.baidu.com/pypi/simple
```



```
nohup ./run.sh >output.log 2>&1 & 

nohup ./finetune.sh >output.log 2>&1 & 
```

```
kill -9 PID
```



save shell

```

```



清华大学 ：https://pypi.tuna.tsinghua.edu.cn/simple/

阿里云：http://mirrors.aliyun.com/pypi/simple/

中国科学技术大学 ：http://pypi.mirrors.ustc.edu.cn/simple/

华中科技大学：http://pypi.hustunique.com/

豆瓣源：http://pypi.douban.com/simple/

腾讯源：http://mirrors.cloud.tencent.com/pypi/simple

华为镜像源：https://repo.huaweicloud.com/repository/pypi/simple/



```
scp /Users/erlich_jaso/Code/sd-v1-4.ckpt ubuntu@1.116.101.204:/home/ubuntu/ej/stable-diffusion/models/ldm/stable-diffusion-v1
```





```
ModuleNotFoundError: No module named 'cv2'

python -m pip install -r requirements.txt
```





```
Loading model from models/ldm/stable-diffusion-v1/model.ckpt
Global Step: 470000
LatentDiffusion: Running in eps-prediction mode
DiffusionWrapper has 859.52 M params.
making attention of type 'vanilla' with 512 in_channels
Working with z of shape (1, 4, 32, 32) = 4096 dimensions.
making attention of type 'vanilla' with 512 in_channels
Downloading: "https://github.com/DagnyT/hardnet/raw/master/pretrained/train_liberty_with_aug/checkpoint_liberty_with_aug.pth" to /home/ubuntu/.cache/torch/hub/checkpoints/checkpoint_liberty_with_aug.pth


```



```
Global seed set to 42
Loading model from models/ldm/stable-diffusion-v1/model.ckpt
Global Step: 470000
LatentDiffusion: Running in eps-prediction mode
DiffusionWrapper has 859.52 M params.
making attention of type 'vanilla' with 512 in_channels
Working with z of shape (1, 4, 32, 32) = 4096 dimensions.
making attention of type 'vanilla' with 512 in_channels
Downloading: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 961k/961k [00:01<00:00, 820kB/s]
Downloading: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 525k/525k [00:00<00:00, 637kB/s]
Downloading: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 389/389 [00:00<00:00, 324kB/s]
Downloading: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 905/905 [00:00<00:00, 804kB/s]
Downloading: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 4.52k/4.52k [00:00<00:00, 3.79MB/s]
Downloading:   2%|█████▍                                                                                                                                                                                                                                             | 38.6M/1.71G [00:12<05:17, 5.27MB/s]
```



```
Your samples are ready and waiting for you here: 
outputs/txt2img-samples 
 
Enjoy.
```





```
 python scripts/txt2img.py --prompt "Big Mac, Health Code:: hightly detailed, hyper realistic, photographic, wide angle lens:: in the style of Richard Avedon, Patrick Demarchelier, Vogue, Baron Adolphe De Meyer"  --plms
```





```

python scripts/txt2img.py --prompt "Chang Chen in Peru, vintage, promiscuous, black and white, detailed, intricate ink, illustration, bittersweet, hd, surreal"  --plms
```





```
python scripts/txt2img.py --prompt "Hangzhou city, modern landscape architectural design for industrialpunk, water in the middle, dramatic lighting and composition, octane render, unreal engine 5, 8k "  --plms --H 512 --W 1536
```



```

python scripts/txt2img.py --prompt "synthwave galaxy being eaten by Galactus, HDR, cinematic, ultrawide, realistic, highly detailed "

```



```
python scripts/txt2img.py --prompt "hungarian parliament underwater-beach, palm trees behind, aerial shot, real photography, unreal-engine, 4k, highly detailed --wallpaper --uplight" --W 720 --H 1080
```





```
python scripts/txt2img.py --prompt "Midjourney style| perplexing ominous otherworldly creature emerging from unknown space| Lovecraftian cosmic entities| Cthulhu| horror| vibrant| sharp focus| massive scale| highly detailed| unreal engine| 8k uhd| raytracing| by Ross Tran and Guillermo del Toro" 


python scripts/txt2img.py --prompt "the source of future growth dramatic, elaborate emotive Golden Baroque and Rococo styles to emphasise beauty as a transcendental, seamless pattern, symmetrical, large motifs, sistine chapel ceiling, 8k image, supersharp, spirals and swirls in rococo style, cartouches, white smoke and rainbow ink dropping in water, Gold black and rainbow colors, perfect symmetry, 3D, no blur, sharp focus, photorealistic, insanely detailed and intricate, cinematic lighting, Octane render, epic scene, 8K" 



python scripts/txt2img.py --prompt "Lofi nuclear war to relax and study to" 

python scripts/txt2img.py --prompt "a ultradetailed beautiful panting of a stylish woman sitting on a chair, by conrad roset, greg rutkowski and makoto shinkai, trending on artstation" 
python scripts/txt2img.py --prompt "detailed portrait of European Pretty Young Girl Storm Rain movie Jacket coat, Futuristic sci-fi fashion, royal attire by ismail inceoglu dragan bibin hans thoma greg rutkowski Alexandros Pyromallis Nekro Rene Margitte illustrated Perfect face, sharp chine, fine details, realistic shaded, fine-face, pretty face cyberpunk, neotokyo, synthwave, aesthetics, futuristic, low-emission-neon, bladerunner movie scene" 
python scripts/txt2img.py --prompt "Agnes Varda, detailed portrait, Storm Rain movie Jacket coat, Futuristic sci-fi fashion, royal attire by ismail inceoglu dragan bibin hans thoma greg rutkowski Alexandros Pyromallis Nekro Rene Margitte illustrated Perfect face, sharp chine, fine details, realistic shaded, fine-face, pretty face cyberpunk, neotokyo, synthwave, aesthetics, futuristic, low-emission-neon, bladerunner movie scene" 



((princess_peach)), (anime face), pink dress, blonde hair, female, by Artgerm

python scripts/txt2img.py --prompt "a matte painting of an insanely beautiful female goddess of seduction, sharp focus on eyes, insanely detailed hair, symmetrical, wet luscious lips, few water droplets, intricate details, professionally retouched, elegant, 8k high definition, by artgerm and greg Rutkowski, lighting by albert Bierstadt" 





```

