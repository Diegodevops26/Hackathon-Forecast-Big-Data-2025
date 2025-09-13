# Previsão de Vendas para Varejo 🏪

Este repositório contém a solução desenvolvida para o desafio de previsão de vendas semanais, com o objetivo de apoiar o setor de varejo na otimização da reposição de estoque.

---

## 🎯 Objetivo do Desafio

Desenvolver um modelo de previsão de vendas (*forecast*) para prever a quantidade semanal de vendas por **PDV** (Ponto de Venda) e **SKU** (Unidade de Manutenção de Estoque) para as cinco semanas de janeiro de 2023, utilizando como base o histórico de vendas de 2022.

---

## 📂 Estrutura dos Dados

Para o desenvolvimento do modelo, foram utilizados os seguintes conjuntos de dados referentes ao ano de 2022:

* **Transações:** Contém o histórico de vendas.
    * `Data`, `PDV`, `Produto`, `Quantidade`, `Faturamento`.
* **Cadastro de Produtos:** Metadados dos produtos.
    * `Produto`, `Categoria`, `Descrição`, e até 4 atributos adicionais.
* **Cadastro de PDVs:** Metadados dos pontos de venda.
    * `PDV`, `On/Off Prem`, `Categoria`, `Zipcode`.

*Observação: Os arquivos de dados não estão incluídos neste repositório por questões de tamanho e privacidade. A estrutura de pastas para a execução do projeto pressupõe que eles sejam colocados no diretório `/data/raw`.*

---

## 🛠️ Metodologia Aplicada

A solução foi desenvolvida seguindo as etapas clássicas de um projeto de Machine Learning:

1.  **Análise Exploratória de Dados (EDA):**
    * Investigação da distribuição das vendas ao longo do tempo para identificar tendências, sazonalidades e padrões.
    * Análise de correlação entre as vendas e os atributos de produtos e PDVs.
    * Verificação de dados faltantes e outliers.

2.  **Engenharia de Features (Feature Engineering):**
    * Criação de *features* temporais (semana do ano, dia da semana, mês).
    * Criação de *features* de *lag* (vendas da semana anterior para o mesmo par PDV/SKU).
    * Criação de *features* de janela móvel (média móvel de vendas nas últimas 4 semanas).
    * Agregação de dados para consolidar as vendas em uma base semanal.

3.  **Modelagem:**
    * O modelo escolhido para a previsão foi o **[Ex: XGBoost Regressor]**, um algoritmo baseado em *gradient boosting* conhecido por sua alta performance em competições e problemas tabulares.
    * **[Opcional, se usou mais de um]** Outros modelos como LightGBM e SARIMA foram testados, mas o XGBoost apresentou os melhores resultados na validação.

4.  **Validação:**
    * A validação do modelo foi realizada utilizando uma estratégia de *time series split*, onde as últimas 4 semanas de 2022 foram usadas como conjunto de validação para simular o cenário real de previsão. A métrica de avaliação principal foi o **[Ex: Erro Médio Absoluto (MAE)]**.

---

## 🚀 Como Executar o Projeto

Siga os passos abaixo para replicar o ambiente e gerar as previsões.

### **Pré-requisitos**

* Python 3.9+
* Git

### **Passo a Passo**

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/](https://github.com/)[SEU_USUARIO]/[NOME_DO_REPOSITORIO].git
    cd [NOME_DO_REPOSITORIO]
    ```

2.  **Crie e ative um ambiente virtual:**
    ```bash
    # Para Linux/macOS
    python3 -m venv venv
    source venv/bin/activate

    # Para Windows
    python -m venv venv
    .\venv\Scripts\activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Adicione os dados:**
    Crie a pasta `data/raw` na raiz do projeto e coloque os arquivos de dados fornecidos (`transacoes.csv`, `produtos.csv`, `pdvs.csv`) dentro dela.

5.  **Gere a previsão:**
    Para treinar o modelo e gerar o arquivo de submissão, execute o script principal:
    ```bash
    python src/predict.py
    ```

---

## 📄 Formato do Arquivo de Saída

O script de previsão gera o arquivo `previsao_final.csv` dentro da pasta `/output`. O arquivo segue o formato especificado:

* **Colunas:** `semana;pdv;produto;quantidade`
* **Separador:** Ponto e vírgula (`;`)
* **Encoding:** UTF-8
* **Cabeçalho:** O arquivo não deve conter cabeçalho.

**Exemplo:**
```csv
1;1023;123;120
1;1045;234;85
2;1023;456;110
...
```

---

## 🧑‍💻 Autor

* **[Diego Sousa dos Santos]**
    * [LinkedIn](www.linkedin.com/in/diegosousasantosdev)
    * [GitHub](https://github.com/Diegodevops26)

---

## 📜 Licença

Este projeto está distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
