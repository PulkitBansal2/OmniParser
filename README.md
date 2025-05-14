# OmniParser

**OmniParser** is a multimodal document understanding model developed by Microsoft. It combines icon detection and vision-language captioning to parse and extract structured information from visually-rich documents such as forms, tables, and charts. This repository contains code and instructions to set up and run OmniParser locally, including a Gradio-based user interface for demonstration.

---

## 🔧 System Requirements

Before getting started, ensure your system meets the following requirements:

- **Operating System**: Linux, macOS, or Windows (WSL2 recommended)  
- **Python Version**: 3.12 (required)  
- **Memory**: At least 8 GB RAM (16 GB+ recommended)  
- **Disk Space**: ~5 GB of free space  
- **GPU**: Recommended for faster inference (NVIDIA GPU with CUDA support)  

---

## 🛠️ Installation & Setup

Follow the steps below to install and run the OmniParser model:


# 1. Clone the Repository
```bash
git clone https://github.com/microsoft/OmniParser.git
cd OmniParser
```

# 2. Create and Activate Conda Environment
```bash
conda create -n "omni" python==3.12
conda activate omni
```

# 3. Install Required Python Packages
```bash
pip install -r requirements.txt
```

# 4. Log In to Hugging Face
```bash
huggingface-cli login
```
# If you don't have an account, create one at https://huggingface.co/join

# 5. Download Model Weights
```bash
for f in icon_detect/{train_args.yaml,model.pt,model.yaml} \
        icon_caption/{config.json,generation_config.json,model.safetensors}; do
  huggingface-cli download microsoft/OmniParser-v2.0 "$f" --local-dir weights
done
```

# 6. Organize Model Weights
```bash
mv weights/icon_caption weights/icon_caption_blip2  # or icon_caption_florence
```

#7. Launch the Application
```bash
python gradio_demo.py
```
