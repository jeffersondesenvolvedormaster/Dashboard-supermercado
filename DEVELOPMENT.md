# 📖 Guia de Desenvolvimento - Dashboard Supermercado

## 🏗️ Arquitetura do Dashboard

Este documento descreve a estrutura técnica e o desenvolvimento do Dashboard de Vendas Supermercado.

---

## 📊 Modelo de Dados (Data Model)

### Tabelas Principais

#### 1. **fato_Vendas** (Fato)
Tabela de fatos contendo todas as transações de vendas.

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `ID_Venda` | PK | Identificador único da venda |
| `Data` | Date | Data da transação |
| `ID_Loja` | FK | Referência à loja |
| `ID_Produto` | FK | Referência ao produto |
| `Quantidade` | Integer | Quantidade vendida |
| `Valor_Unitario` | Decimal | Preço unitário |
| `Valor_Total` | Decimal | Valor total da venda |
| `Desconto` | Decimal | Desconto aplicado |

#### 2. **dim_Lojas** (Dimensão)
Informações sobre as unidades de venda.

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `ID_Loja` | PK | Identificador único |
| `Nome_Loja` | String | Nome da filial |
| `Cidade` | String | Localização |
| `Região` | String | Região geográfica |
| `Area_Venda` | Decimal | Metragem da loja |
| `Data_Abertura` | Date | Data de inauguração |

#### 3. **dim_Produtos** (Dimensão)
Catálogo de produtos vendidos.

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `ID_Produto` | PK | Identificador único |
| `Nome_Produto` | String | Descrição do produto |
| `Categoria` | String | Classificação |
| `Subcategoria` | String | Classificação secundária |
| `Preco_Custo` | Decimal | Valor de custo |
| `Preco_Venda` | Decimal | Preço de venda |
| `Margem_Lucro` | Decimal | % de margem |
| `Ativo` | Boolean | Status |

#### 4. **dim_Tempo** (Dimensão)
Tabela de calendário para análises temporais.

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `Data` | PK | Data no formato YYYY-MM-DD |
| `Ano` | Integer | Ano |
| `Mês` | Integer | Mês (1-12) |
| `Dia` | Integer | Dia do mês |
| `DiaNoMês` | String | Nome do dia |
| `MêsNome` | String | Nome do mês |
| `Trimestre` | String | Q1, Q2, Q3, Q4 |
| `Semana` | Integer | Semana do ano |
| `IsFimDeSemana` | Boolean | True se fim de semana |

---

## 🧮 Medidas DAX

### Medidas de Vendas

```dax
-- Total de Vendas
Total_Vendas = SUM(fato_Vendas[Valor_Total])

-- Quantidade Vendida
Total_Quantidade = SUM(fato_Vendas[Quantidade])

-- Número de Transações
Total_Transacoes = COUNTA(fato_Vendas[ID_Venda])

-- Ticket Médio
Ticket_Medio = DIVIDE([Total_Vendas], [Total_Transacoes])

-- Venda Média por Produto
Venda_Media_Produto = DIVIDE([Total_Vendas], [Total_Quantidade])
```

### Medidas de Desempenho

```dax
-- Crescimento MoM (Month-over-Month)
Crescimento_MoM = 
VAR VendaMesAtual = [Total_Vendas]
VAR VendaMesAnterior = CALCULATE([Total_Vendas], 
    DATEADD(dim_Tempo[Data], -1, MONTH))
RETURN DIVIDE(VendaMesAtual - VendaMesAnterior, VendaMesAnterior)

-- Participação de Loja
Participacao_Loja = DIVIDE([Total_Vendas], 
    CALCULATE([Total_Vendas], ALL(dim_Lojas)))

-- Cumprimento de Meta
Cumprimento_Meta = DIVIDE([Total_Vendas], [Meta_Vendas])
```

### Medidas de Margem

```dax
-- Custo Total
Custo_Total = SUMPRODUCT(fato_Vendas[Quantidade], dim_Produtos[Preco_Custo])

-- Lucro
Lucro = [Total_Vendas] - [Custo_Total]

-- Margem %
Margem_Percentual = DIVIDE([Lucro], [Total_Vendas])

-- Margem em R$
Margem_Reais = [Lucro]
```

---

## 📄 Páginas do Dashboard

### 🏠 Página 1: Resumo Executivo
**Objetivo:** Visão geral das métricas principais  
**Públicos:** Executivos, Gerentes

**Visualizações:**
- Cartões de KPI (Total Vendas, Transações, Ticket Médio)
- Gráfico de linhas com evolução temporal
- Mapa com distribuição geográfica
- Top 10 produtos

**Filtros:** Data, Região, Categoria

---

### 🏪 Página 2: Análise por Loja
**Objetivo:** Comparar performance entre filiais  
**Públicos:** Gerentes Regionais, Supervisores

**Visualizações:**
- Ranking de lojas (barras)
- Participação no total (pizza)
- Matriz: Loja vs. Período
- Indicadores de crescimento

**Filtros:** Data, Loja, Trimestre

---

### 📦 Página 3: Análise de Produtos
**Objetivo:** Analisar mix e margem de produtos  
**Públicos:** Compradores, Analistas de Categoria

**Visualizações:**
- Top produtos por receita
- Análise de margem por categoria
- Volume vs. Margem (scatter)
- Tabela detalhada

**Filtros:** Categoria, Subcategoria, Período

---

## 🔧 Técnicas e Boas Práticas

### 1. **Relacionamentos**
- Usar relacionamentos 1:N entre dimensões e fatos
- Ativar "Filtro cruzado" para navegação

### 2. **Otimização**
- Usar DirectQuery para dados muito grandes (>100M linhas)
- Import mode para < 100M linhas
- Comprimir dados com "Auto date/time" desativado

### 3. **Segurança**
- Implementar RLS (Row Level Security) por região/loja
- Nunca expor credenciais em arquivo .pbix

### 4. **Design**
- Usar paleta de cores corporativa
- Tamanho mínimo de fonte: 11pt
- Contraste suficiente para acessibilidade

### 5. **Performance**
- Limitar visuais por página a 6-8 gráficos
- Usar slicers para filtrar em vez de filtros visuais
- Desabilitar "Cross filter" desnecessários

---

## 📋 Checklist de Qualidade

- [ ] Todos os KPIs têm definição clara
- [ ] Medidas DAX testadas com valores esperados
- [ ] Relacionamentos validados (1:N, sem bidirecionais desnecessários)
- [ ] Filtros funcionam corretamente
- [ ] Paginação testada em diferentes resoluções
- [ ] Formatação consistente em todas as páginas
- [ ] Documentação das medidas incluída
- [ ] Tempo de carregamento < 5 segundos
- [ ] Sem avisos de performance
- [ ] Dados atualizados corretamente

---

## 🚀 Deployment

### Power BI Service
1. Publicar em workspace seguro
2. Configurar schedule de refresh (diário 8h, 16h, 20h)
3. Ativar notificações de falha
4. Configurar RLS se necessário
5. Compartilhar links de acesso

### Backup
- Guardar .pbix em repositório privado
- Versionar alterações em Power BI
- Documentar mudanças em changelog

---

## 📞 Suporte e Manutenção

**Contato:** jeffersondesenvolvedormaster@gmail.com

**Frequência de Atualização:**
- Dados: Diário
- Dashboard: Conforme necessidade
- Documentação: Mensal

**SLA:** Resolução de bugs em 48 horas

---

**Última Atualização:** 24 de Dezembro de 2025
