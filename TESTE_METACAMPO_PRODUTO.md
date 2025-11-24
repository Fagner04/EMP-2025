# 🧪 TESTE: Metacampo do Produto - Passo a Passo

## ✅ Código Atualizado

O código foi atualizado para suportar **múltiplos formatos** de metacampo:
- ✅ `product.metafields.custom.color_mapping.value`
- ✅ `product.metafields.custom.color_mapping`
- ✅ `product.metafields.color_mapping.value`
- ✅ `product.metafields.color_mapping`
- ✅ `product.metafields.color.mapping`

---

## 🔍 TESTE COMPLETO (10 Minutos)

### PASSO 1: Verificar Definição do Metacampo

```
Admin Shopify → Configurações → Metacampos → Produtos
```

**Verificar se existe:**
- Nome: Mapeamento de Cores (ou similar)
- Namespace: `custom` ⭐ IMPORTANTE
- Key: `color_mapping` ⭐ IMPORTANTE
- Tipo: Texto de linha única (ou Texto multilinha)

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

### PASSO 2: Criar Produto de Teste

```
Admin → Produtos → Adicionar produto
```

**Configurar:**
```
Nome: TESTE CORES
Preço: 10.00

Opções:
- Nome: Cor
- Valores: Vermelho, Azul, Verde

Variantes: (criar automaticamente)
```

**SALVAR** (importante salvar antes de adicionar metacampo)

---

### PASSO 3: Adicionar Metacampo no Produto

**No mesmo produto (TESTE CORES):**

1. **Rolar até o final da página**
2. **Procurar seção "Metacampos"**
3. **Preencher "Mapeamento de Cores":**
   ```
   Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00
   ```

**IMPORTANTE:**
- Sem espaços antes/depois de `:`
- Sem espaços antes/depois de `|`
- Nomes EXATAMENTE iguais às opções (Vermelho, Azul, Verde)
- Use `#` antes do código hex

4. **SALVAR**

---

### PASSO 4: Adicionar Debug no Tema

```
Admin → Loja Online → Temas → Ações → Editar código
```

**Abrir:**
```
sections/main-product.liquid
OU
sections/product-template.liquid
```

**Procurar linha:**
```liquid
{% render 'product-info' %}
```

**Adicionar logo APÓS:**
```liquid
{% render 'product-info' %}
{% render 'debug-product-metafields' %}
```

**SALVAR**

---

### PASSO 5: Testar na Loja

1. **Abrir produto "TESTE CORES" na loja**
   ```
   Clicar em "Visualizar" no admin
   OU
   Ir direto na URL do produto
   ```

2. **Fazer hard refresh:**
   ```
   Ctrl + F5 (Windows)
   Cmd + Shift + R (Mac)
   ```

3. **Ver caixa laranja de debug**

---

### PASSO 6: Interpretar Debug

#### ✅ CENÁRIO A: Funcionando

```
🎨 METACAMPO color_mapping:
✅ product.metafields.custom.color_mapping.value:
Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00

🎨 OPÇÕES DE COR DO PRODUTO:
• Vermelho
  ✅ Encontrado: #FF0000
• Azul
  ✅ Encontrado: #0000FF
• Verde
  ✅ Encontrado: #00FF00

💡 DIAGNÓSTICO:
✅ Nomes correspondem! Cores devem funcionar.
```

**Resultado esperado:**
- Bolinha vermelha 🔴
- Bolinha azul 🔵
- Bolinha verde 🟢

**Se cores aparecem:** ✅ FUNCIONANDO!

---

#### ❌ CENÁRIO B: Metacampo Vazio

```
🎨 METACAMPO color_mapping:
❌ Vazio

💡 DIAGNÓSTICO:
❌ PROBLEMA: Metacampo não existe ou está vazio!
```

**SOLUÇÃO:**
1. Voltar no produto
2. Verificar se metacampo foi salvo
3. Tentar adicionar novamente
4. SALVAR
5. Testar novamente (Ctrl + F5)

---

#### ❌ CENÁRIO C: Nomes Não Correspondem

```
🎨 METACAMPO color_mapping:
✅ Vermelho:#FF0000|Azul:#0000FF

🎨 OPÇÕES DE COR DO PRODUTO:
• vermelho (minúscula)
  ❌ NÃO encontrado no metacampo

💡 DIAGNÓSTICO:
❌ PROBLEMA: Nomes não correspondem!
```

**SOLUÇÃO:**
1. Copiar nomes EXATOS do debug
2. Editar metacampo
3. Usar nomes exatos
4. SALVAR
5. Testar novamente (Ctrl + F5)

---

#### ❌ CENÁRIO D: Formato Errado

```
🎨 METACAMPO color_mapping:
✅ Vermelho #FF0000, Azul #0000FF

🎨 OPÇÕES DE COR DO PRODUTO:
• Vermelho
  ❌ NÃO encontrado no metacampo
```

**PROBLEMA:** Formato errado (espaços, vírgulas)

**SOLUÇÃO:**
Formato correto:
```
❌ Vermelho #FF0000, Azul #0000FF (espaços e vírgulas)
❌ Vermelho: #FF0000 | Azul: #0000FF (espaços extras)
✅ Vermelho:#FF0000|Azul:#0000FF (correto)
```

---

### PASSO 7: Remover Debug (Após Funcionar)

```
Admin → Loja Online → Temas → Ações → Editar código
sections/main-product.liquid (ou product-template.liquid)
```

**Remover linha:**
```liquid
{% render 'debug-product-metafields' %}
```

**SALVAR**

---

## 🎯 Teste Rápido (3 Minutos)

Se você já tem produto configurado:

1. **Adicionar debug** (PASSO 4)
2. **Abrir produto na loja** (PASSO 5)
3. **Ver debug** (PASSO 6)
4. **Seguir solução** conforme cenário

---

## 📋 Checklist de Verificação

### Definição do Metacampo:
- [ ] Existe em Configurações → Metacampos → Produtos
- [ ] Namespace = `custom`
- [ ] Key = `color_mapping`
- [ ] Tipo = Texto de linha única (ou multilinha)

### Produto:
- [ ] Tem opção "Cor" (ou similar)
- [ ] Opção tem valores (ex: Vermelho, Azul)
- [ ] Produto foi salvo

### Metacampo no Produto:
- [ ] Seção "Metacampos" existe no produto
- [ ] Campo "Mapeamento de Cores" aparece
- [ ] Valor preenchido: `Cor:#HEX|Cor:#HEX`
- [ ] Nomes EXATOS das opções
- [ ] Produto foi salvo após preencher

### Debug:
- [ ] Snippet adicionado no tema
- [ ] Tema salvo
- [ ] Produto aberto na loja
- [ ] Ctrl + F5 feito
- [ ] Caixa laranja aparece

### Resultado:
- [ ] Debug mostra metacampo ✅
- [ ] Debug mostra nomes correspondem ✅
- [ ] Cores aparecem nas bolinhas ✅

---

## 🐛 Problemas Comuns

### 1. "Metacampo não aparece no produto"

**Causa:** Definição não criada ou tipo errado

**Solução:**
```
1. Configurações → Metacampos → Produtos
2. Verificar se existe "Mapeamento de Cores"
3. Verificar namespace: custom
4. Verificar key: color_mapping
5. Se não existe, criar
```

---

### 2. "Não consigo salvar o valor"

**Causa:** Valor muito longo (256+ caracteres)

**Solução:**
```
1. Editar definição do metacampo
2. Mudar tipo para "Texto multilinha"
3. Salvar
4. Tentar adicionar valor novamente
```

---

### 3. "Debug não aparece"

**Causa:** Snippet não adicionado ou arquivo errado

**Solução:**
```
1. Verificar se adicionou em main-product.liquid ou product-template.liquid
2. Verificar se salvou o tema
3. Fazer Ctrl + F5
4. Tentar navegador anônimo
```

---

### 4. "Cores aparecem brancas"

**Causa:** CSS do tema sobrescrevendo

**Solução:**
```
Adicionar em assets/theme.css:

.color-swatch__item {
  background-image: none !important;
}

.color-swatch__item[style*="background"] {
  background-image: none !important;
}
```

---

### 5. "Funciona em alguns produtos, não em outros"

**Causa:** Nomes diferentes em cada produto

**Solução:**
```
1. Usar debug em cada produto
2. Copiar nomes exatos das opções
3. Ajustar metacampo com nomes corretos
4. Salvar
```

---

## 💡 Dicas Importantes

### 1. Sempre use nomes EXATOS
```
Opção: "Azul claro"
Metacampo: "Azul claro:#ADD8E6" ✅
Metacampo: "Azul Claro:#ADD8E6" ❌ (C maiúsculo)
Metacampo: "azul claro:#ADD8E6" ❌ (a minúsculo)
```

### 2. Formato sem espaços extras
```
✅ Vermelho:#FF0000|Azul:#0000FF
❌ Vermelho: #FF0000 | Azul: #0000FF
❌ Vermelho:#FF0000 | Azul:#0000FF
```

### 3. Sempre salvar antes de testar
```
1. Adicionar/editar metacampo
2. SALVAR produto
3. Abrir na loja
4. Ctrl + F5
```

### 4. Use debug para tudo
```
Debug mostra EXATAMENTE o que está errado:
- Metacampo vazio?
- Nomes não correspondem?
- Formato errado?
```

### 5. Teste com cores vibrantes
```
Use vermelho (#FF0000) para testar
Mais fácil de ver se funciona
Depois mude para cor correta
```

---

## ✅ Exemplo Completo

### Produto:
```
Nome: Camiseta Básica
Opções:
- Cor: Amarelo, Azul, Verde
```

### Metacampo:
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
```

### Debug Esperado:
```
✅ Metacampo: Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
✅ Amarelo encontrado: #FFFF00
✅ Azul encontrado: #0000FF
✅ Verde encontrado: #00FF00
```

### Resultado:
```
🟡 Bolinha amarela
🔵 Bolinha azul
🟢 Bolinha verde
```

---

## 📞 Ainda Não Funciona?

Se após seguir TODOS os passos ainda não funcionar:

1. **Tire screenshot do debug**
2. **Copie o valor do metacampo**
3. **Copie os nomes das opções**
4. **Verifique:**
   - Namespace = `custom`?
   - Key = `color_mapping`?
   - Formato correto?
   - Nomes exatos?
   - Produto salvo?
   - Ctrl + F5 feito?

---

**Use o debug! Ele vai te dizer EXATAMENTE o que está errado! 🔍**
