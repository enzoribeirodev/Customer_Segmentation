# 🎯 Customer Personality Analysis: Segmentation with K-Medoids & PCA

## 💼 Visão de Negócio

Em um mercado competitivo, tratar todos os clientes da mesma forma é ineficiente. O objetivo deste projeto é desenvolver um sistema de **Segmentação de Clientes** utilizando Machine Learning não supervisionado.

Ao agrupar a base de clientes em clusters com comportamentos similares, permitimos que a empresa implemente estratégias de marketing personalizadas (como campanhas de upsell para clientes de alta renda ou conversão para visitantes frequentes), otimizando o orçamento de publicidade e maximizando o lucro.

## 🗂️ Sobre os Dados

O dataset contém 29 variáveis comportamentais e demográficas, incluindo:
* **Perfil:** Ano de nascimento, Educação, Estado Civil, Renda (`Income`), Crianças/Adolescentes em casa.
* **Consumo:** Gastos em Vinhos, Frutas, Carnes, Pescados, Doces e Produtos Gold.
* **Canais:** Compras via Web, Catálogo e Loja Física.
* **Engajamento:** Visitas ao site, Aceitação de campanhas anteriores, Reclamações.

## 🛠️ Metodologia e Engenharia de Dados

Para garantir uma segmentação de alta qualidade, foi aplicado um pipeline robusto de processamento:

### 1. Tratamento de Outliers (Winsorization)
A análise exploratória revelou diversos outliers. Simplesmente removê-los resultaria em perda significativa de informação.
* **Solução:** Aplicação da técnica de **Winsorization**.
* **Como funciona:** Substitui os valores extremos (muito altos ou baixos) pelos valores dos percentis limite (ex: 5% e 95%), reduzindo o impacto dos outliers sem descartar os dados.

### 2. Feature Engineering & PCA
* Criação de novas features para sintetizar comportamentos de compra.
* Aplicação de **PCA (Principal Component Analysis)** para redução de dimensionalidade. Isso removeu a redundância entre variáveis correlacionadas e melhorou a performance do algoritmo de clusterização.

### 3. Modelagem com K-Medoids
Optou-se pelo algoritmo **K-Medoids** ao invés do tradicional K-Means.
* **Motivo:** O K-Medoids utiliza pontos de dados reais como centros (medoids) e é mais robusto a ruídos e outliers, gerando clusters mais estáveis para este tipo de distribuição.
* **Definição do K:** O número ideal de **4 Clusters** foi escolhido equilibrando o *Silhouette Score* e a Distorção (Inércia).

## 📊 Análise dos Perfis (Clusters)

A segmentação revelou 4 perfis distintos de consumidores:

### 🟢 Cluster 0: "Famílias Tradicionais Econômicas"
* **Renda:** Média Baixa (~U$ 41.9k).
* **Perfil:** Pais de família (méd. 1.52 filhos), idade média de 53 anos.
* **Comportamento:** Gastos modestos. Preferem lojas físicas e web, visitam o site com frequência, mas compram itens de menor valor agregado.
* **Ação Sugerida:** Promoções baseadas em preço e descontos em volume para itens familiares.

### 🔵 Cluster 1: "Otimizadores Digitais"
* **Renda:** Média-Alta (~U$ 61k).
* **Perfil:** Mais velhos (méd. 56 anos), famílias médias (1.15 filhos).
* **Comportamento:** Gastadores consideráveis em Vinhos, Carnes e Ouro. Fortes no digital (Web) e Catálogo.
* **Ação Sugerida:** Campanhas de e-mail marketing focadas em produtos premium e conveniência online.

### 🟣 Cluster 2: "Elite VIP"
* **Renda:** A mais alta (~U$ 75.6k).
* **Perfil:** Famílias pequenas ou sem filhos (0.14 filhos), idade média de 52 anos.
* **Comportamento:** **High Spenders**. Gastam muito em Vinhos e Carnes. Preferem Catálogo e Loja Física; acessam pouco o site.
* **Ação Sugerida:** Atendimento exclusivo, ofertas de luxo via catálogo e eventos de degustação em loja. Não adianta investir em ads digitais massivos para este grupo.

### 🟠 Cluster 3: "Novos Prospectos"
* **Renda:** Baixa (~U$ 28.7k).
* **Perfil:** Os mais jovens (méd. 44 anos).
* **Comportamento:** Baixo gasto geral. Visitam **muito** o site, mas convertem pouco em compras.
* **Ação Sugerida:** Estratégias de conversão (CRO), cupons de primeira compra e produtos de entrada para fidelização.

## 🚀 Tecnologias Utilizadas
* **Python**
* **Pandas & Numpy** (Manipulação e Winsorization)
* **Scikit-learn** (PCA, Preprocessing)
* **Scikit-learn-extra** (K-Medoids)
* **Seaborn & Matplotlib** (Visualização dos Clusters)

## ⚙️ Como Executar
1. Clone o repositório:
```bash
git clone https://github.com/enzoribeirodev/Customer_Segmentation
```
2. Instale as dependências:
```bash
pip install pandas numpy seaborn scikit-learn scikit-learn-extra
```
