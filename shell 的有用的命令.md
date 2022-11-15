

## shell 的有用的命令

${var##*/}
该命令的作用是去掉变量var从左边算起的最后一个'/'字符及其左边的内容，返回从左边算起的最后一个'/'（不含该字符）的右边的内容。使用例子及结果如下：

![img](https://img-blog.csdnimg.cn/2022010613551267496.png)

${var##*.}

该命令的作用是去掉变量var从左边算起的最后一个'.'字符及其左边的内容，返回从左边算起的最后一个'.'（不含该字符）的右边的内容。使用例子及结果如下：

![img](https://img-blog.csdnimg.cn/2022010613551343495.png)



${var#*.}
该命令的作用是去掉变量var从左边算起的第一个'.'字符及其左边的内容，返回从左边算起第一个'.'（不含该字符）的右边部分的内容。使用例子及结果如下：

从运行结果可以看到，使用该命令，可以提取出文件的多个后缀。

![img](https://img-blog.csdnimg.cn/2022010613551342199.png)

4、${var%/*}
该命令的使用是去掉变量var从右边算起的第一个'/'字符及其右边的内容，返回从右边算起的第一个'/'（不含该字符）的左边的内容。使用例子及结果如下：

![img](https://img-blog.csdnimg.cn/2022010613551378857.png)

从运行的结果可以看到，使用该命令，可以提取出我们需要的文件所在的目录



5、${var%%.*}
该命令的使用是去掉变量var从右边算起的最后一个'.'字符及其右边的内容，返回从右边算起的最后一个'.'（不含该字符）的左边的内容。使用例子及结果如下：

![img](https://img-blog.csdnimg.cn/2022010613551488385.png)

当我们需要建立一个与文件名相同名字（没有后缀）的目录与对应的文件相对应时，就可以使用该命令来进行操作。例如，解压文件的情况就与此类似，我们压缩文件file.zip时，会在与file.zip同级目录下建立一个名为file的目录。



```
for file in /data/huajian/clid/mbart50_plan-en/generated_summary_test_*
do

sudo scp $file zhanghuajian@10.0.2.39:/nfsshare/userspace/zhanghuajian/re-experiment/mbart50_plan-en/${file##*/}

done
```



```
scp /data/huajian/clid/mbart50_merge-zhen/_ckpt_epoch_2.ckpt zhanghuajian@10.0.2.39:/nfsshare/userspace/zhanghuajian/re-experiment/mbart50_merge-zhen


```



```
for ((a=10;a<=19;a++))

do
python ../xl-sum/multilingual_rouge_scoring/rouge.py \
    --rouge_types=rouge1,rouge2,rougeL \
    --target_filepattern=generated_summary_test_1.post.txt \
    --prediction_filepattern=../res/SAMSum_gold_val_zh.txt \
    --output_filename=results/val/scores_1.csv  \
    --lang="chinese"  # "zhongwen" for Chinese
    # --use_stemmer=true

done
```

