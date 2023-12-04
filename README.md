Windows 下 TensorFlow-gpu 安裝教學
===

###目前已知Windows之下能Native支持gpu最新版本為
###`tensorflow-gpu 2.10`
###以下教學皆基於此版本

---
依賴項
---

|TF ver.|Python ver.|cuDNN|CUDA|NVIDIA Driver|
|:--:|:--:|:--:|:--:|:--:|
|tensorflow-gpu 2.10|3.7 - 3.10|8.1|11.2|450.80.02+|

#####以下教學預設讀者已安裝Python
#####Python推薦版本: `3.10.11`

---
1.1 安裝驅動
---
#####已有驅動並且版本大於依賴項即可跳過此步驟

去 [https://www.nvidia.com.tw](https://www.nvidia.com.tw/Download/index.aspx?lang=tw "Nvidia_driver") 下載最新驅動
選擇對應顯示卡型號 按照步驟安裝即可

---
1.2 確認驅動
---
在 console 輸入 `nvidia-smi` 會顯示以下畫面

![nv_smi](\pics\nvidia-smi.png)

確認驅動版本滿滿足需求即可

---
2 安裝CUDA 
---
進入 [https://developer.nvidia.com](https://developer.nvidia.com/cuda-11.2.0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10 "Nvidia_CUDA") 
按下圖紅框指示下載安裝CUDA

==***注:Windows 11 同樣可用 Windows 10 版本 CUDA**==

![nv_cuda](\pics\nvidia_cuda.png)

按照軟體指示安裝 CUDA 即可

---
3.1 下載cuDNN
---
#####可能需要登入或註冊Nvidia會員才能安裝

進入 [https://developer.nvidia.com](https://developer.nvidia.com/rdp/cudnn-archive "Nvidia_cuDNN") 並下滑找到
`Download cuDNN v8.1.0 (January 26th, 2021), for CUDA 11.0,11.1 and 11.2`

![nv_cudnn](\pics\nvidia_cudnn.png)

下載 `cuDNN Library for Windows (x86)` 並解壓縮

---
3.2 安裝cuDNN
---
開啟CUDA的安裝路徑 (通常在: `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2`)
並將剛剛從cuDNN壓縮包的所有資料 ==**貼上並取代**== 

![nv_cudnn](\pics\nvidia_cudnn2.png)

---
4.1 安裝Tensorflow-gpu
---
回到 console 輸入 `pip install tensorflow-gpu==2.10`
等待安裝完即完成此步驟

---
4.2 測試gpu狀態
---
執行倉庫內 `test_gpu.py` 檔案測試
或是執行以下

```Python
import tensorflow as tf
print(tf.config.list_physical_devices('GPU'))
```
看到gpu列出來就代表成功了

![nv_cudnn](\pics\gpu_test.png)