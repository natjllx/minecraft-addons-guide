# Modificando a Terra

Vamos criar nosso primeiro addon para entender melhor como tudo funciona na prática.

## Passo 1: Criar a Estrutura do Addon

1. Abra a pasta **development_resource_packs**
2. Crie uma nova pasta com um nome descritivo, por exemplo: **primeiro_addon_rp** (rp significa Resource Pack)
3. Dentro dessa pasta, crie a seguinte estrutura de pastas:

```
primeiro_addon_rp/
├─ textures/
│  └─ blocks/
├─ manifest.json
└─ pack_icon.png (opcional)
```

## Passo 2: Adicionar o Ícone (Opcional)

Se quiser, coloque um ícone do addon na raiz com o nome **pack_icon.png**. Este será a capa/ícone do seu addon que aparece na tela de seleção.

**Recomendações de tamanho:** 256x256, 128x128 ou 64x64 pixels (PNG).

## Passo 3: Criar o Manifest

Na raiz da pasta do addon, crie um arquivo chamado **manifest.json** com as informações do seu addon.

## Próximo Passo

Agora você tem a estrutura pronta para adicionar arquivos de modificação. A pasta `textures/blocks/` é onde você colocará as texturas dos blocos que quer modificar.
