# Interpolação Espacial de Precipitação em Redes Pluviométricas Esparsas

**Uma Avaliação Comparativa de IDW, Krigagem e Splines em Contextos Sul-Americanos**

🌐 **Idioma / Language:** **Português** | [English](README.md)

---

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-pesquisa-blueviolet.svg)]()

> Parte da pesquisa de doutorado em Pesquisa Operacional na **UNIFESP / ITA**.
> Veja a visão geral da pesquisa: [PhD-Research-Operational-Research](https://github.com/roberval1994).

## Visão geral

Este projeto apresenta uma comparação reprodutível de três métodos clássicos de
interpolação espacial — **Inverso da Distância Ponderado (IDW)**, **Krigagem Ordinária**
e **Splines** — aplicados à estimativa de campos de precipitação em regiões com
**cobertura esparsa de pluviômetros**, cenário comum e desafiador em toda a América do Sul.

O objetivo é quantificar o comportamento de cada método quando as estações são poucas e
distribuídas de forma irregular, oferecendo orientação prática para a escolha do método
sob escassez de dados.

## Motivação

Superfícies confiáveis de precipitação são pré-requisito para modelagem hidrológica,
avaliação de risco de inundações e gestão de recursos hídricos. Em muitas bacias
sul-americanas a rede de monitoramento é esparsa, o que amplifica o erro de interpolação
e torna a escolha do método determinante. Este estudo avalia essa escolha de forma
sistemática.

## Métodos

| Método | Família | Propriedade principal |
|---|---|---|
| **IDW** | Determinístico | Simples, sem suposições sobre a estrutura espacial |
| **Krigagem Ordinária** | Geoestatístico | Modela a autocorrelação espacial via variograma, fornece incerteza |
| **Splines** | Determinístico (suavização) | Superfícies suaves, sensível aos parâmetros de tensão |

A avaliação usa **validação cruzada leave-one-out / k-fold** com as métricas:
**MAE**, **RMSE** e viés. Os parâmetros do variograma (efeito pepita, patamar, alcance)
são ajustados e reportados por conjunto de dados.

## Estrutura do repositório

```
.
├── notebooks/
│   ├── interpolation_test.ipynb              # Comparação central IDW vs Krigagem vs Splines
│   ├── Interpolation_Month.ipynb             # Experimentos com agregação mensal
│   └── analise_estatistica_complementar.ipynb# Análise estatística complementar
├── data/                                     # Dados das estações (ver seção Dados)
├── outputs/                                  # Figuras, variogramas, tabelas de métricas
├── requirements.txt
├── LICENSE
├── README.md                                 # Inglês
└── README.pt-BR.md                           # Português (este arquivo)
```

## Dados

O estudo utiliza dados de estações pluviométricas de diversas fontes sul-americanas,
organizados por região (São José dos Campos, Rio de Janeiro, São Paulo, Uruguai, entre
outras). Cada conjunto contém as coordenadas das estações e os registros de precipitação
usados como referência (ground truth) na validação cruzada.

> Os arquivos de dados estão incluídos em `data/`. Arquivos grandes são fornecidos compactados.

## Como começar

```bash
# 1. Clonar
git clone https://github.com/roberval1994/Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks.git
cd Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks

# 2. Criar ambiente e instalar dependências
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux / macOS
# source .venv/bin/activate
pip install -r requirements.txt

# 3. Abrir o Jupyter
jupyter notebook
```

## Principais resultados

- Comparação sistemática validada por validação cruzada entre IDW, Krigagem e Splines sob redes esparsas.
- Modelos de variograma ajustados por conjunto de dados (efeito pepita, patamar, alcance).
- Análise de sensibilidade do raio de busca / número de vizinhos.

Veja a pasta `outputs/` para as figuras e tabelas de métricas geradas.

## Tecnologias

`Python` · `NumPy` · `pandas` · `SciPy` · `scikit-learn` · `PyKrige` · `GeoPandas` · `Matplotlib`

## Como citar

Se utilizar este trabalho, por favor cite:

```bibtex
@misc{moreirafilho_spatial_interpolation,
  author       = {Moreira Filho, Roberval Gon{\c c}alves},
  title        = {Spatial Interpolation of Precipitation in Sparse Rainfall
                  Networks: A Comparative Evaluation of IDW, Kriging, and Splines
                  in South American Contexts},
  year         = {2026},
  howpublished  = {\url{https://github.com/roberval1994/Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks}}
}
```

## Autor

**Roberval Gonçalves Moreira Filho**
Cientista de Dados | Analista de Pesquisa Operacional — Doutorando, UNIFESP/ITA

[![Email](https://img.shields.io/badge/Email-roberval.researcher.or%40outlook.com-red)](mailto:roberval.researcher.or@outlook.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-robervalOr-blue)](https://www.linkedin.com/in/robervalOr)
[![GitHub](https://img.shields.io/badge/GitHub-roberval1994-black)](https://github.com/roberval1994)

## Licença

Distribuído sob a Licença MIT. Veja [LICENSE](LICENSE).
