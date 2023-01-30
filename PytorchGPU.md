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
