🚲 Cyclistic Bike-Share: Como membros anuais e ciclistas casuais usam as bicicletas de forma diferente?

Estudo de caso de análise de dados (Google Data Analytics Capstone) seguindo as seis etapas do processo: Ask → Prepare → Process → Analyze → Share → Act.

Mostrar Imagem Mostrar Imagem

📑 Índice
Contexto
Tarefa de negócio
Perguntas norteadoras
Fonte de dados
Processamento e limpeza
Análise
Principais insights
Recomendações
Estrutura do repositório
Como reproduzir
Próximos passos
Autor
🏢 Contexto

A Cyclistic é uma empresa fictícia de bike-share sediada em Chicago. Lançado em 2016, o programa cresceu para uma frota de 5.824 bicicletas com geolocalização, distribuídas em 692 estações. As bicicletas podem ser retiradas em uma estação e devolvidas em qualquer outra, a qualquer momento.

Além das bicicletas tradicionais, a Cyclistic oferece bikes reclináveis, triciclos de mão e bikes de carga, tornando o serviço mais inclusivo (cerca de 8% dos usuários utilizam as opções assistivas).

Planos de preço:

Tipo de cliente	Plano
Casual	Passe de viagem única ou passe diário
Membro	Assinatura anual

A análise financeira da empresa concluiu que membros anuais são muito mais lucrativos do que ciclistas casuais. Por isso, a diretora de marketing, Lily Moreno, acredita que o crescimento futuro depende de converter ciclistas casuais em membros anuais, já que eles conhecem o serviço e já o escolheram para suas necessidades de mobilidade.

Stakeholders:

Lily Moreno: diretora de marketing e gestora direta
Equipe de análise de marketing da Cyclistic
Equipe executiva da Cyclistic: responsável por aprovar as recomendações
🎯 Tarefa de negócio

Identificar como membros anuais e ciclistas casuais utilizam as bicicletas da Cyclistic de maneira diferente, para embasar uma nova estratégia de marketing voltada à conversão de casuais em membros.

❓ Perguntas norteadoras

Três perguntas guiam o futuro programa de marketing. Este projeto responde à primeira:

✅ Como membros anuais e ciclistas casuais usam as bicicletas de forma diferente? (escopo deste projeto)
⬜ Por que ciclistas casuais comprariam uma assinatura anual?
⬜ Como a Cyclistic pode usar mídia digital para influenciá-los a se tornarem membros?
📦 Fonte de dados
Dados: histórico de viagens públicas da Divvy (Chicago), disponibilizado pela Motivate International Inc. sob licença de uso de dados. O nome "Cyclistic" é fictício; os dados reais são da Divvy.
Download: divvy-tripdata
Período: últimos 12 meses de dados de viagens (preencha: ex. jan/2025 a dez/2025)
Formato: arquivos .csv mensais.

Opcional (script inicial em Python): Divvy 2019 Q1 e Divvy 2020 Q1.

Principais campos
Campo	Descrição
ride_id / trip_id	Identificador da viagem
rideable_type	Tipo de bicicleta
started_at / ended_at	Data e hora de início e fim
start_station_name / end_station_name	Estações de partida e chegada
start_lat/lng / end_lat/lng	Coordenadas
member_casual	Tipo de cliente: member ou casual
Avaliação de credibilidade (ROCCC)
Critério	Avaliação
Reliable (confiável)	preencher
Original (original)	Dados de primeira mão da operadora
Comprehensive (abrangente)	preencher
Current (atual)	Últimos 12 meses
Cited (citado)	Fonte e licença identificadas
Privacidade e limitações

Por questões de privacidade, não há dados pessoalmente identificáveis. Isso impede, por exemplo, ligar compras de passes a cartões de crédito para saber se casuais moram na área de serviço ou se compraram múltiplos passes avulsos.

🧹 Processamento e limpeza

Ferramenta escolhida: (ex.: SQL / Python / Excel, e justificativa)

Passos executados:

Download e descompactação dos arquivos; manutenção de uma cópia dos dados originais em subpasta separada.
Padronização dos nomes e tipos de colunas entre os arquivos mensais.
Criação da coluna ride_length = ended_at − started_at (formato HH:MM:SS).
Criação da coluna day_of_week = dia da semana do início da viagem (1 = domingo … 7 = sábado).
Verificação de duplicatas, valores nulos e inconsistências.
Remoção de viagens com duração negativa ou inválida (descrever critérios).
Consolidação dos 12 meses em uma única base.

Registro de limpeza:

Etapa	Problema encontrado	Ação	Linhas afetadas
1	ex.: duração negativa	remoção	N
2	ex.: estações nulas	tratamento	N
📊 Análise

Análise descritiva comparando member vs. casual:

Média e máximo de ride_length
Moda de day_of_week
Duração média por tipo de cliente
Duração média e número de viagens por dia da semana
Número de viagens por mês / estação do ano
Preferência por tipo de bicicleta
Estações mais utilizadas por cada grupo

O resumo exportado fica em /data/summary.

💡 Principais insights

⚠️ Preencha com os resultados reais da sua análise.

Dimensão	Membros anuais	Casuais
Duração média da viagem	a preencher	a preencher
Dias de maior uso	a preencher	a preencher
Sazonalidade	a preencher	a preencher
Tipo de bicicleta	a preencher	a preencher

Visualizações: insira aqui as imagens ou links (Tableau, Power BI, etc.).

markdown
![Viagens por dia da semana](./visuals/rides_by_weekday.png)
✅ Recomendações

Top 3 recomendações baseadas nos dados (a preencher):

Recomendação 1: …
Recomendação 2: …
Recomendação 3: …
🗂 Estrutura do repositório
cyclistic-bike-share/
├── README.md
├── data/
│   ├── raw/            # CSVs originais (não alterar)
│   ├── clean/          # Dados limpos e consolidados
│   └── summary/        # Tabelas-resumo exportadas
├── scripts/
│   ├── 01_clean.sql | .py
│   └── 02_analysis.sql | .py
├── visuals/            # Gráficos e dashboards
└── reports/            # Apresentação / relatório final
▶️ Como reproduzir
bash
# 1. Clone o repositório
git clone https://github.com/<seu-usuario>/cyclistic-bike-share.git
cd cyclistic-bike-share

# 2. (Python) instale as dependências
pip install pandas numpy matplotlib seaborn

# 3. Baixe os CSVs da Divvy para data/raw/ e execute os scripts
python scripts/01_clean.py
python scripts/02_analysis.py
🔭 Próximos passos
Responder às perguntas 2 e 3 do estudo de caso.
Incluir dados adicionais (demográficos, clima, preços) para aprofundar a análise.
Testar a eficácia das campanhas propostas por meio de testes A/B.
👤 Autor

Seu Nome LinkedIn · Portfólio · E-mail

Este é um estudo de caso fictício para fins educacionais. Dados fornecidos pela Motivate International Inc. sob licença.
