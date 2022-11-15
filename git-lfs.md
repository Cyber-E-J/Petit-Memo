1. Navigate to [git-lfs.github.com](https://git-lfs.github.com/) and click **Download**. Alternatively, you can install Git LFS using a package manager:

   - To use [Homebrew](http://brew.sh/), run `brew install git-lfs`.
   - To use [MacPorts](https://www.macports.org/), run `port install git-lfs`.

   If you install Git LFS with Homebrew or MacPorts, skip to step six.

2. On your computer, locate and unzip the downloaded file.

3. Open Terminal.

4. Change the current working directory into the folder you downloaded and unzipped.

   ```shell
   $ cd ~/Downloads/git-lfs-1.X.X
   ```

   **Note:** The file path you use after `cd` depends on your operating system, Git LFS version you downloaded, and where you saved the Git LFS download.

5. To install the file, run this command:

   ```shell
   $ ./install.sh
    > Git LFS initialized.
   ```

   **Note:** You may have to use `sudo ./install.sh` to install the file.

6. Verify that the installation was successful:

   ```shell
   $ git lfs install
   > Git LFS initialized.
   ```

7. If you don't see a message indicating that `git lfs install` was successful, please contact [GitHub Support](https://support.github.com/contact?tags=docs-generic). Be sure to include the name of your operating system.



```
apt-get install git-lfs
```





进入下载的model中并且git lfs pull

lfs large file storage

```shell
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej/Bertscore# ./evaluate.sh          
Traceback (most recent call last):
  File "/opt/conda/lib/python3.8/site-packages/transformers/modeling_utils.py", line 1348, in from_pretrained
    state_dict = torch.load(resolved_archive_file, map_location="cpu")
  File "/opt/conda/lib/python3.8/site-packages/torch/serialization.py", line 608, in load
    return _legacy_load(opened_file, map_location, pickle_module, **pickle_load_args)
  File "/opt/conda/lib/python3.8/site-packages/torch/serialization.py", line 777, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
_pickle.UnpicklingError: invalid load key, 'v'.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/opt/conda/bin/bert-score", line 8, in <module>
    sys.exit(main())
  File "/opt/conda/lib/python3.8/site-packages/bert_score_cli/score.py", line 106, in main
    all_preds, hash_code = bert_score.score(
  File "/opt/conda/lib/python3.8/site-packages/bert_score/score.py", line 98, in score
    model = get_model(model_type, num_layers, all_layers)
  File "/opt/conda/lib/python3.8/site-packages/bert_score/utils.py", line 255, in get_model
    model = AutoModel.from_pretrained(model_type)
  File "/opt/conda/lib/python3.8/site-packages/transformers/models/auto/auto_factory.py", line 419, in from_pretrained
    return model_class.from_pretrained(pretrained_model_name_or_path, *model_args, config=config, **kwargs)
  File "/opt/conda/lib/python3.8/site-packages/transformers/modeling_utils.py", line 1353, in from_pretrained
    raise OSError(
OSError: You seem to have cloned a repository without having git-lfs installed. Please install git-lfs and run `git lfs install` followed by `git lfs pull` in the folder you cloned.
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej/Bertscore# ls 
chinese-bert-wwm-ext  ckpt5_zh.py  evaluate.sh
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej/Bertscore# cd c
bash: cd: c: 没有那个文件或目录
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej/Bertscore# cd chinese-bert-wwm-ext/
(base) root@pai-worker13-v100-37:/mnt/nfs-storage/ej/Bertscore/chinese-bert-wwm-ext# git lfs pull
Downloading LFS objects:   0% (0/3), 160 MB | 7.1 MB/s                                                                                                
```

