# 🚫 Como Desabilitar Cores da Coleção em Produtos Específicos

## 🎯 Problema

Você tem cores configuradas na coleção, mas alguns produtos **não devem** usar essas cores.

## ✅ Solução

Use um metacampo especial para desabilitar as cores da coleção em produtos específicos.

---

## 📝 PASSO 1: Criar Metacampo de Controle

```
Admin Shopify → Configurações → Metacampos → Produtos
```

**Clicar:** "Adicionar definição"

**Preencher:**
```
Nome: Ignorar Cores da Coleção
Namespace: custom
Key: ignore_collection_colors
Tipo: Verdadeiro ou falso (Boolean)
Descrição: Marque para que este produto NÃO use as cores da coleção
```

**SALVAR**

---

## 📝 PASSO 2: Marcar Produtos que NÃO Devem Usar Cores da Coleção

### Para cada produto que você quer desabilitar:

```
Admin → Produtos → Editar produto
```

**Rolar até:** "Metacampos" (no final da página)

**Marcar:** ☑️ "Ignorar Cores da Coleção"

**SALVAR**

---

## 🎨 Como Funciona

### Produto COM o metacampo marcado:

```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Especial" → ☑️ Ignorar Cores da Coleção

RESULTADO: 
- NÃO usa cores da coleção
- Usa cores automáticas (nome da cor)
- Ou usa metacampo próprio do produto (se configurado)
```

### Produto SEM o metacampo marcado:

```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Normal" → ☐ Ignorar Cores da Coleção

RESULTADO: 
- USA cores da coleção normalmente
- Amarelo aparece como #FFFF00
```

---

## 💡 Casos de Uso

### Caso 1: Produto com Cores Próprias

**Cenário:** Produto tem cores únicas que não seguem o padrão da coleção

**Solução:**
1. Marcar ☑️ "Ignorar Cores da Coleção"
2. Configurar metacampo `color_mapping` no produto
3. Produto usa suas próprias cores

**Exemplo:**
```
Coleção "Roupas Casuais" → Preto:#000000|Branco:#FFFFFF
Produto "Camiseta Tie-Dye" → ☑️ Ignorar + color_mapping: Arco-íris:#FF0000|Psicodélico:#FF00FF
```

---

### Caso 2: Produto Sem Cores Definidas

**Cenário:** Produto não deve mostrar cores específicas

**Solução:**
1. Marcar ☑️ "Ignorar Cores da Coleção"
2. Não configurar metacampo no produto
3. Produto usa cores automáticas (nome CSS)

**Exemplo:**
```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Básica" → ☑️ Ignorar
Resultado: Usa "amarelo" (cor CSS automática)
```

---

### Caso 3: Produto com Imagens de Variante

**Cenário:** Produto tem imagens para cada cor, não precisa de cores sólidas

**Solução:**
1. Marcar ☑️ "Ignorar Cores da Coleção"
2. Adicionar imagens nas variantes
3. Produto mostra imagens ao invés de cores

**Exemplo:**
```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Premium" → ☑️ Ignorar + Imagens nas variantes
Resultado: Mostra imagens das variantes
```

---

## 🔄 Ordem de Prioridade Completa

Com o novo metacampo, a ordem fica:

```
1. Imagem da Variante
   ↓
2. PNG em Assets (ex: amarelo.png)
   ↓
3. Metacampo da Variante (variant.metafields.custom.color)
   ↓
4. Metacampo do Produto (product.metafields.custom.color_mapping)
   ↓
5. Metacampo da Coleção (SE ignore_collection_colors = false) ⭐
   ↓
6. Cor Automática (nome da cor)
```

---

## 📊 Exemplos Práticos

### Exemplo 1: Coleção com Exceções

**Coleção "Verão 2024":**
```
Cores: Amarelo:#FFFF00|Laranja:#FFA500|Rosa:#FFC0CB
```

**Produtos:**

1. **Camiseta Básica** (usa cores da coleção)
   - ☐ Ignorar Cores da Coleção
   - Resultado: Amarelo=#FFFF00, Laranja=#FFA500

2. **Camiseta Premium** (cores próprias)
   - ☑️ Ignorar Cores da Coleção
   - color_mapping: Dourado:#FFD700|Prata:#C0C0C0
   - Resultado: Dourado=#FFD700, Prata=#C0C0C0

3. **Camiseta Estampada** (sem cores específicas)
   - ☑️ Ignorar Cores da Coleção
   - Resultado: Cores automáticas

---

### Exemplo 2: Loja de Eletrônicos

**Coleção "Smartphones":**
```
Cores: Preto:#000000|Branco:#FFFFFF|Azul:#0000FF
```

**Produtos:**

1. **iPhone 15** (usa cores da coleção)
   - ☐ Ignorar
   - Resultado: Preto=#000000, Branco=#FFFFFF

2. **Samsung Galaxy** (cores próprias)
   - ☑️ Ignorar
   - color_mapping: Phantom Black:#1A1A1A|Cream:#F5F5DC
   - Resultado: Cores específicas do Samsung

3. **Xiaomi** (imagens de variante)
   - ☑️ Ignorar
   - Imagens nas variantes
   - Resultado: Mostra imagens

---

## 🔧 Solução de Problemas

### Problema: "Marquei para ignorar mas ainda usa cores da coleção"

**Verificar:**

1. **Metacampo criado corretamente?**
   ```
   Configurações → Metacampos → Produtos
   Namespace: custom
   Key: ignore_collection_colors
   Tipo: Verdadeiro ou falso
   ```

2. **Checkbox marcado no produto?**
   ```
   Editar produto → Metacampos
   ☑️ Ignorar Cores da Coleção
   ```

3. **Produto salvo?**
   ```
   Clicar em SALVAR após marcar
   ```

4. **Cache limpo?**
   ```
   Ctrl + F5 no navegador
   ```

---

### Problema: "Quero que produto use cores próprias E ignore coleção"

**Solução:**
1. Marcar ☑️ "Ignorar Cores da Coleção"
2. Configurar metacampo `color_mapping` no produto
3. Produto usará apenas suas próprias cores

**Exemplo:**
```
Produto:
- ☑️ Ignorar Cores da Coleção
- color_mapping: Vermelho:#FF0000|Azul:#0000FF

Resultado: Usa apenas Vermelho e Azul do produto
```

---

## ✅ Checklist

### Configuração Inicial:
- [ ] Metacampo `ignore_collection_colors` criado
- [ ] Tipo: "Verdadeiro ou falso"
- [ ] Namespace: `custom`
- [ ] Key: `ignore_collection_colors`

### Para Cada Produto:
- [ ] Decidir se deve ignorar cores da coleção
- [ ] Se SIM: Marcar ☑️ checkbox
- [ ] Se NÃO: Deixar ☐ desmarcado
- [ ] Salvar produto
- [ ] Testar (Ctrl + F5)

---

## 📋 Resumo

### Produto Normal (usa cores da coleção):
```
☐ Ignorar Cores da Coleção
```

### Produto Especial (não usa cores da coleção):
```
☑️ Ignorar Cores da Coleção
```

### Produto com Cores Próprias:
```
☑️ Ignorar Cores da Coleção
+ color_mapping: Cor1:#HEX|Cor2:#HEX
```

---

## 💡 Dicas

1. **Use para exceções** - Marque apenas produtos que realmente precisam
2. **Mantenha consistência** - A maioria deve usar cores da coleção
3. **Documente** - Anote quais produtos ignoram e por quê
4. **Teste sempre** - Ctrl + F5 após cada mudança

---

## 🎯 Vantagens

✅ **Flexibilidade total** - Controle por produto
✅ **Fácil de usar** - Apenas um checkbox
✅ **Não afeta outros** - Produtos normais continuam funcionando
✅ **Reversível** - Desmarque para voltar ao normal
✅ **Sem código** - Tudo via admin

---

**Agora você tem controle total sobre quais produtos usam cores da coleção! 🎉**
