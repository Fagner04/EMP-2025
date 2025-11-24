# 🔧 Solução: Metacampos de Cor Não Aparecem

## 🔍 Diagnóstico do Problema

### Passo 1: Adicionar Debug no Tema

1. **Abrir o arquivo do produto:**
   ```
   Admin Shopify → Loja Online → Temas
   → Ações → Editar código
   → sections/product-template.liquid
   ```

2. **Adicionar snippet de debug** (logo após a linha que contém `{% render 'product-info' %}`):
   ```liquid
   {% render 'product-info' %}
   {% render 'debug-color-metafields' %}
   ```

3. **Salvar e visualizar produto na loja**

4. **Verificar o que aparece no debug:**
   - Se metacampos aparecem vazios → Problema de configuração
   - Se metacampos aparecem com valores → Problema no código
   - Se debug não aparece → Problema no snippet

---

## ✅ Solução 1: Configurar Metacampos Corretamente

### A. Criar Definição de Metacampo (IMPORTANTE!)

#### Para Mapeamento de Produto:

1. **Acessar:**
   ```
   Admin Shopify → Configurações → Metacampos
   ```

2. **Selecionar:**
   ```
   Produtos (na lista à esquerda)
   ```

3. **Adicionar definição:**
   ```
   Clique em "Adicionar definição"
   ```

4. **Configurar:**
   ```
   Nome: Mapeamento de Cores
   Namespace e key: custom.color_mapping
   Descrição: Formato: NomeCor:#HEX|OutraCor:#HEX
   Tipo: Texto de linha única
   ```

5. **Salvar**

#### Para Cor de Variante:

1. **Acessar:**
   ```
   Admin Shopify → Configurações → Metacampos
   ```

2. **Selecionar:**
   ```
   Variantes de produto (na lista à esquerda)
   ```

3. **Adicionar definição:**
   ```
   Clique em "Adicionar definição"
   ```

4. **Configurar:**
   ```
   Nome: Cor
   Namespace e key: custom.color
   Descrição: Código de cor hexadecimal (ex: #FF0000)
   Tipo: Texto de linha única
   ```

5. **Salvar**

### B. Adicionar Valores aos Metacampos

#### Para Produto (Mapeamento):

1. **Editar produto:**
   ```
   Admin → Produtos → Selecionar produto
   ```

2. **Rolar até seção "Metacampos"** (no final da página)

3. **Preencher "Mapeamento de Cores":**
   ```
   Vermelho:#DC143C|Azul:#0000FF|Verde:#00FF00
   ```
   
   **IMPORTANTE:** 
   - Os nomes devem corresponder EXATAMENTE às opções do produto
   - Sem espaços antes/depois de : ou |
   - Use códigos hexadecimais válidos

4. **Salvar**

#### Para Variante (Cor Individual):

1. **Editar produto:**
   ```
   Admin → Produtos → Selecionar produto
   ```

2. **Clicar em uma variante** (ex: "Vermelho")

3. **Rolar até "Metacampos"**

4. **Preencher "Cor":**
   ```
   #DC143C
   ```

5. **Salvar**

6. **Repetir para cada variante**

---

## ✅ Solução 2: Verificar Namespace Correto

O código busca metacampos em dois namespaces. Verifique qual você está usando:

### Opção A: Namespace `custom`
```liquid
product.metafields.custom.color_mapping
variant.metafields.custom.color
```

### Opção B: Namespace `color`
```liquid
variant.metafields.color.value
```

**Se você criou com namespace diferente**, atualize o código:

<function_calls>
<invoke name="readFile">
<parameter name="path">snippets/product-info.liquid


---

## ✅ Solução 3: Verificar Tipo de Metacampo

O Shopify tem diferentes tipos de metacampos. Certifique-se de usar o tipo correto:

### Tipo Correto: "Texto de linha única" (Single line text)

**NÃO use:**
- ❌ Cor (Color picker) - Retorna objeto, não string
- ❌ Texto multilinha
- ❌ JSON

**Use:**
- ✅ Texto de linha única (Single line text)

### Se você criou com tipo "Cor":

O código foi atualizado para suportar `.value`. Teste novamente.

---

## ✅ Solução 4: Exemplos Práticos

### Exemplo 1: Produto com 3 Cores

**Produto:** Camiseta Básica
**Opções:** Cor (Vermelho, Azul, Verde)

#### Configuração no Admin:

1. **Editar produto**
2. **Metacampos → Mapeamento de Cores:**
   ```
   Vermelho:#DC143C|Azul:#0000FF|Verde:#00FF00
   ```
3. **Salvar**
4. **Visualizar na loja**

**Resultado esperado:** Amostras com cores exatas

### Exemplo 2: Variante com Cor Individual

**Produto:** Tênis Esportivo
**Variantes:** Preto, Branco, Vermelho

#### Configuração no Admin:

1. **Editar produto**
2. **Clicar na variante "Preto"**
3. **Metacampos → Cor:**
   ```
   #000000
   ```
4. **Salvar**
5. **Repetir para outras variantes:**
   - Branco: `#FFFFFF`
   - Vermelho: `#DC143C`
6. **Visualizar na loja**

**Resultado esperado:** Cada amostra com sua cor

---

## 🔧 Solução 5: Código Atualizado

O código foi atualizado para suportar múltiplos namespaces e formatos:

### Agora suporta:
- ✅ `product.metafields.custom.color_mapping`
- ✅ `product.metafields.custom.color_mapping.value`
- ✅ `product.metafields.color.mapping`
- ✅ `variant.metafields.custom.color`
- ✅ `variant.metafields.custom.color.value`
- ✅ `variant.metafields.color.value`
- ✅ `variant.metafields.color.color`

### Também adiciona:
- ✅ `.strip` para remover espaços extras
- ✅ Suporte a diferentes formatos de metacampo

---

## 📋 Checklist de Verificação

Use este checklist para garantir que tudo está configurado:

### Configuração de Metacampos:
- [ ] Metacampo criado em Configurações → Metacampos
- [ ] Namespace correto: `custom`
- [ ] Key correta: `color_mapping` (produto) ou `color` (variante)
- [ ] Tipo: "Texto de linha única"
- [ ] Definição salva

### Valores nos Produtos:
- [ ] Produto editado
- [ ] Metacampo preenchido
- [ ] Formato correto: `Nome:#HEX|Nome:#HEX`
- [ ] Nomes correspondem às opções
- [ ] Sem espaços extras
- [ ] Produto salvo

### Código do Tema:
- [ ] Arquivos atualizados:
  - [ ] snippets/product-info.liquid
  - [ ] snippets/product-item.liquid
- [ ] Código salvo no admin
- [ ] Cache limpo (Ctrl+F5)

### Teste:
- [ ] Debug snippet adicionado
- [ ] Produto visualizado na loja
- [ ] Debug mostra valores dos metacampos
- [ ] Cores aparecem nas amostras

---

## 🐛 Problemas Comuns e Soluções

### Problema 1: "Metacampo não aparece no produto"

**Causa:** Definição não criada

**Solução:**
1. Ir em Configurações → Metacampos
2. Criar definição primeiro
3. Depois adicionar valores nos produtos

### Problema 2: "Valores não salvam"

**Causa:** Tipo de metacampo incorreto

**Solução:**
1. Deletar definição antiga
2. Criar nova com tipo "Texto de linha única"
3. Adicionar valores novamente

### Problema 3: "Cores não aparecem mesmo com metacampo"

**Causa:** Nomes não correspondem

**Solução:**
```
Opção do produto: "Vermelho"
Mapeamento: "Vermelho:#DC143C"  ✅ Correto
Mapeamento: "vermelho:#DC143C"  ❌ Errado (minúscula)
Mapeamento: " Vermelho:#DC143C" ❌ Errado (espaço extra)
```

### Problema 4: "Debug não aparece"

**Causa:** Snippet não adicionado corretamente

**Solução:**
1. Verificar se arquivo `debug-color-metafields.liquid` existe em snippets
2. Verificar se `{% render 'debug-color-metafields' %}` foi adicionado
3. Salvar e fazer hard refresh (Ctrl+F5)

### Problema 5: "Funciona em alguns produtos, não em outros"

**Causa:** Metacampos não configurados em todos

**Solução:**
1. Verificar cada produto individualmente
2. Copiar/colar mapeamento entre produtos similares
3. Usar debug para identificar qual está faltando

---

## 🎯 Teste Rápido (5 Minutos)

### Teste Mínimo para Validar:

1. **Criar metacampo:**
   ```
   Configurações → Metacampos → Produtos
   Nome: Teste Cor
   Namespace: custom
   Key: color_mapping
   Tipo: Texto de linha única
   ```

2. **Adicionar em produto:**
   ```
   Editar produto qualquer
   Metacampos → Teste Cor:
   red:#FF0000|blue:#0000FF
   ```

3. **Adicionar debug:**
   ```
   sections/product-template.liquid
   Adicionar: {% render 'debug-color-metafields' %}
   ```

4. **Visualizar:**
   ```
   Abrir produto na loja
   Ver debug mostrando valores
   ```

**Se debug mostra valores:** ✅ Metacampos funcionando!
**Se debug mostra vazio:** ❌ Problema na configuração

---

## 📞 Ainda Não Funciona?

Se após seguir todos os passos ainda não funcionar:

1. **Tire screenshots:**
   - Configuração do metacampo
   - Valores no produto
   - Debug na loja
   - Console do navegador (F12)

2. **Verifique:**
   - Versão do Shopify
   - Plano da loja (alguns metacampos requerem plano específico)
   - Permissões de usuário

3. **Teste básico:**
   - Criar produto novo do zero
   - Configurar apenas 1 cor
   - Ver se funciona

4. **Contato:**
   - Suporte Shopify
   - Desenvolvedor do tema
   - Comunidade Shopify

---

## ✅ Resumo da Solução

1. ✅ **Criar definição de metacampo** (Configurações → Metacampos)
2. ✅ **Usar tipo "Texto de linha única"**
3. ✅ **Namespace: `custom`, Key: `color_mapping` ou `color`**
4. ✅ **Adicionar valores nos produtos** (formato correto)
5. ✅ **Atualizar código do tema** (já feito)
6. ✅ **Adicionar debug** (temporário)
7. ✅ **Testar e validar**
8. ✅ **Remover debug** (após confirmar funcionamento)

---

**Última atualização:** Código atualizado com suporte a múltiplos namespaces e formatos!
