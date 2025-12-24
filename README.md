# 📊 Dashboard de Vendas - Supermercado

> Um dashboard interativo e profissional desenvolvido em **Power BI** para análise de vendas, desempenho de lojas e indicadores-chave de negócio (KPIs).

![Dashboard Preview](https://github.com/user-attachments/assets/b53b6906-6073-4da8-9a6b-1355ddbd917a)

![Dashboard Preview 2](https://github.com/user-attachments/assets/19567ed9-5732-4c6e-97bb-9003b68af219)

---

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Dados e Estrutura](#dados-e-estrutura)
- [Como Usar](#como-usar)
- [Visualizações Incluídas](#visualizações-incluídas)
- [Insights e Análises](#insights-e-análises)
- [Autor](#autor)
- [Contribuições](#contribuições)

---

## 📌 Sobre o Projeto

Este projeto apresenta um **Dashboard de Vendas para Supermercado** desenvolvido com Power BI, criado para fins de portfólio e demonstração de habilidades em:

- **Análise de Dados** com Power BI
- **Modelagem de Dados** (ETL)
- **Criação de Visualizações** profissionais
- **Business Intelligence (BI)**
- **KPI Tracking** e métricas de negócio

O dashboard fornece uma visão consolidada do desempenho de vendas, permitindo tomadas de decisão baseadas em dados.

---

## ✨ Funcionalidades

✅ **Análise de Vendas por Loja** - Comparação de desempenho entre diferentes unidades  
✅ **Indicadores-Chave (KPIs)** - Métricas de faturamento, ticket médio e volume de vendas  
✅ **Filtros Interativos** - Seleção por período, loja e categorias de produtos  
✅ **Gráficos Comparativos** - Visualizações de tendências e desempenho  
✅ **Análise de Produtos** - Performance por categoria e produção  
✅ **Relatórios de Período** - Comparações mensais, trimestrais e anuais  

---

## 🛠️ Tecnologias Utilizadas

| Ferramenta | Versão | Descrição |
|-----------|--------|-----------|
| **Power BI Desktop** | 2024+ | Ferramenta principal de BI e visualização |
| **DAX** | - | Linguagem para cálculos e medidas |
| **M Query** | - | Linguagem para transformação de dados |
| **SQL** | - | Preparação e consulta de dados |

---

## 📊 Dados e Estrutura

### Estrutura de Dados

O projeto trabalha com as seguintes dimensões e fatos:

```
📦 Modelo de Dados
├── 📋 Tabela de Vendas
│   ├── ID Venda
│   ├── Data da Venda
│   ├── ID Loja
│   ├── ID Produto
│   └── Valor da Venda
├── 🏪 Dimensão Lojas
│   ├── ID Loja
│   ├── Nome da Loja
│   ├── Cidade
│   └── Região
├── 📦 Dimensão Produtos
│   ├── ID Produto
│   ├── Nome do Produto
│   ├── Categoria
│   └── Preço
└── 📅 Dimensão Data
    ├── Data
    ├── Mês
    ├── Trimestre
    └── Ano
```

### Relações Entre Tabelas

- **Vendas ↔ Lojas** (1:N) - Múltiplas vendas por loja
- **Vendas ↔ Produtos** (1:N) - Múltiplos produtos vendidos
- **Vendas ↔ Data** (1:N) - Múltiplas vendas por data

---

## 🚀 Como Usar

### Pré-requisitos

- Power BI Desktop (Download: [powerbi.microsoft.com](https://powerbi.microsoft.com))
- Windows 7 ou superior
- Aproximadamente 500 MB de espaço em disco

### Instalação e Abertura

1. **Clone ou baixe o repositório**
   ```bash
   git clone https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado.git
   cd Dashboard-supermercado
   ```

2. **Abra o arquivo no Power BI Desktop**
   - Navegue até a pasta do projeto
   - Clique duas vezes em `Dashboard Vendas Mercados (1).pbix`
   - Aguarde o Power BI carregar o arquivo

3. **Interaja com o Dashboard**
   - Use os filtros para explorar os dados
   - Clique nos gráficos para fazer drill-down
   - Navegue entre as páginas do relatório

### Funcionalidades Interativas

- 🔍 **Filtro por Período**: Selecione datas específicas para análise temporal
- 🏪 **Filtro por Loja**: Isolize dados de uma ou múltiplas unidades
- 📦 **Filtro por Categoria**: Analise performance de categorias específicas
- 📈 **Drill-Down**: Clique nos gráficos para detalhar informações

---

## 📊 Visualizações Incluídas

### Página 1: Visão Geral
- **Cartão de KPI** - Total de Vendas
- **Cartão de KPI** - Número de Transações
- **Cartão de KPI** - Ticket Médio
- **Gráfico de Linhas** - Evolução de vendas ao longo do tempo
- **Mapa** - Vendas por região
- **Tabela** - Top 10 produtos mais vendidos

### Página 2: Análise por Loja
- **Gráfico de Barras** - Ranking de lojas por faturamento
- **Gráfico de Pizza** - Participação de cada loja no total
- **Matriz** - Performance detalhada por loja e período
- **Indicadores** - Crescimento percentual vs. período anterior

### Página 3: Análise de Produtos
- **Gráfico de Barras** - Produtos mais lucrativos
- **Tabela dinâmica** - Análise de margens por categoria
- **Scatter Plot** - Volume vs. Margem de Lucro
- **Filtros** - Seleção de categorias

---

## 💡 Insights e Análises

### KPIs Principais

| Métrica | Fórmula DAX | Objetivo |
|---------|------------|----------|
| **Total de Vendas** | `SUM(Vendas[Valor])` | Receita bruta total |
| **Ticket Médio** | `SUM(Vendas[Valor])/COUNTA(Vendas[ID])` | Valor médio por transação |
| **Crescimento MoM** | `(Vendas_Mês_Atual - Vendas_Mês_Anterior) / Vendas_Mês_Anterior` | Crescimento mês a mês |
| **Participação de Mercado** | `Vendas_Loja / Vendas_Total` | % de contribuição por loja |

### Análises Possíveis

1. **Sazonalidade** - Identificar períodos de pico e baixa
2. **Performance Comparativa** - Qual loja performa melhor?
3. **Mix de Produtos** - Quais categorias têm maior margem?
4. **Tendências** - Crescimento ou declínio ao longo do tempo
5. **Oportunidades** - Identificar lojas com potencial de melhoria

---

## 📂 Estrutura de Arquivos

```
📦 Dashboard-supermercado/
├── 📄 Dashboard Vendas Mercados (1).pbix    # Arquivo principal do Power BI
├── 📄 README.md                              # Documentação (este arquivo)
└── 📄 LICENSE                                # Licença do projeto
```

---

## 🎯 Habilidades Demonstradas

Através deste projeto, demonstro competência em:

✅ **Power BI Desktop** - Criação de dashboards profissionais  
✅ **Modelagem de Dados** - Estrutura de tabelas e relacionamentos  
✅ **DAX** - Cálculos avançados e medidas  
✅ **Power Query** - Transformação e limpeza de dados  
✅ **Visualização de Dados** - Design e UX de dashboards  
✅ **Storytelling com Dados** - Comunicação clara de insights  
✅ **Business Intelligence** - Análise de KPIs e métricas  

---

## 📈 Próximas Melhorias (Roadmap)

- [ ] Integração com dados em tempo real via API
- [ ] Previsão de vendas com análise preditiva
- [ ] Análise de sazonalidade avançada
- [ ] Exportação automática de relatórios por email
- [ ] Dashboard para celular (Power BI Mobile)
- [ ] Integração com dados de RH (absenteísmo vs. vendas)
- [ ] Análise de satisfação do cliente

---

## 👤 Autor

**Jefferson Lemos**  
📧 Email: jeffersondesenvolvedormaster@gmail.com  
🔗 GitHub: [@jeffersondesenvolvedormaster](https://github.com/jeffersondesenvolvedormaster)  

---

## 📝 Licença

Este projeto está sob licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 🤝 Contribuições

Contribuições, sugestões e melhorias são bem-vindas! Para contribuir:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

---

## ⭐ Se Gostou do Projeto

Se este projeto foi útil para você, considere dar uma ⭐ no repositório!

---

## 📧 Contato e Suporte

Para dúvidas, sugestões ou reportar problemas:
- 📧 Email: jeffersondesenvolvedormaster@gmail.com
- 🐙 GitHub Issues: [Abra uma issue](https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado/issues)

---

**Última atualização:** 24 de Dezembro de 2025  
**Status:** ✅ Completo e funcional
