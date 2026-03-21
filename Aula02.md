# Fundamentos IA IA Generativa e Prompting Aula 02 11 mar 26


## Pergunta 1: Prompt Genérico
o que é Machine Learning .

**Resposta:**
```python 
Python Machine Learning (Aprendizado de Máquina) é um ramo da Inteligência Artificial que permite que sistemas aprendam padrões a partir de dados e façam previsões ou decisões sem serem explicitamente programados para cada tarefa.  
```

---

## Pergunta 2: Prompt Elaborado
Pergunta:
Considerando um cenário em que uma empresa deseja prever o churn de clientes em uma plataforma de streaming, descreva detalhadamente como você aplicaria técnicas de Machine Learning. Inclua explicações sobre pré-processamento dos dados, escolha de algoritmos, métricas de avaliação e possíveis melhorias no modelo, justificando cada decisão com base em boas práticas da área.

**Resposta:**  
```
Para prever o churn de clientes em uma plataforma de streaming, o processo de Machine Learning poderia ser estruturado da seguinte forma:

### 1. Coleta e Pré-processamento de Dados
- **Coleta:** extrair dados históricos de uso da plataforma, como número de logins, tempo assistido, interações com conteúdo, reclamações ou cancelamentos.  
- **Limpeza:** remover valores faltantes ou inconsistentes.  
- **Transformação:** normalizar dados numéricos, codificar variáveis categóricas (ex.: tipo de assinatura, país).  
- **Engenharia de Features:** criar métricas relevantes, como frequência média de uso por semana ou número de dispositivos conectados.  

### 2. Escolha de Algoritmo
- Inicialmente, modelos supervisionados de classificação, pois temos dados rotulados (churn: sim ou não).  
- Exemplos:  
  - **Árvore de decisão / Random Forest:** fácil interpretação, captura interações não lineares.  
  - **Gradient Boosting (XGBoost, LightGBM):** alto desempenho em problemas tabulares.  
  - **Redes neurais:** útil se houver muitos dados e padrões complexos.

### 3. Métricas de Avaliação
- **Acurácia:** útil, mas pode ser enganosa se o dataset estiver desbalanceado.  
- **Precision e Recall:** medir corretamente clientes que vão cancelar (churn) e reduzir falsos positivos.  
- **F1-Score:** equilíbrio entre precisão e recall.  
- **AUC-ROC:** avaliar capacidade do modelo de separar classes.
```


- **Monitoramento contínuo:** atualizar o modelo com novos dados e detectar mudanças no comportamento dos clientes.

> Cada passo é baseado em boas práticas para garantir que o modelo seja preciso, confiável e interpretable, ajudando a empresa a tomar decisões estratégicas para reduzir churn.
>
> A resposta da **Pergunta 2 (prompt elaborado)** foi mais útil, pois forneceu um detalhamento passo a passo do processo de aplicação de Machine Learning no contexto real de previsão de churn. A estrutura organizada em seções claras — pré-processamento, escolha de algoritmos, métricas e melhorias — reduziu a ambiguidade, tornando cada decisão explícita e justificável, o que facilita a compreensão e aplicação prática do conteúdo.

