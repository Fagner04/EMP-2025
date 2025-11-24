# 🔍 DEBUG ATIVO - Veja os Valores dos Metacampos

## ✅ Debug Foi Adicionado ao Código

O arquivo `snippets/product-info.liquid` agora tem debug inline que mostra:
1. Valores dos metacampos do produto
2. Valores processados para cada cor
3. Qual fonte está sendo usada (imagem, metacampo, auto)

---

## 🚀 Como Usar

### PASSO 1: Atualizar o Arquivo

```
Admin Shopify → Temas → Editar código → snippets/product-info.liquid
```

1. Copiar TODO o conteúdo do arquivo local `snippets/product-info.liquid`
2. Colar no admin (substituir tudo)
3. **SALVAR**

---

### PASSO 2: Visualizar Produto

1. Abrir qualquer produto com opção de cor na loja
2. Fazer **Ctrl + F5** (hard refresh)
3. Ver caixas de debug amarelas/brancas

---

## 🔍 O Que Você Vai Ver

### Caixa Amarela (Metacampos do Produto):
```
🔍 DEBUG METACAMPOS:
product.metafields.custom.color_mapping = "Preto:#000000|Branco:#FFFFFF"
product.metafields.custom.color_mapping.value = ""
product.metafields.color.mapping = ""
```

### Caixas Brancas (Para Cada Cor):
```
Cor: Preto
variant_image: NÃO
variant_color_metafield: ""
category_color_metafield: "#000000"
color_mapping_value: "Preto:#000000|Branco:#FFFFFF"
```

---

## 📊 Interpretação dos Resultados

### ✅ CASO 1: Metacampo Funcionando
```
🔍 DEBUG METACAMPOS:
product.metafields.custom.color_mapping = "Preto:#000000"

Cor: Preto
category_color_metafield: "#000000"
```

**Resultado:** Bolinha deve estar PRETA
**Se ainda branca:** Problema no CSS do tema

---

### ❌ CASO 2: Metacampo Vazio
```
🔍 DEBUG METACAMPOS:
product.metafields.custom.color_mapping = ""

Cor: Preto
category_color_metafield: ""
```

**Resultado:** Usando cor automática (preto)
**Problema:** Metacampo não configurado

**Solução:**
1. Admin → Configurações → Metacampos
2. Criar definição (se não existe)
3. Admin → Produtos → Editar produto
4. Preencher metacampo
5. Salvar

---

### ⚠️ CASO 3: Metacampo Existe Mas Não Mapeia
```
🔍 DEBUG METACAMPOS:
product.metafields.custom.color_mapping = "Vermelho:#FF0000"

Cor: Preto
category_color_metafield: ""
```

**Problema:** Nome "Preto" não está no mapeamento
**Solução:** Adicionar "Preto" no metacampo:
```
Vermelho:#FF0000|Preto:#000000
```

---

## 🔧 Configurar Metacampo (Se Vazio)

### Criar Definição:
```
Admin → Configurações → Metacampos → Produtos
↓
Adicionar definição
↓
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
↓
Salvar
```

### Adicionar Valores:
```
Admin → Produtos → Editar produto
↓
Rolar até "Metacampos"
↓
Mapeamento de Cores: Preto:#000000|Branco:#FFFFFF
↓
Salvar
```

---

## 🎨 Teste com Cor Vibrante

Para ter certeza que está funcionando:

1. **Editar produto**
2. **Metacampo:**
   ```
   Preto:#FF0000
   ```
   (Sim, vermelho!)
3. **Salvar**
4. **Recarregar produto (Ctrl+F5)**
5. **Ver debug:**
   ```
   category_color_metafield: "#FF0000"
   ```
6. **Bolinha deve ficar VERMELHA**

Se ficar vermelha: ✅ Metacampo funciona!
Se continuar branca: ❌ Problema no CSS

---

## 🐛 Se Bolinha Continua Branca (Mesmo com Metacampo)

### Verificar no Console:

1. **F12** (abrir DevTools)
2. **Clicar na bolinha branca**
3. **Ver aba "Elements" ou "Elementos"**
4. **Procurar:**
   ```html
   <label class="color-swatch__item" style="background-color: #000000 !important; ...">
   ```

5. **Ver estilos aplicados**

### Se o style está lá mas não funciona:

**Problema:** CSS do tema sobrescrevendo

**Solução:** Adicionar CSS customizado:

```
Admin → Temas → Editar código → assets/theme.css
```

**Adicionar no final:**
```css
/* Forçar cores dos metacampos */
.color-swatch__item[data-debug="category-meta"],
.color-swatch__item[data-debug="variant-meta"],
.color-swatch__item[data-debug="auto"] {
  background-image: none !important;
}

.color-swatch__item[style*="background-color"] {
  background-image: none !important;
}
```

**Salvar e testar**

---

## 📋 Checklist de Debug

- [ ] Arquivo product-info.liquid atualizado
- [ ] Salvo no admin
- [ ] Produto aberto na loja
- [ ] Ctrl+F5 feito
- [ ] Debug amarelo aparece
- [ ] Debug branco aparece para cada cor
- [ ] Valores dos metacampos visíveis

### Se Metacampo Vazio:
- [ ] Definição criada
- [ ] Valores adicionados no produto
- [ ] Produto salvo
- [ ] Página recarregada

### Se Metacampo Tem Valor Mas Bolinha Branca:
- [ ] F12 aberto
- [ ] Elemento inspecionado
- [ ] Style com background-color visível
- [ ] CSS customizado adicionado (se necessário)

---

## 💡 Exemplo Completo

### Produto: Camiseta
### Opções: Cor (Preto, Branco, Cinza)

**Metacampo:**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080
```

**Debug Esperado:**
```
🔍 DEBUG METACAMPOS:
product.metafields.custom.color_mapping = "Preto:#000000|Branco:#FFFFFF|Cinza:#808080"

Cor: Preto
category_color_metafield: "#000000"

Cor: Branco
category_color_metafield: "#FFFFFF"

Cor: Cinza
category_color_metafield: "#808080"
```

**Resultado:**
- Bolinha preta
- Bolinha branca
- Bolinha cinza

---

## 🎯 Próximos Passos

1. **Atualizar arquivo** (Passo 1)
2. **Ver debug** (Passo 2)
3. **Interpretar resultados** (seção acima)
4. **Configurar metacampo** (se vazio)
5. **Adicionar CSS** (se necessário)
6. **Remover debug** (quando funcionar)

---

## 🧹 Remover Debug (Depois de Funcionar)

Quando tudo estiver funcionando, remova as caixas de debug:

1. Procurar por `{%- comment -%}DEBUG:` no código
2. Remover blocos de debug
3. Manter apenas o código funcional
4. Salvar

---

**O debug vai mostrar EXATAMENTE o que está acontecendo! 🔍**
