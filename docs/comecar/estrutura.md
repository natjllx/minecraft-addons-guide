# Estrutura de pastas

O addon é composto por duas pastas raiz: o behavior pack (comportamento) e o resource pack (recursos).
Ambos possuem uma estrutura específica que organiza os arquivos:

## Behavior_pack

Behavior_pack
  manifest.json
  pack_icon.png
  functons/
  scripts/
  blocks/

- **manifest.json** - Identificador do pacote (falaremos sobre isso em breve)
- **pack_icon.png** - Ícone/capa do pacote (opcional)
- **functions/** - Comandos e funções do addon
- **scripts/** - Scripts de comportamento
- **blocks/** - Definição de blocos customizados

## Resource_pack

Resource_pack
  manifest.json
  pack_icon.png
  blocks/
  textures/

- **manifest.json** - Identificador do pacote
- **pack_icon.png** - Ícone/capa do pacote
- **blocks/** - Modelos de blocos
- **textures/** - Texturas e visuais
