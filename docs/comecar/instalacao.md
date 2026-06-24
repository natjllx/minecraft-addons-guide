# PREPARAÇÃO DE AMBIENTE

## O setup ideal que eu uso para preparar o ambiente:

### Editor de código
O editor de código que eu recomendo é o Visual Studio Code. Caso queira usá-lo, clique no link que te levará ao site oficial:
[VS Code](https://code.visualstudio.com/)

### Extensões essenciais do VS Code:
Elas serão úteis mais adiante, mas é bom estar preparado para quando estiver pronto.

- **Bedrock Definitions** — autor: destruc7i0n
- **Minecraft Bedrock Debugger** — autor: Mojang Studios
- **Blockception's Minecraft Bedrock Development** — autor: Blockception Ltd

### Ambiente de teste:

Para o ambiente de teste, recomendo rodar o servidor local de Minecraft, assim é mais fácil pois você modifica o addon e depois é só rodar o servidor, abrir o Minecraft e testar seu addon.

Para isso, instale o Minecraft Bedrock Server Oficial: [Aqui](https://www.minecraft.net/en-us/download/server/bedrock)

---

#### Windows:

1. Ao baixar o arquivo, extraia o .zip em um local ideal (ex: `C:\MinecraftServer`)
2. Vá no Firewall do Windows e libere a porta 19132 (UDP)
3. Abra a pasta que extraiu e clique em `bedrock_server.exe`

O servidor está pronto para ser usado. O endereço do servidor é o IP do computador. Caso não saiba qual é, abra o CMD, escreva `ipconfig` e procure por **IPv4 Address**. Exemplo: `192.168.1.100`. A porta normalmente é `19132`.

**Nota:** Normalmente o servidor tem o modo LAN ativado, então provavelmente quando você abrir o Minecraft, encontrará o servidor logo de cara na aba de mundos, sem precisar colocar endereço e porta.

**⚠️ AVISO:** NÃO RECOMENDO rodar o servidor em rede aberta ou da universidade! Sua rede fica exposta e, se houver alguém mal-intencionado, ele invadirá sua rede sem dificuldades. Caso queira mesmo fazer isso, sugiro que pesquise e use a ferramenta **Tailscale** (pesquise bastante como se usa e como se aplica ao seu caso).

Na pasta onde você extraiu, terá um arquivo chamado `server.properties`. Lá você pode configurar como vai funcionar seu mundo, como modo de dificuldade e jogo experimental (recomendo colocar como `true`!).

Na mesma pasta, terá duas pastas importantes: `development_behavior_pack` e `development_resource_packs`. Nessas pastas, uma ficará com o pacote de comportamento e a outra com o pacote de recursos. Falaremos sobre isso e como funciona a organização em breve. Isso é tudo que você precisa saber.

---

#### Linux:

É praticamente o mesmo que no Windows, mas com algumas diferenças. Para abrir a porta 19132, abra o terminal (CTRL+ALT+T) e escreva esses comandos:

```bash
sudo ufw allow 19132/udp
sudo ufw enable
sudo ufw status
```

Para iniciar o servidor, diferente do Windows, você precisa iniciá-lo pelo terminal. Para isso, entre na pasta que você extraiu:

```bash
cd ~/caminho-da-pasta
LD_LIBRARY_PATH=. ./bedrock_server
```

Durante a modificação do behavior pack ou resource pack no VS Code, você testará o addon apenas rodando o servidor e testando pelo Minecraft. É o jeito mais prático que eu uso.
