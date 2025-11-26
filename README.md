# Análise Exploratória e Visualização de Dados Ecommerce

1. Visão Geral do Projeto
Este documento detalha o código Python desenvolvido para o Projeto Final do Módulo 10, focado na Análise Exploratória de Dados (EDA) e Visualização da base de dados de e-commerce (ecommerce_preparados.csv). O principal objetivo do projeto é transformar dados brutos em insights de negócio acionáveis, avaliando o desempenho de vendas, a satisfação do cliente (Nota) e a relação de preço entre as diferentes marcas.

2. Configurações e Leitura dos Dados
Esta é a seção inicial do código, responsável por configurar o ambiente de trabalho.

Importação de Bibliotecas: As bibliotecas pandas, matplotlib.pyplot e seaborn foram importadas.

Pandas: Essencial para carregar a base de dados em formato DataFrame e realizar a manipulação, limpeza e cálculo de estatísticas.

Matplotlib e Seaborn: Juntas, são as ferramentas padrão para a criação de gráficos e visualizações estatísticas. O uso do Seaborn (sns) facilita a criação de gráficos mais complexos e esteticamente agradáveis com poucas linhas de código.

Configurações: sns.set_theme(style="whitegrid") foi aplicado para definir um fundo quadriculado nos gráficos, melhorando a visibilidade e o contraste, o que é uma boa prática para relatórios de dados.

Leitura: O arquivo ecommerce_preparados.csv é carregado no DataFrame chamado df.

3. Informações Gerais e Estatísticas Descritivas
Esta etapa representa a fase de Inspeção de Dados, onde a qualidade e a estrutura dos dados são verificadas.

df.info(): Exibe um resumo estrutural da base, incluindo o número de linhas, o tipo de dado de cada coluna (por exemplo, float64 para números com casas decimais ou object para texto/strings) e, crucialmente, verifica se há a presença de valores nulos.

df.describe().T: Gera as Estatísticas Descritivas para todas as colunas numéricas. Esta tabela mostra a média, o desvio padrão (que mede a dispersão dos dados), os valores mínimo e máximo, e os quartis (25%, 50% e 75%). Essa visão inicial é vital para entender a distribuição dos preços e das notas. Por exemplo, uma grande diferença entre o valor médio e o valor máximo pode indicar a presença de outliers.

4. Análise de Correlação (Matriz de Calor)
O foco aqui é quantificar a relação linear entre as variáveis numéricas.

df.corr(numeric_only=True): Calcula o Coeficiente de Correlação de Pearson entre todos os pares de colunas numéricas. Este coeficiente varia de -1 (correlação negativa forte) a +1 (correlação positiva forte) e é fundamental para identificar relações.

sns.heatmap(...): A matriz de correlação é visualizada através de um Mapa de Calor (heatmap). O uso do mapa de calor é a melhor forma de apresentar essa matriz, pois as cores facilitam a identificação imediata das correlações mais fortes (cores mais intensas). O parâmetro annot=True garante que os valores numéricos exatos de correlação sejam exibidos diretamente no gráfico.

5. Análises por Variável Categórica (Marca)
Esta seção aprofunda a análise, segmentando as métricas numéricas pela variável categórica principal, a Marca.

Boxplots (Preço por Marca): O sns.boxplot é a ferramenta escolhida para essa comparação.

Justificativa: O Boxplot é excelente para visualizar a dispersão dos preços e os outliers (pontos fora das "caixas") para cada marca. Permite responder perguntas como: "Qual marca tem a maior variação de preços?" ou "Qual marca tem o preço mediano mais alto?".

Gráfico de Barras (Nota Média por Marca): O sns.barplot calcula e exibe a média da Nota para cada marca.

Justificativa: O gráfico de barras com a média é a forma mais clara de avaliar a satisfação média do cliente por categoria. As barras de erro (que representam o desvio padrão ou o intervalo de confiança) mostram quão consistente é essa nota média.

6. Geração de Insights de Negócio
Esta é a etapa final, onde o código traduz os resultados da análise estatística (Correlação, Média e Distribuição) em sentenças claras de negócio.

O código utiliza comandos if/elif/else e a consulta aos valores da matriz de correlação para gerar insights automatizados sobre a relação entre Preço e Nota, e Desconto e Preço.

Também são calculadas e exibidas estatísticas diretas, como a Nota Média Geral e a Marca mais popular (aquela com maior frequência na base, usando df["Marca"].mode()), fornecendo conclusões imediatas para a gestão de estoque e marketing.
