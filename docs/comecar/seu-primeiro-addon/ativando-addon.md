# Ativando o addon
Antes disso, é bom você saber como funciona as coisas, no minecraft,qunado você entra no jogo, cria seu mundo, a pasta do seu mundo do minecraft é criada, 
quando você ativa o addon, os dois arquivos é criado na pasta do mundo, o **world_behavior_packs.json** e **world_resource_packs.json**
ela serve para o mundo reconhecer o addon, sem ela, o mundo nao sabe que o addon existe e nao aplica, a estrutura é assim:

[
  {

    "pack_id": "uuid-do-header-aqui",

    "version": [1, 0, 0]

  }
]

O UUID desta estrutura tem que ser igual a UUID da header do seu addon, por exemplo, quando você ativa o addon resource packs, a uuid da header do pacote resouce pack
é adicionada no arquivo **world_resource_packs.json**, o mesmo vale para o addon da behavior pack com a **world_behavior_packs.json**

Sem isso o mundo nao reconhece o addon, por isso é importante, POREM tudo isso é automatico, o minecraft faz isso sozinho quando você joga com seu addon, porém isso não
acontece o mesmo quando queremos rodar o servidor do minecraft, então o que faremos?
Na resource packs do seu addon, vá no manifest,json, copie a uuid da header (NÃO É A UUID DO MÓDULO, NÃO CONFUDA!), vá até a raiz onde está o servidor
procure pela pasta words, dentro dela teŕa a pasta do seu mundo, se não tiver, você precisa ligar o servidor para criar o mundo, ensinamos isso na seção *Requisitos e Instalação*
entrando no mundo, procure pelo arquivo **world_resource_packs.json** (como nosso addon apenas modifica a aparencia, será world_resource_packs), se nao existir, crie o arquivo com o nome igual dentro dela, coloque isso:

[
  {

    "pack_id": "uuid-da-header-do-seu-addon",

    "version": [1, 0, 0]

  }
]


Se você tiver mais addons, será assim:

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

desse jeito o nosso addno será ativado! Ligue o servidor e entre no mundoe e veja sua terra mudar de aparência!
