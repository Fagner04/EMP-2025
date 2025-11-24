# 🏷️ Usando Metacampos de Categoria/Coleção

## ✅ Sim! É Possível Usar Metacampos de Categoria

O código foi atualizado para suportar metacampos de:
1. ✅ **Variante** (variant.metafields.custom.color)
2. ✅ **Produto** (product.metafields.custom.color_mapping)
3. ✅ **Categoria/Coleção** (collection.metafields.custom.color_mapping) ⭐ NOVO!

---

## 🎯 Ordem de Prioridade

O sistema busca cores nesta ordem:

```
1. Imagem da Variante
   ↓
2. PNG em Assets (ex: amarelo.png)
   ↓
3. Metacampo da Variante (variant.metafields.custom.color)
   ↓
4. Metacampo do Produto (product.metafields.custom.color_mapping)
   ↓
5. Metacampo da Categoria (collection.metafields.custom.color_mapping) ⭐
   ↓
6. Cor Automática (nome da cor)
```

---

## 📝 Como Configurar Metacampo de Categoria

### PASSO 1: Criar Definição de Metacampo

```
Admin Shopify → Configurações → Metacampos → Coleções
```

**Clicar:** "Adicionar definição"

**Preencher:**
```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
Descrição: Cores padrão para produtos desta categoria
```

**SALVAR**

---

### PASSO 2: Configurar na Categoria/Coleção

```
Admin → Produtos → Coleções → Selecionar coleção
```

**Rolar até:** "Metacampos" (no final da página)

**Preencher "Mapeamento de Cores":**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00|Vermelho:#FF0000|Preto:#000000|Branco:#FFFFFF
```

**SALVAR**

---

## 🎨 Casos de Uso

### Caso 1: Cores Padrão por Categoria

**Cenário:** Você tem várias categorias com paletas de cores diferentes

**Solução:** Configurar metacampo na categoria

**Exemplo:**

**Categoria "Roupas de Verão":**
```
Amarelo:#FFFF00|Laranja:#FFA500|Rosa:#FFC0CB|Azul Claro:#ADD8E6
```

**Categoria "Roupas de Inverno":**
```
Preto:#000000|Cinza:#808080|Marrom:#A52A2A|Azul Marinho:#000080
```

**Vantagem:** Todos os produtos da categoria herdam as cores automaticamente!

---

### Caso 2: Sobrescrever Cores da Categoria

**Cenário:** Categoria tem cores padrão, mas um produto específico precisa de cores diferentes

**Solução:** Configurar metacampo no produto (tem prioridade sobre categoria)

**Exemplo:**

**Categoria "Roupas Casuais":**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080
```

**Produto Específico "Camiseta Especial":**
```
Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00
```

**Resultado:** Produto usa suas próprias cores, outros produtos da categoria usam cores padrão

---

### Caso 3: Cores Específicas por Variante

**Cenário:** Cada variante tem uma cor única que não segue padrão

**Solução:** Configurar metacampo na variante (maior prioridade)

**Exemplo:**

**Variante "Edição Limitada - Dourado":**
```
variant.metafields.custom.color = #FFD700
```

**Resultado:** Esta variante usa cor específica, outras usam padrão da categoria/produto

---

## 🔧 Atualizar Código

### Substituir Bloco de Cores

**Arquivo:** `snippets/product-info.liquid`

**Procurar por:**
```liquid
{%- when 'color' -%}
```

**Substituir TODO o bloco** com o conteúdo de:
`snippets/product-info-COM-CATEGORIA.liquid`

**SALVAR**

---

## 📊 Comparação: Produto vs Categoria

### Metacampo no Produto:

**Vantagens:**
- ✅ Controle específico por produto
- ✅ Sobrescreve categoria
- ✅ Ideal para produtos únicos

**Desvantagens:**
- ❌ Precisa configurar em cada produto
- ❌ Mais trabalho manual

---

### Metacampo na Categoria:

**Vantagens:**
- ✅ Configurar uma vez, aplicar em todos
- ✅ Consistência na categoria
- ✅ Menos trabalho manual
- ✅ Fácil de manter

**Desvantagens:**
- ❌ Menos flexibilidade por produto
- ❌ Pode ser sobrescrito por produto

---

## 💡 Estratégias Recomendadas

### Estratégia 1: Categoria como Padrão

```
1. Configurar cores na categoria (padrão)
2. Sobrescrever no produto quando necessário
3. Sobrescrever na variante para casos especiais
```

**Exemplo:**
```
Categoria "Roupas" → Cores básicas
Produto "Camiseta Premium" → Cores especiais
Variante "Edição Limitada" → Cor única
```

---

### Estratégia 2: Produto Individual

```
1. Não usar categoria
2. Configurar cada produto individualmente
3. Máximo controle
```

**Exemplo:**
```
Cada produto tem seu próprio mapeamento
Ideal para lojas com poucos produtos
```

---

### Estratégia 3: Híbrida

```
1. Categoria para produtos padrão
2. Produto para produtos especiais
3. Variante para edições limitadas
```

**Exemplo:**
```
80% dos produtos → Categoria
15% dos produtos → Produto
5% das variantes → Variante
```

---

## 🎯 Exemplos Práticos

### Exemplo 1: Loja de Moda

**Categorias:**

**"Verão 2024":**
```
Amarelo:#FFFF00|Laranja:#FFA500|Rosa:#FFC0CB|Azul Claro:#ADD8E6|Verde Limão:#32CD32
```

**"Inverno 2024":**
```
Preto:#000000|Cinza:#808080|Marrom:#A52A2A|Azul Marinho:#000080|Verde Escuro:#006400
```

**"Primavera 2024":**
```
Rosa Pastel:#FFD1DC|Azul Pastel:#AEC6CF|Verde Pastel:#B2E0D4|Amarelo Pastel:#FDFD96
```

---

### Exemplo 2: Loja de Eletrônicos

**Categorias:**

**"Smartphones":**
```
Preto:#000000|Branco:#FFFFFF|Azul:#0000FF|Vermelho:#FF0000|Dourado:#FFD700
```

**"Acessórios":**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Rosa:#FFC0CB|Azul:#0000FF
```

---

### Exemplo 3: Loja de Casa e Decoração

**Categorias:**

**"Minimalista":**
```
Preto:#000000|Branco:#FFFFFF|Cinza Claro:#D3D3D3|Bege:#F5F5DC
```

**"Colorido":**
```
Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00|Amarelo:#FFFF00|Roxo:#800080
```

**"Natural":**
```
Marrom:#A52A2A|Bege:#F5F5DC|Verde Oliva:#808000|Terracota:#E2725B
```

---

## 📋 Checklist de Implementação

### Para Categoria:
- [ ] Criar definição em Metacampos → Coleções
- [ ] Configurar cores na categoria
- [ ] Atualizar código do tema
- [ ] Testar produtos da categoria

### Para Produto:
- [ ] Criar definição em Metacampos → Produtos
- [ ] Configurar cores no produto
- [ ] Testar produto específico

### Para Variante:
- [ ] Criar definição em Metacampos → Variantes
- [ ] Configurar cor na variante
- [ ] Testar variante específica

---

## 🔍 Como Testar

### Teste 1: Categoria

1. Configurar cores na categoria
2. Abrir produto da categoria
3. Ver cores aplicadas
4. ✅ Funcionando!

---

### Teste 2: Produto Sobrescreve Categoria

1. Configurar cores na categoria
2. Configurar cores DIFERENTES no produto
3. Abrir produto
4. Ver cores do PRODUTO (não da categoria)
5. ✅ Prioridade funcionando!

---

### Teste 3: Variante Sobrescreve Tudo

1. Configurar cores na categoria
2. Configurar cores no produto
3. Configurar cor na variante
4. Abrir produto
5. Ver cor da VARIANTE
6. ✅ Prioridade máxima funcionando!

---

## 🆘 Problemas Comuns

### "Cores da categoria não aparecem"

**Verificar:**
1. Metacampo criado em "Coleções"?
2. Valores configurados na coleção?
3. Produto pertence à coleção?
4. Código atualizado com versão COM-CATEGORIA?

---

### "Produto não usa cores da categoria"

**Possíveis causas:**
1. Produto tem próprio metacampo (prioridade maior)
2. Produto não está na coleção
3. Nome da coleção diferente

---

## 💡 Dicas

1. **Use categoria para padrões** - Menos trabalho
2. **Use produto para exceções** - Mais controle
3. **Use variante para casos especiais** - Máxima flexibilidade
4. **Documente suas cores** - Mantenha consistência
5. **Teste a hierarquia** - Entenda as prioridades

---

## 📊 Resumo

### 3 Níveis de Metacampos:

1. **Categoria** → Padrão para todos produtos
2. **Produto** → Sobrescreve categoria
3. **Variante** → Sobrescreve tudo

### Vantagens:

- ✅ Flexibilidade total
- ✅ Menos trabalho manual
- ✅ Fácil manutenção
- ✅ Consistência automática

---

**Use metacampos de categoria para facilitar sua vida! 🎉**
