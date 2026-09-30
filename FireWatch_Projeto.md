# 🔥 FireWatch --- Plataforma Inteligente de Prevenção e Resposta a Incêndios

## 1. Visão geral

**FireWatch** é uma plataforma de inteligência climática e ambiental
criada para **reduzir os danos causados por incêndios florestais e
queimadas**.

A proposta não é apenas detectar incêndios depois que eles começam. O
objetivo é criar um ciclo de:

> **Detectar → Analisar → Prever → Prevenir → Alertar → Responder →
> Aprender**

O sistema combina dados de satélites, meteorologia, vegetação, histórico
de ocorrências e características territoriais para identificar regiões
com maior risco de incêndio.

Quando um foco de calor é detectado, o sistema pode gerar um alerta
direcionado às unidades de emergência responsáveis pela região.

Ao mesmo tempo, o FireWatch analisa as condições ambientais para
identificar **áreas vulneráveis antes que um incêndio aconteça** e
recomendar medidas preventivas adequadas.

------------------------------------------------------------------------

# 2. Problema

Incêndios podem gerar:

-   perda de vegetação e biodiversidade;
-   danos a propriedades;
-   riscos à população;
-   interrupção de estradas e serviços;
-   aumento da poluição do ar;
-   custos para órgãos públicos;
-   danos à agricultura;
-   destruição de áreas de preservação.

Um sistema puramente reativo atua depois que o incêndio já começou.

O FireWatch pretende trabalhar em duas frentes:

### Resposta

Detectar focos rapidamente e encaminhar informações para as equipes
responsáveis.

### Prevenção

Identificar áreas de risco, entender os fatores que aumentam a
vulnerabilidade e apoiar ações preventivas antes de uma ocorrência.

------------------------------------------------------------------------

# 3. Objetivo principal

Criar uma plataforma capaz de:

1.  coletar dados ambientais e de focos de calor;
2.  identificar áreas com maior risco de incêndio;
3.  visualizar o risco em um mapa;
4.  detectar novos focos;
5.  gerar alertas geográficos;
6.  identificar quais fatores estão contribuindo para o risco;
7.  recomendar ações preventivas baseadas em regras e evidências;
8.  acompanhar a evolução do risco ao longo do tempo;
9.  avaliar posteriormente se as previsões e intervenções foram
    eficazes.

------------------------------------------------------------------------

# 4. Diferencial do projeto

O FireWatch não deve ser apresentado simplesmente como:

> "Um sistema que detecta queimadas."

A proposta é:

> **"Uma plataforma que transforma dados ambientais em inteligência
> preventiva, identificando onde o risco de incêndio está aumentando,
> por que ele está aumentando e quais ações podem ser priorizadas antes
> que uma ocorrência aconteça."**

Isso cria três níveis de atuação:

### 🔴 Resposta

Existe um foco detectado → gerar alerta.

### 🟠 Prevenção

Não existe necessariamente um incêndio → identificar condições
favoráveis e priorizar ações preventivas.

### 🟢 Aprendizado

Comparar previsões, ocorrências e intervenções → melhorar continuamente
o modelo.

------------------------------------------------------------------------

# 5. Funcionamento geral

``` text
                 DADOS
                   │
       ┌───────────┼───────────┐
       ▼           ▼           ▼
    Satélite   Meteorologia  Vegetação
       │           │           │
       └───────────┼───────────┘
                   ▼
             PROCESSAMENTO
                   │
                   ▼
            MOTOR DE RISCO
                   │
          ┌────────┴────────┐
          ▼                 ▼
     RISCO ATUAL       RISCO FUTURO
          │                 │
          └────────┬────────┘
                   ▼
              MAPA DE RISCO
                   │
       ┌───────────┴───────────┐
       ▼                       ▼
   RESPOSTA                 PREVENÇÃO
       │                       │
       ▼                       ▼
   🚒 ALERTA              🌱 AÇÕES
```

------------------------------------------------------------------------

# 6. Fontes de dados

O projeto pode combinar diferentes categorias de dados.

## 6.1 Dados de satélite

Informações relacionadas a:

-   focos de calor;
-   localização;
-   horário/data;
-   intensidade quando disponível;
-   recorrência de focos;
-   concentração espacial.

Uma fonte importante para o contexto brasileiro é o **Programa Queimadas
do INPE**, que disponibiliza informações relacionadas a focos de calor e
queimadas.

Outras fontes de observação da Terra podem ser avaliadas conforme a
necessidade do projeto.

------------------------------------------------------------------------

## 6.2 Dados meteorológicos

Variáveis importantes:

-   temperatura;
-   umidade relativa;
-   precipitação;
-   velocidade do vento;
-   direção do vento;
-   pressão atmosférica;
-   previsão meteorológica;
-   chuva acumulada em diferentes períodos.

Essas variáveis ajudam a identificar condições ambientais favoráveis à
propagação ou ocorrência de incêndios.

------------------------------------------------------------------------

## 6.3 Dados de vegetação

Possíveis variáveis:

-   cobertura vegetal;
-   índice de vegetação;
-   condição/sequidão da vegetação;
-   umidade da vegetação;
-   uso e cobertura do solo.

Índices derivados de imagens de satélite podem ajudar a identificar
mudanças na condição da vegetação.

------------------------------------------------------------------------

## 6.4 Dados históricos

O sistema pode armazenar:

-   localização de incêndios anteriores;
-   data;
-   horário;
-   frequência;
-   sazonalidade;
-   duração quando disponível;
-   características ambientais no momento da ocorrência.

O histórico é importante para descobrir padrões espaciais e temporais.

------------------------------------------------------------------------

## 6.5 Dados territoriais

Também podem ser considerados:

-   áreas urbanas;
-   áreas rurais;
-   unidades de conservação;
-   estradas;
-   rios;
-   escolas;
-   hospitais;
-   população;
-   infraestrutura crítica.

Esses dados não necessariamente aumentam a probabilidade de incêndio,
mas ajudam a calcular o **impacto potencial** caso uma ocorrência
aconteça.

------------------------------------------------------------------------

# 7. Fire Risk Score

O sistema pode transformar diferentes variáveis em um índice de risco de
0 a 100.

Exemplo conceitual:

``` text
Fire Risk Score =
    temperatura
  + umidade
  + chuva recente
  + condição da vegetação
  + vento
  + histórico
  + focos próximos
```

Uma primeira versão pode usar pesos definidos pela equipe.

Exemplo experimental:

``` text
Temperatura             25%
Umidade                 20%
Vegetação               20%
Chuva recente           15%
Vento                   10%
Histórico               10%
```

Esses pesos são **hipóteses de modelagem**, não uma fórmula oficial.

Durante o desenvolvimento, devem ser testados e calibrados com dados
históricos.

------------------------------------------------------------------------

# 8. Normalização dos dados

As variáveis possuem escalas diferentes.

Por exemplo:

-   temperatura: °C;
-   umidade: %;
-   chuva: mm;
-   vento: km/h.

Por isso, o sistema precisa transformar as variáveis para uma escala
comparável.

Uma possibilidade é normalizar cada variável para:

``` text
0 → baixo risco
100 → alto risco
```

Depois:

``` text
Score =
(T × peso_T)
+
(U × peso_U)
+
(V × peso_V)
+
...
```

------------------------------------------------------------------------

# 9. Categorias de risco

Uma classificação inicial pode ser:

``` text
0–24   🟢 Baixo
25–49  🟡 Moderado
50–74  🟠 Alto
75–100 🔴 Crítico
```

Esses limites também devem ser tratados como parâmetros do projeto e
posteriormente validados.

------------------------------------------------------------------------

# 10. Risco não é a mesma coisa que impacto

Uma das partes mais importantes do FireWatch é separar:

## Probabilidade/risco

> "As condições favorecem um incêndio?"

de:

## Impacto potencial

> "Se um incêndio acontecer aqui, quais podem ser as consequências?"

Uma área remota pode apresentar risco muito alto, mas baixo impacto
populacional.

Uma área próxima a uma cidade pode apresentar risco um pouco menor, mas
impacto potencial muito maior.

Por isso, o sistema pode ter:

``` text
RISCO
+
IMPACTO
=
PRIORIDADE
```

------------------------------------------------------------------------

# 11. Índice de prioridade

Uma segunda métrica pode ser criada para auxiliar gestores.

Exemplo conceitual:

``` text
Prioridade =
    60% Fire Risk Score
  + 40% Impact Score
```

O cálculo deve ser transparente e configurável.

O sistema pode então produzir uma lista:

``` text
1. Região A
   Risco: 91
   Impacto: 82

2. Região B
   Risco: 87
   Impacto: 94

3. Região C
   Risco: 95
   Impacto: 31
```

O objetivo não é substituir decisões das autoridades, mas **organizar
informações para apoiar a priorização operacional**.

------------------------------------------------------------------------

# 12. Perfil de risco

Ao clicar em uma região, o sistema deve explicar por que ela recebeu
determinada classificação.

Exemplo:

``` text
🔥 ALERTA FIREWATCH

Região: Área X

Risco: 87/100 🔴

Temperatura:       37°C
Umidade:           19%
Chuva recente:      4 mm
Vegetação:         Muito seca
Vento:             28 km/h
Focos próximos:     7
```

### Principais fatores

``` text
Umidade          █████████████
Vegetação        ███████████
Temperatura      ██████████
Chuva            ███████
Focos próximos   █████
```

Isso aumenta a **explicabilidade** do sistema.

------------------------------------------------------------------------

# 13. Detecção de focos

Quando uma fonte de satélite informar um novo foco:

``` text
SATÉLITE
   ↓
NOVO FOCO
   ↓
LOCALIZAÇÃO
   ↓
CONSULTA DOS DADOS LOCAIS
   ↓
ANÁLISE DE RISCO
   ↓
ALERTA
```

O sistema pode verificar:

-   distância para outros focos;
-   distância para áreas urbanas;
-   condições meteorológicas;
-   condição da vegetação;
-   risco calculado;
-   unidade de emergência responsável.

------------------------------------------------------------------------

# 14. Agrupamento de focos

Vários focos próximos podem indicar uma área que merece investigação.

Exemplo:

``` text
          🔴
       🔴 🔴
          🔴
       🔴
```

O sistema pode agrupar esses pontos em um **cluster**.

Para isso podem ser estudadas técnicas de geoprocessamento e algoritmos
de agrupamento, como DBSCAN.

O objetivo é identificar:

> "Existe concentração anormal de focos nesta região?"

------------------------------------------------------------------------

# 15. Sistema de alertas

Quando um evento atingir critérios definidos, o FireWatch pode gerar um
alerta.

Exemplo:

``` text
🚨 NOVO ALERTA

Foco detectado
Localização: Região X
Horário: 14:32

Risco ambiental: ALTO
Focos próximos: 5
Distância para área urbana: 8 km

Unidade responsável:
Corpo de Bombeiros / órgão competente

Ação:
Verificar ocorrência e acompanhar evolução.
```

No MVP, a integração real com sistemas oficiais de emergência pode ser
simulada.

É importante não presumir que um alerta enviado diretamente ao Corpo de
Bombeiros será aceito ou integrado à operação real sem autorização
institucional.

------------------------------------------------------------------------

# 16. Prevenção: o grande diferencial

O FireWatch deve ter um módulo chamado, por exemplo:

## 🛡️ Prevention Engine

Ele analisa:

``` text
RISCO
+
FATORES
+
CARACTERÍSTICAS DA REGIÃO
```

e gera recomendações preventivas.

------------------------------------------------------------------------

# 17. Recomendações preventivas

As recomendações devem vir de uma **base de conhecimento com regras e
referências**, e não de uma IA inventando medidas.

Exemplos:

### Área rural

Condições:

-   vegetação seca;
-   baixa umidade;
-   alta temperatura;
-   histórico elevado.

Possíveis recomendações:

-   intensificar fiscalização;
-   orientar proprietários sobre riscos e regras aplicáveis;
-   monitorar áreas críticas;
-   priorizar comunicação preventiva.

------------------------------------------------------------------------

### Área florestal

Condições:

-   vegetação muito seca;
-   baixa umidade;
-   vento elevado;
-   histórico de ocorrências.

Possíveis recomendações:

-   intensificar monitoramento;
-   priorizar patrulhamento preventivo;
-   verificar acessos para equipes de emergência;
-   reforçar comunicação de prevenção.

------------------------------------------------------------------------

### Área próxima a região urbana

Condições:

-   vegetação seca;
-   área residencial próxima;
-   risco elevado.

Possíveis recomendações:

-   avaliar necessidade de manejo de material combustível;
-   verificar faixas de proteção onde tecnicamente aplicável;
-   priorizar comunicação com moradores;
-   monitorar pontos críticos.

As ações devem ser adaptadas às regras locais e às orientações dos
órgãos competentes.

------------------------------------------------------------------------

# 18. IA no FireWatch

A IA não precisa ser responsável por prever incêndios sozinha.

Uma aplicação mais segura e útil é usar IA para:

-   interpretar dados;
-   explicar o score;
-   gerar resumos;
-   responder perguntas;
-   contextualizar tendências;
-   explicar recomendações já existentes na base de conhecimento.

Exemplo:

> **Por que essa região está em alerta?**

Resposta:

> A região apresenta risco elevado devido à combinação de baixa umidade,
> temperatura elevada, baixa precipitação recente, condição seca da
> vegetação e presença de focos próximos.

------------------------------------------------------------------------

# 19. Assistente climático

O usuário poderia perguntar:

> "Qual região está apresentando maior risco hoje?"

> "Por que o risco aumentou?"

> "Quais fatores estão influenciando essa região?"

> "Quais áreas precisam de maior monitoramento?"

> "Como o risco mudou nos últimos sete dias?"

A IA consulta os dados estruturados e responde com base neles.

------------------------------------------------------------------------

# 20. Previsão de risco

Uma evolução do sistema é criar um:

## 🔮 Fire Risk Forecast

Em vez de mostrar somente o risco atual, estimar o risco para os
próximos dias.

Exemplo:

``` text
Hoje       🟠 68
Amanhã     🔴 79
+2 dias    🔴 84
+3 dias    🟠 72
+4 dias    🟡 49
```

O objetivo seria identificar antecipadamente períodos de maior atenção.

É importante diferenciar:

-   **previsão meteorológica**;
-   **estimativa de risco de incêndio**;
-   **detecção de fogo já observado**.

São coisas diferentes.

------------------------------------------------------------------------

# 21. Análise histórica

Uma das funcionalidades mais importantes para validar o projeto.

O sistema pode analisar:

-   onde ocorreram incêndios;
-   quando ocorreram;
-   quais eram as condições meteorológicas;
-   como estava a vegetação;
-   quantos focos apareceram;
-   quais condições se repetem antes das ocorrências.

Isso permite descobrir padrões.

Exemplo:

``` text
Histórico de 5 anos
        ↓
Ocorrências
        ↓
Condições ambientais
        ↓
Padrões
        ↓
Modelo de risco
```

------------------------------------------------------------------------

# 22. Avaliação científica

O projeto precisa medir se o modelo funciona.

Possíveis métricas:

### Precisão da classificação

Quantas áreas classificadas como alto risco realmente apresentaram
ocorrências?

### Recall

Quantas ocorrências reais estavam em áreas previamente classificadas
como de risco?

### Falsos positivos

Quantas áreas receberam alerta e não tiveram ocorrência?

### Falsos negativos

Quantas ocorrências aconteceram sem que o modelo tivesse identificado
risco?

### Lead time

Quanto tempo antes de uma ocorrência o sistema conseguiu identificar
condições de risco?

------------------------------------------------------------------------

# 23. Avaliação das ações preventivas

Uma evolução importante é comparar:

``` text
Risco previsto
        ×
Incêndios observados
        ×
Ações realizadas
```

Por exemplo:

``` text
Região A
Risco inicial: 82

Depois da intervenção:
Risco observado: 61
```

Isso **não prova sozinho que a intervenção causou a redução**.

Para investigar causalidade, seria necessário um desenho experimental ou
observacional adequado, com controles para clima, sazonalidade e outros
fatores.

No hackathon, a funcionalidade pode ser apresentada como módulo de
**monitoramento e avaliação de intervenções**.

------------------------------------------------------------------------

# 24. Arquitetura tecnológica

Uma arquitetura inicial:

``` text
                 APIs / SATÉLITES
                       │
                       ▼
                DATA INGESTION
                       │
                       ▼
                Python / ETL
                       │
                       ▼
                  BANCO DE DADOS
                       │
          ┌────────────┴────────────┐
          ▼                         ▼
     MOTOR DE RISCO             API BACKEND
          │                         │
          └────────────┬────────────┘
                       ▼
                  FRONTEND
                       │
              ┌────────┴────────┐
              ▼                 ▼
           MAPA GIS             IA
```

------------------------------------------------------------------------

# 25. Stack sugerida

## Backend

-   Python
-   FastAPI

## Processamento de dados

-   Python
-   Pandas
-   NumPy
-   GeoPandas
-   Scikit-learn, se houver modelo de machine learning
-   bibliotecas geoespaciais conforme necessidade

## Banco

-   PostgreSQL
-   PostGIS para dados geográficos

## Frontend

-   React
-   JavaScript/TypeScript
-   biblioteca de mapas como Leaflet ou MapLibre

## Visualização

-   mapas de calor;
-   marcadores;
-   polígonos;
-   gráficos temporais;
-   indicadores.

## IA

Pode ser adicionada posteriormente para interpretação e interação com os
dados.

------------------------------------------------------------------------

# 26. Estrutura inicial do banco

### `regions`

``` text
id
name
state
geometry
population
land_use
```

### `weather_data`

``` text
id
region_id
timestamp
temperature
humidity
rainfall
wind_speed
wind_direction
```

### `vegetation_data`

``` text
id
region_id
timestamp
vegetation_index
vegetation_condition
```

### `fire_hotspots`

``` text
id
latitude
longitude
timestamp
source
confidence
region_id
```

### `risk_scores`

``` text
id
region_id
timestamp
temperature_score
humidity_score
vegetation_score
rain_score
wind_score
history_score
hotspot_score
total_score
risk_level
```

### `alerts`

``` text
id
region_id
created_at
alert_type
severity
message
status
```

### `preventive_actions`

``` text
id
region_id
action_type
reason
created_at
status
```

------------------------------------------------------------------------

# 27. MVP do hackathon

Não tentar construir o sistema nacional completo.

O MVP deve provar o conceito.

## MVP 1 --- Mapa

Mostrar:

-   Brasil;
-   regiões;
-   focos de calor;
-   nível de risco.

## MVP 2 --- Motor de risco

Calcular um score inicial.

## MVP 3 --- Histórico

Permitir analisar uma janela de tempo.

## MVP 4 --- Alertas

Quando um foco atingir critérios definidos:

``` text
FOCO DETECTADO
     ↓
ANÁLISE
     ↓
RISCO
     ↓
ALERTA
```

## MVP 5 --- Prevenção

Ao selecionar uma área:

``` text
Risco: 84 🔴

Principais fatores:
- baixa umidade
- vegetação seca
- temperatura elevada
- histórico elevado

Ações sugeridas:
- aumentar monitoramento
- comunicação preventiva
- priorização operacional
```

## MVP 6 --- IA

Uma interface simples:

> "Por que essa região está em risco?"

------------------------------------------------------------------------

# 28. O que NÃO fazer no primeiro MVP

Evitar:

-   tentar cobrir todos os municípios do Brasil;
-   criar um modelo de IA extremamente complexo;
-   integrar diretamente com sistemas oficiais de bombeiros sem
    parceria;
-   prometer previsão exata de incêndios;
-   criar recomendações automáticas sem fonte ou validação;
-   construir dezenas de dashboards;
-   tentar fazer uma aplicação mobile completa;
-   depender de dados que não estejam disponíveis de maneira estável.

O objetivo inicial é provar:

> **"Conseguimos transformar dados públicos em um sistema que identifica
> e explica áreas prioritárias de risco."**

------------------------------------------------------------------------

# 29. Roadmap

## Fase 1 --- Pesquisa

-   identificar fontes de dados;
-   verificar APIs;
-   entender formatos;
-   estudar dados históricos;
-   definir área inicial.

## Fase 2 --- Data Pipeline

``` text
Fonte
 ↓
Download/API
 ↓
Tratamento
 ↓
Banco
```

## Fase 3 --- Motor de risco

-   normalização;
-   pesos;
-   score;
-   categorias;
-   validação histórica.

## Fase 4 --- Mapa

-   mapa;
-   focos;
-   regiões;
-   heatmap;
-   filtros.

## Fase 5 --- Alertas

-   regras;
-   notificações;
-   histórico;
-   simulação de destinatários.

## Fase 6 --- Prevenção

-   regras de recomendação;
-   base de conhecimento;
-   perfil de risco.

## Fase 7 --- IA

-   assistente;
-   explicações;
-   resumo;
-   consulta aos dados.

## Fase 8 --- Validação

-   precisão;
-   recall;
-   falsos positivos;
-   falsos negativos;
-   lead time.

------------------------------------------------------------------------

# 30. Exemplo de fluxo completo

``` text
09:00
        ↓
Satélite fornece novo foco
        ↓
FireWatch recebe coordenadas
        ↓
Consulta dados meteorológicos
        ↓
Consulta condição da vegetação
        ↓
Consulta histórico
        ↓
Calcula Fire Risk Score
        ↓
Score = 88 🔴
        ↓
Verifica proximidade com população
        ↓
Calcula impacto potencial
        ↓
Prioridade elevada
        ↓
🚨 Gera alerta
        ↓
Identifica unidade/órgão responsável
        ↓
Disponibiliza informações para resposta
        ↓
Atualiza mapa
        ↓
Registra ocorrência
        ↓
Sistema acompanha evolução
```

------------------------------------------------------------------------

# 31. Exemplo da experiência do usuário

### Dashboard

``` text
🔥 FIREWATCH

Risco nacional
━━━━━━━━━━━━━━━━

🔴 18 regiões críticas
🟠 43 regiões de alto risco
🟡 71 regiões moderadas

Focos detectados hoje
🔥 328

Áreas prioritárias
1. Região A
2. Região B
3. Região C
```

------------------------------------------------------------------------

### Detalhes da região

``` text
REGIÃO A

🔥 Risco: 88/100
🔴 CRÍTICO

Temperatura       38°C
Umidade           18%
Chuva             2 mm
Vento             27 km/h
Vegetação         Muito seca
Focos próximos    6

Principais fatores:
████████████ Vegetação
███████████  Umidade
██████████   Temperatura
████████     Focos
```

------------------------------------------------------------------------

# 32. Conceito de produto

O FireWatch pode ser pensado como três produtos em um:

### 1. Monitoramento

> O que está acontecendo?

### 2. Inteligência preventiva

> Onde o risco está aumentando e por quê?

### 3. Resposta

> Onde existe uma ocorrência e quem precisa ser informado?

------------------------------------------------------------------------

# 33. Público-alvo

Possíveis usuários:

-   Defesa Civil;
-   órgãos ambientais;
-   brigadas de incêndio;
-   gestores de unidades de conservação;
-   municípios;
-   governos estaduais;
-   propriedades rurais;
-   organizações ambientais;
-   centros de monitoramento.

A adoção real dependeria de validação institucional, integração com
sistemas existentes e acordos com os órgãos responsáveis.

------------------------------------------------------------------------

# 34. Possíveis extensões futuras

Depois do MVP:

### 🚁 Drones

Enviar drones para inspeção de áreas críticas.

### 📱 Aplicativo

Alertas para equipes e gestores.

### 🛰️ Mais fontes de satélite

Combinar diferentes sensores.

### 🤖 Machine Learning

Treinar modelos usando ocorrências históricas.

### 🌬️ Propagação

Estimar direção potencial de propagação com base em vento, relevo e
combustível vegetal.

### 🧑‍🚒 Gestão operacional

Gerenciar equipes, viaturas e recursos disponíveis.

### 📊 Painel municipal

Cada município poderia visualizar suas áreas prioritárias.

------------------------------------------------------------------------

# 35. Machine Learning --- evolução

Depois de criar um modelo baseado em regras, pode-se comparar com
modelos de machine learning.

Possíveis modelos:

-   Random Forest;
-   XGBoost;
-   Logistic Regression;
-   Gradient Boosting.

Variáveis de entrada:

``` text
temperatura
umidade
chuva
vento
vegetação
histórico
distância de focos
sazonalidade
uso do solo
```

Saída:

``` text
probabilidade estimada de ocorrência
```

O modelo deve ser validado com dados históricos e separado temporalmente
para evitar vazamento de informação.

------------------------------------------------------------------------

# 36. Cuidados científicos

O projeto deve evitar afirmar:

> "O sistema prevê incêndios com certeza."

A formulação adequada é:

> "O sistema estima o risco de ocorrência com base nas variáveis
> disponíveis."

Também é importante:

-   diferenciar foco de calor de incêndio confirmado;
-   considerar limitações dos sensores;
-   lidar com dados ausentes;
-   considerar resolução espacial;
-   considerar horário de passagem dos satélites;
-   validar o modelo com dados históricos;
-   documentar todos os pesos e regras.

------------------------------------------------------------------------

# 37. Métrica central do projeto

Uma métrica interessante para apresentação:

## Lead Time

Quanto tempo antes de uma ocorrência o sistema conseguiu identificar uma
condição de risco.

Exemplo:

``` text
Incêndio detectado: 16:30

Risco elevado identificado:
12:00

Lead Time:
4h30
```

Quanto maior o tempo de antecipação **sem aumento excessivo de falsos
alarmes**, maior o potencial operacional da informação.

------------------------------------------------------------------------

# 38. Hipótese do projeto

Uma hipótese que pode orientar o trabalho:

> **"A combinação de dados de focos de calor, meteorologia, vegetação e
> histórico de ocorrências pode identificar espacialmente áreas com
> maior risco de incêndio e fornecer informação antecipada para apoiar
> ações preventivas e resposta mais rápida."**

------------------------------------------------------------------------

# 39. Perguntas que o projeto deve responder

O FireWatch precisa conseguir responder:

### Onde?

> Onde está o maior risco?

### Quando?

> Quando o risco está aumentando?

### Por quê?

> Quais fatores estão contribuindo?

### O quê?

> O que pode ser feito preventivamente?

### Quem?

> Qual órgão/equipe deve receber a informação?

### E depois?

> O que aconteceu após o alerta?

### Funcionou?

> O modelo e as ações preventivas tiveram resultados observáveis?

------------------------------------------------------------------------

# 40. Pitch resumido

> **Incêndios não começam quando o fogo aparece. As condições que
> favorecem sua ocorrência podem surgir horas ou dias antes.**
>
> O FireWatch utiliza dados de satélite, meteorologia, vegetação e
> histórico de ocorrências para identificar regiões onde o risco está
> aumentando.
>
> A plataforma transforma esses dados em um mapa inteligente de risco,
> identifica os principais fatores responsáveis pela classificação,
> recomenda ações preventivas e, quando um foco é detectado, direciona
> alertas para os responsáveis pela região.
>
> Assim, o objetivo deixa de ser apenas combater o incêndio depois que
> ele começou e passa a ser **antecipar o risco, reduzir a
> vulnerabilidade e acelerar a resposta.**

------------------------------------------------------------------------

# 41. Próximo passo recomendado

Antes de começar a programar a interface, definir:

``` text
1. Qual região será utilizada no MVP?
          ↓
2. Quais dados estarão disponíveis?
          ↓
3. Qual fonte fornece cada dado?
          ↓
4. Qual será a unidade espacial?
          ↓
5. Como calcular o primeiro Risk Score?
          ↓
6. Como validar o score?
          ↓
7. Qual será o fluxo de alerta?
          ↓
8. Quais ações preventivas serão suportadas?
          ↓
9. Qual será o dashboard?
          ↓
10. Qual será a demonstração do hackathon?
```

------------------------------------------------------------------------

# 42. Definição do MVP em uma frase

> **FireWatch é uma plataforma que combina dados ambientais e de
> satélite para identificar áreas com maior risco de incêndio, explicar
> os fatores de risco, apoiar ações preventivas e acelerar a comunicação
> de ocorrências às equipes responsáveis.**
