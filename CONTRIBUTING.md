# 🤝 Contribuindo para o Dashboard-supermercado

Obrigado por considerar contribuir para este projeto! Este documento fornece diretrizes e instruções para contribuições.

---

## 📋 Índice

- [Código de Conduta](#código-de-conduta)
- [Como Começar](#como-começar)
- [Reportar Bugs](#reportar-bugs)
- [Sugerir Melhorias](#sugerir-melhorias)
- [Pull Requests](#pull-requests)
- [Padrões de Codificação](#padrões-de-codificação)

---

## 📖 Código de Conduta

### Nosso Compromisso

Nós, como membros, contribuidores e líderes, nos comprometemos a tornar a participação em nossa comunidade uma experiência livre de assédio para todos, independentemente de idade, tamanho corporal, deficiência visível ou invisível, etnia, características sexuais, identidade e expressão de gênero, nível de experiência, educação, status socioeconômico, nacionalidade, aparência pessoal, raça, religião ou identidade e orientação sexual.

### Nossos Padrões

Exemplos de comportamento que contribuem para um ambiente positivo:
- Usar linguagem acolhedora e inclusiva
- Ser respeitoso com pontos de vista e experiências diferentes
- Aceitar críticas construtivas com graça
- Focar no que é melhor para a comunidade
- Mostrar empatia com outros membros da comunidade

---

## 🚀 Como Começar

### Pré-requisitos

- Power BI Desktop 2024+ instalado
- Git configurado em sua máquina
- Uma conta GitHub
- Conhecimento básico de Power BI, DAX e Git

### Setup Local

1. **Faça um fork do repositório**
   ```bash
   # Clique em "Fork" no GitHub
   ```

2. **Clone seu fork**
   ```bash
   git clone https://github.com/seu-usuario/Dashboard-supermercado.git
   cd Dashboard-supermercado
   ```

3. **Adicione o repositório original como upstream**
   ```bash
   git remote add upstream https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado.git
   ```

4. **Crie uma branch para sua feature**
   ```bash
   git checkout -b feature/sua-feature-descritiva
   ```

5. **Faça suas alterações**
   - Abra o arquivo .pbix no Power BI Desktop
   - Faça as mudanças desejadas
   - Teste completamente

6. **Commit suas mudanças**
   ```bash
   git add "Dashboard Vendas Mercados (1).pbix"
   git add seu-arquivo.md
   git commit -m "feat: descrição clara do que foi adicionado"
   ```

7. **Push para sua fork**
   ```bash
   git push origin feature/sua-feature-descritiva
   ```

8. **Abra um Pull Request**
   - Vá ao repositório original
   - Clique em "New Pull Request"
   - Selecione sua branch
   - Descreva as mudanças

---

## 🐛 Reportar Bugs

### Antes de Reportar

Procure no [GitHub Issues](https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado/issues) se o bug já foi reportado.

### Como Reportar um Bug

Crie uma issue com as seguintes informações:

**Título:** Resuma o problema de forma clara
```
Exemplo: "Dashboard não carrega com Windows 7"
```

**Descrição:**
```markdown
## Comportamento Esperado
[Descreva o que deveria acontecer]

## Comportamento Atual
[Descreva o que está acontecendo]

## Passos para Reproduzir
1. [Primeiro passo]
2. [Segundo passo]
3. [...]

## Ambiente
- Sistema Operacional: Windows 10, versão 22H2
- Power BI Desktop: versão 2.127.806.0
- Arquivos envolvidos: Dashboard Vendas Mercados (1).pbix

## Logs e Screenshots
[Cole qualquer mensagem de erro ou screenshot]
```

---

## 💡 Sugerir Melhorias

Crie uma issue com a label `enhancement`:

```markdown
## Resumo
[Descrição breve da melhoria sugerida]

## Motivação
Por que essa melhoria seria útil?

## Exemplo de Uso
[Como a feature seria usada]

## Alternativas Consideradas
[Outras soluções pensadas]
```

---

## 📤 Pull Requests

### Processo

1. **Atualize sua branch com a versão mais recente**
   ```bash
   git fetch upstream
   git rebase upstream/Principal
   ```

2. **Resolva conflitos se houver**
   ```bash
   # Edite os arquivos com conflito
   git add .
   git rebase --continue
   ```

3. **Verifique sua alteração**
   - Abra o arquivo no Power BI Desktop
   - Teste todos os filtros e gráficos
   - Valide as medidas DAX
   - Confirme que não há erros

4. **Force push se necessário**
   ```bash
   git push origin feature/sua-feature-descritiva --force
   ```

### Diretrizes de PR

**Título:** Comece com um verbo e seja descritivo
```
feat: adiciona análise de sazonalidade
fix: corrige cálculo de margem percentual
docs: atualiza guia de instalação
```

**Descrição:**
```markdown
## Descrição
[O que essa PR faz?]

## Tipo de Mudança
- [ ] Bug fix
- [ ] Nova feature
- [ ] Breaking change
- [ ] Documentação

## Alterações
- Mudança 1
- Mudança 2

## Como Testar
[Passo a passo para testar]

## Checklist
- [ ] Meu código segue as convenções
- [ ] Testei completamente
- [ ] Atualizei a documentação
- [ ] Não há conflitos
```

---

## 📐 Padrões de Codificação

### Convenções de Nomes (DAX)

**Medidas:**
```dax
-- PascalCase com prefixo de tipo
Total_Vendas
Crescimento_MoM
Margem_Percentual
```

**Colunas Calculadas:**
```dax
-- PascalCase
Mes_Nome
Trimestre_Ano
```

**Tabelas:**
```dax
-- fato_ para tabelas de fatos
-- dim_ para dimensões
fato_Vendas
dim_Lojas
dim_Tempo
```

### Boas Práticas DAX

✅ **Faça:**
```dax
-- Use variáveis para legibilidade
Crescimento = 
VAR VendaAtual = [Total_Vendas]
VAR VendaAnterior = CALCULATE([Total_Vendas], DATEADD(...))
RETURN DIVIDE(VendaAtual - VendaAnterior, VendaAnterior)
```

❌ **Evite:**
```dax
-- Não faça cálculos complexos sem variáveis
Crescimento = DIVIDE([Total_Vendas] - CALCULATE(...), CALCULATE(...))
```

### Formatação Power BI

- **Cores:** Use paleta corporativa consistente
- **Fontes:** Mínimo 11pt para legibilidade
- **Gráficos:** Máximo 6-8 por página
- **Filtros:** Agrupe logicamente
- **Labels:** Seja claro e conciso

---

## 🧪 Testes

### Checklist de Teste

- [ ] Dashboard abre sem erros
- [ ] Todos os filtros funcionam
- [ ] Gráficos exibem dados corretamente
- [ ] Não há valores #ERROR
- [ ] Relacionamentos validados
- [ ] Tempo de carregamento < 5 segundos
- [ ] Funciona em diferentes resoluções
- [ ] Exportação de dados funciona

### Teste de Performance

```
Arquivo tamanho: < 500 MB
Refresh time: < 2 minutos
Consulta aos dados: < 5 segundos
```

---

## 📚 Documentação

Atualize a documentação se sua mudança afeta:
- README.md
- DEVELOPMENT.md
- TROUBLESHOOTING.md
- CHANGELOG.md

---

## 🎓 Recursos Úteis

- [Documentação Power BI](https://docs.microsoft.com/power-bi/)
- [DAX Function Reference](https://dax.guide/)
- [Power Query Documentation](https://learn.microsoft.com/power-query/)
- [GitHub Guides](https://guides.github.com/)

---

## ❓ Perguntas?

Abra uma discussion ou entre em contato:
- 📧 Email: jeffersondesenvolvedormaster@gmail.com
- 💬 GitHub Discussions: [Dashboard-supermercado](https://github.com/jeffersondesenvolvedormaster/Dashboard-supermercado)

---

**Obrigado por contribuir! 🙏**

---

**Última Atualização:** 24 de Dezembro de 2025
