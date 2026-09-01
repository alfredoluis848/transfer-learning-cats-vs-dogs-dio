# Transfer Learning - Cats vs Dogs

Projeto desenvolvido como parte do desafio de **Transfer Learning** da formação **Machine Learning Specialist - DIO**.

## Objetivo

Aplicar Transfer Learning em uma rede de Deep Learning para realizar classificação binária de imagens entre gatos e cachorros.

O projeto foi desenvolvido em Python utilizando TensorFlow e Google Colab.

## Dataset

Foi utilizado o dataset **Cats vs Dogs**, contendo imagens organizadas nas classes:

- Cat
- Dog

Antes do treinamento, os dados foram analisados e arquivos inválidos ou corrompidos foram removidos.

As imagens foram redimensionadas para:

`224 x 224 x 3`

Os dados foram divididos aproximadamente em:

- 80% treinamento
- 10% validação
- 10% teste

## Transfer Learning

Foi utilizada a arquitetura **MobileNetV2**, previamente treinada no dataset ImageNet.

O classificador original da rede foi removido utilizando:

`include_top=False`

Os pesos da base MobileNetV2 foram congelados durante o treinamento inicial, permitindo utilizar a rede como extratora de características.

Sobre essa base foram adicionadas as camadas:

- GlobalAveragePooling2D
- Dropout (0.2)
- Dense com ativação sigmoid

A camada final possui apenas um neurônio por se tratar de um problema de classificação binária.

## Treinamento

O modelo foi treinado utilizando:

- Optimizer: Adam
- Learning rate: 0.001
- Loss: Binary Crossentropy
- Métrica: Accuracy
- Épocas: 5

## Resultados

O modelo apresentou aproximadamente:

| Métrica | Resultado |
|---|---:|
| Acurácia final de treinamento | 92,85% |
| Acurácia final de validação | 94,24% |
| Acurácia no teste | **94,87%** |
| Loss no teste | **0,1377** |

Os resultados mostraram boa capacidade de generalização para imagens não utilizadas durante o treinamento.

Não foram observados sinais fortes de overfitting durante as cinco épocas utilizadas.

## Exemplo de predição

O modelo produz uma probabilidade entre 0 e 1 utilizando uma função sigmoid:

- valores menores que 0,5 → Cat
- valores maiores ou iguais a 0,5 → Dog

As previsões realizadas sobre imagens do conjunto de teste apresentaram resultados coerentes com as classes reais.

## Tecnologias utilizadas

- Python
- TensorFlow / Keras
- MobileNetV2
- Matplotlib
- Pillow
- Google Colab

## Estrutura do projeto

```text
.
├── README.md
└── transfer_learning_cats_vs_dogs.ipynb
