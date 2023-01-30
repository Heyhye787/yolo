conda 產生的安裝指令如下：

```js 
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

pip 產生的安裝指令如下：

```js 
pip install torch==1.10.0+cu113 torchvision==0.11.1+cu113 torchaudio===0.10.0+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
```
# 驗證

以 Python 執行下列程式碼驗證CUDA安裝是否成功：
```Python
import torch
tensor = torch.rand(3,4)
print(f"Device tensor is stored on: {tensor.device}")
# Device tensor is stored on: cpu

print(torch.cuda.is_available())
#True

tensor = tensor.to('cuda')
print(f"Device tensor is stored on: {tensor.device}")
# Device tensor is stored on: cuda:0
```
# 注意事項

1.TensorFlow安裝需另外安裝NVidia CUDA Toolkit/CuDNN，而PyTorch安裝會一併安裝CUDA Toolkit，但是兩者並不同，PyTorch安裝的cudatoolkit是NVidia CUDA Toolkit的子集合，目前(2021/11/08)TensorFlow要求CUDA Toolkit須為v11.2，而PyTorch安裝的是v11.3，兩者並不衝突。

2.NVidia CUDA Toolkit的路徑設在環境變數Path中，並不會影響PyTorch。

3.筆者先使用 conda 安裝PyTorch CPU 版本，再移除，改安裝 CUDA 版本，安裝沒問題，但以上述程式碼驗證，卻一直偵測不到 GPU，最後*改用pip才成功*。

資料來源:https://ithelp.ithome.com.tw/articles/10282119
