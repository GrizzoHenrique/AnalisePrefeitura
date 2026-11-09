Análise de Despesas da Prefeitura: Preparação dos Dados (Exercício 2026)
Objetivo

Tratar e padronizar os dados de despesas gerais do Portal da Transparência da Prefeitura (exercício 2026), deixando a base consistente para ser carregada em um banco SQL e consumida em um dashboard no Power BI.

Fonte dos dados

Arquivo CSV exportado do Portal da Transparência (Despesas Gerais - Exercício 2026), com separador ; e codificação latin1. A base tem 13.052 registros e 35 colunas, cobrindo o período de Janeiro a Outubro.

Etapas realizadas
Importação e diagnóstico inicial: leitura com a codificação correta, e verificação de dimensões, tipos e valores nulos (shape, info, dtypes, isnull).
Conversão de datas: a coluna Data passou de texto para datetime (formato dd/mm/aaaa).
Conversão de valores monetários: 11 colunas financeiras (Dotação, Valor Empenhado, Valor Liquidado, Valor Pago, entre outras) estavam como texto no padrão brasileiro. Removi o símbolo R$ e os separadores de milhar, troquei a vírgula decimal por ponto e converti para numérico.
Remoção de registros vazios: descartei as linhas totalmente em branco.
Análise de valores ausentes: quantifiquei os nulos por coluna. Os maiores percentuais estão em Processo licitatório, que pode indicar despesas sem licitação associada, e em Nome fonte STN, que ainda precisa ser investigada antes de decidir o tratamento.
Padronização de textos: removi espaços desnecessários no início e no fim de todos os campos de texto.
Tipagem dos identificadores: Empenho, N° Ficha, Cód. Forn., Local, Função, Subfunção e Fonte viraram inteiros anuláveis (Int64). Já Funcional, Cód. de aplicação, Natureza, Cód. Fonte e Fonte STN ficaram como texto, para preservar zeros à esquerda e a estrutura hierárquica dos códigos.
Validação final: conferi os tipos, as estatísticas descritivas das colunas numéricas e os nulos após as transformações.
Resultado

Uma base com tipos coerentes (datas, valores numéricos, identificadores e códigos), pronta para ser exportada e modelada em SQL. A partir dela, o dashboard no Power BI vai acompanhar o ciclo da despesa pública (dotação, empenho, liquidação e pagamento), com cortes por função, subfunção, fonte de recurso, fornecedor e período.

Próximos passos
Definir o tratamento dos nulos em Processo licitatório e Nome fonte STN.
Modelar as tabelas no SQL (fato de despesas e dimensões de fornecedor, função/subfunção e fonte).
Construir o dashboard no Power BI com indicadores de execução orçamentária.
