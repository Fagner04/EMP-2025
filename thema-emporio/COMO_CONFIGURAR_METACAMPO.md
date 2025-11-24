# 📝 Como Configurar o Metacampo - Passo a Passo

## 🎯 Onde Configurar

Você configura isso no **Admin do Shopify**, não nos arquivos do tema!

---

## 📍 PASSO A PASSO COM IMAGENS

### PASSO 1: Acessar Configurações

```
1. Abrir Admin do Shopify (sua-loja.myshopify.com/admin)
2. No menu lateral esquerdo, rolar até o final
3. Clicar em ⚙️ "Configurações" (Settings)
```

**Localização:**
```
┌─────────────────────────┐
│ 🏠 Início               │
│ 📦 Pedidos              │
│ 🛍️  Produtos            │
│ 👥 Clientes             │
│ 📊 Análises             │
│ 💰 Marketing            │
│ 🎨 Loja Online          │
│ ...                     │
│ ⚙️  Configurações  ← AQUI│
└─────────────────────────┘
```

---

### PASSO 2: Acessar Metacampos

```
1. Na página de Configurações
2. No menu lateral, procurar "Metacampos" (Metafields)
3. Clicar em "Metacampos"
```

**Localização:**
```
Configurações
├── Geral
├── Plano
├── Usuários e permissões
├── Pagamentos
├── Checkout
├── Envio e entrega
├── Impostos
├── Locais
├── Mercados
├── Domínios
├── Metacampos  ← AQUI
├── Notificações
└── ...
```

---

### PASSO 3: Selecionar "Produtos"

```
1. Na página de Metacampos
2. No menu lateral esquerdo, clicar em "Produtos"
```

**Você verá:**
```
┌─────────────────────────────────────┐
│ Metacampos                          │
│                                     │
│ Lista à esquerda:                   │
│ ○ Loja                              │
│ ● Produtos  ← CLICAR AQUI           │
│ ○ Variantes de produto              │
│ ○ Coleções                          │
│ ○ Clientes                          │
│ ○ Pedidos                           │
│ ...                                 │
└─────────────────────────────────────┘
```

---

### PASSO 4: Adicionar Definição

```
1. Na página de Produtos
2. Clicar no botão azul "Adicionar definição"
```

**Você verá:**
```
┌─────────────────────────────────────┐
│ Produtos                            │
│                                     │
│ ┌─────────────────────────────┐    │
│ │ + Adicionar definição       │    │
│ └─────────────────────────────┘    │
│                                     │
│ (Lista de metacampos existentes)   │
└─────────────────────────────────────┘
```

---

### PASSO 5: Preencher Formulário

Um formulário vai abrir. Preencha assim:

```
┌─────────────────────────────────────────────┐
│ Adicionar definição                         │
│                                             │
│ Nome                                        │
│ ┌─────────────────────────────────────┐    │
│ │ Mapeamento de Cores                 │    │
│ └─────────────────────────────────────┘    │
│                                             │
│ Namespace e key                             │
│ ┌──────────┐ . ┌──────────────────┐        │
│ │ custom   │ . │ color_mapping    │        │
│ └──────────┘   └──────────────────┘        │
│                                             │
│ Descrição (opcional)                        │
│ ┌─────────────────────────────────────┐    │
│ │ Formato: Nome:#HEX|Nome:#HEX        │    │
│ └─────────────────────────────────────┘    │
│                                             │
│ Tipo                                        │
│ ┌─────────────────────────────────────┐    │
│ │ Texto de linha única            ▼   │    │
│ └─────────────────────────────────────┘    │
│                                             │
│ [Cancelar]  [Salvar]                        │
└─────────────────────────────────────────────┘
```

**Preencher:**
- **Nome:** `Mapeamento de Cores`
- **Namespace:** `custom`
- **Key:** `color_mapping`
- **Descrição:** `Formato: Nome:#HEX|Nome:#HEX` (opcional)
- **Tipo:** `Texto de linha única` (Single line text)

---

### PASSO 6: Salvar

```
Clicar no botão "Salvar" (azul, canto inferior direito)
```

---

## ✅ Pronto! Metacampo Criado

Agora você pode usar o metacampo nos produtos!

---

## 📦 USAR O METACAMPO NO PRODUTO

### PASSO 1: Editar Produto

```
1. Admin → Produtos
2. Clicar em um produto para editar
```

---

### PASSO 2: Rolar até Metacampos

```
1. Na página de edição do produto
2. Rolar até o FINAL da página
3. Procurar seção "Metacampos"
```

**Localização:**
```
Editar produto
├── Título
├── Descrição
├── Mídia
├── Preço
├── Estoque
├── Envio
├── Variantes
├── Opções
├── ...
├── SEO
└── Metacampos  ← AQUI (no final!)
```

---

### PASSO 3: Preencher Metacampo

```
Você verá o campo "Mapeamento de Cores"
```

**Exemplo:**
```
┌─────────────────────────────────────────────┐
│ Metacampos                                  │
│                                             │
│ Mapeamento de Cores                         │
│ ┌─────────────────────────────────────┐    │
│ │ Amarelo:#FFFF00|Azul:#0000FF        │    │
│ └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

**Preencher:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00|Vermelho:#FF0000|Preto:#000000|Branco:#FFFFFF
```

**IMPORTANTE:**
- Nomes EXATOS das opções do produto
- Sem espaços antes/depois de : ou |
- Códigos hexadecimais com #

---

### PASSO 4: Salvar Produto

```
Clicar em "Salvar" (canto superior direito)
```

---

## 🎨 Exemplo Completo

### Produto: Camiseta Básica
### Opções: Cor (Amarelo, Azul, Verde)

**Metacampo:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00
```

**Resultado:**
- Bolinha amarela para "Amarelo"
- Bolinha azul para "Azul"
- Bolinha verde para "Verde"

---

## 🔍 Como Saber se Funcionou

### Verificar se Metacampo Foi Criado:

```
Admin → Configurações → Metacampos → Produtos
```

Você deve ver:
```
┌─────────────────────────────────────┐
│ Produtos                            │
│                                     │
│ Mapeamento de Cores                 │
│ custom.color_mapping                │
│ Texto de linha única                │
└─────────────────────────────────────┘
```

---

### Verificar se Produto Tem Valores:

```
Admin → Produtos → Editar produto → Rolar até Metacampos
```

Você deve ver o campo preenchido:
```
Mapeamento de Cores
[Amarelo:#FFFF00|Azul:#0000FF|...]
```

---

## 🆘 Problemas Comuns

### "Não vejo a seção Metacampos no produto"

**Causa:** Definição não foi criada

**Solução:**
1. Criar definição PRIMEIRO (Passos 1-6 acima)
2. DEPOIS editar produto
3. Recarregar página do produto se necessário

---

### "Campo aparece mas não salva"

**Causa:** Tipo de metacampo incorreto

**Solução:**
1. Deletar definição antiga
2. Criar nova com tipo "Texto de linha única"
3. Tentar novamente

---

### "Cores não aparecem na loja"

**Causa:** Nomes não correspondem

**Solução:**
```
Opção do produto: "Amarelo"
Metacampo: "Amarelo:#FFFF00"  ✅ Correto

Opção do produto: "Amarelo"
Metacampo: "amarelo:#FFFF00"  ❌ Errado (minúscula)
```

---

## 📋 Checklist

- [ ] Acessei Admin do Shopify
- [ ] Fui em Configurações
- [ ] Cliquei em Metacampos
- [ ] Selecionei "Produtos"
- [ ] Cliquei em "Adicionar definição"
- [ ] Preenchi Nome: "Mapeamento de Cores"
- [ ] Preenchi Namespace: "custom"
- [ ] Preenchi Key: "color_mapping"
- [ ] Selecionei Tipo: "Texto de linha única"
- [ ] Salvei a definição
- [ ] Editei um produto
- [ ] Rolei até "Metacampos"
- [ ] Preenchi o campo
- [ ] Salvei o produto

---

## 💡 Dica

**Copie e cole este mapeamento para testar:**
```
Amarelo:#FFFF00|Azul:#0000FF|Verde:#00FF00|Vermelho:#FF0000|Preto:#000000|Branco:#FFFFFF
```

---

## 🎯 Resumo

1. **Admin** → Configurações → Metacampos → Produtos
2. **Adicionar definição** com os dados acima
3. **Salvar**
4. **Editar produto** → Rolar até Metacampos
5. **Preencher** com cores
6. **Salvar produto**
7. **Testar** na loja

---

**Pronto! Agora você sabe exatamente onde configurar! 🎉**
