# ComfyUI-MiniMax-H3-V100-Workflow
THIS IS A WORKFLOW OPTIMIZED FOR LEGACY BUT CHEAP CARD——V100, BOTH 16 / 32G SUPPORTED / 行者十六的V100专用工作流，16G / 32G都好使

## IF YOU USE HUAQIANGBEI TECH MODIFIED SXM2 TO PCIE V100 --disable-cuda-malloc MUST BE APPLIED BEFORE STARTUP YOUR COMFYUI WITH YOUR V100！
## 华强北特制SMX2转PCIE的V100必须开--disable-cuda-malloc！

适用于V100在 MiniMax H3 的 ComfyUI 视频生成工作流。
WORKFLOWS FOR MINIMAX H3 IN COMFYUI W/ V100

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
