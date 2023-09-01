# 在 macOS 上安裝 Stable Diffusion

參考資料：
1. [🖥️ 安裝至macOS | Stable Diffusion WebUI使用手冊(正體中文)｜Ivon的部落格](https://ivonblog.com/posts/stable-diffusion-webui-manuals/installation/macos-installation/)
2. [Stable Diffusion on Apple M1 - Jianqing's Blog](https://pjq.me/?p=1959)

```bash
# 要先有 Homebrew 及 Python

brew install --cask anaconda

# 加入以下兩行到 ~/.zshrc，然後 source 或重開終端機
## Anaconda
export PATH="/opt/homebrew/anaconda3/bin:$PATH"

conda init zsh

conda create --name sdwebui python=3.10.6

mkdir -p AI/Text-to-image
cd $WORKSPACE/AI/Text-to-image
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git

activate sdwebui

# 修改 $WORKSPACE/AI/Text-to-image/stable-diffusion-webui/webui-user.sh 第 13 行
export COMMANDLINE_ARGS="--reinstall-torch --skip-version-check --skip-torch-cuda-test --share --no-half"

$WORKSPACE/AI/Text-to-image/stable-diffusion-webui/webui.sh
```
