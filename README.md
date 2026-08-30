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

As métricas de regressão incluem MAE, RMSE e R², e a avaliação de classificação inclui métricas de desempenho e análise da matriz de confusão.

### Projeto 2 — Reconhecimento de Atividades Humanas com GRU

Reconhecimento de atividades humanas a partir de dados temporais de sensores utilizando uma Gated Recurrent Unit (GRU). O projeto aplica a dados sequenciais o pipeline de treinamento e diagnóstico desenvolvido no Projeto 1.

Uma arquitetura CNN 1D também é discutida como alternativa de uma família arquitetural diferente para o mesmo problema.

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

## Configuração do ambiente

O assessment utiliza o ambiente Conda definido em `environment.yml`. A partir da raiz do repositório, crie o ambiente com:

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

## Inicialização do JupyterLab

Com o ambiente `deep-neural-networks` ativo e estando na raiz do repositório, inicialize o JupyterLab com:

```bash
jupyter lab
```

Selecione o kernel:

```text
Python (deep-neural-networks)
```

## Execução do Projeto 1

No JupyterLab, abra o notebook:

```text
project_1_mlp/notebooks/01_energy_efficiency.ipynb
```

Para reproduzir todo o pipeline do Projeto 1, reinicie o kernel e execute todas as células do notebook em sequência. A execução realiza o carregamento e o pré-processamento dos dados, os experimentos de classificação, os diagnósticos de estabilidade, a variante de regressão, a avaliação final e a geração dos checkpoints e artefatos.

### TensorBoard — Projeto 1

Os logs produzidos durante os experimentos são armazenados em `runs/project_1/`. Para visualizá-los, execute na raiz do repositório:

```bash
tensorboard --logdir runs/project_1
```

O endereço exibido pelo TensorBoard pode então ser aberto no navegador para acompanhar curvas de loss de treino e validação, métricas de desempenho, learning rate e normas dos gradientes.

## Execução do Projeto 2

No JupyterLab, abra o notebook:

```text
project_2_gru/notebooks/01_har_gru.ipynb
```

Para reproduzir todo o pipeline do Projeto 2, reinicie o kernel e execute todas as células do notebook em sequência. O notebook realiza automaticamente o download e a preparação do UCI Human Activity Recognition Using Smartphones Dataset, a divisão dos dados por participante, a padronização dos sinais, o treinamento do baseline, os experimentos com GRU, o diagnóstico do modelo, a avaliação final e a geração dos checkpoints e artefatos.

### TensorBoard — Projeto 2

Os logs do Projeto 2 são armazenados em `runs/project_2/`. Para visualizá-los, execute:

```bash
tensorboard --logdir runs/project_2
```

Os experimentos registram loss de treino e validação, accuracy, Macro F1, learning rate e normas dos gradientes.

## Checkpoints e artefatos

Os melhores estados dos modelos são armazenados nas pastas:

```text
project_1_mlp/checkpoints/
project_2_gru/checkpoints/
```

Os resultados auxiliares produzidos pelos notebooks, como tabelas, métricas, auditorias e figuras utilizadas nas análises, são armazenados em:

```text
project_1_mlp/artifacts/
project_2_gru/artifacts/
```

Os checkpoints são salvos por meio de `state_dict` e podem ser reconstruídos executando os respectivos notebooks.

## Reprodutibilidade

Os notebooks foram estruturados para execução sequencial a partir de um kernel reiniciado. As versões das dependências utilizadas estão registradas em `environment.yml` e `requirements.txt`.

O diretório `runs/` contém os logs do TensorBoard dos Projetos 1 e 2, incluindo curvas de loss de treino e validação, learning rate e métricas de desempenho por época.
