# Ativando o Addon

Antes de ativar seu addon, é importante entender como o Minecraft reconhece e aplica addons ao seu mundo.

## Como o Minecraft Reconhece Addons

Quando você cria um mundo no Minecraft, uma pasta dedicada é criada no seu computador. Quando você ativa um addon, o Minecraft cria dois arquivos nessa pasta:

- **world_behavior_packs.json** — para addons de comportamento
- **world_resource_packs.json** — para addons de aparência

Estes arquivos informam ao mundo qual addon deve ser aplicado. Sem eles, o mundo não sabe que o addon existe e não o aplica.

## Estrutura do Arquivo

A estrutura padrão é:

```json
[
  {
    "pack_id": "uuid-do-header-aqui",
    "version": [1, 0, 0]
  }
]
```

**Importante:** O `pack_id` deve ser **exatamente igual ao UUID do header do seu addon**, não o UUID do módulo!

## Como Funciona Automaticamente

Quando você joga normalmente no Minecraft e ativa um addon pela interface, o jogo faz isso automaticamente:

- Se ativar um resource pack, a UUID da header é adicionada ao **world_resource_packs.json**
- Se ativar um behavior pack, a UUID da header é adicionada ao **world_behavior_packs.json**

## Ativando no Servidor

Quando você quer rodar um servidor local do Minecraft, o processo é diferente — você deve fazer isso manualmente.

### Passo 1: Copiar o UUID

1. Abra o arquivo `manifest.json` do seu addon
2. Copie o UUID que está em `"header"` (não confunda com o UUID do módulo!)

### Passo 2: Localizar a Pasta do Mundo

1. Vá até a pasta raiz do servidor
2. Entre na pasta **worlds**
3. Abra a pasta do seu mundo (se não existir, ligue o servidor uma vez para criá-la)

> **Dica:** Se não sabe onde fica a pasta do servidor, consulte a seção "Requisitos e Instalação"

### Passo 3: Editar o Arquivo

1. Procure pelo arquivo **world_resource_packs.json** (já que nosso addon apenas modifica aparência)
2. Se não existir, crie um novo arquivo com este nome exato
3. Coloque o seguinte conteúdo:

```json
[
  {
    "pack_id": "uuid-da-header-do-seu-addon",
    "version": [1, 0, 0]
  }
]
```

### Passo 4: Múltiplos Addons

Se você tiver mais de um addon, adicione cada um como um novo objeto no array:

```json
[
  {
    "pack_id": "4870548d-b735-4df3-8ca2-4954f2ad44e9",
    "version": [1, 0, 0]
  },
  {
    "pack_id": "uuid-da-header-do-seu-outro-addon",
    "version": [1, 0, 0]
  }
]
```

## Testando o Addon

1. Salve o arquivo
2. Ligue o servidor
3. Entre no mundo
4. Veja sua terra mudar de aparência!

Seu addon está ativado e funcionando!
