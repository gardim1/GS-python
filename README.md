# GS- Computational Thinking With Python
 Camila Feitosa RM:558808 
 
 Gustavo Berlanga RM:555298
 
 Vinicius Gardim RM:556013
# Projeto Detector de Lixo usando YOLOv8 e Roboflow

Este projeto consiste em um detector de lixo desenvolvido utilizando a técnica de deep learning com o modelo YOLOv8 e a plataforma Roboflow para treinamento e inferência. O detector é capaz de identificar objetos de lixo em imagens.
## Requisitos e Dependências

Para utilizar este projeto, você precisa ter as seguintes dependências instaladas:

- Python 3.x
- Pacotes Python:
  - roboflow
  - inference_sdk
  - ultralytics==8.0.196
  - cv2
  - google.colab
## Configuração do Projeto

Antes de utilizar o detector de lixo, é necessário configurar a API do Roboflow. Você precisará de uma chave de API válida para isso. 

```python
from roboflow import Roboflow

# Configurar a API do Roboflow
rf = Roboflow(api_key="SUA_CHAVE_DE_API")

### 4. Uso do Projeto

Explique como usar o projeto, fornecendo exemplos de código ou instruções passo a passo. Isso pode incluir como executar o código, fornecer inputs, e o que esperar como output.

Exemplo:
```markdown
## Uso do Projeto

Para utilizar o detector de lixo, siga estes passos:

1. Baixe o dataset e configure o modelo utilizando o Roboflow:

```python
project = rf.workspace("NOME_DO_SEU_WORKSPACE").project("NOME_DO_SEU_PROJETO")
version = project.version(VERSÃO_DO_MODELO)
dataset = version.download("yolov8")
import cv2
from google.colab.patches import cv2_imshow

img_lixo = cv2.imread('CAMINHO_DA_SUA_IMAGEM')
cv2_imshow(img_lixo)
from inference_sdk import InferenceHTTPClient

# Configurar o cliente de inferência
CLIENT = InferenceHTTPClient(
    api_url="https://detect.roboflow.com",
    api_key="SUA_CHAVE_DE_API"
)

# Realizar a inferência da imagem
result = CLIENT.infer(
    img_lixo,
    model_id="detector-de-lixo-qxxca/2"
)

# Imprimir os resultados da inferência
if result['predictions']:
    classe = result['predictions'][0]['class']
    confianca = result['predictions'][0]['confidence']
    print(f"Classe: {classe} - Confiança: {confianca:.2f}%")
else:
    print("Nenhuma predição encontrada.")




```

### 5. Conclusão

Esse programa pode ser utulizado para a detectacao de lixo presente nos eceanos, rios, mares, etc.

Exemplo:
```markdown

O detector de lixo desenvolvido utilizando YOLOv8 e Roboflow oferece uma solução eficiente para identificar objetos de lixo em imagens. Com a capacidade de inferir em tempo real, este modelo pode ser útil em uma variedade de aplicações, desde a limpeza urbana até a conscientização ambiental.


