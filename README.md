# Redes Neurais Profundas - Assessment

O repositório contém dois projetos aplicados de deep learning implementados em PyTorch, juntamente com os logs do TensorBoard e os recursos necessários para reproduzir os experimentos.

## Projetos

### Projeto 1 — Pipeline MLP

Aplicação de um Multilayer Perceptron (MLP) ao conjunto de dados UCI Energy Efficiency.

O projeto aborda:

- Classificação e regressão;
- Implementação explícita de MLP com `torch.nn.Module`;
- Divisão dos dados em treino, validação e teste;
- Treinamento baseado em DataLoader;
- Comparação de funções de ativação;
- Experimentos com inicialização de pesos;
- Batch Normalization;
- Dropout;
- Monitoramento da norma dos gradientes;
- Otimização com Adam/AdamW;
- Agendamento da taxa de aprendizado;
- Monitoramento com TensorBoard;
- Salvamento de checkpoints do modelo;
- Diagnóstico do treinamento.

As métricas de regressão incluem MAE, RMSE and R² e a avaliação de classificação inclui métricas de desempenho e análise da matriz de confusão.

### Projeto 2 — Reconhecimento de Atividades Humanas com GRU

Reconhecimento de Atividades Humanas a partir de dados temporais de sensores utilizando uma Gated Recurrent Unit (GRU), o projeto aplica a dados sequenciais o pipeline de treinamento e diagnóstico desenvolvido no Projeto 1.

Uma arquitetura CNN 1D também é discutida como uma alternativa entre diferentes paradigmas.

## Estrutura do Repositório

```text
.
├── project_1_mlp/
│   ├── notebooks/
│   ├── checkpoints/
│   └── artifacts/
│
├── project_2_gru/
│   ├── notebooks/
│   ├── checkpoints/
│   └── artifacts/
│
├── runs/
├── requirements.txt
├── environment.yml
├── .gitignore
└── README.md
```

## Execução do Projeto 1

O Projeto 1 utiliza o ambiente Conda definido em `environment.yml`. A partir da raiz do repositório, crie o ambiente com:

```bash
conda env create -f environment.yml
```

Em seguida, ative o ambiente:

```bash
conda activate deep-neural-networks
```

Caso o ambiente já tenha sido criado anteriormente, ele pode ser atualizado com:

```bash
conda env update -f environment.yml --prune
```

Para disponibilizar o ambiente como kernel do Jupyter, execute:

```bash
python -m ipykernel install --user --name deep-neural-networks --display-name "Python (deep-neural-networks)"
```

### Inicialização do JupyterLab

Com o ambiente `deep-neural-networks` ativo e estando na raiz do repositório, inicialize o JupyterLab com:

```bash
jupyter lab
```

No JupyterLab, abra o notebook:

```text
project_1_mlp/notebooks/01_energy_efficiency.ipynb
```

Selecione o kernel:

```text
Python (deep-neural-networks)
```

Para reproduzir todo o pipeline do Projeto 1, reinicie o kernel e execute todas as células do notebook em sequência. A execução realiza o carregamento e pré-processamento dos dados, os experimentos de classificação, os diagnósticos de estabilidade, a variante de regressão, a avaliação final e a geração dos checkpoints e artefatos.

### TensorBoard

Os logs produzidos durante os experimentos são armazenados em `runs/`. Para visualizar os experimentos do Projeto 1 fora do notebook, execute na raiz do repositório:

```bash
tensorboard --logdir runs/project_1
```

O endereço exibido pelo TensorBoard pode então ser aberto no navegador para acompanhar curvas de loss, métricas, learning rate e normas dos gradientes.