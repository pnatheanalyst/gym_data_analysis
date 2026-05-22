# Análise de Cancelamentos do Ginásio

Este projeto contém uma análise exploratória dos cancelamentos dos clientes de um ginásio, realizada no notebook `main.ipynb`. O objetivo é identificar quais fatores estão associados às altas taxas de cancelamento e quais ações podem ajudar a reduzir esse impacto.

## Objetivo

- Entender por que o ginásio tem taxas de cancelamento significativas.
- Identificar padrões nos clientes que cancelam.
- Destacar fatores que podem ser priorizados para reduzir a rotatividade.

## Dados

O conjunto de dados está em `cancelamentos.csv` e contém informações sobre clientes e seu comportamento antes do cancelamento.

### Principais passos da análise

1. Carregamento e limpeza dos dados
   - Importação do arquivo CSV com `pandas`.
   - Remoção da coluna `CustomerID`, que não é relevante para a análise.
   - Exclusão de linhas com valores ausentes usando `dropna()`.

2. Análise inicial
   - Contagem dos clientes que cancelaram (`cancelou`) e que não cancelaram.
   - Cálculo das porcentagens de cancelamento.
   - Análise da distribuição da duração do contrato (`duracao_contrato`) entre os clientes.

3. Filtro de contratos mensais
   - Observou-se que contratos mensais aumentam a taxa de cancelamento.
   - A análise posterior foi feita retirando os clientes com contrato `monthly` para focar em outros fatores.

4. Análise por tipo de assinatura
   - Verificação da distribuição de `assinatura` e sua relação com o cancelamento.
   - Agrupamento por `assinatura` para calcular médias de variáveis numéricas por tipo de plano.

5. Visualização e investigação profunda
   - Uso de `plotly.express` para gerar histogramas de todas as colunas, coloridos por status de cancelamento.
   - Identificação de padrões visuais que ajudam a entender o comportamento dos cancelantes.

## Principais descobertas

- A taxa de cancelamento era elevada, próxima de 43% após remover contratos mensais.
- Dois fatores muito importantes foram identificados:
  - Clientes que fizeram mais de 6 ligações ao call center apresentaram uma probabilidade muito alta de cancelamento.
  - Clientes com mais de 20 dias de atraso também tiveram maior probabilidade de cancelar.
- Ao filtrar clientes com `ligacoes_callcenter <= 6` e `dias_atraso <= 20`, a taxa de cancelamento caiu de 43% para 35%.

## Conclusões

- `ligacoes_callcenter` e `dias_atraso` são sinais importantes de risco de cancelamento.
- Reduzir o volume de chamadas de suporte e diminuir o número de dias em atraso pode ser uma prioridade para reduzir a rotatividade.

## Tecnologias usadas

- Python
- pandas
- plotly.express

## Como usar

1. Abra o notebook `main.ipynb`.
2. Execute as células na ordem para reproduzir a análise.
3. Certifique-se de que o arquivo `cancelamentos.csv` esteja no mesmo diretório do notebook.

