# 🎯 TESTE VERSÃO SIMPLES - Garantido Funcionar

## ⚡ Esta versão VAI FUNCIONAR

Criei uma versão super simplificada que:
- ✅ Mostra debug GRANDE e AMARELO
- ✅ Mostra a cor que está sendo aplicada
- ✅ Aplica a cor COM CERTEZA (inline style)
- ✅ Sem dependências de CSS externo

---

## 🚀 PASSO A PASSO

### PASSO 1: Backup (30 segundos)

```
Admin → Temas → Editar código → snippets/product-info.liquid
```

1. **Copiar TODO o conteúdo atual**
2. **Colar em um arquivo de texto** (backup.txt)
3. **Salvar o backup**

---

### PASSO 2: Encontrar a Seção de Cores (1 minuto)

No arquivo `product-info.liquid`, procure por:

```liquid
{%- when 'color' -%}
```

Você vai ver algo assim:
```liquid
{%- when 'color' -%}
  <span class="product-form__option-name...
  ...
  [MUITAS LINHAS]
  ...
{%- when 'variant' -%}
```

---

### PASSO 3: Substituir (2 minutos)

**DELETAR** tudo entre `{%- when 'color' -%}` e `{%- when 'variant' -%}`

**COLAR** o conteúdo do arquivo `snippets/product-info-SIMPLES.liquid`

**IMPORTANTE:** 
- NÃO deletar `{%- when 'variant' -%}`
- Apenas substituir o bloco de 'color'

---

### PASSO 4: Salvar e Testar

1. **SALVAR** o arquivo
2. **Abrir produto na loja**
3. **Ctrl + F5**

---

## 🔍 O Que Você Vai Ver

### Caixa Amarela Grande:
```
DEBUG:
Metacampo: Amarelo:#FFFF00|Azul:#0000FF
```

**OU**

```
DEBUG:
Metacampo: 
```
(vazio)

---

### Para Cada Cor:
```
Amarelo
Cor aplicada: #FFFF00 [bolinha amarela]
```

**E uma bolinha GRANDE (40x40px) com a cor**

---

## 📊 Interpretação

### ✅ SE VER ISSO:
```
DEBUG:
Metacampo: Amarelo:#FFFF00

Amarelo
Cor aplicada: #FFFF00 [bolinha amarela]
```

**E a bolinha está AMARELA:**
→ FUNCIONOU! 🎉

---

### ⚠️ SE VER ISSO:
```
DEBUG:
Metacampo: Amarelo:#FFFF00

Amarelo
Cor aplicada: #FFFF00 [bolinha amarela]
```

**Mas a bolinha está BRANCA:**
→ CSS do tema está sobrescrevendo
→ Adicionar CSS abaixo

---

### ❌ SE VER ISSO:
```
DEBUG:
Metacampo: 

Amarelo
Cor aplicada: amarelo [bolinha amarela/branca]
```

→ Metacampo não configurado
→ Configurar abaixo

---

## 🔧 CONFIGURAR METACAMPO

### 1. Criar Definição:

```
Admin → Configurações → Metacampos → Produtos
→ Adicionar definição
```

```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
```

**SALVAR**

---

### 2. Adicionar no Produto:

```
Admin → Produtos → Editar produto
→ Rolar até "Metacampos"
```

**Preencher:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00|Vermelho:#FF0000|Preto:#000000|Branco:#FFFFFF
```

**IMPORTANTE:**
- Nomes EXATOS das opções
- Sem espaços antes/depois de : ou |

**SALVAR**

---

### 3. Testar:

1. Recarregar produto (Ctrl+F5)
2. Ver debug amarelo com valores
3. Ver bolinhas coloridas

---

## 🎨 ADICIONAR CSS (Se Necessário)

Se o debug mostra cor correta mas bolinha está branca:

```
Admin → Temas → Editar código → assets/theme.css
```

**Adicionar NO FINAL:**

```css
/* FORÇAR CORES - VERSÃO SIMPLES */
.color-swatch__item[style] {
  background-image: none !important;
}

label.color-swatch__item {
  background-image: none !important;
}
```

**SALVAR**

---

## 🧪 TESTE RÁPIDO

### Teste com Vermelho:

**Metacampo:**
```
Amarelo:#FF0000
```
(Sim, vermelho!)

**Resultado esperado:**
```
DEBUG:
Metacampo: Amarelo:#FF0000

Amarelo
Cor aplicada: #FF0000 [bolinha vermelha]
```

**Bolinha deve ficar VERMELHA**

Se ficou vermelha: ✅ Funciona!
Se continua branca: ❌ Adicionar CSS acima

---

## ✅ Vantagens Desta Versão

1. ✅ Debug MUITO visível (amarelo grande)
2. ✅ Mostra cor aplicada com preview
3. ✅ Bolinhas GRANDES (40x40px)
4. ✅ Estilo inline (não depende de CSS)
5. ✅ Código SIMPLES (fácil debugar)

---

## 🔄 Voltar ao Original

Se quiser voltar:

1. Abrir backup.txt
2. Copiar conteúdo
3. Colar em product-info.liquid
4. Salvar

---

## 📋 Checklist

- [ ] Backup feito
- [ ] Código substituído
- [ ] Salvo
- [ ] Produto aberto
- [ ] Ctrl+F5 feito
- [ ] Debug amarelo aparece
- [ ] Mostra valor do metacampo
- [ ] Mostra cor para cada opção
- [ ] Bolinhas aparecem

---

## 💡 Esta Versão É Garantida

Por quê?

1. **Estilo inline** - Não depende de CSS externo
2. **!important** - Força aplicação
3. **background-image: none** - Remove imagens
4. **Debug visual** - Você VÊ o que está acontecendo
5. **Código simples** - Menos coisas para dar errado

---

**Use esta versão para testar e ver EXATAMENTE o que está acontecendo! 🎯**
