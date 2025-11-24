# 🔍 VERIFICAR: Metacampo Está Sendo Salvo?

## 🎯 Objetivo

Descobrir se o metacampo está realmente sendo salvo no Shopify.

---

## 📝 PASSO A PASSO (3 Minutos)

### PASSO 1: Adicionar Snippet de Verificação

```
Admin Shopify → Loja Online → Temas → Ações → Editar código
```

**Abrir:**
```
sections/main-product.liquid
OU
sections/product-template.liquid
```

**Procurar:**
```liquid
{% render 'product-info' %}
```

**Adicionar logo APÓS:**
```liquid
{% render 'product-info' %}
{% render 'verificar-metacampos' %}
```

**SALVAR**

---

### PASSO 2: Abrir Produto na Loja

1. Ir no produto que você configurou
2. **Ctrl + F5** (hard refresh)
3. Ver caixa azul de verificação

---

### PASSO 3: Interpretar Resultado

## ✅ CENÁRIO A: Metacampo Salvo

```
🎨 METACAMPO: custom.color_mapping
✅ EXISTE!
Azul bebe:#0066ff|Marrom:#993300

🎨 OPÇÕES DE COR
✅ PRODUTO TEM OPÇÃO DE COR!
Valores: Azul bebe, Marrom

💡 DIAGNÓSTICO
✅ METACAMPO ESTÁ SALVO!
✅ PRODUTO TEM OPÇÃO DE COR!
Tudo configurado corretamente.
```

**Resultado:** Metacampo está salvo! ✅

**Se cores não aparecem:**
- Problema é com nomes que não correspondem
- Ou CSS do tema
- Ou cache do navegador

**Solução:**
1. Verificar se nomes são EXATOS
2. Fazer Ctrl + F5
3. Testar em navegador anônimo

---

## ❌ CENÁRIO B: Metacampo NÃO Salvo

```
🎨 METACAMPO: custom.color_mapping
❌ VAZIO

💡 DIAGNÓSTICO
❌ PROBLEMA: METACAMPO NÃO ESTÁ SALVO!
```

**Resultado:** Metacampo NÃO está sendo salvo! ❌

**Causas possíveis:**
1. Definição não foi criada
2. Tipo de metacampo errado
3. Valor muito longo (256+ caracteres)
4. Produto não foi salvo após adicionar

---

## 🔧 SOLUÇÕES

### Solução 1: Verificar Definição

```
Admin → Configurações → Metacampos → Produtos
```

**Verificar:**
- [ ] Existe "Mapeamento de Cores"?
- [ ] Namespace = `custom`?
- [ ] Key = `color_mapping`?
- [ ] Tipo = Texto de linha única?

**Se NÃO existe:**
1. Clicar "Adicionar definição"
2. Preencher:
   ```
   Nome: Mapeamento de Cores
   Namespace: custom
   Key: color_mapping
   Tipo: Texto de linha única
   ```
3. SALVAR

---

### Solução 2: Verificar Tipo

**Se tipo está errado:**

1. Editar definição
2. Mudar para "Texto de linha única"
3. SALVAR
4. Tentar adicionar valor novamente

---

### Solução 3: Valor Muito Longo

**Se tem muitas cores (256+ caracteres):**

1. Editar definição
2. Mudar tipo para "Texto multilinha"
3. SALVAR
4. Adicionar valor novamente

---

### Solução 4: Adicionar Novamente

1. **Editar produto**
2. **Rolar até "Metacampos"**
3. **Apagar valor atual**
4. **Digitar novamente** (não copiar/colar):
   ```
   Azul bebe:#0066ff|Marrom:#993300
   ```
5. **SALVAR**
6. **Verificar novamente** (Ctrl + F5)

---

### Solução 5: Usar Tags (Alternativa)

**Se metacampo continua não salvando:**

1. **Esquecer metacampos**
2. **Usar tags:**
   ```
   color:Azul bebe:#0066ff
   color:Marrom:#993300
   ```
3. **SALVAR**
4. **Funciona 100%!** ✅

---

## 🎯 Teste Completo

### 1. Criar Produto Novo de Teste

```
Admin → Produtos → Adicionar produto

Nome: TESTE METACAMPO
Preço: 10.00
Opções:
- Nome: Cor
- Valores: Vermelho, Azul
```

**SALVAR**

---

### 2. Adicionar Metacampo

**No mesmo produto:**

1. Rolar até "Metacampos"
2. Preencher "Mapeamento de Cores":
   ```
   Vermelho:#FF0000|Azul:#0000FF
   ```
3. **SALVAR**

---

### 3. Verificar

1. Abrir produto na loja
2. Ctrl + F5
3. Ver caixa azul de verificação

**Se aparecer:**
```
✅ EXISTE!
Vermelho:#FF0000|Azul:#0000FF
```

**Metacampo funciona!** ✅

**Se aparecer:**
```
❌ VAZIO
```

**Metacampo NÃO funciona!** ❌ → Usar tags

---

## 📊 Comparação de Resultados

### Metacampo Salvo ✅
```
🎨 METACAMPO: custom.color_mapping
✅ EXISTE!
Azul bebe:#0066ff|Marrom:#993300
```
→ Problema é com nomes ou CSS

### Metacampo Vazio ❌
```
🎨 METACAMPO: custom.color_mapping
❌ VAZIO
```
→ Problema é com definição ou salvamento

### Tem Tags ✅
```
🏷️ TAGS DO PRODUTO
✅ TEM TAGS DE COR:
color:Azul bebe:#0066ff
color:Marrom:#993300
```
→ Usando tags (funciona!)

---

## 💡 Dicas

### 1. Sempre verificar após salvar
```
Adicionar metacampo → SALVAR → Verificar na loja
```

### 2. Testar com produto novo
```
Criar produto teste → Adicionar metacampo → Ver se salva
```

### 3. Se não salva, usar tags
```
Tags sempre funcionam!
color:Nome:#HEX
```

### 4. Limpar cache
```
Ctrl + F5 sempre após mudanças
```

---

## ✅ Checklist

### Antes de Verificar:
- [ ] Snippet adicionado no tema
- [ ] Tema salvo
- [ ] Produto tem metacampo preenchido
- [ ] Produto foi salvo

### Durante Verificação:
- [ ] Produto aberto na loja
- [ ] Ctrl + F5 feito
- [ ] Caixa azul aparece
- [ ] Ler diagnóstico

### Após Verificação:
- [ ] Problema identificado
- [ ] Solução aplicada
- [ ] Testado novamente
- [ ] Snippet removido

---

## 🎯 Resumo

### Para verificar:
1. Adicionar snippet
2. Abrir produto na loja
3. Ver caixa azul

### Se metacampo salvo:
- ✅ Problema é com nomes ou CSS
- Verificar nomes exatos
- Fazer Ctrl + F5

### Se metacampo vazio:
- ❌ Problema é com definição
- Verificar/criar definição
- Ou usar tags

### Alternativa:
- 🏷️ Usar tags sempre funciona!
- `color:Nome:#HEX`

---

## 🔄 Remover Snippet

**Após verificar, remover:**

```
Admin → Loja Online → Temas → Editar código
sections/main-product.liquid (ou product-template.liquid)
```

**Remover linha:**
```liquid
{% render 'verificar-metacampos' %}
```

**SALVAR**

---

**Use este snippet para descobrir exatamente o que está acontecendo! 🔍**
