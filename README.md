# LIgaBetclicPredict

Projeto em Python para prever o campeão e a classificação final da **Liga Portuguesa de Futebol** utilizando apenas APIs gratuitas e scraping de fontes públicas. O objetivo é fornecer uma ferramenta aberta para análise preditiva da competição, permitindo que qualquer pessoa acompanhe as probabilidades de cada equipa ao longo da temporada.

## 1. Título e Descrição
- **Nome:** LIgaBetclicPredict
- **Objetivo:** Prever o campeão e a classificação final da Liga Portuguesa de Futebol.
- **Contexto:** Previsões de desempenho permitem identificar tendências de forma antecipada, possibilitando análises estratégicas e maior envolvimento dos adeptos com a competição.

## 2. Funcionalidades Principais
- Previsão do resultado de **cada jogo** da temporada.
- **Simulação completa** da temporada para gerar classificação final.
- Cálculo das **probabilidades de campeão**, qualificação europeia e descida de divisão.
- **Atualização automática** quando novos resultados são adicionados ao sistema.

## 3. Fontes de Dados
| Fonte | Tipo | Formato | Descrição |
|-------|------|---------|-----------|
| [Football-Data.org](https://www.football-data.org/) | API gratuita | JSON | Resultados históricos e calendário de jogos. |
| [OpenLigaDB](https://www.openligadb.de/) | API gratuita | JSON | Dados de jogos em tempo real e históricos. |
| [API-Football](https://rapidapi.com/api-sports/api/api-football) (free tier) | API gratuita | JSON | Estatísticas detalhadas de equipas e jogadores. |
| [ZeroZero.pt](https://www.zerozero.pt/) | Scraping | HTML/CSV | Informação detalhada de equipas e jogos. |
| [Flashscore](https://www.flashscore.com/) | Scraping | HTML/CSV | Resultados ao vivo e históricos. |
| [Wikipedia](https://pt.wikipedia.org/) | Scraping | HTML/CSV | Tabelas e dados históricos. |

**Recolha e Pré-Processamento:**
1. **Recolha:** Os dados são obtidos via `requests` para APIs e `BeautifulSoup` para scraping.
2. **Limpeza:** Normalização de nomes de equipas, tratamento de valores nulos e padronização de formatos.
3. **Pré-processamento:** Conversão para CSV/JSON, cálculo de métricas agregadas (ex.: forma recente, golos marcados).

## 4. Tecnologias Utilizadas
- **Linguagem:** Python 3.10+
- **Bibliotecas Principais:**
  - [Pandas](https://pandas.pydata.org/) e [NumPy](https://numpy.org/) para manipulação de dados.
  - [scikit-learn](https://scikit-learn.org/) e [XGBoost](https://xgboost.readthedocs.io/) para modelagem.
  - [Matplotlib](https://matplotlib.org/) e [Plotly](https://plotly.com/python/) para visualização.
  - [Requests](https://pypi.org/project/requests/) e [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/) para acesso a dados e scraping.
- **Estrutura de Pastas Sugerida:**
```
LIgaBetclicPredict/
├── data/              # Dados brutos e processados
├── models/            # Modelos treinados e artefactos
├── notebooks/         # Análises exploratórias
├── src/               # Código-fonte do projeto
│   ├── data/          # Scripts de recolha e preparação
│   ├── features/      # Engenharia de features
│   ├── models/        # Treino e avaliação
│   └── simulation/    # Simulação da temporada
├── tests/             # Testes automatizados
├── requirements.txt   # Dependências
└── main.py            # Script principal
```

## 5. Como Funciona o Modelo
1. **Dados históricos** gratuitos são recolhidos e utilizados para treinar o modelo.
2. **Features criadas:**
   - Forma recente (últimos 5 jogos).
   - Golos marcados e sofridos.
   - Desempenho em casa vs. fora.
   - Posição atual na tabela.
3. **Algoritmos:** Modelos como **XGBoost** ou **Random Forest** são treinados para prever o resultado de cada jogo (vitória/empate/derrota).
4. **Simulação:**
   - Cada jogo da temporada é simulado usando probabilidades estimadas pelo modelo.
   - Realizam-se múltiplas simulações (Monte Carlo) para gerar uma distribuição de classificações finais.
   - As probabilidades de campeão, qualificação europeia e descida são calculadas a partir dessas simulações.

## 6. Instalação e Execução
```bash
# Clonar o repositório
git clone https://github.com/seu-utilizador/LIgaBetclicPredict.git
cd LIgaBetclicPredict

# Criar e ativar o ambiente virtual
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Instalar dependências
pip install -r requirements.txt

# Executar o script principal
python main.py --season 2024-25 --simulations 10000
```

**Parâmetros Opcionais:**
- `--season` : Define a época (ex.: `2023-24`).
- `--simulations` : Número de simulações da temporada (default: 5000).
- `--update` : Recolhe novos resultados antes de executar a simulação.

## 7. Exemplos de Uso
```bash
# Simular temporada com parâmetros padrão
python main.py

# Simular com 20.000 simulações e atualizar dados
python main.py --simulations 20000 --update
```

**Exemplo de Saída (Tabela):**

| Posição | Equipa | Pontos | Prob. Campeão |
|---------|--------|--------|---------------|
| 1 | FC Porto | 85 | 35% |
| 2 | Sporting CP | 83 | 32% |
| 3 | SL Benfica | 80 | 28% |
| ... | ... | ... | ... |

**Exemplo de Gráfico:**

Um gráfico de barras gerado com Matplotlib/Plotly mostrando a probabilidade de cada equipa ser campeã.

## 8. Possíveis Melhorias Futuras
- Inclusão de variáveis adicionais: **lesões, transferências** e suspensões via APIs gratuitas.
- Criação de um **dashboard interativo** (ex.: Streamlit, Dash).
- Melhoria da precisão com **modelos híbridos** (combinação de estatísticos e aprendizado profundo).

## 9. Licença e Créditos
- **Licença:** [MIT](LICENSE)
- **Autores:** Daniel Santos e contribuidores.
- **Referências:**
  - [Football-Data.org](https://www.football-data.org/)
  - [OpenLigaDB](https://www.openligadb.de/)
  - [API-Football](https://rapidapi.com/api-sports/api/api-football)
  - [ZeroZero.pt](https://www.zerozero.pt/)
  - [Flashscore](https://www.flashscore.com/)
  - [Wikipedia](https://pt.wikipedia.org/)

---
Contribuições são bem-vindas! Abra uma issue ou envie um pull request para sugerir melhorias.
