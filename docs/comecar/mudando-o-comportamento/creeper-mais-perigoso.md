# O Creeper Mais Perigoso!

Nesta seção, vamos aprender na prática como modificar componentes de mobs complexos. Usaremos o Creeper como exemplo, aumentando a potência de sua explosão para ver o resultado no jogo.

---

## Passo 1: Obter o Arquivo Vanilla

O Bedrock usa arquivos JSON como base. Precisamos copiar o arquivo oficial do Creeper.

### Onde baixar:

1. Acesse: [Bedrock Samples - GitHub](https://github.com/Mojang/bedrock-samples/)
2. Navegue até: **behavior_pack → entities → creeper.json**
3. Baixe ou copie o arquivo

### Alternativa (sem GitHub):

Se tiver dificuldade, você também pode extrair o `creeper.json` do próprio Minecraft Bedrock instalado, mas a versão do GitHub é mais recente.

---

## Passo 2: Adicionar ao Seu Addon

Agora vamos adicionar o arquivo ao seu Behavior Pack:

```
seu_addon_BP/
├── manifest.json
└── entities/
    └── creeper.json 
```

**Importante:** O caminho deve ser exatamente `entities/creeper.json`. O Bedrock saberá que você está modificando o Creeper vanilla porque o identifier continua sendo `"minecraft:creeper"`.

---

## Passo 3: Entender a Estrutura

Abra o arquivo `creeper.json`. Você verá algo como:

```json
{
  "format_version": "1.20.80",
  "minecraft:entity": {
    "description": { ... },
    "component_groups": {
      "minecraft:exploding": { ... },
      "minecraft:charged_creeper": { ... },
      "minecraft:forced_exploding": { ... }
    },
    "components": { ... },
    "events": { ... }
  }
}
```
e vários outros componentes.

Cada seção tem uma função:
- **`components`**: Comportamentos básicos (saúde, movimento, etc)
- **`component_groups`**: Grupos de comportamentos que podem ser ativados/desativados
- **`events`**: O que acontece quando algo específico ocorre

---

## Passo 4: Modificar a Explosão (Survival)

Quando você está em **Survival**, o Creeper te persegue, chega perto e explode. Isso é controlado pelo grupo `minecraft:exploding`.

### Localize este bloco:

```json
"minecraft:exploding": {
  "minecraft:explode": {
    "causes_fire": false,
    "fuse_lit": true,
    "power": 3,
    "destroy_affected_by_griefing": true,
    "fuse_length": 1.5
  }
}
```

### O que cada valor significa:

| `power` | Força da explosão | 3 (normal), 5 (forte), 10 (muito forte) |
| `causes_fire` | Se coloca fogo quando explode | `true` ou `false` |
| `fuse_length` | Tempo até explodir (em segundos) | 1.5 (padrão) |
| `fuse_lit` | Se a explosão é visível | `true` ou `false` |
| `destroy_affected_by_griefing` | Se respeita gamerule mobGriefing | `true` ou `false` |

### Teste 1: Explosão Mais Forte

Mude o valor de `power` de **3** para **5**:

```json
"minecraft:exploding": {
  "minecraft:explode": {
    "causes_fire": false,
    "fuse_lit": true,
    "power": 5,  ← Mude aqui!
    "destroy_affected_by_griefing": true,
    "fuse_length": 1.5
  }
}
```

**Resultado:** Creeper em Survival explode com mais potencia.

---
Caso queira explodir o creeper no criativo usando isqueiro sem querer mudar pro survival, faça isso:

Diferente da explosão no survival que dispara no grupo ```minecraft:exploding```, no criativo o grupo que disparará quando usa isqueiro é o grupo `minecraft:forced_exploding`.

### Localize este bloco:

```json
"minecraft:forced_exploding": {
  "minecraft:target_nearby_sensor": { },
  "minecraft:explode": {
    "fuse_length": 1.5,
    "fuse_lit": true,
    "power": 3,
    "causes_fire": false,
    "destroy_affected_by_griefing": true
  },
  "minecraft:on_target_escape": { }
}
```

mude o valor conforme o que quiser explorar!

**Resultado:** Use Isqueiro no Creeper em Criativo para ver a explosão customizada.

---

Cuidado com a potencia, se colocar muito alto como 1000 ou mais, provavelmente seu jogo irá crashar KKK!
