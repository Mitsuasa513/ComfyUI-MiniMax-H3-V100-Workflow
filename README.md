# ComfyUI-MiniMax-H3-V100-Workflow
# THIS IS A WORKFLOW OPTIMIZED FOR LEGACY BUT CHEAP CARD——V100, BOTH 16 / 32G SUPPORTED  
# 行者十六的V100专用工作流，16G / 32G都好使

### IF YOU USE HUAQIANGBEI TECH MODIFIED SXM2 TO PCIE V100 --disable-cuda-malloc MUST BE APPLIED BEFORE STARTUP YOUR COMFYUI WITH YOUR V100！
### 华强北特制SMX2转PCIE的V100必须开--disable-cuda-malloc！其他卡不需要开(OTHER CARD DO NOT ADD THIS)


WORKFLOWS FOR MINIMAX H3 IN COMFYUI W/ V100 (ALSO CAN USE FOR 30 40 50 SERIES GRAPHICS CARD)  
适用于V100在 MiniMax H3 的 ComfyUI 视频生成工作流。(也可以在30 40 50 系显卡使用)

NOTE: 720P HERE MEANS PARAMETER 0.7 (720P-) NOT 0.9 ACTUAL 720P BECAUSE IT IS TESTED AND IS A BALANCE BETWEEN TIME ELAPSE AND QUALITY:)  
备注：这里的720P指的准720P（0.7）不是0.9因为测试下来是质量和速度的平衡的甜点区：）    


## 20260911更新 / UPDATE
### 001 minimax_h3_fp16_fix.py for python 3.13 thanks to the original authors & @Alanpoe-mount compiling (ONLY FOR V100) 
put it into \comfyui\custom_nodes\ and add --fp16-unet in startup parameter of comfyui (DO NOT DO IT FOR 30 40 50 SERIES OTHER GRAPHICS CARDS)  
+++ Which may boost V100 from baselink to higher performance with startup parameter --fp16-unet in comfyui  
+++ 感谢原作者和编译者@Alanpoe-mount，放在\comfyui\custom_nodes\并在启动加入 --fp16-unet，效果倍儿爽  
### 002 Tested by several users, In H3 LOW VRAM Nodes, set  `head_chunks` to 5 may lightly reduce output time as well as lower the vram. (FOR ALL GRAPHICS CARDS) 
+++ Thanks to the @老林说 of its tik-tok's inspiration and I have tested in my V100-SXM2-32G, effective.(May varies in best value w/ different cards,v100 is 5, and test value recommended is 5/10/15)  
+++ 感谢@老林说，激发的加速灵感，并且实测有效。（V100-SXM2-32G甜点值是5，其他显卡建议5/10/15自行测试一下。）  


  
GRAPHICS CARD / 显卡 ：V100-SXM2-32G RAM / 内存：96G DDR4
| 设置Setup | 格式Format | 输出时间（分钟）Output time |
|---|---|---|
| 4步STEPS LORA+4步+T8(BASE LINE)           | 480P24F帧  5秒    | 349s （≈6分钟mins） |
| 4步SETPS LORA+4步+T8+FP16FIX           | 480P24F帧  5秒    | 315s（≈5.2分钟mins）      |
| 4步SETPS LORA+4步+T8+FP16FIX+ `head_chunks`=5           | 480P24F帧  5秒    | 300s（≈5分钟mins）   |
| 4步SETPS LORA+4步+T8(BASE LINE)           | 720P24F帧  5秒    | 1154s（≈19.2分钟mins）      |
| 4步SETPS LORA+4步+T8+FP16FIX+ `head_chunks`=5           | 720P24帧  5秒    | 853s（≈14.2分钟mins）   |  
  
GRAPHICS CARD / 显卡 ：RTX A2000M 8G (GA107/3050) RAM / 内存：128G DDR3 1866MHz
| 设置Setup | 格式Format | 输出时间（分钟）Output time |
|---|---|---|
| 4步STEPS LORA+4步+T8(BASE LINE)           | 480P24F帧  5秒    | 612s （≈6分钟mins） |
| 4步SETPS LORA+4步+T8+`head_chunks`=5+sageattn2_trion            | 480P24F帧  5秒    | 358s（≈5.9分钟mins）      |
| 4步SETPS LORA+4步+T8+`head_chunks`=5+sageattn2_cuda            | 480P24F帧  5秒    | 355s（≈5.9分钟mins）      |  
  
GRAPHICS CARD / 显卡 ：RTX 5060Ti 16G RAM / 内存：32G DDR4 3647MHz *5060Ti NOT TESTED `head_chunks`=5 YET DUE TO LAZYNESS（懒，后面再测吧）
| 设置Setup | 格式Format | 输出时间（分钟）Output time |
|---|---|---|
| 4步STEPS LORA+4步+T8(BASE LINE)           | 480P24F帧  5秒    | 151s （≈2.5分钟mins） |
| 4步SETPS LORA+4步+T8+sageattn2_triton            | 480P24F帧  5秒    | 100s（≈1.7分钟mins）      |
| 4步SETPS LORA+4步+T8+sageattn2_cuda            | 480P24F帧  5秒    | 96s（≈1.5分钟mins）      |  
  
################
  
## 性能表现 / PERFORMANCE REFERENCE  
  
GRAPHICS CARD / 显卡 ：V100-SXM2-32G RAM / 内存：96G DDR4
| 设置 | 格式 | 输出时间（分钟） & 品质得分 |
|---|---|---|
| 4步LORA+4步           | 480P24帧  5秒    | 349s （≈6分钟）   =4  |
| 4步LORA+6步           | 480P24帧  5秒    | 387s（≈7分钟）    =5  |
| 4步LORA+8步           | 480P24帧  5秒    | 682s（≈12分钟）   =7  |
| 4步LORA+4步           | 480P24帧  10秒   | 829s （≈14分钟）   =6  |
| 4步LORA+8步           | 480P24帧  10秒   | 1662s（≈28分钟）   =7  |
| 4步LORA4步+防爆显存   | 720P24帧  5秒     | 1154s （≈20分钟）   =8.5|
| 4步LORA6步+防爆显存   | 720P24帧  5秒     | 1549s （≈26分钟）  =9  |
| 无LORA+20X           | 480P24帧  5秒     | 1284s （≈22分钟）   =10 |


## Tested Configuration

- GPU: Tesla V100 32GB
- Resolution: 0.7(BALANCE BETWEEN PERFORMANCE AND QUALITY) or 0.4 (FASTER, DRAFT)
- Duration: 5 seconds
- head_chunks: 1 (IF OOM CHANGE INTO 2 OR HIGHER)
- chunks: 4 (IF OOM CHANGE INTO 2 OR HIGHER)
- Sampler steps: 4
- Turbo LoRA strength: 0.8 OR 0.75


## Usage

1. INSTALL NODES AND ACCELERATION FROM ACCELERATION DEVELOPERS / COMFYUI MANAGER;
2. DOWNLOAD THE H3 MODELS;
3. OPEN THIS WORKFLOW FROM COMFYUI;
4. ADD YOUR MULTIMEDIA ELEMENTS;
5. IF OOM CHANGE `head_chunks` AND `chunks` , TRY SMALLEST VALUE BEFORE LAST OMM AND SUCCESS;
6. --lowvram IS RECOMMANDED IF UR COMPUTER DON'T HAVE ENOUGH ~~MONEY~~ MEMORY.

## 使用说明

1. 安装所需自定义节点;
2. 下载对应模型并放入 ComfyUI 模型目录;
3. 将工作流导入 ComfyUI;
4. 替换参考图片和音频;
5. 根据显存情况调整 `head_chunks` 和 `chunks`。(建议从1/2开始2/2,2/4,4/4直到不爆显存);
6. 如果内存（~~钱~~）不够的话， --lowvram 也可以使用。
