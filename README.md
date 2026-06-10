# Análise de Viabilidade de Mercado e Inteligência de Localização (Geomarketing): Setor de Alimentação em Los Angeles

## Descrição do Projeto
Este projeto foi desenvolvido com foco em Inteligência de Mercado (*Market Intelligence*), Data-Driven Decision Making e Análise de Capacidade para o setor de alimentação urbana na cidade de Los Angeles (LA). O desafio consistiu em extrair insights estratégicos de uma base de dados com 9.651 estabelecimentos para dar suporte a investidores na abertura de um novo local. A análise envolveu o saneamento de dados com tratamento de nulos estruturais, análise de faturamento potencial por meio do dimensionamento de assentos (capacidade), identificação do *market share* de grandes redes versus comércios independentes e o mapeamento de densidade de concorrência por nomes de ruas para mitigar riscos de saturação de mercado.

---

## Tecnologias e Ferramentas Utilizadas
* **Linguagem:** Python
* **Análise e Manipulação de Dados:** Pandas e NumPy
* **Visualização de Dados Interativa:** Plotly Express
* **Visualização de Dados Estática:** Seaborn e Matplotlib
* **Ambiente de Desenvolvimento:** Jupyter Notebook

---

## Pipeline de Dados e Metodologia

### 1. Auditoria, Saneamento e Engenharia de Atributos (Feature Engineering)
* Carga e inspeção de uma base de dados contendo o cadastro de 9.651 estabelecimentos em Los Angeles em formato `.csv`.
* Identificação de dados ausentes residuais na coluna `chain` (apenas 3 registros nulos), optando-se pela filtragem direta (`.dropna`) para garantir a pureza estatística da base.
* Aplicação de técnicas de manipulação de strings (`.str.split`) para extrair o nome da rua principal a partir do endereço completo (`address`), isolando a numeração física e permitindo o agrupamento por localidade geográfica.

### 2. Análise de Distribuição e Representatividade de Mercado (Market Share)
* Cálculo da frequência absoluta e da proporção relativa (percentual) das tipologias de negócios presentes na cidade.
* Modelagem da dinâmica competitiva através do mapeamento do ecossistema, segmentando os dados entre estabelecimentos independentes e pertencentes a grandes redes (*chains*).
* Construção de gráficos de pizza interativos com o Plotly para evidenciar visualmente o domínio do mercado e o comportamento de expansão de marca.

### 3. Análise de Correlação de Expansão (Quantidade vs. Capacidade)
* Filtragem seletiva da base de dados com foco exclusivo em redes corporativas para decodificar suas estratégias de escalabilidade.
* Aplicação de agrupamentos avançados (`.groupby`) combinando múltiplas funções de agregação (`.agg`) para cruzar a quantidade total de filiais por marca contra o número médio de assentos de seus locais.
* Geração de gráficos de dispersão (*scatterplot*) com o Seaborn para mapear se as redes focam em "muitos locais pequenos" ou em "poucos locais de grande porte".

### 4. Dimensionamento Estatístico de Capacidade (Assentos por Categoria)
* Agrupamento de dados focado em tipologias de estabelecimento (`object_type`) e cálculo da média aritmética descritiva de assentos disponíveis.
* Cruzamento de dados de penetração de mercado para calcular o *Market Share de Redes* em cada categoria (quantidade de redes dividida pela quantidade total do tipo).
* Plotagem de gráficos de barras interativos com gradiente de cor (*color scale*) para rankear de forma clara os líderes em capacidade física instalada.

---

## Principais Insights & Impacto de Negócio
* **Predomínio dos Restaurantes:** O modelo de negócios no formato tradicional de "Restaurante" é o maior pilar do setor em LA, abocanhando massivos **75,2%** de todos os pontos comerciais da cidade, enquanto o formato de "Fast Food" aparece em segundo lugar com apenas **11,0%**.
* **Independência Local:** O mercado de alimentação na região é majoritariamente composto por comércios locais e independentes, que representam **61,9%** do ecossistema, apontando para um ambiente favorável à aceitação de novas marcas autorais (fora de redes).
* **Domínio de Redes nas Padarias:** A análise de *Market Share* revelou uma dinâmica agressiva no segmento de panificação: **100% das padarias (Bakery)** cadastradas operam sob o modelo de rede. Cafeterias (`Cafe`) e `Fast Food` também possuem forte presença de redes, com **61,1%** e **56,7%** respectivamente.
* **Líderes de Capacidade:** Se o objetivo do investidor for maximizar o giro de clientes por assento, os Restaurantes e Bares lideram o ranking de espaço físico, registrando médias de **48,04** e **44,77** assentos por estabelecimento, enquanto as padarias possuem a menor estrutura física, com média de apenas **21,77** assentos.
* **Identificação de Saturação (Gargalo de Concorrência):** A rua **W Sunset Blvd** lidera de forma disparada como a região mais saturada e competitiva da cidade, acumulando **296** estabelecimentos concorrentes ativos, seguida de perto pela **W Pico Blvd** com **288** pontos. Essas zonas exigem um orçamento de marketing muito mais agressivo para aquisição de clientes.

---

