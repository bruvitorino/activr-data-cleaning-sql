# 🎮 ActiVR - Limpeza e Análise de Dados com SQL e Python

Este projeto foi desenvolvido como exercício prático de análise e limpeza de dados utilizando SQL e Python (pandas + SQLite) no Google Colab.

A empresa fictícia **ActiVR** desenvolve dispositivos de realidade virtual voltados para atividades físicas e deseja utilizar seus dados para melhorar estratégias de marketing e vendas.

## 🧠 Objetivo

Preparar, limpar e explorar os dados da empresa ActiVR para:

- Corrigir valores ausentes e inconsistentes.
- Unificar informações entre tabelas relacionadas.
- Obter insights sobre o comportamento dos usuários em diferentes tipos de jogos.

## 📁 Dados Utilizados

Os dados foram fornecidos em formato `.csv`:

- `users.csv`: informações dos usuários.
- `events.csv`: registros de eventos dentro dos jogos.
- `games.csv`: dados dos jogos disponíveis na plataforma.
- `devices.csv`: detalhes dos dispositivos VR utilizados.

## 🧩 Tarefas Realizadas

### 🔹 Tarefa 1 - Limpeza da Tabela `users`
Limpeza de valores ausentes e padronização dos campos:
- Substituição de `age` ausente pela média.
- Substituição de `registration_date` ausente por `2024-01-01-00-00-000`.
- E-mails ausentes preenchidos com `Unknown`.
- Frequência de treino (`workout_frequency`) padronizada e valores inválidos tratados como `flexible`.

### 🔹 Tarefa 2 - Preenchimento de `game_id` em `events`
Eventos anteriores a 2021 não tinham `game_id`. Sabemos que nessa época só existiam jogos do tipo `running`. Esses `game_id` foram recuperados da tabela `games`.

### 🔹 Tarefa 3 - Filtragem por tipo de jogo `biking`
Identificamos todos os eventos relacionados a jogos do tipo `biking`, extraindo `user_id` e `event_time` desses registros.

### 🔹 Tarefa 4 - Contagem de usuários únicos por tipo de jogo
Calculamos quantos usuários únicos participaram de eventos agrupados por `game_type` e `game_id`.

## ⚙️ Ferramentas Utilizadas

- 🐍 Python 3
- 📊 pandas
- 🗃️ SQLite (em memória)
- 💻 Google Colab

## 📌 Como Executar

1. Abra o notebook no Google Colab.
2. Faça upload dos arquivos `.csv` para o ambiente.
3. Execute as células sequencialmente.
4. Os resultados de cada tarefa são salvos em DataFrames (`clean_data`, `events_with_game_id`, `event_biking`, `users_game`).

## 🧾 Exemplo de Visualização

```python
# Visualizar os primeiros registros da tabela users
pd.read_sql_query("SELECT * FROM users LIMIT 5", conn)
