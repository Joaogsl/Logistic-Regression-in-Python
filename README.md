# Predição de Risco de Óbito por SRAG (COVID-19/Influenza) 

Este projeto desenvolve um modelo de classificação binária utilizando **Regressão Logística** para prever o risco de óbito em pacientes hospitalizados com Síndrome Respiratória Aguda Grave (SRAG).
Desenvolvido como parte da disciplina de **Métodos Quantitativos para Análise Multivariada (MQAM)** na EACH-USP.

## Contexto e Objetivo
Utilizando dados reais do SIVEP-Gripe, o objetivo é identificar pacientes com alto risco de evolução para óbito (`target = 1`)
Dada a natureza crítica do problema, o modelo prioriza a **Sensibilidade (Recall)** para atuar como uma ferramenta segura de triagem médica, minimizando Falsos Negativos.

## Desafios e Estratégia
- **Desbalanceamento Severo:** A base apresentava 92.4% de casos de cura e apenas 7.6% de óbitos.
- **Seleção de Features (Lasso):** Utilização de **Regularização L1 (Lasso)** para seleção automática de variáveis em um dataset de alta dimensionalidade, lidando com a multicolinearidade entre sintomas.
- **Calibração de Limiar:** Ajuste do *threshold* de decisão (de 0.5 para ~0.029) para maximizar a detecção de casos graves.

## Resultados
A calibração transformou o modelo de uma ferramenta estatística conservadora em um instrumento de triagem eficaz:

| Métrica | Modelo Padrão (Limiar 0.5) | Modelo Calibrado (Limiar Otimizado) |
| :--- | :---: | :---: |
| **Recall (Sensibilidade)** | < 30% | **> 95%** |
| **Falsos Negativos** | 4.159 (Alto Risco) | **285 (Minimizado)** |

*Dados baseados na matriz de confusão do conjunto de teste.*

### Achados Clínicos:
- **Fatores de Risco:** Idade avançada, admissão em UTI, dispneia e saturação baixa foram confirmados como os maiores preditores de óbito.
- **Fatores de Proteção:** O uso de suporte ventilatório não invasivo mostrou forte correlação com a sobrevivência, indicando quadros menos críticos que a intubação.
- **Ajuste Etário:** A inclusão de faixas etárias revelou riscos não-lineares específicos para o grupo de 18-39 anos.

## Autores
* **João Gabriel de Senna Lamolha**
* Gustavo Pompermayer Fulanetti Silva
