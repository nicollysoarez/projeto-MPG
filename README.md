# projeto-MPG
Modelo de Regressão Polinomial para prever consumo de combustível (MPG) com base no peso do veículo.

<div align="center">
  <!-- Aumentei o width para 500 abaixo -->
  <img src="logo-mpg.png.png" alt="Logo Projeto MPG" width="500">
</div>

# 🚗 Previsão de Consumo de Combustível (MPG)
> **Desafio de Machine Learning:** Construção e avaliação de um modelo preditivo de eficiência de combustível (`mpg`) utilizando dados de características técnicas de veículos.

---

## 🎯 O Desafio / A Missão
Atuando como uma dupla de cientistas de dados para uma montadora, o objetivo deste projeto foi desenvolver um modelo capaz de prever o consumo de combustível (milhas por galão - `mpg`) de um carro com base em suas especificações técnicas — sem a necessidade de realizar testes físicos reais na pista.

## 📊 Sobre o Dataset
* **Fonte:** Dataset `Auto MPG` com **339 veículos reais** fabricados entre 1970 e 1982.
* **Variável Alvo ($y$):** `mpg` (Consumo em milhas por galão).
* **Variável Preditora ($X$):** `weight` (Peso do veículo em libras), escolhida estrategicamente por apresentar a maior correlação negativa com a variável alvo (~ -0.83).

---

## 🔬 Metodologia & Etapas
1. **Exploração de Dados:** Análise de estrutura, tipos de dados e matriz de correlação das variáveis numéricas.
2. **Seleção de Feature:** Definição da variável `weight` com base na forte correlação linear e física com o consumo.
3. **Divisão Treino/Teste:** Separação dos dados na proporção 80/20 com seed fixa (`random_state`) para reprodutibilidade.
4. **Treinamento e Comparação de Modelos:**
   * **Regressão Linear Simples:** Modelo de linha reta base.
   * **Regressão Polinomial (Grau 2 e Grau 3):** Aplicação de transformações polinomiais para capturar a não-linearidade dos dados.
5. **Avaliação:** Comparação de métricas ($MAE$, $MSE$ e $R^2$) nos dados de teste.

---

## 📈 Resultados e Comparativo de Modelos

| Modelo | $R^2$ (Treino) | $R^2$ (Teste) | Observações |
| :--- | :---: | :---: | :--- |
| **Regressão Linear** | ~0.69 | ~0.71 | Modelo simples, erra nos extremos de peso. |
| **Polinomial (Grau 2)** | ~0.72 | **~0.73** | **Modelo Escolhido:** Captura a curvatura real sem overfitting. |
| **Polinomial (Grau 3)** | ~0.72 | ~0.73 | Apresenta ganho marginal e aumenta a complexidade. |

> *Nota: Os valores exatos de $R^2$ variam ligeiramente conforme a seed utilizada no `train_test_split`.*

---

## 💡 Decisão Final & Justificativa Técnica

**Modelo Selecionado:** Regressão Polinomial de Grau 2.

* **Física do Problema:** A perda de eficiência de combustível não é linear em relação ao aumento de peso. Carros mais leves ganham eficiência em uma proporção curva, o que torna o ajuste quadrático (Grau 2) muito mais fiel à realidade.
* **Prevenção de Overfitting:** O modelo de Grau 2 manteve desempenho consistente entre treino e teste. A elevação para o Grau 3 adiciona termos desnecessários que aumentam a complexidade sem gerar melhoria expressiva na validação.

---

## 🛠️ Tecnologias Utilizadas
* **Linguagem:** Python
* **Ambiente:** Google Colab
* **Bibliotecas:** `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
