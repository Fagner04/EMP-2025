# 🔧 Corrigir Bolinhas Brancas - Cores Não Aparecem

## ✅ Correção Aplicada

O código foi atualizado para:
1. ✅ Remover classe `lazyload` quando usar cores (não imagens)
2. ✅ Adicionar `!important` para sobrescrever CSS existente
3. ✅ Adicionar `background-image: none !important` para remover imagens de fundo

---

## 🚀 Passo a Passo para Corrigir

### PASSO 1: Atualizar Arquivos (OBRIGATÓRIO)

Copie os arquivos atualizados para o tema:

```
Admin Shopify → Temas → Editar código
```

**Arquivos para atualizar:**

1. **snippets/product-info.liquid**
   - Copiar TODO o conteúdo do arquivo local
   - Colar no admin
   - Salvar

2. **snippets/product-item.liquid**
   - Copiar TODO o conteúdo do arquivo local
   - Colar no admin
   - Salvar

3. **snippets/debug-inline-colors.liquid** (NOVO)
   - Criar novo snippet
   - Copiar conteúdo
   - Salvar

---

### PASSO 2: Adicionar Debug Inline

**Em: snippets/product-info.liquid**

Procure por esta linha (aproximadamente linha 260):
```liquid
{%- when 'color' -%}
```

**Adicione LOGO ACIMA:**
```liquid
{% render 'debug-inline-colors' %}
{%- when 'color' -%}
```

**Salvar**

---

### PASSO 3: Configurar Metacampo

#### A. Criar Definição (se ainda não criou):

```
Admin → Configurações → Metacampos → Produtos
```

**Adicionar definição:**
```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
```

**Salvar**

#### B. Adicionar Valores no Produto:

```
Admin → Produtos → Editar produto
```

**Rolar até "Metacampos"**

**Preencher "Mapeamento de Cores":**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080
```

**IMPORTANTE:**
- Use os nomes EXATOS das opções do produto
- Sem espaços antes/depois de : ou |
- Códigos hexadecimais válidos

**Exemplo para o produto da imagem:**
```
Preto:#000000
```

**Salvar**

---

### PASSO 4: Limpar Cache e Testar

1. **Salvar todas as mudanças**
2. **Abrir produto na loja**
3. **Fazer hard refresh:**
   - Windows: `Ctrl + Shift + R` ou `Ctrl + F5`
   - Mac: `Cmd + Shift + R`

---

## 🔍 Verificar Debug

Você deve ver uma caixa amarela com informações:

### ✅ Se aparecer assim:
```
🔍 DEBUG - Valores de Cor

Metacampo do Produto:
custom.color_mapping: Preto:#000000|Branco:#FFFFFF

Opção: Preto
Cor do Mapeamento: #000000 [bolinha preta]
```

**Significa:** Metacampo configurado corretamente!

### ❌ Se aparecer assim:
```
Metacampo do Produto:
custom.color_mapping: 
(vazio)

Opção: Preto
Cor do Mapeamento: NÃO ENCONTRADO
```

**Significa:** Metacampo não configurado ou nome não corresponde

---

## 🎨 Exemplos de Configuração

### Para o Produto da Imagem (Cor: Preto):

**Metacampo:**
```
Preto:#000000
```

**Resultado esperado:**
- Bolinha preta sólida

---

### Para Produto com Múltiplas Cores:

**Opções:** Preto, Branco, Cinza, Vermelho

**Metacampo:**
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Vermelho:#DC143C
```

**Resultado esperado:**
- Bolinha preta
- Bolinha branca
- Bolinha cinza
- Bolinha vermelha

---

## 🐛 Problemas Comuns

### Problema 1: Bolinhas Ainda Brancas

**Causa:** Nomes não correspondem

**Solução:**
1. Ver debug inline
2. Comparar "Opção:" com nome no metacampo
3. Devem ser IDÊNTICOS (maiúsculas/minúsculas)

**Exemplo:**
```
❌ Opção: "Preto" → Metacampo: "preto:#000000"
✅ Opção: "Preto" → Metacampo: "Preto:#000000"
```

---

### Problema 2: Debug Não Aparece

**Causa:** Snippet não adicionado

**Solução:**
1. Verificar se arquivo `debug-inline-colors.liquid` existe
2. Verificar se `{% render 'debug-inline-colors' %}` foi adicionado
3. Salvar e fazer Ctrl+F5

---

### Problema 3: Metacampo Vazio no Debug

**Causa:** Definição não criada ou valores não salvos

**Solução:**
1. Criar definição PRIMEIRO (Passo 3A)
2. DEPOIS adicionar valores (Passo 3B)
3. Salvar produto
4. Aguardar alguns segundos
5. Recarregar página

---

### Problema 4: Cor Aparece no Debug, Mas Não na Bolinha

**Causa:** CSS do tema sobrescrevendo

**Solução:** O código já foi atualizado com `!important`. Se ainda não funcionar:

1. Inspecionar elemento (F12)
2. Clicar na bolinha branca
3. Ver estilos aplicados
4. Procurar por `background-color` ou `background-image`
5. Ver qual CSS está sobrescrevendo

**Adicionar no tema (se necessário):**
```css
.color-swatch__item[style*="background-color"] {
  background-image: none !important;
}
```

---

## ✅ Checklist de Verificação

- [ ] Arquivos atualizados no tema
- [ ] Debug inline adicionado
- [ ] Definição de metacampo criada
- [ ] Valores adicionados no produto
- [ ] Nomes correspondem EXATAMENTE
- [ ] Cache limpo (Ctrl+F5)
- [ ] Debug mostra valores
- [ ] Cores aparecem nas bolinhas

---

## 📊 Teste Rápido

### Teste Mínimo (2 minutos):

1. **Editar produto da imagem**
2. **Metacampos → Mapeamento de Cores:**
   ```
   Preto:#FF0000
   ```
   (Sim, vermelho para testar!)
3. **Salvar**
4. **Recarregar página do produto**
5. **Bolinha deve ficar VERMELHA**

Se ficar vermelha: ✅ Funcionando!
Se continuar branca: ❌ Ver problemas comuns acima

---

## 🎯 Resultado Esperado

### Antes:
```
Cor: Preto
┌───┐ ┌───┐ ┌───┐
│   │ │   │ │   │  ← Bolinhas brancas
└───┘ └───┘ └───┘
```

### Depois:
```
Cor: Preto
┌───┐ ┌───┐ ┌───┐
│ ● │ │ ● │ │ ● │  ← Bolinhas com cores!
└───┘ └───┘ └───┘
```

---

## 🔧 Código Aplicado

### Mudança Principal:

**Antes:**
```liquid
<label class="color-swatch__item lazyload" ... style="background-color: {{ cor }}">
```

**Depois:**
```liquid
<label class="color-swatch__item" ... style="background-color: {{ cor }} !important; background-image: none !important;">
```

**Diferenças:**
1. ✅ Removido `lazyload` (só para imagens)
2. ✅ Adicionado `!important` (força aplicação)
3. ✅ Adicionado `background-image: none` (remove imagens de fundo)

---

## 📞 Ainda Não Funciona?

Se após seguir TODOS os passos ainda não funcionar:

1. **Tire screenshot do debug inline**
2. **Tire screenshot do console (F12)**
3. **Tire screenshot do elemento inspecionado**
4. **Verifique:**
   - Tema está salvo?
   - Cache limpo?
   - Produto correto?
   - Metacampo preenchido?

---

## 💡 Dica Final

**Teste com cor vibrante primeiro:**
```
Preto:#FF0000
```

Se aparecer vermelho, você sabe que está funcionando!
Depois mude para a cor correta:
```
Preto:#000000
```

---

**Boa sorte! As cores devem aparecer agora! 🎨**
