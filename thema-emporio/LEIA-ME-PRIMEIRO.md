# 📖 LEIA-ME PRIMEIRO

## 🎯 Problema: Metacampos de Cor Não Aparecem

### ✅ Solução Rápida (15 minutos)

---

## 1️⃣ Atualizar Código do Tema

### Arquivos que DEVEM ser atualizados:

```
✓ snippets/product-info.liquid
✓ snippets/product-item.liquid
✓ snippets/debug-color-metafields.liquid (NOVO)
```

**Como:**
1. Admin Shopify → Temas → Editar código
2. Copiar conteúdo dos arquivos locais
3. Colar no admin
4. Salvar cada um

---

## 2️⃣ Criar Metacampo no Shopify

### Passo a Passo:

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

**IMPORTANTE:** Criar a definição ANTES de adicionar valores!

---

## 3️⃣ Adicionar Debug (Temporário)

### Em: sections/product-template.liquid

**Procurar:**
```liquid
{% render 'product-info' %}
```

**Adicionar abaixo:**
```liquid
{% render 'debug-color-metafields' %}
```

**Salvar**

---

## 4️⃣ Configurar Produto

### Editar qualquer produto:

**Rolar até "Metacampos"**

**Preencher "Mapeamento de Cores":**
```
Vermelho:#DC143C|Azul:#0000FF|Verde:#00FF00
```

**Regras:**
- Nomes EXATAMENTE iguais às opções
- Sem espaços extras
- Formato: Nome:#HEX|Nome:#HEX

**Salvar**

---

## 5️⃣ Testar

### Abrir produto na loja

**Verificar:**
1. ✅ Debug aparece?
2. ✅ Debug mostra valores?
3. ✅ Cores aparecem nas amostras?

---

## 🔍 Interpretação do Debug

### ✅ Se mostra valores:
```
Metacampo: ✓ Existe
Valor: Vermelho:#DC143C|...
→ FUNCIONANDO! Cores devem aparecer
```

### ❌ Se mostra vazio:
```
Metacampo: ✗ Vazio
→ Voltar ao passo 2
→ Criar definição primeiro
→ Depois adicionar valores
```

---

## 📚 Documentação Completa

### Guias Disponíveis:

1. **PROXIMOS_PASSOS.md** ← Comece aqui
2. **GUIA_VISUAL_METACAMPOS.md** - Com "imagens"
3. **SOLUCAO_METACAMPOS_NAO_APARECEM.md** - Troubleshooting
4. **EXEMPLOS_PRATICOS.md** - Casos de uso
5. **GUIA_RAPIDO.md** - Referência rápida

---

## 🆘 Problemas Comuns

### "Metacampo não aparece no produto"
→ Criar definição PRIMEIRO (passo 2)

### "Debug não aparece"
→ Verificar passo 3
→ Fazer Ctrl+F5 (hard refresh)

### "Cores não aparecem"
→ Verificar nomes exatos
→ Ver debug para comparar

---

## ✅ Checklist Mínimo

- [ ] Código atualizado (passo 1)
- [ ] Metacampo criado (passo 2)
- [ ] Debug adicionado (passo 3)
- [ ] Produto configurado (passo 4)
- [ ] Testado (passo 5)

---

## 🎯 Resultado Esperado

### Antes:
```
Amostras com cores genéricas
```

### Depois:
```
Amostras com cores EXATAS da sua marca!
```

---

## 💡 Exemplo Completo

### Produto: Camiseta Básica
### Opções: Cor (Vermelho, Azul, Verde)

**Metacampo:**
```
Vermelho:#DC143C|Azul:#0000FF|Verde:#00FF00
```

**Resultado:**
- Amostra vermelha: #DC143C
- Amostra azul: #0000FF
- Amostra verde: #00FF00

---

## ⏱️ Tempo Estimado

- Atualizar código: 5 min
- Criar metacampo: 3 min
- Adicionar debug: 2 min
- Configurar produto: 2 min
- Testar: 3 min

**Total: ~15 minutos**

---

## 🚀 Começar Agora

**Abra:** PROXIMOS_PASSOS.md

**Siga os passos 1 a 5**

**Pronto!**

---

## 📞 Ainda com Dúvidas?

1. Leia SOLUCAO_METACAMPOS_NAO_APARECEM.md
2. Veja GUIA_VISUAL_METACAMPOS.md
3. Consulte EXEMPLOS_PRATICOS.md

---

**Boa sorte! 🎉**
