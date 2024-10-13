

# Projeto: Detecção de IPs Maliciosos com Redes Neurais em Grafos (GCN)

Este projeto utiliza uma Graph Convolutional Network (GCN) para a detecção de IPs maliciosos com base em dados reportados por agentes de monitoramento. Além disso, utilizamos **Label Propagation** para aprendizado semi-supervisionado e **XGBoost** para complementar o aprendizado e gerar previsões mais robustas.

## Sumário
- [Introdução](#introdução)
- [Instalação](#instalação)
- [Uso](#uso)
- [Descrição Técnica](#descrição-técnica)
- [Resultados](#resultados)
- [Contribuição](#contribuição)

## Introdução
O objetivo deste projeto é identificar IPs maliciosos a partir de dados de monitoramento, modelando-os como um grafo onde:
- Os **nós** representam os IPs.
- As **arestas** indicam que dois IPs foram reportados pelos mesmos agentes.

Utilizamos técnicas avançadas de aprendizado de máquina, incluindo:

- **Graph Convolutional Network (GCN)** para explorar as relações nos dados de grafos.
- **Label Propagation** para realizar aprendizado semi-supervisionado.
- **XGBoost** para refinar as previsões.

## Instalação
Para executar este projeto, instale as seguintes bibliotecas:

```bash
pip install torch==1.13.1
pip install torch_geometric
pip install torch_sparse
pip install torch_scatter
pip install networkx
pip install pyvis
pip install xgboost
pip install tensorboard
```

Além disso, certifique-se de ter um compilador **C++** configurado no sistema para compilar pacotes como `torch_sparse` e `torch_scatter`.

## Uso
1. Clone este repositório e baixe os dados necessários:
    - Coloque os arquivos `dataset1.csv`, `dataset2.csv` e `dataset3.csv` na pasta `dados/`.

2. Execute o notebook **Projeto4.ipynb** para:
    - Carregar e processar os dados.
    - Treinar o modelo.
    - Visualizar os resultados.

O notebook está dividido nas seguintes etapas:

1. **Carregamento e limpeza de dados:** Pré-processa os dados dos IPs maliciosos, agentes de monitoramento e provedores.
2. **Engenharia de atributos:** Aplicamos a transformação **Box-Cox** para normalizar a distribuição dos dados.
3. **Criação do grafo:** Modela os IPs como nós em um grafo, com arestas representando IPs reportados pelos mesmos agentes.
4. **Treinamento de GCN:** Treina uma Graph Convolutional Network para classificar os IPs.
5. **Avaliação:** Mede a precisão do modelo GCN no conjunto de teste.
6. **Label Propagation:** Propaga rótulos no grafo utilizando aprendizado semi-supervisionado.
7. **XGBoost:** Refina as previsões com um classificador baseado em árvores de decisão.

## Descrição Técnica

### Graph Convolutional Network (GCN)
- O GCN foi utilizado para modelar o grafo e classificar os IPs.
- A arquitetura tem duas camadas de convolução e uma camada de classificação.
- O treinamento foi realizado por **400 épocas** utilizando o otimizador **Adam** e a função de perda **CrossEntropyLoss**.

### Aprendizado Semi-Supervisionado com Label Propagation
- O Label Propagation propaga rótulos de IPs validados (rótulos conhecidos) para IPs não validados com base nas relações do grafo.

### Classificação com XGBoost
- O algoritmo **XGBoost** foi utilizado para construir um classificador robusto com base nas previsões do modelo semi-supervisionado.

## Resultados

- **Acurácia da GCN:** 82% no conjunto de teste.
- **Propagação de rótulos:** A técnica de Label Propagation alcançou uma precisão de 92%.
- **Classificação XGBoost:** Acurácia média de 88% utilizando validação cruzada.

## Contribuição
Este projeto está aberto a contribuições. Se você deseja melhorar o código ou adicionar novas funcionalidades:
- Envie um **pull request**.
- Abra uma **issue** com sugestões.
