**--use_stemmer?**

Nov.13, 2022

```
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej1112/rouge# ./evaluate_test_zh.sh 
Building prefix dict from the default dictionary ...
I1113 10:07:19.776443 140240695170880 __init__.py:113] Building prefix dict from the default dictionary ...
Loading model from cache /tmp/jieba.cache
I1113 10:07:19.776774 140240695170880 __init__.py:132] Loading model from cache /tmp/jieba.cache
Loading model cost 0.444 seconds.
I1113 10:07:20.220579 140240695170880 __init__.py:164] Loading model cost 0.444 seconds.
Prefix dict has been built successfully.
I1113 10:07:20.220731 140240695170880 __init__.py:166] Prefix dict has been built successfully.
/opt/conda/lib/python3.8/site-packages/rouge_score/rouge_scorer.py:116: UserWarning: -----unknown stemmer language-> chinese-----
  warnings.warn(
I1113 10:07:20.222075 140240695170880 io.py:108] Reading targets from /mnt/nfs-storage/ej/res/gold_data/media_gold_test_zh.txt.
I1113 10:07:20.222191 140240695170880 io.py:109] Reading predictions from /mnt/nfs-storage/ej/ClidSum/outputs/mdialbart_zh.txt.
I1113 10:07:25.370339 140240695170880 io.py:135] Writing results to evaluation_test_zh.
I1113 10:07:25.371736 140240695170880 io.py:148] Finished writing results.
```

