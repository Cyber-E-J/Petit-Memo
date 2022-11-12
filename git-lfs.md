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