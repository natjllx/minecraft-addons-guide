# Modificando a terra
Iremos criar o nosso primeiro addon para termos noção geral de como irá funcionar
Para isso, abra a pasta **development_resource_packs**, dentro dela crie outa pasta com o nome que quiser, ex:
**primeiro_addon_rp** (rp significa resource pack), dentro dela você criará um arquivo chamado manifest.json

o que é manifest json?
O manifest json é um arquivo que contém informações básicas, mas essenciais pro miencraft reconhecer e fazer ela funcionar.

´´´
{
  "format_version": 2,
  "header": {
    "name": "seu-primeiro-addon",
    "description": "Modificando a terra",
    "uuid": "575b6398-1d1f-7aaa-edb9-982f4490f1e0",
    "version": [
      1,
      0,
      0
    ],
    "min_engine_version": [
      1,
      17,
      0
    ]
  },
  "modules": [
    {
      "type": "resources",
      "uuid": "285aa41a-3702-b0ac-c731-7969ca8e7b28",
      "version": [
        1,
        0,
        0
      ]
    }
  ],
  "metadata": {
    "authors": [
      "Natjllx"
    ],
    "url": "example.com"
  }
}
´´´
