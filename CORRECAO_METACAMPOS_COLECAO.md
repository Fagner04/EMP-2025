# ✅ CORREÇÃO: Metacampos de Coleção Funcionando

## 🎯 O Que Foi Corrigido

O código foi atualizado para suportar **corretamente** os metacampos de coleção/categoria. Agora funciona em **TODAS as categorias**.

### Ordem de Prioridade (do maior para o menor):

1. **Metacampo da Variante** → `variant.metafields.custom.color`
2. **Metacampo do Produto** → `product.metafields.custom.color_mapping`
3. **Metacampo da Coleção** → `collection.metafields.custom.color_mapping` ⭐ **CORRIGIDO**
4. **Cor Automática** → Nome da cor em CSS

---

## 📝 Como Configurar Metacampo de Coleção

### PASSO 1: Criar Definição de Metacampo

```
Admin Shopify → Configurações → Metacampos → Coleções
```

**Clicar:** "Adicionar definição"

**Preencher:**
```
Nome: Mapeamento de Cores
Namespace: custom
Key: color_mapping
Tipo: Texto de linha única
Descrição: Cores padrão para produtos desta categoria (formato: Cor:#HEX|Cor:#HEX)
```

**SALVAR**

---

### PASSO 2: Configurar Cores na Coleção

```
Admin → Produtos → Coleções → Selecionar sua coleção
```

**Rolar até:** "Metacampos" (no final da página)

**Preencher "Mapeamento de Cores":**

#### Exemplo 1: Cores Básicas
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00|Vermelho:#FF0000|Preto:#000000|Branco:#FFFFFF
```

#### Exemplo 2: Tons Específicos
```
Amarelo Claro:#FFFFE0|Amarelo:#FFFF00|Amarelo Ouro:#FFD700|Amarelo Mostarda:#FFDB58
```

#### Exemplo 3: Paleta Completa
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00|Amarelo:#FFFF00|Rosa:#FFC0CB|Roxo:#800080|Laranja:#FFA500|Marrom:#A52A2A|Bege:#F5F5DC
```

**IMPORTANTE:**
- Os nomes devem corresponder **EXATAMENTE** às opções de cor do produto
- Sem espaços antes/depois de `:` ou `|`
- Use códigos hexadecimais válidos (começando com `#`)

**SALVAR**

---

### PASSO 3: Testar

1. Abrir qualquer produto da coleção
2. Fazer **Ctrl + F5** (hard refresh)
3. Ver as cores aplicadas automaticamente

---

## 🎨 Exemplos por Tipo de Loja

### Loja de Moda - Coleção "Verão 2024"
```
Amarelo:#FFFF00|Laranja:#FFA500|Rosa:#FFC0CB|Azul Claro:#ADD8E6|Verde Limão:#32CD32|Coral:#FF7F50|Turquesa:#40E0D0
```

### Loja de Moda - Coleção "Inverno 2024"
```
Preto:#000000|Cinza:#808080|Marrom:#A52A2A|Azul Marinho:#000080|Verde Escuro:#006400|Vinho:#722F37|Cinza Escuro:#696969
```

### Loja de Eletrônicos - Coleção "Smartphones"
```
Preto:#000000|Branco:#FFFFFF|Azul:#0000FF|Vermelho:#FF0000|Dourado:#FFD700|Prata:#C0C0C0|Rosa:#FFC0CB
```

### Loja de Casa - Coleção "Minimalista"
```
Preto:#000000|Branco:#FFFFFF|Cinza Claro:#D3D3D3|Bege:#F5F5DC|Cinza:#808080
```

---

## 🔄 Como Funciona a Prioridade

### Cenário 1: Apenas Coleção Configurada
```
Coleção "Roupas" → Amarelo:#FFFF00
Produto → (sem metacampo)
Variante → (sem metacampo)

RESULTADO: Usa #FFFF00 da coleção ✅
```

### Cenário 2: Coleção + Produto Configurados
```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Premium" → Amarelo:#FFD700
Variante → (sem metacampo)

RESULTADO: Usa #FFD700 do produto (prioridade maior) ✅
```

### Cenário 3: Todos Configurados
```
Coleção "Roupas" → Amarelo:#FFFF00
Produto "Camiseta Premium" → Amarelo:#FFD700
Variante "Edição Limitada" → #FFA500

RESULTADO: Usa #FFA500 da variante (maior prioridade) ✅
```

---

## ✅ Vantagens de Usar Metacampo de Coleção

### 1. Configurar Uma Vez, Aplicar em Todos
- Configure cores na coleção
- Todos os produtos herdam automaticamente
- Menos trabalho manual

### 2. Consistência Automática
- Mesma paleta de cores em toda a categoria
- Fácil de manter
- Mudanças centralizadas

### 3. Flexibilidade
- Produtos específicos podem sobrescrever
- Variantes especiais podem ter cores únicas
- Controle total quando necessário

### 4. Organização
- Cores por categoria/coleção
- Fácil de entender
- Documentação natural

---

## 🔧 Solução de Problemas

### Problema: "Cores não aparecem na coleção"

**Verificar:**

1. **Metacampo criado?**
   ```
   Configurações → Metacampos → Coleções
   Deve existir: custom.color_mapping
   ```

2. **Valores configurados na coleção?**
   ```
   Produtos → Coleções → Sua coleção
   Rolar até "Metacampos"
   Deve ter valores no formato: Cor:#HEX|Cor:#HEX
   ```

3. **Produto pertence à coleção?**
   ```
   Editar produto → Organização → Coleções
   Verificar se está na coleção correta
   ```

4. **Nomes correspondem?**
   ```
   Opção do produto: "Amarelo"
   Metacampo da coleção: "Amarelo:#FFFF00" ✅
   Metacampo da coleção: "amarelo:#FFFF00" ❌ (minúscula)
   ```

5. **Cache limpo?**
   ```
   Ctrl + F5 no navegador
   ```

---

### Problema: "Funciona em algumas coleções, não em outras"

**Causa:** Metacampo não configurado em todas as coleções

**Solução:**
1. Ir em cada coleção
2. Verificar se metacampo está preenchido
3. Copiar/colar valores entre coleções similares

---

### Problema: "Produto não usa cores da coleção"

**Possíveis causas:**

1. **Produto tem próprio metacampo** (prioridade maior)
   - Verificar: Editar produto → Metacampos
   - Se tiver `color_mapping`, ele sobrescreve a coleção

2. **Produto não está na coleção**
   - Verificar: Editar produto → Organização → Coleções
   - Adicionar à coleção correta

3. **Nomes não correspondem**
   - Opção: "Amarelo Claro"
   - Metacampo: "Amarelo:#FFFF00" ❌
   - Deve ser: "Amarelo Claro:#FFFFE0" ✅

---

## 🧪 Teste Rápido (3 Minutos)

### Teste Completo:

1. **Criar metacampo:**
   ```
   Configurações → Metacampos → Coleções
   Nome: Mapeamento de Cores
   Namespace: custom
   Key: color_mapping
   Tipo: Texto de linha única
   SALVAR
   ```

2. **Configurar em uma coleção:**
   ```
   Produtos → Coleções → Selecionar qualquer coleção
   Metacampos → Mapeamento de Cores:
   Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00
   SALVAR
   ```

3. **Testar:**
   ```
   Abrir produto da coleção
   Ctrl + F5
   Ver cores aplicadas
   ```

**Se funcionar:** ✅ Configuração correta!
**Se não funcionar:** Verificar checklist acima

---

## 📊 Tabela de Cores Prontas

### Copie e cole no metacampo da coleção:

#### Paleta Básica (10 cores):
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00|Amarelo:#FFFF00|Rosa:#FFC0CB|Roxo:#800080|Laranja:#FFA500
```

#### Paleta Completa (20 cores):
```
Preto:#000000|Branco:#FFFFFF|Cinza:#808080|Cinza Claro:#D3D3D3|Cinza Escuro:#696969|Vermelho:#FF0000|Azul:#0000FF|Verde:#00FF00|Amarelo:#FFFF00|Rosa:#FFC0CB|Roxo:#800080|Laranja:#FFA500|Marrom:#A52A2A|Bege:#F5F5DC|Azul Marinho:#000080|Verde Escuro:#006400|Vermelho Escuro:#8B0000|Azul Claro:#ADD8E6|Verde Claro:#90EE90|Amarelo Claro:#FFFFE0
```

#### Tons de Pele:
```
Bege:#F5F5DC|Creme:#FFFDD0|Pêssego:#FFDAB9|Bronze:#CD7F32|Caramelo:#AF6E4D|Chocolate:#D2691E
```

#### Tons Pastel:
```
Rosa Pastel:#FFD1DC|Azul Pastel:#AEC6CF|Verde Pastel:#B2E0D4|Amarelo Pastel:#FDFD96|Roxo Pastel:#E0B0FF|Laranja Pastel:#FFB347
```

---

## 💡 Dicas Importantes

1. **Use nomes consistentes**
   - Sempre use a mesma capitalização
   - "Amarelo" ≠ "amarelo" ≠ "AMARELO"

2. **Teste com cores vibrantes primeiro**
   - Use #FF0000 (vermelho) para testar
   - Mais fácil de ver se funciona
   - Depois mude para cor correta

3. **Documente suas cores**
   - Mantenha lista das cores usadas
   - Facilita manutenção futura
   - Copie entre coleções similares

4. **Organize por categoria**
   - Coleções de verão → Cores claras
   - Coleções de inverno → Cores escuras
   - Facilita gestão

5. **Priorize coleções para padrões**
   - Use coleção para 80% dos produtos
   - Use produto para 15% (exceções)
   - Use variante para 5% (casos especiais)

---

## ✅ Checklist Final

### Configuração:
- [ ] Metacampo criado em Coleções
- [ ] Namespace: `custom`
- [ ] Key: `color_mapping`
- [ ] Tipo: "Texto de linha única"

### Valores:
- [ ] Cores configuradas na coleção
- [ ] Formato correto: `Cor:#HEX|Cor:#HEX`
- [ ] Nomes correspondem às opções
- [ ] Sem espaços extras

### Teste:
- [ ] Produto pertence à coleção
- [ ] Ctrl + F5 feito
- [ ] Cores aparecem corretamente
- [ ] Funciona em todos produtos da coleção

---

## 🎯 Resultado Esperado

### Antes (sem metacampo de coleção):
- Configurar cores em cada produto manualmente
- Muito trabalho
- Inconsistências

### Depois (com metacampo de coleção):
- Configurar uma vez na coleção
- Todos produtos herdam automaticamente
- Consistência garantida
- Fácil manutenção

---

## 📞 Suporte

Se após seguir todos os passos ainda não funcionar:

1. Verificar se código foi atualizado (arquivo `product-info.liquid`)
2. Limpar cache do navegador (Ctrl + Shift + Delete)
3. Testar em navegador anônimo
4. Verificar console do navegador (F12) para erros

---

**Atualizado:** Código corrigido para suportar metacampos de coleção em TODAS as categorias! 🎉
