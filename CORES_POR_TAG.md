# 🏷️ Configurar Cores via Tags do Produto

## 🎯 Nova Funcionalidade

Agora você pode configurar cores diretamente nas **tags do produto**, sem precisar criar metacampos!

## ✅ Vantagens

- ✅ **Mais rápido** - Não precisa criar metacampos
- ✅ **Mais simples** - Apenas adicionar tags
- ✅ **Flexível** - Funciona junto com metacampos
- ✅ **Fácil de copiar** - Copie tags entre produtos

---

## 📝 Como Usar

### Formato da Tag:
```
color:NomeDaCor:#CodigoHex
```

### Exemplos:

#### Tag para Amarelo:
```
color:Amarelo:#FFFF00
```

#### Tag para Azul:
```
color:Azul:#0000FF
```

#### Tag para Verde:
```
color:Verde:#00FF00
```

---

## 🛠️ PASSO A PASSO

### PASSO 1: Editar Produto

```
Admin Shopify → Produtos → Editar produto
```

### PASSO 2: Adicionar Tags

Na seção **"Tags"**, adicione as tags de cor:

**Exemplo para produto com 3 cores:**
```
color:Amarelo:#FFFF00
color:Azul:#0000FF
color:Verde:#00FF00
```

**IMPORTANTE:**
- Formato exato: `color:NomeCor:#HEX`
- Nome da cor deve corresponder à opção do produto
- Sem espaços extras
- Use `#` antes do código hexadecimal

### PASSO 3: Salvar

Clicar em **SALVAR**

### PASSO 4: Testar

1. Abrir produto na loja
2. Fazer **Ctrl + F5**
3. Ver cores aplicadas

---

## 🎨 Exemplos Práticos

### Exemplo 1: Produto com Cores Básicas

**Produto:** Camiseta Básica
**Opções de Cor:** Amarelo, Azul, Verde

**Tags:**
```
color:Amarelo:#FFFF00
color:Azul:#0000FF
color:Verde:#00FF00
```

---

### Exemplo 2: Produto com Cores Compostas

**Produto:** Camiseta Premium
**Opções de Cor:** Azul claro, Azul escuro, Verde limão

**Tags:**
```
color:Azul claro:#ADD8E6
color:Azul escuro:#00008B
color:Verde limão:#32CD32
```

**ATENÇÃO:** Nome com espaço funciona normalmente!

---

### Exemplo 3: Produto com Muitas Cores

**Produto:** Camiseta Colorida
**Opções:** 10 cores diferentes

**Tags:**
```
color:Preto:#000000
color:Branco:#FFFFFF
color:Cinza:#808080
color:Vermelho:#FF0000
color:Azul:#0000FF
color:Verde:#00FF00
color:Amarelo:#FFFF00
color:Rosa:#FFC0CB
color:Roxo:#800080
color:Laranja:#FFA500
```

---

## 🔄 Ordem de Prioridade Completa

Com tags, a ordem de prioridade fica:

```
1. Imagem da Variante
   ↓
2. PNG em Assets (ex: amarelo.png)
   ↓
3. Metacampo da Variante
   ↓
4. Metacampo do Produto
   ↓
5. Tag do Produto (color:Nome:#HEX) ⭐ NOVO
   ↓
6. Metacampo da Coleção
   ↓
7. Cor Automática (nome CSS)
```

---

## 💡 Quando Usar Cada Método

### Use TAGS quando:
- ✅ Quer configurar rápido
- ✅ Produto tem cores únicas
- ✅ Não quer criar metacampos
- ✅ Quer copiar facilmente entre produtos

### Use METACAMPO DO PRODUTO quando:
- ✅ Quer organização melhor
- ✅ Tem muitas cores
- ✅ Quer interface mais limpa

### Use METACAMPO DA COLEÇÃO quando:
- ✅ Quer aplicar em vários produtos
- ✅ Cores padrão por categoria
- ✅ Menos trabalho manual

---

## 🎯 Casos de Uso

### Caso 1: Produto Especial com Cores Únicas

**Cenário:** Produto tem cores que não seguem padrão da coleção

**Solução:** Usar tags

**Exemplo:**
```
Produto: Camiseta Tie-Dye
Tags:
color:Arco-íris:#FF0000
color:Psicodélico:#FF00FF
color:Neon:#39FF14
```

---

### Caso 2: Testar Cores Rapidamente

**Cenário:** Quer testar cores antes de configurar metacampos

**Solução:** Usar tags temporariamente

**Exemplo:**
```
Adicionar tags:
color:Teste1:#FF0000
color:Teste2:#00FF00

Ver resultado → Ajustar → Converter para metacampo depois
```

---

### Caso 3: Copiar Cores Entre Produtos

**Cenário:** Vários produtos com mesmas cores

**Solução:** Copiar tags

**Exemplo:**
```
Produto A:
color:Amarelo:#FFFF00
color:Azul:#0000FF

Copiar tags → Colar no Produto B
```

---

## 📋 Tabela de Tags Prontas

### Cores Básicas (copie e cole):
```
color:Preto:#000000
color:Branco:#FFFFFF
color:Cinza:#808080
color:Vermelho:#FF0000
color:Azul:#0000FF
color:Verde:#00FF00
color:Amarelo:#FFFF00
color:Rosa:#FFC0CB
color:Roxo:#800080
color:Laranja:#FFA500
```

### Tons de Azul:
```
color:Azul claro:#ADD8E6
color:Azul escuro:#00008B
color:Azul marinho:#000080
color:Azul royal:#4169E1
color:Azul bebê:#E0FFFF
```

### Tons de Verde:
```
color:Verde claro:#90EE90
color:Verde escuro:#006400
color:Verde limão:#32CD32
color:Verde água:#00FFFF
color:Verde oliva:#808000
```

### Tons de Vermelho:
```
color:Vermelho:#FF0000
color:Vermelho escuro:#8B0000
color:Vermelho vinho:#722F37
color:Rosa:#FFC0CB
color:Rosa claro:#FFB6C1
```

### Tons Neutros:
```
color:Bege:#F5F5DC
color:Creme:#FFFDD0
color:Marrom:#A52A2A
color:Cinza claro:#D3D3D3
color:Cinza escuro:#696969
```

---

## 🔧 Solução de Problemas

### Problema: "Tag não funciona"

**Verificar:**

1. **Formato correto?**
   ```
   ✅ color:Amarelo:#FFFF00
   ❌ cor:Amarelo:#FFFF00 (palavra errada)
   ❌ color:Amarelo:FFFF00 (falta #)
   ❌ color: Amarelo:#FFFF00 (espaço após :)
   ```

2. **Nome corresponde?**
   ```
   Opção do produto: "Amarelo"
   Tag: color:Amarelo:#FFFF00 ✅
   Tag: color:amarelo:#FFFF00 ❌ (minúscula)
   ```

3. **Produto salvo?**
   - Salvar após adicionar tags
   - Ctrl + F5 no navegador

---

### Problema: "Cores da coleção sobrescrevem tags"

**EXPLICAÇÃO:** Tags têm prioridade MAIOR que coleção

**Se isso acontecer:**
1. Verificar se produto tem metacampo próprio
2. Metacampo do produto tem prioridade sobre tags

**Solução:**
- Remover metacampo do produto
- Ou usar metacampo ao invés de tags

---

### Problema: "Quero usar tags E metacampo de coleção"

**FUNCIONA!** Tags têm prioridade maior

**Exemplo:**
```
Coleção: Amarelo:#FFFF00|Azul:#0000FF
Produto (tag): color:Amarelo:#FFD700

Resultado: Amarelo usa #FFD700 (tag), Azul usa #0000FF (coleção)
```

---

## ✅ Checklist

### Para Adicionar Cores via Tag:
- [ ] Editar produto
- [ ] Adicionar tags no formato: `color:Nome:#HEX`
- [ ] Nomes correspondem às opções
- [ ] Sem espaços extras
- [ ] Salvar produto
- [ ] Testar (Ctrl + F5)

---

## 🎯 Comparação: Tags vs Metacampos

### Tags:
**Vantagens:**
- ✅ Mais rápido de configurar
- ✅ Não precisa criar definições
- ✅ Fácil de copiar entre produtos
- ✅ Visível na lista de produtos

**Desvantagens:**
- ❌ Pode poluir lista de tags
- ❌ Menos organizado para muitas cores
- ❌ Não tem validação automática

### Metacampos:
**Vantagens:**
- ✅ Mais organizado
- ✅ Interface dedicada
- ✅ Validação de formato
- ✅ Não polui tags

**Desvantagens:**
- ❌ Precisa criar definições
- ❌ Mais passos para configurar
- ❌ Menos visível

---

## 💡 Dicas

1. **Use tags para testes rápidos**
   - Adicione tags
   - Veja resultado
   - Converta para metacampo depois

2. **Combine métodos**
   - Coleção: cores padrão
   - Tags: exceções rápidas
   - Metacampo: produtos importantes

3. **Documente formato**
   - Mantenha lista de tags usadas
   - Facilita copiar entre produtos

4. **Organize tags**
   - Use prefixo `color:` sempre
   - Facilita busca e filtro

5. **Teste sempre**
   - Ctrl + F5 após mudanças
   - Verifique todas as cores

---

## 📊 Resumo

### Formato da Tag:
```
color:NomeDaCor:#CodigoHex
```

### Exemplo Completo:
```
Produto: Camiseta
Opções: Amarelo, Azul, Verde

Tags:
color:Amarelo:#FFFF00
color:Azul:#0000FF
color:Verde:#00FF00

Outras tags normais:
verão
algodão
básica
```

### Prioridade:
```
Metacampo Produto > Tags > Metacampo Coleção
```

---

**Agora você tem 3 formas de configurar cores: Metacampo do Produto, Tags, e Metacampo da Coleção! 🎨**
