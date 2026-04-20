# 🚀 Treinamento Modelo de IA com MindSpore (CPU)

### 🚀 PARTE 1 — TREINAMENTO

## 🎯 Objetivo

Treinar modelos YOLO (YOLOv5) usando **MindSpore 2.6 em CPU**, com ambiente estável e reproduzível.

---

## 🧱 Requisitos

- Linux (Ubuntu / Pop_OS recomendado)
- Python **3.10**
- CPU (não precisa GPU)
- Git instalado

---

## ⚙️ 1. Criar ambiente virtual

```bash
python3.10 -m venv ~/ms26
source ~/ms26/bin/activate
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

Organize assim:
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
## 📝 6. Configurar Dataset
Editar arquivo:
```
nano configs/coco.yaml
```

Substituir por:

```
data:
  dataset_name: custom

  train_set: /CAMINHO/COMPLETO/train.txt
  val_set: /CAMINHO/COMPLETO/val.txt

  nc: 2
  names: ['objeto', 'dummy']
```

⚠️ Ajuste:

 - nc: número de classes
 - names: nomes das classes

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
Se tudo estiver correto:

```
Epoch 1/50
```

Arquivos serão salvos em:

```
runs/
```

## 🧾 9. Logs

Salvar saída do treino:

```
python train.py ... 2>&1 | tee treino.log
```

🚀 PARTE 2 — Exportar modelo (.ckpt → ONNX)

🎯 Objetivo

Transformar o modelo treinado em ONNX para:

 - usar em outros frameworks
 - rodar inferência rápida
 - deploy

## 📁 1. Localizar o modelo treinado

Após treino:

```
runs/2026.xx.xx/weights/
```

Você terá algo como:

```
best.ckpt
last.ckpt
```
