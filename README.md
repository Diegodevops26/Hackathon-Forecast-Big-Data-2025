# 📊 Previsão de Vendas - Hackathon Big Data 2025

## 👤 Autor
- **Diego Sousa dos Santos**  

---

## 🎯 Desafio
O objetivo deste desafio é prever a **quantidade de vendas semanais** por **ponto de venda (PDV)** e **produto**, utilizando dados históricos fornecidos pela organização.  

A métrica oficial de avaliação é o **WMAPE (Weighted Mean Absolute Percentage Error)**, onde valores mais próximos de **0** indicam melhor desempenho.  

---

## 🛠️ Abordagem da Solução
A solução foi desenvolvida em **Google Colab** (Python 3.10) utilizando bibliotecas de ciência de dados e aprendizado de máquina.  

O armazenamento e exportação dos arquivos foram feitos diretamente no **Google Drive**.  

---

## 🔎 Etapas do pipeline

### 1. Pré-processamento dos dados
- Tratamento de valores ausentes.  
- Conversão de colunas de data para semana (`pd.to_datetime` + `isocalendar().week`).  
- Criação de variáveis derivadas (features de sazonalidade, médias móveis, lags, etc).  
- Codificação de variáveis categóricas (`pdv`, `produto`).  

### 2. Modelagem
Testei diferentes algoritmos de previsão:  
- Regressão Linear  
- Random Forest  
- XGBoost  
- LightGBM  

O modelo final escolhido foi **XGBoost**, por apresentar melhor resultado no WMAPE.  
Ajuste de hiperparâmetros foi feito com **Optuna** para otimização automática.  

### 3. Validação
- Divisão dos dados respeitando a ordem temporal (**TimeSeriesSplit**).  
- Métrica de validação: **WMAPE**.  
- Resultado obtido no conjunto de validação:  

---

## 🧑‍💻 Autor

* **[Diego Sousa dos Santos]**
    * [LinkedIn](www.linkedin.com/in/diegosousasantosdev)
    * [GitHub](https://github.com/Diegodevops26)

---

## 📜 Licença

Este projeto está distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
