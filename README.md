# Cognitive Cybersecurity

**Análise Comparativa entre ITOps e AIOps para Detecção de Ataques DDoS**

## Sobre o Projeto

Este projeto implementa uma análise comparativa entre abordagens tradicionais de ITOps (baseadas em regras estáticas) e modernas AIOps (baseadas em Machine Learning) para detecção de ataques DDoS em tráfego de rede.

**Autor:** Matheus Cardoso  
**Email:** matheus04042006@gmail.com  
**LinkedIn:** [linkedin.com/in/matheus-cardoso-70552b138](http://www.linkedin.com/in/matheus-cardoso-70552b138)

## Objetivo

Demonstrar a superioridade dos modelos de Machine Learning (AIOps) em relação aos sistemas tradicionais de monitoramento baseados em regras (ITOps) para identificação de tráfego malicioso, especificamente ataques DDoS.

## Dataset

O projeto utiliza o dataset **CICIDS2017-Friday-WorkingHours-Afternoon-DDos**, que contém:
- **225.745 registros** de tráfego de rede
- **79 features** descrevendo características dos fluxos
- **Classes:** BENIGN (97.718) e DDoS (128.027)

**Fonte:** [CICIDS2017 Dataset](https://raw.githubusercontent.com/norisjunior/FIAPML/refs/heads/main/datasets/CICIDS2017-Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv)

## Tecnologias Utilizadas

### Bibliotecas Python
- **Análise de Dados:** pandas, numpy
- **Visualização:** matplotlib, seaborn
- **Machine Learning:** scikit-learn, XGBoost, LightGBM

### Modelos de ML Implementados
1. **Random Forest Classifier**
2. **XGBoost Classifier** 
3. **LightGBM Classifier**

## Metodologia

### 1. Análise Exploratória
- Análise estatística das features principais
- Visualização de distribuições por classe
- Identificação de padrões nos dados

**Features analisadas:**
- Flow Duration
- Total Length of Fwd Packets
- Average Packet Size

### 2. Abordagem ITOps (Regras Estáticas)
Implementação de sistemas baseados em limiares fixos:

**Regra AND:** Alerta apenas quando TODAS as condições são atendidas
```python
if (flow_duration > threshold) AND 
   (fwd_packets > threshold) AND 
   (rst_flags > threshold):
    return "Alerta"
```

**Regra OR:** Alerta quando QUALQUER condição é atendida
```python
if (flow_duration > threshold) OR 
   (fwd_packets > threshold) OR 
   (rst_flags > threshold):
    return "Alerta"
```

### 3. Abordagem AIOps (Machine Learning)
Treinamento e avaliação de três modelos de ML com otimização de hiperparâmetros:

## Resultados

### ITOps Performance
- **Regra AND:** 0% de alertas (extremamente restritiva)
- **Regra OR:** 6.87% de alertas (alta taxa de falsos positivos)

### AIOps Performance
| Modelo | Acurácia | Precisão | Recall | F1-Score |
|--------|----------|----------|--------|----------|
| **LightGBM** | **99.998%** | **100.00%** | **99.996%** | **99.998%** |
| XGBoost | 99.996% | 99.996% | 99.996% | 99.996% |
| Random Forest | 99.993% | 100.00% | 99.988% | 99.994% |

## Estrutura do Projeto

```
cognitive-cybersecurity/
│
├── notebooks/
│   └── cognitive_cybersecurity_analysis.ipynb
│
├── data/
│   └── # Dataset baixado automaticamente via URL
│
├── results/
│   ├── confusion_matrices/
│   ├── performance_metrics/
│   └── visualizations/
│
└── README.md
```

## Como Executar

### Pré-requisitos
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm
```

### Execução
1. Clone o repositório
2. Execute o notebook Jupyter ou o script Python
3. O dataset será baixado automaticamente
4. Os resultados serão exibidos com gráficos e métricas

## Principais Insights

### Limitações do ITOps
- **Rigidez:** Regras fixas não se adaptam a novos padrões
- **Falsos Positivos/Negativos:** Dificuldade em balancear sensibilidade
- **Manutenção:** Necessidade constante de ajuste manual

### Vantagens do AIOps
- **Adaptabilidade:** Aprendizado contínuo com novos dados
- **Alta Precisão:** >99.99% de acurácia na detecção
- **Baixa Taxa de Erros:** Minimização de falsos positivos/negativos
- **Escalabilidade:** Capacidade de lidar com grandes volumes

## Análise Técnica

### Hiperparâmetros Otimizados

**Random Forest:**
- n_estimators: 200
- max_depth: None
- min_samples_split: 2

**XGBoost:**
- n_estimators: 300
- max_depth: 6
- learning_rate: 0.10

**LightGBM:**
- n_estimators: 400
- num_leaves: 31
- learning_rate: 0.05

### Features Mais Importantes
Análise das variáveis com maior poder preditivo para detecção de DDoS.

## Visualizações Incluídas

- Distribuições de features por classe
- Boxplots comparativos
- Matrizes de confusão
- Gráficos de performance
- Árvores de decisão
- Comparativos ITOps vs AIOps

## Conclusões

O projeto demonstra claramente que:

1. **AIOps supera ITOps** em todos os aspectos de performance
2. **Machine Learning** oferece detecção mais precisa e confiável
3. **Modelos ensemble** (RF, XGBoost, LightGBM) são altamente efetivos
4. **Automação inteligente** é essencial para cibersegurança moderna

## Trabalhos Futuros

- Implementação de modelos de Deep Learning
- Detecção de outros tipos de ataques
- Análise em tempo real
- Integração com sistemas SIEM
- Deployment em produção



---
