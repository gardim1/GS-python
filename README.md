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
### Para instalar utilize os comandos a seguir:
```python
!pip install roboflow
!pip install inference_sdk
!pip install ultralytics==8.0.196
```
## Configuração do Projeto

Antes de utilizar o detector de lixo, é necessário configurar a API do Roboflow. Você precisará de uma chave de API válida para isso. 

```python

from roboflow import Roboflow

rf = Roboflow(api_key="SUA_CHAVE_DE_API")
project = rf.workspace("nome_do_workspace").project("nome_do_projeto")
version = project.version(numero_da_versao)
dataset = version.download("yolov8")

```
 Uso do Projeto



Saidas:
```markdown
Os outputs mostrarao a % de predicao. ex: quanto mais proximo de 1.00 (100%) mais proximo do objeto detectado na imagem ser oq procuramos, no caso, o lixo
```
## Uso do Projeto

Para utilizar o detector de lixo, siga estes passos:

1. Importe as bibliotecas, baixe o dataset e configure o modelo utilizando o Roboflow:

```python
from roboflow import Roboflow
from inference_sdk import InferenceHTTPClient
import cv2
from google.colab.patches import cv2_imshow

# Configurar a API do Roboflow
rf = Roboflow(api_key="SUA_CAHVE_API")
project = rf.workspace("nome_do_workspace").project("nome_do_projeto")
version = project.version(numero_da_versao)

# Baixar o dataset e configurar o modelo
dataset = version.download("yolov8")
```
2. Configure o cliente de inferência
```python
CLIENT = InferenceHTTPClient(
    api_url="https://detect.roboflow.com",
    api_key="SUA_CHAVE_API"
)

```
3. Carregue a imagem no colab
```python
img_lixo = cv2.imread('caminho_da_imagem')
cv2_imshow(img_lixo)
```
4. Use o modelo treinado na inferencia
```python
result = CLIENT.infer(
    img_lixo,
    model_id="nome_do_modelo"
)
```
5. Output + estrutura logica e concatenacao para fins de melhor leitura
```python
print(result)

if result['predictions']:
    classe = result['predictions'][0]['class']
    confianca = result['predictions'][0]['confidence']
    print(f"Classe: {classe} - Confiança: {confianca:.2f}%")
else:
    print("Nenhuma predição encontrada.")
```
###  Conclusão

Esse programa pode ser utulizado para a detectacao de lixo presente nos eceanos, rios, mares, etc.

Exemplo:
```markdown

O detector de lixo desenvolvido utilizando YOLOv8 e Roboflow oferece uma solução eficiente para identificar objetos de lixo em imagens. Com a capacidade de inferir em tempo real, este modelo pode ser útil em uma variedade de aplicações, desde a limpeza urbana até a conscientização ambiental.


