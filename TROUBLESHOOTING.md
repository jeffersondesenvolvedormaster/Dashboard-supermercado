# ❓ FAQ e Solução de Problemas

## 🆘 Problemas Comuns

### 1. "O arquivo não abre no Power BI Desktop"

**Causa:** Versão desatualizada do Power BI ou arquivo corrompido

**Solução:**
```
1. Atualize o Power BI Desktop para a versão mais recente
   - Vá em: Help > Check for updates
   
2. Se persistir, tente:
   - Feche completamente o Power BI
   - Delete os arquivos temporários:
     C:\Users\[SeuUsuário]\AppData\Local\Microsoft\Power BI Desktop
   
3. Reabra o arquivo
```

---

### 2. "Os dados aparecem vazios ou como #ERROR"

**Causa:** Conexão com dados quebrada ou credenciais inválidas

**Solução:**
```
1. Vá para: Home > Edit Queries
2. Clique em "Data Source Settings"
3. Verifique credenciais de conexão
4. Se usando SQL Server:
   - Confirme que o servidor está online
   - Verifique permissões do usuário
5. Clique em "Refresh" para atualizar
```

---

### 3. "Dashboard muito lento ou trava"

**Causa:** Arquivo grande, muitos visuais ou máquina com recursos limitados

**Solução:**
```
✓ Reduce visualizações por página
✓ Desabilite auto-refresh
✓ Use Mode de Armazenamento "Import" em vez de "Direct Query"
✓ Aumente memória RAM disponível
✓ Feche outros aplicativos durante uso
```

---

### 4. "Filtros não funcionam corretamente"

**Causa:** Relacionamentos mal configurados ou lógica DAX incorreta

**Solução:**
```
1. Clique em: Modeling > Manage Relationships
2. Verifique:
   - Tabelas relacionadas estão corretas
   - Cardinalidade é 1:N
   - Direção do filtro está ativa
3. Se necessário, recrie o relacionamento:
   - Delete e crie novamente
   - Teste com um visual simples
```

---

### 5. "Erro ao publicar no Power BI Service"

**Causa:** Workspace cheio ou permissões insuficientes

**Solução:**
```
1. Verifique capacidade do workspace:
   - Faça login em powerbi.microsoft.com
   - Vá ao workspace
   - Verifique storage utilizado

2. Se capacidade total:
   - Solicite upgrade de plano
   - Ou delete arquivos desnecessários

3. Verifique permissões:
   - Deve ter acesso "Editor" ao workspace
```

---

## 📚 Como Usar o Dashboard

### Navegação Básica

```
1. FILTROS (Esquerda)
   - Clique para expandir/recolher
   - Use múltiplas seleções
   - Clique em "Reset" para limpar tudo

2. GRÁFICOS (Centro)
   - Clique para fazer drill-down em alguns visuais
   - Passe mouse para ver valores
   - Clique em legenda para ocultar categorias

3. PÁGINAS (Inferior)
   - Clique em abas para navegar
   - Use setas para scroll se houver muitas páginas
```

### Dicas de Uso Avançado

**Filtro Cruzado:**
- Clique em um ponto num gráfico para filtrar todos os outros automaticamente
- Clique novamente para desfazer

**Exportar Dados:**
- Clique em ⋮ (três pontos) > "Export data"
- Escolha formato: Excel, CSV ou Power Point

**Drill-Down em Hierarquias:**
- Alguns gráficos têm dados em hierarquia
- Clique com botão direito > "Drill Down"
- Ou use ↓ no gráfico

---

## 🔐 Segurança e Privacidade

### Dados Sensíveis

Se o arquivo contém dados confidenciais:

```
1. NÃO compartilhe em email desprotegido
2. Use Power BI Service com autenticação MFA
3. Configure RLS (Row Level Security) por usuário
4. Revise permissões regularmente
```

### Backup

```
# Windows (PowerShell)
Copy-Item "Dashboard Vendas Mercados (1).pbix" `
  ".\Backup\Dashboard_$(Get-Date -Format 'yyyyMMdd_HHmm').pbix"

# Mac/Linux
cp "Dashboard Vendas Mercados (1).pbix" "Backup/Dashboard_$(date +%Y%m%d_%H%M).pbix"
```

---

## 📞 Obter Ajuda

### Recursos Online

- **[Documentação Power BI](https://docs.microsoft.com/power-bi/)** - Referência oficial
- **[Community Power BI](https://community.powerbi.com/)** - Fórum comunitário
- **[DAX Function Reference](https://dax.guide/)** - Guia de funções DAX

### Contato

**Email:** jeffersondesenvolvedormaster@gmail.com  
**GitHub Issues:** https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado/issues

---

## 📊 Glossário

| Termo | Definição |
|-------|-----------|
| **KPI** | Key Performance Indicator - Indicador-chave de desempenho |
| **DAX** | Data Analysis Expressions - Linguagem de fórmulas |
| **Power Query** | Ferramenta de transformação de dados |
| **Drill-Down** | Aprofundar em dados com mais detalhes |
| **Slice/Slicer** | Filtro visual interativo |
| **RLS** | Row Level Security - Segurança em nível de linha |
| **Refresh** | Atualizar dados do dashboard |
| **Publish** | Publicar para Power BI Service |

---

## ✅ Checklist de Uso Inicial

- [ ] Arquivo aberto sem erros
- [ ] Filtros respondendo corretamente
- [ ] Todos os gráficos carregados
- [ ] Data de atualização é recente
- [ ] Navegação entre páginas funcionando
- [ ] Exportação de dados testada
- [ ] Zoom/resolução confortável
- [ ] Relatório publicado no Power BI (se necessário)

---

**Última Atualização:** 24 de Dezembro de 2025
