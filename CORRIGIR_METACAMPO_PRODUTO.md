# 🔧 CORRIGIR: Metacampo do Produto Não Funciona

## 🎯 Problema

Você configurou cores no metacampo do produto mas elas não aparecem.

---

## 🔍 PASSO 1: Adicionar Debug

### 1. Abrir tema:
```
Admin Shopify → Loja Online → Temas → Ações → Editar código
```

### 2. Abrir arquivo do produto:
```
sections/main-product.liquid
OU
sections/product-template.liquid
```

### 3. Adicionar debug (após `{% render 'product-info' %}`):
```liquid
{% render 'product-info' %}
{% render 'debug-product-metafields' %}
```

### 4. SALVAR

### 5. Abrir produto na loja:
```
Ctrl + F5 (hard refresh)
```

### 6. Ver caixa laranja de debug

---

## 📋 O Que o Debug Mostra

### Cenário A: Metacampo Vazio ❌

```
🎨 METACAMPO color_mapping:
product.metafields.custom.color_mapping.value:
❌ Vazio

💡 DIAGNÓSTICO:
❌ PROBLEMA: Metacampo não existe ou está vazio!
```

**SOLUÇÃO:** Ir para PASSO 2 (Criar Metacampo)

---

### Cenário B: Metacampo Existe Mas Nomes Não Correspondem ❌

```
🎨 METACAMPO color_mapping:
✅ Amarelo:#FFFF00|Azul:#0000FF

🎨 OPÇÕES DE COR DO PRODUTO:
• Amarelo claro
  ❌ NÃO encontrado no metacampo

💡 DIAGNÓSTICO:
❌ PROBLEMA: Nomes não correspondem!
```

**SOLUÇÃO:** Ir para PASSO 3 (Corrigir Nomes)

---

### Cenário C: Tudo Correto Mas Não Aparece ⚠️

```
🎨 METACAMPO color_mapping:
✅ Amarelo:#FFFF00|Azul:#0000FF

🎨 OPÇÕES DE COR DO PRODUTO:
• Amarelo
  ✅ Encontrado: #FFFF00

💡 DIAGNÓSTICO:
✅ Nomes correspondem! Cores devem funcionar.
Se não aparecem: Problema no CSS ou prioridade.
```

**SOLUÇÃO:** Ir para PASSO 4 (Verificar Prioridade)

---

## 🛠️ PASSO 2: Criar Metacampo (Se Não Existe)

### A. Criar Definição:

```
Admin Shopify → Configurações → Metacampos → Produtos
```

**Clicar:** "Adicionar definição"

**Preencher:**
```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única (ou Texto multilinha para muitas cores)
Descrição: Formato: NomeCor:#HEX|OutraCor:#HEX
```

**SALVAR**

---

### B. Adicionar Valores no Produto:

```
Admin → Produtos → Editar produto
```

**Rolar até:** "Metacampos" (no final da página)

**Preencher "Mapeamento de Cores":**

**IMPORTANTE:** Nomes devem ser EXATAMENTE iguais às opções do produto!

**Exemplo:**
```
Se opções são: Amarelo, Azul, Verde

Metacampo deve ser:
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
```

**SALVAR**

---

### C. Testar:

1. Abrir produto na loja
2. **Ctrl + F5**
3. Ver debug
4. Verificar se aparece ✅

---

## 🎯 PASSO 3: Corrigir Nomes (Se Não Correspondem)

### Problema Comum: Nomes Diferentes

**Opção do produto:**
```
Amarelo claro
```

**Metacampo:**
```
Amarelo:#FFFF00  ❌ ERRADO
```

**Correto:**
```
Amarelo claro:#FFFFE0  ✅ CORRETO
```

---

### Como Descobrir Nomes Exatos:

1. **Ver no debug:**
   ```
   🎨 OPÇÕES DE COR DO PRODUTO:
   Opção: Cor
   Valores:
   • Amarelo claro  ← COPIE ESTE NOME EXATO
   • Azul escuro
   ```

2. **Ou ver no admin:**
   ```
   Admin → Produtos → Editar produto
   Seção "Opções" → Ver valores
   ```

3. **Copiar nome EXATO**

4. **Colar no metacampo:**
   ```
   Amarelo claro:#FFFFE0|Azul escuro:#00008B
   ```

---

### Erros Comuns:

❌ **Maiúsculas/Minúsculas:**
```
Opção: Amarelo
Metacampo: amarelo:#FFFF00  ❌ ERRADO (minúscula)
Correto: Amarelo:#FFFF00    ✅
```

❌ **Espaços extras:**
```
Opção: Amarelo
Metacampo: Amarelo :#FFFF00  ❌ ERRADO (espaço antes de :)
Correto: Amarelo:#FFFF00     ✅
```

❌ **Acentos:**
```
Opção: Azul Bebê
Metacampo: Azul Bebe:#ADD8E6  ❌ ERRADO (sem acento)
Correto: Azul Bebê:#ADD8E6    ✅
```

---

## 🔄 PASSO 4: Verificar Prioridade

Se o debug mostra que tudo está correto mas cores não aparecem, pode ser problema de prioridade.

### Ordem de Prioridade:

```
1. Imagem da Variante (maior)
2. PNG em Assets
3. Metacampo da Variante
4. Metacampo do Produto ← VOCÊ ESTÁ AQUI
5. Tags do Produto
6. Metacampo da Coleção
7. Cor Automática (menor)
```

---

### Verificar:

**A. Produto tem imagens nas variantes?**
```
Se SIM: Imagens têm prioridade maior
Solução: Remover imagens ou aceitar que imagens aparecem
```

**B. Tem PNGs em Assets?**
```
Verificar: assets/amarelo.png existe?
Se SIM: PNG tem prioridade maior
Solução: Remover PNG ou renomear
```

**C. Variantes têm metacampo de cor?**
```
Editar produto → Clicar em variante → Ver metacampos
Se tem "Cor": Variante tem prioridade maior
Solução: Remover metacampo da variante
```

---

## ✅ PASSO 5: Teste Completo

### Teste Mínimo:

1. **Criar produto novo:**
   ```
   Nome: Teste Cores
   Opções: Cor (Vermelho, Azul)
   ```

2. **Adicionar metacampo:**
   ```
   Metacampos → Mapeamento de Cores:
   Vermelho:#FF0000|Azul:#0000FF
   ```

3. **Salvar**

4. **Abrir na loja:**
   ```
   Ctrl + F5
   Ver debug
   ```

5. **Verificar:**
   ```
   ✅ Metacampo aparece no debug?
   ✅ Nomes correspondem?
   ✅ Cores aparecem nas bolinhas?
   ```

---

## 🎨 Exemplos Práticos

### Exemplo 1: Cores Básicas

**Opções do produto:**
```
Cor: Amarelo, Azul, Verde
```

**Metacampo:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
```

**Resultado esperado:**
- Bolinha amarela 🟡
- Bolinha azul 🔵
- Bolinha verde 🟢

---

### Exemplo 2: Cores com Espaço

**Opções do produto:**
```
Cor: Azul claro, Azul escuro, Verde limão
```

**Metacampo:**
```
Azul claro:#ADD8E6|Azul escuro:#00008B|Verde limão:#32CD32
```

**Resultado esperado:**
- Bolinha azul clara
- Bolinha azul escura
- Bolinha verde limão

---

### Exemplo 3: Muitas Cores

**Opções do produto:**
```
Cor: Preto, Branco, Cinza, Vermelho, Azul, Verde, Amarelo, Rosa, Roxo, Laranja
```

**Metacampo:**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00|Amarelo:#FFFF00|Rosa:#FFC0CB|Roxo:#800080|Laranja:#FFA500
```

**Se ultrapassar 256 caracteres:**
- Mudar tipo para "Texto multilinha"

---

## 🐛 Problemas Específicos

### Problema 1: "Metacampo não aparece na lista"

**Causa:** Definição não criada

**Solução:**
1. Configurações → Metacampos → Produtos
2. Verificar se existe "Mapeamento de Cores"
3. Se não existe, criar (PASSO 2)

---

### Problema 2: "Não consigo salvar valores"

**Causa:** Tipo de metacampo errado ou muito longo

**Solução:**
1. Verificar tipo: deve ser "Texto de linha única" ou "Texto multilinha"
2. Se muito longo (256+ caracteres), mudar para "Texto multilinha"

---

### Problema 3: "Cores aparecem em alguns produtos, não em outros"

**Causa:** Nomes diferentes em cada produto

**Solução:**
1. Usar debug em cada produto
2. Verificar nomes exatos
3. Copiar/colar entre produtos similares

---

### Problema 4: "Cores da coleção sobrescrevem produto"

**IMPOSSÍVEL!** Produto tem prioridade maior que coleção.

**Se acontecer:**
1. Verificar se metacampo do produto está realmente preenchido
2. Ver debug para confirmar
3. Pode ser cache do navegador (Ctrl + Shift + Delete)

---

## 📋 Checklist Final

### Configuração:
- [ ] Metacampo criado em Produtos
- [ ] Namespace: `custom`
- [ ] Key: `color_mapping`
- [ ] Tipo: Texto de linha única (ou multilinha)

### Valores:
- [ ] Metacampo preenchido no produto
- [ ] Formato: `Cor:#HEX|Cor:#HEX`
- [ ] Nomes EXATAMENTE iguais às opções
- [ ] Sem espaços extras
- [ ] Produto salvo

### Debug:
- [ ] Debug adicionado no tema
- [ ] Produto aberto na loja
- [ ] Ctrl + F5 feito
- [ ] Debug mostra metacampo ✅
- [ ] Debug mostra nomes correspondem ✅

### Resultado:
- [ ] Cores aparecem nas bolinhas
- [ ] Funciona em todos produtos configurados
- [ ] Debug removido após confirmar

---

## 🎯 Resumo Rápido

1. **Adicionar debug** → Ver o que está acontecendo
2. **Criar metacampo** → Se não existe
3. **Corrigir nomes** → Devem ser EXATOS
4. **Verificar prioridade** → Imagens/variantes podem sobrescrever
5. **Testar** → Ctrl + F5 sempre
6. **Remover debug** → Após funcionar

---

## 💡 Dica Final

Se após tudo isso ainda não funcionar:

1. **Tire screenshot do debug**
2. **Copie o JSON dos metacampos** (aparece no debug)
3. **Verifique:**
   - Código atualizado?
   - Cache limpo?
   - Navegador anônimo?

---

**Use o debug para descobrir exatamente o que está errado! 🔍**
