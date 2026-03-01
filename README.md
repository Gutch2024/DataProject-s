README — EuroEdu Analytics Center · Data Warehouse & Business Intelligence
Objetivo do Projeto
O projeto consiste no desenvolvimento de análises de um tema no contexto de Business Intelligence assente num modelo de Data Warehouse para analisar a paridade de género no ensino superior europeu entre 2013 e 2023, utilizando dados públicos do Eurostat/PORDATA sobre alunos inscritos por ano, país, género, ciclo de estudo e área de educação.

A solução permite:

Avaliar o grau de paridade de género no ensino superior europeu.

Comparar países, ciclos de estudo e áreas de educação/formação.

Analisar a evolução temporal da paridade ao longo da década.

Apoiar decisões institucionais e políticas educativas com base em indicadores robustos.
​

Contexto
Organização fictícia: EuroEdu Analytics Center, centro especializado em análise de dados de educação e igualdade social.
​

Fonte de dados: PORDATA/Eurostat — alunos no ensino superior por sexo, ciclo de estudos e área de educação (última atualização 15‑09‑2025).

Período de análise: 2013–2023.
​

Unidade de análise: número de alunos inscritos por Ano, País, Género, Ciclo de Estudo e Área de Educação.

Estrutura da Tabela de Factos
A tabela de factos utilizada no modelo dimensional tem a seguinte estrutura:

Ano (2013–2023)

País (países europeus em análise)

Género (Homens, Mulheres)

Ciclo de Estudo (Ciclo Curto, Licenciatura, Mestrado, Doutoramento)

Área de Educação (conforme categorias PORDATA/Eurostat)

Número de Alunos (medida quantitativa central)

Cada linha representa uma combinação única destas dimensões, permitindo cruzar a mesma métrica (Número de Alunos) por diferentes perspetivas: temporal, geográfica, académica e de género.

Metodologia e Processo de Trabalho
O processo começou com a extração dos dados da PORDATA/Eurostat em formato CSV, contendo registos agregados por ano, país, género, ciclo de estudo, área de educação e número de alunos inscritos no ensino superior europeu. Esse ficheiro CSV foi convertido para Excel (.xlsx) e transformado numa tabela estruturada, o que facilitou a limpeza inicial e a normalização dos cabeçalhos e valores de texto (por exemplo, uniformização de nomes como CiclodeEstudo e remoção de espaços em branco).

De seguida, o ficheiro Excel foi importado para o Power BI, utilizando o Power Query para concluir o processo ETL (Extração, Transformação e Carregamento. Nesta fase foram verificados e ajustados os tipos de dados, tratados valores em falta na coluna “Número de Alunos” através de medidas DAX (em vez de eliminar linhas), eliminados duplicados e garantida a consistência das categorias de Ano, País, Género, Ciclo e Área de Educação.
​

Depois do ETL, foi construída a tabela de factos FactEnsinoSuperior, com granularidade ao nível de Ano, País, Género, Ciclo de Estudo e Área de Educação, tendo como medida central o Número de Alunos. A partir desta tabela foram criadas medidas DAX para os principais indicadores: total de alunos, total de homens, total de mulheres, percentagens por género, diferença absoluta e percentual entre géneros e o IPG (Índice de Paridade de Género), garantindo que todos os cálculos se adaptam dinamicamente aos filtros aplicados nos relatórios.

Com o modelo de dados validado, foram desenvolvidos vários dashboards em Power BI, organizados por tema: visão geral dos KPIs globais, análise comparativa por país, análise por ciclo de estudo, análise por área de educação e tendências temporais. Cada página utiliza gráficos de barras, mapas, rankings e segmentadores interativos para permitir uma exploração flexível dos dados, mantendo um design simples, coerente e focado na leitura dos indicadores.
​

Indicadores‑Chave de Desempenho (KPIs)
KPIs Globais — Estado Geral da Paridade
Focam a visão macro da distribuição de género no ensino superior europeu:
​

Total de Alunos.

Total de Homens.

Total de Mulheres.

Percentagem de Homens.

Percentagem de Mulheres.

Diferença Percentual entre Géneros.

Estes indicadores permitem verificar rapidamente se há equilíbrio próximo de 50/50 ou desvios relevantes a favor de um dos géneros.
​

KPIs Comparativos — Onde Estão os Desvios?
Analisam diferenças entre categorias específicas:
​

Percentagem de Homens/Mulheres por País.

Percentagem de Homens/Mulheres por Ciclo de Estudo.

Percentagem de Homens/Mulheres por Área de Educação.

Permitem identificar se os desvios são:

Culturais (associados ao país).

Estruturais (associados ao nível/ciclo).

Vocacionais (associados à área de formação).
​

KPIs Temporais — Como Evoluiu a Paridade?
Medem a evolução da paridade ao longo do tempo:
​

Variação anual da percentagem de mulheres.

Variação anual da percentagem de homens.

Estes KPIs mostram se há tendências de crescimento, estabilidade ou retrocesso na paridade de género na última década.
​

KPIs de Contributo — Quem Pesa Mais no Total Europeu?
Avaliam o peso de cada país no total europeu de alunos:
​

Contributo de Homens por País.

Contributo de Mulheres por País.

Permitem identificar países com maior influência estatística (por exemplo, Alemanha, França, Itália, Espanha) no panorama global.

Modelo de Dados (DW/BI)
Modelo Conceptual — Esquema Estrela
O modelo segue um esquema estrela com uma tabela de factos central e cinco dimensões conceptuais.
​

Tabela de Factos: FactEnsinoSuperior

Ano

País

Género

Ciclo de Estudo

Área de Educação

Número de Alunos

Dimensões conceptuais (não necessariamente materializadas em tabelas separadas):
​

DimAno (2013–2023)

DimPaís (países europeus em análise)

DimGénero (Masculino, Feminino)

DimCiclo (Ciclo Curto, Licenciatura, Mestrado, Doutoramento)

DimÁreaEducação (categorias Eurostat/PORDATA)

A granularidade é definida pela combinação Ano + País + Género + Ciclo de Estudo + Área de Educação.
​

Resultados e Principais Conclusões
As análises mostram que o ensino superior europeu apresenta um equilíbrio global entre géneros, com uma ligeira predominância feminina ao longo de todo o período em estudo, aproximadamente 54% mulheres e 46% homens, num total de cerca de 390 milhões de alunos entre 2013 e 2023.

Verificam‑se diferenças moderadas entre países, sem casos extremos: países como a Suécia evidenciam maior predominância feminina (IPG elevado), enquanto Alemanha e Grécia apresentam valores ligeiramente abaixo da paridade, mas dentro de uma margem reduzida.
​

As assimetrias mais fortes surgem por área de educação: há maior presença feminina em Educação, Saúde, Artes e Ciências Sociais, e maior presença masculina em TIC e Engenharias, refletindo padrões vocacionais consolidados. Ao nível dos ciclos de estudo, observa‑se maior presença feminina na Licenciatura e Mestrado, quase equilíbrio no ciclo curto e ligeira predominância masculina nos Doutoramentos.

No global, as tendências ao longo do tempo são estáveis, sem ruturas abruptas, o que indica que os padrões de participação de género se mantiveram relativamente constantes na última década, com variações anuais pequenas. Os dashboards permitem monitorizar estas dinâmicas e apoiar recomendações moderadas para promover maior diversidade, especialmente nas áreas com maior desequilíbrio (TIC, Engenharias, Educação e Saúde).
​

Tecnologias Utilizadas
Excel — limpeza inicial dos dados, conversão de CSV para tabela estruturada, normalização de cabeçalhos.

Power BI Desktop — Power Query (ETL), modelação de dados, criação de medidas DAX, construção de dashboards interativos.
​

PORDATA/Eurostat — fonte oficial de dados de ensino superior europeu.

Conteúdo do Repositório
Data-Warehouse-e-Business-Projetct.xlsx — tabela de factos consolidada e dados base usados no Power BI.
​

