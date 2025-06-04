# 📊 Análise de Chamados GLPI com SQL

Este repositório contém um mini projeto de simulação e análise de chamados de suporte técnico baseados no sistema **GLPI**, com foco na prática de consultas SQL.

## 🎯 Objetivo

O objetivo deste projeto é **praticar SQL** utilizando um conjunto de dados fictício que simula registros reais de chamados técnicos. A partir desses dados, é possível treinar:

- Criação de tabelas
- Inserção de dados
- Consultas com `SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`
- Funções de agregação (`COUNT`, `AVG`, `MAX`, etc.)
- Filtros e subconsultas
- Criação de views e relatórios simples

---

## 📁 Estrutura sugerida da tabela SQL

CREATE TABLE chamados (
    ID INTEGER PRIMARY KEY,
    Data_Abertura DATE,
    Tecnico TEXT,
    Categoria TEXT,
    Prioridade TEXT,
    Status TEXT,
    "Tempo_Resolucao (h)" REAL
);


##  🧰 Ferramentas que Você Pode Usar

- MySQL / MariaDB
- PostgreSQL
- SQLite (ideal para começar, simples e leve)
- DB Browser for SQLite ou DBeaver para visualização
- Pandas + SQLite se quiser conectar Python + SQL

## 📊 Exemplos de Consultas que Você Pode Praticar

-- Quantos chamados cada técnico solucionou?
SELECT Tecnico, COUNT(*) AS Total_Solucionados
FROM chamados
WHERE Status = 'Solucionado'
GROUP BY Tecnico;

-- Tempo médio de resolução por categoria
SELECT Categoria, AVG("Tempo_Resolucao (h)") AS Media_Resolucao
FROM chamados
WHERE Status = 'Solucionado'
GROUP BY Categoria;

-- Quantidade de chamados por prioridade
SELECT Prioridade, COUNT(*) AS Total
FROM chamados
GROUP BY Prioridade;

-- Chamados pendentes abertos em uma data específica
SELECT *
FROM chamados
WHERE Status = 'Pendente' AND Data_Abertura = '2025-05-05';


