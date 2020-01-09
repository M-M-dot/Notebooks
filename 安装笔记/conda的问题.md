

### 问题： [How to Fix Entry Point Not Found while installing libraries in conda environment](https://stackoverflow.com/questions/57254007/how-to-fix-entry-point-not-found-while-installing-libraries-in-conda-environment)

* ```
  python.exe-Entry Point Not Found
     The procedure entry point OPENSSL_sk_new_reserve could not be 
     located in the dynamic link library.
     C:\Users\abc\Anaconda3\Library\bin\libssl11_-x64.dll
  ```

* 解决方法：

  把 `Anaconda/DLLS` 里面的 `libssl-1_1-x64 dlls` 移动到 `Anaconda/Library/bin`， 记得将`Anaconda/Library/bin`原来的`libssl-1_1-x64 dlls`备份

  https://github.com/conda/conda/issues/9003

  ```
  原文：I found out libssl-1_1-x64 dlls in Anaconda/DLLS and Anaconda/Library/bin being installed at different dates, so, as an experiment, I copied the one in Anaconda/DLLS and replaced that in Anaconda/Library/bin and conda started working again, at least for now - I could install new packages again.
  ```

  