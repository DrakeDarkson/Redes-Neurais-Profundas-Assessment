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