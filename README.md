# Análise de Despesas da Prefeitura — Exercício 2026

Projeto de preparação e análise exploratória dos dados de despesas gerais disponíveis no Portal da Transparência da Prefeitura. O objetivo é transformar o arquivo original em uma base mais consistente e organizada, pronta para análises posteriores, modelagem em SQL e criação de dashboards.

## Fonte dos dados

O projeto utiliza o arquivo **Despesas Gerais — Exercício 2026**, exportado do Portal da Transparência em formato CSV. A base original possui **13.052 linhas e 35 colunas**, com informações sobre empenhos, fornecedores, dotações, valores pagos e liquidados, funções orçamentárias, fontes de recurso e licitações.

O CSV é lido com separador `;` e codificação `latin1`, conforme o formato do arquivo disponibilizado. A base pode ser atualizada no portal; portanto, os resultados dependem da versão presente neste repositório.

## Tecnologias utilizadas

| Tecnologia | Aplicação no projeto |
|---|---|
| Python | Linguagem utilizada no notebook |
| Jupyter Notebook | Ambiente para executar e documentar as etapas da análise |
| Pandas | Leitura, inspeção, transformação e validação dos dados |
| Matplotlib e Seaborn | Bibliotecas importadas para visualização e análise gráfica |
| Plotly Express | Biblioteca importada para visualizações interativas |

## Etapas realizadas

1. **Importação dos dados:** leitura do CSV com a codificação e o separador adequados.
2. **Inspeção inicial:** verificação das dimensões, colunas, tipos de dados, valores ausentes e estatísticas descritivas.
3. **Conversão de datas:** transformação da coluna `Data` para o tipo data, considerando o formato brasileiro `dd/mm/aaaa`.
4. **Tratamento dos valores monetários:** conversão de 11 colunas financeiras do padrão brasileiro (ponto para milhar e vírgula decimal) para valores numéricos.
5. **Remoção de linhas vazias:** descarte de registros totalmente em branco.
6. **Análise de valores ausentes:** quantificação dos nulos para apoiar decisões de tratamento. Na base analisada, `Proc. Licitatório` concentra a maior parte das ausências; esse campo pode não se aplicar a todas as despesas.
7. **Padronização e tipagem:** remoção de espaços excedentes em textos e conversão de identificadores e códigos para tipos mais apropriados, preservando valores ausentes quando necessário.
8. **Validação final:** conferência dos tipos, dos valores ausentes e das estatísticas das colunas numéricas após as transformações.

## Resultado

O notebook prepara uma base com datas, valores financeiros e identificadores em tipos mais adequados para análise, além de registrar a estrutura e os pontos de atenção dos dados. O resultado atual é produzido durante a execução do notebook; não há um arquivo separado com a base tratada neste repositório.

Essa preparação cria uma etapa inicial para análises da execução orçamentária e para trabalhos futuros de modelagem em SQL e construção de dashboards. Os valores ausentes, especialmente em `Proc. Licitatório`, devem ser avaliados conforme o contexto antes de qualquer uso analítico.

## Como executar

1. Clone o repositório e entre na pasta do projeto:

   ```bash
   git clone https://github.com/GrizzoHenrique/AnalisePrefeitura.git
   cd AnalisePrefeitura
   ```

2. Instale as bibliotecas utilizadas:

   ```bash
   pip install pandas matplotlib seaborn plotly jupyter
   ```

3. Abra o notebook:

   ```bash
   jupyter notebook AnalisePrefeitura.ipynb
   ```

4. Execute as células em ordem. Mantenha o CSV na mesma pasta do notebook para que a leitura dos dados funcione.

## Arquivos do projeto

- `AnalisePrefeitura.ipynb`: notebook com a importação, exploração, preparação e validação dos dados.
- `Portal Transparencia Despesas Gerais - Exercício 2026.csv`: base de dados original utilizada na análise.
