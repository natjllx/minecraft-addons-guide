# CREEPER MAIS PERIGOSO!
Iremos aumentar a potência da explosão do creeper para vermos na prática como é! 

Para isso precisamos pegar o arquivo json do creeper, que contém todas as informações do creeper de como ela funciona.

Recomendo pegar json no [aqui](https://github.com/Mojang/bedrock-samples/)

Pesquise ou baixe ela e navegue pelas pastas: /behavior_pack/entities/creeper.json, copie esse arquivo e cole em meu_addon_rp/entities/creeper.json,

Abre esse arquivo, você se deparará com vários componentes, são isso que constrói e transforma os mobs em como são eles,
este componente espcífico:

```
"minecraft:exploding": {
        "minecraft:explode": {
          "causes_fire": false,
          "fuse_lit": true,
          "power": 3,
          "destroy_affected_by_griefing": true,
          "fuse_length": 1.5
        }
```

é ela que faz explodir quando você está no survival e o creeper te aproxima, se quiser mudar a potencia da explosão, só mudar o valor do "power", se quiser que a explosão contenha fogos, coloque o "causes_fire" como true, e teste e verá oq acontecerá, mas se quiser testar o creeper no criativo com isqueiro, desça um pouco abaixo e procure o "minecraft:forced_exploding" e mude os valores e teste e verá oq acontecerá! (cuidado com a força da explosão que você coloca, pode travar seu celular por alguns segundos ou minutos!
