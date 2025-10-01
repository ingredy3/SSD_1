# 🚗 MVP - Sistema de Suporte à Decisão: Previsão de Preço de Veículos Usados

## 📖 Definição do Problema
O mercado de veículos usados possui alta variação de preços, influenciada por fatores como ano, marca, modelo, quilometragem, estado de conservação e localização.  
Prever corretamente o preço de venda ajuda concessionárias, lojistas e consumidores a tomarem decisões mais informadas.  

Este projeto tem como objetivo **criar um modelo preditivo para estimar o preço de venda de veículos usados**, utilizando dados públicos de um dataset do Kaggle.

---

## 🎯 Hipótese
- **Hipótese principal:** Veículos mais novos e com menor quilometragem tendem a ter preços de venda mais altos.  
- **Hipóteses secundárias:**  
  - A marca e o modelo exercem grande influência no preço.  
  - Variáveis como estado e cor do veículo têm menor impacto.

---

## 📊 Conjunto de Dados
O dataset utilizado foi **[Car Prices Dataset (Kaggle)]([https://www.kaggle.com/](https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data/data))**.  

- Total de registros: ~150.000 veículos  
- Principais variáveis:  
  - `year` → Ano de fabricação  
  - `make` → Marca  
  - `model` → Modelo  
  - `body` → Tipo de carroceria  
  - `transmission` → Transmissão  
  - `condition` → Condição do veículo  
  - `odometer` → Quilometragem  
  - `state` → Estado (EUA)  
  - `sellingprice` → Preço de venda (variável alvo)

---

## 🛠️ Metodologia

1. **Importação dos dados** via Kaggle API e Pandas.  
2. **EDA (Exploração dos Dados):**  
   - Identificação de valores nulos.  
   - Análise estatística das variáveis.  
   - Identificação de outliers (carros com preços ou quilometragens fora da faixa).  
3. **Pré-processamento:**  
   - Tratamento de valores faltantes.  
   - Criação da variável `vehicle_age` (idade do carro).  
   - Tratamento da variável `odometer` (eliminação de valores fora da faixa).  
   - Redução da cardinalidade (agrupamento de marcas e modelos raros).  
4. **Modelagem:**  
   - Modelos testados: **Baseline (Dummy Median), Regressão Linear, Random Forest**.  
   - Divisão em treino (80%) e teste (20%).  
   - Métricas utilizadas: MAE, RMSE e R².  
5. **Avaliação e Seleção:**  
   - Comparação entre os modelos.  
   - Escolha do **Random Forest** como melhor modelo.  
6. **Visualizações:**  
   - Distribuição de preços.  
   - Real vs. Predito.  
   - Distribuição dos resíduos.  
   - Distribuição dos anos.  
   - Importância das variáveis (Permutation Importance).  

---

## 📈 Resultados

### Modelos testados
- **Baseline (Dummy median)** → Serve apenas como referência mínima.  
- **Regressão Linear** → Melhor que o baseline, mas limitado em relações complexas.  
- **Random Forest** → Melhor desempenho geral.  

### Métricas finais do modelo escolhido (Random Forest):
- **MAE (Erro Médio Absoluto):** ≈ R$ 2.892  
- **RMSE (Raiz do Erro Quadrático Médio):** ≈ R$ 4.678  
- **R² (Coeficiente de Determinação):** ≈ 0.75  

### Interpretação:
- O modelo consegue explicar cerca de **75% da variação dos preços**.  
- Em média, o erro é de ≈ **R$ 2.900 por carro**.  
- As variáveis mais importantes foram:  
  - **Idade do veículo (`vehicle_age`)**  
  - **Quilometragem (`odometer`)**  
  - **Marca/Modelo (`make`, `model`)**

---

## 📊 Visualizações
- Distribuição dos preços → maioria dos carros custa menos de R$ 20.000, com outliers caros.  
- Real vs. Predito → bom ajuste no centro, maior erro nos extremos (carros muito baratos ou caros).  
- Resíduos → centrados em zero, mas com cauda longa (outliers).  
- Distribuição dos anos → maioria dos veículos entre 2007 e 2013.  
- Importância das features → idade, quilometragem e marca/modelo dominam.

---

## ✅ Conclusão
- A hipótese foi confirmada: carros mais novos e com menor quilometragem realmente tendem a ter preços mais altos.  
- O modelo **Random Forest** apresentou melhor desempenho entre os testados.  
- A análise mostrou coerência com o mercado automotivo real.  

---

## 🚀 Próximos Passos
- Melhorar tratamento de **outliers**.  
- Aplicar **otimização de hiperparâmetros** no Random Forest.  
- Testar outros modelos mais avançados (ex.: Gradient Boosting, XGBoost).  
- Explorar segmentação do mercado (carros populares vs. premium).  
- Disponibilizar uma **API de previsão** para consultas em tempo real.

---

## 📂 Estrutura do Projeto
