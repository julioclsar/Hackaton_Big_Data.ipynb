# Instruções de Execução (README)
Este notebook Python foi desenvolvido para criar um modelo de previsão de vendas semanais por PDV (Ponto de Venda) e SKU (Stock Keeping Unit) para as cinco primeiras semanas de janeiro de 2023, utilizando dados históricos de vendas de 2022.

## Para executar este notebook, siga os passos abaixo:

Abrir no Google Colab: Certifique-se de que o notebook está aberto no ambiente Google Colab.

Carregar os Dados:

Os dados de vendas de 2022 devem estar disponíveis em formato Parquet no diretório /content/.
Execute a célula de código sob o título "Carregar os dados" para carregar e combinar os arquivos Parquet em um DataFrame pandas (df_sales_2022).
Explorar e Pré-processar os Dados:

Execute as células de código sob os títulos "Explorar a estrutura dos dados" e "Tratar valores ausentes e outliers" para entender a estrutura dos dados, verificar tipos de dados, identificar valores ausentes e outliers, e aplicar o tratamento definido.
Execute as células sob "Analisar a distribuição das vendas" e "Analisar a granularidade" para visualizar tendências e distribuições das vendas.
Feature Engineering:

Execute a célula sob "Agregação semanal" para agregar os dados diários em vendas semanais por PDV/SKU.
Execute a célula sob "Criação de variáveis de tempo" para gerar features temporais (semana do ano, mês, dia da semana).
Execute a célula sob "Identificação de feriados" para criar a variável binária indicando semanas de feriado.
Execute a célula sob "Criação de features de lag e média móvel" para calcular as vendas de períodos anteriores (lags) e médias móveis.
Execute a célula sob "Criação de feature de sazonalidade anual" para calcular as vendas da mesma semana no ano anterior.
Execute a célula sob "Tratamento de variáveis categóricas" para preparar e codificar as variáveis categóricas.
Execute a célula sob "Estruturação final do dataset" para organizar todas as features em um DataFrame pronto para modelagem.
Criação de Baseline e Divisão dos Dados:

Execute a célula sob "Criação de Baseline (Média Móvel)" para calcular a baseline de comparação.
Execute a célula sob "Divisão dos Dados" para dividir o dataset em conjuntos de treinamento e validação (usando as últimas semanas de 2022 para validação).
Treinamento e Otimização do Modelo:

Execute a célula que instala a biblioteca Optuna (!pip install optuna).
Execute a célula de código sob o título "Treinamento do Modelo LightGBM e Otimização de Hiperparâmetros com Optuna" para treinar o modelo LightGBM e otimizar seus hiperparâmetros usando Optuna. Este passo pode levar um tempo considerável dependendo do número de tentativas de otimização definidas.
Validação da Previsão:

Execute as células de código sob os títulos "Validação do Modelo Treinado" e "Avaliação do Modelo Otimizado" para avaliar o desempenho do modelo LightGBM (inicial e otimizado) no conjunto de validação, comparando seu WMAPE com a baseline.
Geração do Arquivo de Submissão:

Execute a célula sob "Preparação dos Dados para Previsão (Janeiro 2023)" para criar a estrutura de dados para as 5 semanas de janeiro de 2023 e gerar as features correspondentes.
Execute a célula sob "Realização das Previsões para Janeiro 2023" para gerar as previsões de vendas usando o modelo LightGBM otimizado.
Execute a célula sob "Formatação do Arquivo de Submissão" para formatar as previsões no formato de submissão e salvar o arquivo submission_january_2023.parquet.
Ao seguir estes passos, você executará todas as etapas do pipeline de previsão, desde o carregamento dos dados até a geração do arquivo final de previsões.
