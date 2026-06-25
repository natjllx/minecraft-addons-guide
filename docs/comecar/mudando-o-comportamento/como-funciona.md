# Como funciona o pacote de comportamentos?

O jogo usa a behavior pack para definir o comportamento dos blocos, mobs, itens, etc.

Sem o Behavior Pack, seus blocos e mobs são apenas visuais. Com ele, você controla:
- Como os blocos quebram
- Quanto dano um bloco causa
- Como os mobs se comportam
- Que itens dropam
- Velocidade de mineração

### Arquitetura Básica

Cada elemento (bloco, entidade, item) é definido através de arquivos **JSON** que descrevem:

1. **Descrição** (`description`)
   - Identificador único
   - Categoria/grupo
   - Informações básicas

2. **Componentes** (`components`)
   - Propriedades que definem o comportamento
   - Cada componente controla um aspecto específico

### Exemplo: Estrutura Geral de um Bloco

```json
{
  "format_version": "1.26.30",
  "minecraft:block": {
    "description": {
      "identifier": "seu_namespace:seu_bloco",
      "menu_category": {
        "category": "construction"
      }
    },
    "components": {
      "minecraft:destructible_by_mining": { "seconds_to_destroy": 2 },
      "minecraft:light_emission": 5,
      "minecraft:map_color": "#ff0000"
    }
  }
}
```

---

## Entidades: Definindo Comportamentos de Mobs

As entidades (como a vaca) têm seus comportamentos definidos em arquivos JSON na pasta `entities/`.

### Estrutura de uma Entidade

```
entities/
├── cow.json           # Define visuals da vaca
├── chicken.json
├── zombie.json
└── seu_mob_custom.json
```

### Exemplo Prático: Arquivo cow.json

```json
{
  "format_version": "1.20.80",
  "minecraft:entity": {
    "description": {
      "identifier": "minecraft:cow",
      "is_spawnable": true,
      "is_summonable": true,
      "is_experimental": false
    },
    "components": {
      "minecraft:type_family": {
        "family": ["mob", "animal"]
      },
      "minecraft:health": {
        "value": 10
      },
      "minecraft:movement": {
        "value": 0.25
      },
      "minecraft:damage_sensor": {
        "triggers": [
          {
            "on_damage": {
              "event": "minecraft:entity_hurt"
            }
          }
        ]
      }
    },
    "events": {
      "minecraft:entity_hurt": {
        "sound": "mob.cow.hurt"
      }
    }
  }
}
```

---

## Blocos: Definindo Comportamentos Simples

Os blocos customizados são definidos na pasta `blocks/`.

### Componentes Comuns em Blocos

`minecraft:destructible_by_mining` | Tempo para quebrar | `"seconds_to_destroy": 3` |
`minecraft:light_emission` | Quanto de luz emite | `5` (0-15) |
`minecraft:map_color` | Cor no mapa | `"#ff0000"` (vermelho) |
`minecraft:geometry` | Formato do bloco | `"minecraft:geometry.full_block"` |
`minecraft:material_instances` | Texturas | `{ "*": { "texture": "bloco" } }` |

### Exemplo Prático: Bloco Customizado

```json
{
  "format_version": "1.26.30",
  "minecraft:block": {
    "description": {
      "identifier": "meu_addon:bloco_especial",
      "menu_category": {
        "category": "construction"
      }
    },
    "components": {
      "minecraft:geometry": "minecraft:geometry.full_block",
      "minecraft:material_instances": {
        "*": {
          "texture": "bloco_especial"
        }
      },
      "minecraft:destructible_by_mining": {
        "seconds_to_destroy": 1.5
      },
      "minecraft:light_emission": 8,
      "minecraft:map_color": "#00ff00"
    }
  }
}
```
