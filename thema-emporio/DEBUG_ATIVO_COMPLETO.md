# 🔍 DEBUG ATIVO - Diagnóstico Completo

## ✅ Debug Foi Adicionado

O código agora tem debug COMPLETO que mostra:
1. ✅ Valores dos metacampos (produto e categoria)
2. ✅ Qual fonte está sendo usada para cada cor
3. ✅ Cores sendo aplicadas
4. ✅ Se CSS está funcionando

---

## 🚀 Como Usar

### PASSO 1: Atualizar Arquivo

```
Admin Shopify → Temas → Editar código
→ snippets/product-info.liquid
```

1. Copiar TODO o conteúdo do arquivo local
2. Colar no admin (substituir tudo)
3. **SALVAR**

---

### PASSO 2: Visualizar Produto

1. Abrir produto na loja
2. **Ctrl + Shift + R** (limpar cache)
3. Ver caixas de debug

---

## 🔍 O Que Você Vai Ver

### Caixa Vermelha (Metacampos):

```
🔍 DEBUG METACAMPOS:

PRODUTO:
product.metafields.custom.color_mapping = "Amarelo:#FFFF00|Azul:#0000FF"
✅ TEM VALOR

CATEGORIA/COLEÇÃO:
collection = Roupas de Verão
collection.metafields.custom.color_mapping = "Vermelho:#FF0000"
✅ TEM VALOR

CSS APLICADO?
Verifique se theme.css tem o CSS corretivo no final
```

---

### Caixas Brancas (Para Cada Cor):

```
Amarelo
Fonte: produto
Cor: #FFFF00 [bolinha amarela]
product_color: "#FFFF00"
collection_color: ""
```

---

## 📊 Interpretação dos Resultados

### CENÁRIO 1: Metacampo do Produto Funciona ✅

```
PRODUTO:
✅ TEM VALOR

Amarelo
Fonte: produto
Cor: #FFFF00
product_color: "#FFFF00"
```

**Resultado:** Usando cor do produto
**Se bolinha está branca:** Problema no CSS

---

### CENÁRIO 2: Metacampo da Categoria Funciona ✅

```
PRODUTO:
❌ VAZIO

CATEGORIA:
✅ TEM VALOR

Amarelo
Fonte: categoria
Cor: #FFFF00
collection_color: "#FFFF00"
```

**Resultado:** Usando cor da categoria
**Se bolinha está branca:** Problema no CSS

---

### CENÁRIO 3: Ambos Vazios ❌

```
PRODUTO:
❌ VAZIO

CATEGORIA:
❌ VAZIO

Amarelo
Fonte: automatica
Cor: amarelo
product_color: ""
collection_color: ""
```

**Resultado:** Usando cor automática
**Problema:** Metacampos não configurados

---

### CENÁRIO 4: Categoria Não Aparece ❌

```
CATEGORIA:
collection = 
collection.metafields.custom.color_mapping = ""
❌ VAZIO
```

**Possíveis causas:**
1. Produto não está em nenhuma coleção
2. Metacampo não foi criado em "Coleções"
3. Metacampo não foi preenchido na coleção

---

## 🔧 Soluções por Cenário

### Se "CATEGORIA: ❌ VAZIO"

#### Solução 1: Criar Metacampo de Coleção

```
Admin → Configurações → Metacampos → Coleções
→ Adicionar definição
```

**Preencher:**
```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
```

**SALVAR**

---

#### Solução 2: Configurar na Coleção

```
Admin → Produtos → Coleções → Selecionar coleção
→ Rolar até "Metacampos"
```

**Preencher:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
```

**SALVAR**

---

#### Solução 3: Adicionar Produto à Coleção

```
Admin → Produtos → Editar produto
→ Seção "Organização"
→ Tipo de produto / Fornecedor / Coleções
→ Adicionar à coleção
```

**SALVAR**

---

### Se "Fonte: produto" ou "Fonte: categoria" MAS Bolinha Branca

**Problema:** CSS não está aplicando

**Solução:** Verificar CSS

```
Admin → Temas → Editar código → assets/theme.css
```

**Ir até o FINAL e verificar se tem:**

```css
/* CORREÇÃO: Cores de Metacampos */
.color-swatch__item[style*="background-color"] {
  background-size: auto !important;
  background-image: none !important;
}

label.color-swatch__item[style] {
  background-image: none !important;
}
```

**Se não tem:** Adicionar e salvar

---

### Se "Fonte: automatica"

**Problema:** Nenhum metacampo configurado

**Solução:** Configurar metacampo (produto OU categoria)

---

## 🧪 Teste Passo a Passo

### Teste 1: Verificar se Produto Está em Coleção

```
Admin → Produtos → Editar produto
→ Ver seção "Organização"
→ Ver campo "Coleções"
```

**Se vazio:** Adicionar à coleção

---

### Teste 2: Verificar Metacampo da Coleção

```
Admin → Produtos → Coleções → Editar coleção
→ Rolar até "Metacampos"
```

**Se não aparece:** Criar definição primeiro

**Se aparece vazio:** Preencher com cores

---

### Teste 3: Verificar CSS

```
Admin → Temas → Editar código → assets/theme.css
→ Ir até o final
→ Procurar por "Cores de Metacampos"
```

**Se não encontrar:** Adicionar CSS

---

## 📋 Checklist de Debug

- [ ] Debug aparece na página?
- [ ] Caixa vermelha mostra metacampos?
- [ ] Caixas brancas mostram cada cor?
- [ ] "Fonte" mostra de onde vem a cor?
- [ ] Cor está sendo aplicada?

### Se Metacampo Vazio:
- [ ] Definição foi criada?
- [ ] Valores foram adicionados?
- [ ] Produto está na coleção? (para categoria)
- [ ] Produto foi salvo?

### Se Cor Não Aparece:
- [ ] CSS foi adicionado?
- [ ] CSS foi salvo?
- [ ] Cache foi limpo?
- [ ] Página foi recarregada?

---

## 💡 Dicas

1. **Limpe o cache sempre:** Ctrl + Shift + R
2. **Teste em navegador anônimo:** Sem cache
3. **Verifique o console:** F12 → Console (ver erros)
4. **Inspecione a bolinha:** F12 → Clicar na bolinha → Ver estilos

---

## 🎯 Próximos Passos

1. **Atualizar arquivo** com debug
2. **Visualizar produto** na loja
3. **Ler o debug** e identificar problema
4. **Aplicar solução** correspondente
5. **Testar novamente**

---

**O debug vai mostrar EXATAMENTE o que está acontecendo! 🔍**
