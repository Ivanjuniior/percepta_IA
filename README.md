# 🚀 AI Model Training with MindSpore (CPU)

---

## 🇺🇸 English Version

## 🧱 Requirements

- Linux (Debian12 / Ubuntu 24.04)
- Python **3.10**
- CPU

---

## ⚙️ 1. Create Virtual Environment

```bash
python3.10 -m venv ~/percepta
source ~/percepta/bin/activate
pip install --upgrade pip
```

## 🧠 2. Install MindSpore 2.6
```
pip install mindspore==2.6.0
```

Check:
```
python -c "import mindspore as ms; print(ms.__version__)"
```

Expected output:
```
2.6.0
```

## 📦 3. Fix Dependencies (CRITICAL)

Remove conflicts:
```
pip uninstall -y numpy opencv-python-headless albumentations albucore
```

Install compatible versions:
```
pip install numpy==1.26.4 opencv-python-headless==4.8.1.78 albumentations==1.3.1 --no-deps
```

## 📥 4. Clone Project
```
git clone https://github.com/mindspore-lab/mindyolo.git
cd mindyolo
```

## 📁 5. Dataset Structure

```
dataset/
 ├── images/
 │   ├── train/
 │   ├── val/
 │
 ├── labels/
 │   ├── train/
 │   ├── val/
 │
 ├── train.txt
 ├── val.txt
```

## 📁 5.1 Dataset Download
```
https://drive.google.com/file/d/1q-o-TEWubit3msdnpfrKLhX4IcG_uJcw/view?usp=sharing
```

## 📝 6. Configure Dataset
```
nano configs/coco.yaml
```

```
data:
  dataset_name: custom

  train_set: /FULL/PATH/train.txt
  val_set: /FULL/PATH/val.txt

  nc: 2
  names: ['object', 'dummy']
```

## 🚀 7. Train Model (CPU)

```
python train.py \
  --config configs/yolov5/yolov5n.yaml \
  --device_target CPU \
  --epochs 50 \
  --per_batch_size 4 \
  --img_size 640 \
  --ms_jit False
```

## 📊 8. Expected Output

```
Epoch 1/50
```

Files saved in:
```
runs/
```

## 🧾 9. Logs

```
python train.py ... 2>&1 | tee treino.log
```

---

## 🔁 Training Pipeline

```
Data Collection
      ↓
Annotation (COCO)
      ↓
Preprocessing
      ↓
Training (MindSpore)
      ↓
Validation
      ↓
Model Selection (best.ckpt)
      ↓
Deployment
```

---

## 🇧🇷 Versão em Português

## 🧱 Requisitos

- Linux (Debian12 / Ubuntu 24.04)
- Python **3.10**
- CPU

---

## ⚙️ 1. Criar ambiente virtual

```bash
python3.10 -m venv ~/percepta
source ~/percepta/bin/activate
pip install --upgrade pip
```

## 🧠 2. Instalar MindSpore 2.6
```
pip install mindspore==2.6.0
```

Verifique:
```
python -c "import mindspore as ms; print(ms.__version__)"
```

Saída esperada:
```
2.6.0
```

## 📦 3. Corrigir dependências (CRÍTICO)

Remover conflitos:
```
pip uninstall -y numpy opencv-python-headless albumentations albucore
```

Instalar versões compatíveis:
```
pip install numpy==1.26.4 opencv-python-headless==4.8.1.78 albumentations==1.3.1 --no-deps
```

## 📥 4. Clonar o projeto
```
git clone https://github.com/mindspore-lab/mindyolo.git
cd mindyolo
```

## 📁 5. Estrutura do Dataset

```
dataset/
 ├── images/
 │   ├── train/
 │   ├── val/
 │
 ├── labels/
 │   ├── train/
 │   ├── val/
 │
 ├── train.txt
 ├── val.txt
```

## 📁 5.1. Download do Dataset
```
https://drive.google.com/file/d/1q-o-TEWubit3msdnpfrKLhX4IcG_uJcw/view?usp=sharing
```

## 📝 6. Configurar Dataset
```
nano configs/coco.yaml
```

```
data:
  dataset_name: custom

  train_set: /CAMINHO/COMPLETO/train.txt
  val_set: /CAMINHO/COMPLETO/val.txt

  nc: 2
  names: ['objeto', 'dummy']
```

## 🚀 7. Treinar modelo (CPU)

```
python train.py \
  --config configs/yolov5/yolov5n.yaml \
  --device_target CPU \
  --epochs 50 \
  --per_batch_size 4 \
  --img_size 640 \
  --ms_jit False
```

## 📊 8. Resultado esperado

```
Epoch 1/50
```

Arquivos serão salvos em:
```
runs/
```

## 🧾 9. Logs

```
python train.py ... 2>&1 | tee treino.log
```

---

## 🔁 Fluxo de Treino

```
Coleta de Dados
      ↓
Anotação (COCO)
      ↓
Pré-processamento
      ↓
Treinamento (MindSpore)
      ↓
Validação
      ↓
Seleção do Modelo (best.ckpt)
      ↓
Deploy
```
