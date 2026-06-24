# Modificando a Terra

Iremos criar nosso primeiro addon para entender melhor como tudo funciona na prática.

## Passo 1: Criar a Pasta do Addon

1. Abra a pasta **development_resource_packs**
2. Crie uma nova pasta com um nome descritivo, por exemplo: **primeiro_addon_rp** (rp significa Resource Pack)
3. Dentro dessa pasta, crie um arquivo chamado **manifest.json**

## Passo 2: Entender o Manifest.json

O manifest.json é um arquivo essencial que contém informações básicas sobre seu addon. Sem ele, o Minecraft não consegue reconhecer nem carregar seu addon.

### Estrutura Base

Copie este conteúdo para seu arquivo manifest.json:

```json
{
  "format_version": 2,
  "header": {
    "name": "seu-primeiro-addon",
    "description": "Modificando a terra",
    "uuid": "seu-uuid-aqui",
    "version": [1, 0, 0],
    "min_engine_version": [1, 17, 0]
  },
  "modules": [
    {
      "type": "resources",
      "uuid": "seu-uuid-aqui",
      "version": [1, 0, 0]
    }
  ],
  "metadata": {
    "authors": ["Natjllx"],
    "url": "example.com"
  }
}
```

---

## Explicação Detalhada de Cada Campo

### `"format_version": 2`

Este é o número da versão do formato do manifest que você está usando. O Minecraft evolui constantemente, e o formato também. Atualmente existem versões 2 e 3, mas a versão **2 é mais estável e recomendada** para addons modernos.

---

### `"header": {...}`

O header é o "cabeçalho" do seu addon — é aqui que você coloca as informações principais. Tudo que está dentro do header será exibido quando você visualizar o addon na tela de seleção do Minecraft.

#### `"name": "seu-primeiro-addon"`

Este é o nome do seu addon que aparecerá na lista de addons disponíveis do Minecraft. Você pode escolher qualquer nome que desejar.

**Boas práticas:**
- Use `-` ou `_` em vez de espaços
- Evite caracteres especiais

---

#### `"description": "Modificando a terra"`

A descrição explica brevemente o que seu addon faz. Quando o jogador clica no addon ou abre seus detalhes, esta descrição é exibida.

**Dica:** Seja descritivo e conciso, como:
- "Adiciona 10 novos itens mágicos"
- "Modifica texturas de blocos de terra"
- "Novo sistema de combate aprimorado"

---

#### `"uuid": "seu-uuid-aqui"`

O UUID (Identificador Único Universal) é como um CPF do seu addon — é o que garante que o Minecraft não confunda seu addon com outro.

**Por que é importante:**
- Se você mudar o UUID depois de testar o addon, o Minecraft o tratará como um addon completamente novo
- Isso pode quebrar mundos já criados com seu addon anterior

**Como gerar:**
Use um gerador de UUID online, como: [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/)

**Exemplo de UUID válido:**
```
0757beb6-39cc-4800-82da-e9712449af5f
```

**Importante:** Cada addon deve ter um UUID diferente!

---

#### `"version": [1, 0, 0]`

Este é o número da versão do seu addon. Você atualiza este número conforme faz mudanças e melhorias no seu addon.

**Formato de Versionamento (Semantic Versioning):**

A versão é composta por 3 números: `[MAJOR, MINOR, PATCH]`

- **MAJOR** (primeiro número): Mudanças grandes e significativas
  - Exemplo: Reescrever todo o sistema de mobs
- **MINOR** (segundo número): Novidades e adições
  - Exemplo: Adicionar novos itens ou blocos
- **PATCH** (terceiro número): Correções de bugs
  - Exemplo: Corrigir erro em um efeito de poção

**Exemplos de Progressão de Versão:**

1.0.0 = Corrige um bug = 1.0.1
1.0.1 = Adiciona 5 itens novos = 1.1.0
1.1.0 = Adiciona novo sistema = 1.2.0
1.2.0 = Reescreve tudo = 2.0.0

**Regra importante:** Quando você aumenta um número, todos os números à direita volta para 0.

- `1.3.8` → adiciona novos itens → `1.4.0` (o PATCH volta para 0)
- `1.4.0` → mudança grande → `2.0.0` (MINOR e PATCH voltam para 0)

Esta é apenas uma questão de boa prática e organização — recomendo usar isso sempre!

---

#### `"min_engine_version": [1, 17, 0]`

Esta é a **versão mínima do Minecraft necessária** para seu addon funcionar.

**Como funciona:**
- Se seu addon usa features do Minecraft 1.17, jogadores com 1.16 **não conseguirão** usar seu addon
- Se deixar como `[1, 0, 0]`, seu addon funcionará em qualquer versão

**Exemplo prático:**
Se você usar uma feature nova do 1.19, coloque:
```json
"min_engine_version": [1, 19, 0]
```

---

### `"modules": [...]`

Os módulos definem que tipo de alterações seu addon faz no jogo. Este é um array, então você pode ter múltiplos módulos.

#### `"type": "resources"`

Define o tipo do módulo. As opções principais são:

- `"resources"` → Resource Pack (modifica visual, texturas, sons)
- `"data"` → Behavior Pack (modifica comportamento, mobs, regras)

**Neste exemplo:** Usamos `"resources"` porque estamos apenas modificando a aparência da terra.

---

#### `"uuid": "seu-uuid-aqui"` (dentro de modules)

Este UUID é **específico do módulo**, diferente do UUID do header.

**Por quê dois UUIDs?**
- O primeiro UUID identifica o addon inteiro
- Este segundo UUID identifica este módulo específico
- Se seu addon tiver Resource Pack E Behavior Pack, cada um terá seu próprio UUID

Gere um novo UUID diferente para este campo!

---

#### `"version": [1, 0, 0]` (dentro de modules)

A versão do módulo (independente da versão geral do addon).

**Caso de uso:** Você pode ter versões diferentes para cada módulo:
- Resource Pack na versão 1.2.0
- Behavior Pack na versão 2.0.0

Isso é útil quando você atualiza um módulo mas não o outro.

---

### `"metadata": {...}`

Metadata são informações adicionais e **opcionais** sobre seu addon. Elas fornecem contexto adicional.

#### `"authors": ["Natjllx"]`

Lista dos criadores do addon. Como é um array, você pode adicionar múltiplos autores:

```json
"authors": ["Natjllx", "Outro Dev", "Mais Um Criador"]
```

---

#### `"url": "example.com"`

Um link relacionado ao seu addon. Pode ser:
- Seu site pessoal
- Repositório GitHub
- Página de documentação
- Discord do seu projeto

**Recomendação:**
```json
"url": "https://github.com/seu-usuario/seu-addon"
```

Agora que seu manifest.json está pronto, seu addon será reconhecido pelo Minecraft! Na próxima seção, vamos entender como o Resource Pack funciona e começar a modificar a textura da terra.
