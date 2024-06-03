<div align="center">
    <img src="https://github.com/Mugen-Builders/.github/assets/153661799/7ed08d4c-89f4-4bde-a635-0b332affbd5d" width="150" height="150">
</div>
<br>
<div align="center">
    <i>Cartesi Masterclass Day 01 - Inteli Edition</i>
</div>
<div align="center">
Uma introdução à blockchain e ao Cartesi Rollups.
</div>
<br>
<div align="center">
    
  <a href="">[![Static Badge](https://img.shields.io/badge/cartesi--rollups-1.3.0-5bd1d7)](https://docs.cartesi.io/cartesi-rollups/)</a>
  <a href="">[![Static Badge](https://img.shields.io/badge/cartesi/cli-0.6.2-blue)](https://docs.sunodo.io/guide/introduction/what-is-sunodo)</a>
  <a href="">[![Static Badge](https://img.shields.io/badge/nonodo-2.1.0-blue)](https://github.com/gligneul/nonodo/releases/tag/v0.1.0)</a>
  <a href="">[![Static Badge](https://img.shields.io/badge/python-3.10.4-yellow)](https://www.python.org/)</a>
</div>


## Teoria:
Abaixo estão referenciados algumas referências que auxiliarão no entendimento da teoria coberta durante durante o primeiro dia.

 - https://br.cointelegraph.com/learn/what-is-ethereum-a-beginners-guide-to-eth-cryptocurrency
 - https://www.youtube.com/watch?v=BOn9q97CFNE
 - Acessar topicos da documentação:
 	- Overview: https://docs.cartesi.io/cartesi-rollups/1.3/
 	- https://docs.cartesi.io/cartesi-rollups/1.3/quickstart/

## Prática 
Durante esse recorte nós iremos colocar a mão na massa, começando pelo setup do ambiente de desenvolvimento e seguindo para o desenvolvimento da nossa primeira aplicação Cartesi juntos.

### User Stories:
| #   | Description                                                                                    
| --- | -------------------------------------------------------------------------------------------------------------------------- |
| 0   | Como desenvolvedor, quero fazer o setup das ferramentas necessárias para cumprir o ciclo de vida de uma aplicação Cartesi. |
| 1   | Como desenvolvedor, eu quero criar uma aplicação Cartesi utilizando a cli.                                                    |
| 2   | Como desenvolvedor, eu quero personalizar o meu backend.                                                                   |
| 3   | Como desenvolvedor, eu quero dar "build" na minha aplicação, utilizando a cli.                                             |
| 4   | Como desenvolvedor, eu quero rodar e interagir com o meu dApp utilizando a cli em modo de produção.                                |
| 5   | Como desenvolvedor, quero analisar os outputs do meu dApp, i.e., Notificações e Relatórios.                                |
 

### Setup dos pré-requisitos
Nessa etapa, nós instalaremos as ferramentas citadas na User Story 0 e no início deste documento.

#### Docker:
Docker é uma plataforma de software que permite a criação, teste e implantação de aplicações rapidamente através do uso de contêineres. No nosso contexto, ele será a ferramenta de distribuição da cartesi machine por baixo dos panos utilizada pelo Cartesi-Cli

Siga as intruções dessse [link](https://www.docker.com/products/docker-desktop/).

#### Cartesi-Cli
O Cartesi-Cli é uma ferramenta que auxilia na criação de aplicações Cartesi. Ele inclui comandos que ajudam os desenvolvedores a criar, construir, rodar e implantar seus dApps.

```bash
$ npm i -g @cartesi/cli
```

> [!WARNING]
> Rode o seguinte comando para verificar se instalação foi reaizada com sucesso e a sua máquina está pronta, antes de seguir em frente:
>
> **_Input:_**
> 
> ```bash
> $ cartesi doctor
> ```
>
> **_Output_**
>
> ```bash
> Your system is ready.
> ```

#### Nonodo:
NoNodo é um nó de desenvolvimento para Cartesi Rollups que foi projetado para funcionar com aplicações que rodam na máquina hospedeira em vez da máquina Cartesi.

```bash
$ npm i -g nonodo
```

> [!WARNING]
> Novamente, rode o seguinte comando para verificar se instalação foi reaizada com sucesso e a sua máquina está pronta, antes de seguir em frente:
>
> **_Input:_**
> 
> ```bash
> $ nonodo
> ```
>
> **_Output_**
>
> ```bash
> [22:22:54.358] INF http: server is ready address=127.0.0.1:8080
> [22:22:54.358] INF nonodo: ready after=79.016898ms
> ```

### _"Talk is cheap. Show me the code"_:

#### Criar um dApp Cartesi:

_User story 1_

_Interações passadas requeridas: Nenhuma._

##### Passo 1:

###### Input:

```shell
$ cartesi create calculator --template python
```

###### Output:

```shell
✔ Application created at /$HOME/masterclass/calculator
```

> [!NOTE]
> Perceba que quando você entrar na pasta criada e listar os seus arquivos verá provavelmente alguns arquivos familiares como um arquivo .py e um requirements.txt. Ademais, haverá também um arquivo Dockerfile, esse arquivo contém as intruções para criar uma [Imagem Docker](https://chatgpt.com/share/836ae92f-bff6-4a8f-9c53-51176294b632) do seu dApp rodando dentro da [Cartesi Machine](https://chatgpt.com/share/a12326f3-bd28-4a0a-a077-fb2bc0d58c21), por hora nós não vamos precisar adentrar isso muito afundo, pois a cli já abstrai isso para você.

#### Personalizar o dApp:

_User story 2_

_Interações passadas requeridas: Criar um dApp._

##### Passo 1:

Nessa etapa você deverá copiar deste [arquivo](https://raw.githubusercontent.com/henriquemarlon/cartesi-masterclass-day1/main/me_copie.py) e substituir pelo presente no arquivo ```dapp.py```. Além disso, é necessário que vc atualize o arquivo requirements.txt com as mesmas dependências contidas neste [arquivo](https://raw.githubusercontent.com/henriquemarlon/cartesi-masterclass-day1/main/requirements.txt).

#### Build da aplicação:

_User story 3_

_Interações passadas requeridas: Personalizar o dApp._

##### Passo 1:

###### Input:

```shell
cartesi build
```

###### Output:

```shell
copying from tar archive /tmp/input
         .
        / \
      /    \
\---/---\  /----\
 \       X       \
  \----/  \---/---\
       \    / CARTESI
        \ /   MACHINE
         '

[INFO  rollup_http_server] starting http dispatcher service...
[INFO  rollup_http_server::http_service] starting http dispatcher http service!
[INFO  actix_server::builder] starting 1 workers
[INFO  actix_server::server] Actix runtime found; starting in Actix runtime
[INFO  rollup_http_server::dapp_process] starting dapp: python3 dapp.py
```

#### Rodar e Interagir com a aplicação:

_User Story 4_

_Interações passadas requeridas: Build da aplicação._

##### Passo 1

###### Input:
```shell
$ cartesi run
```

###### Output:
```shell
Attaching to prompt-1, validator-1
validator-1  | 2024-06-03 02-11-43 info remote-cartesi-machine pid:120 ppid:73 Initializing server on localhost:0
prompt-1     | Anvil running at http://localhost:8545
prompt-1     | GraphQL running at http://localhost:8080/graphql
prompt-1     | Inspect running at http://localhost:8080/inspect/
prompt-1     | Explorer running at http://localhost:8080/explorer/
prompt-1     | Press Ctrl+C to stop the node
```
##### Passo 2

###### Input:
```shell
$ cartesi send generic \
    --dapp=0xab7528bb862fB57E8A2BCd567a2e929a0Be56a5e \
    --chain-id=31337 \
    --rpc-url=http://127.0.0.1:8545 \
    --mnemonic-passphrase='test test test test test test test test test test test junk' \
    --input='1+2'
```
###### Output:
```shell
validator-1  | [INFO  rollup_http_server::http_service] Received new request of type ADVANCE
validator-1  | [INFO  actix_web::middleware::logger] 127.0.0.1 "POST /finish HTTP/1.1" 200 206 "-" "python-requests/2.31.0" 0.001600
validator-1  | INFO:__main__:Received finish status 200
validator-1  | INFO:__main__:Received advance request data {'metadata': {'msg_sender': '0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266', 'epoch_index': 0, 'input_index': 0, 'block_number': 27, 'timestamp': 1717381889}, 'payload': '0x312b32'}
validator-1  | INFO:__main__:Received input: 1+2
validator-1  | INFO:__main__:Adding notice with payload: '3'
validator-1  | [INFO  actix_web::middleware::logger] 127.0.0.1 "POST /notice HTTP/1.1" 201 11 "-" "python-requests/2.31.0" 0.000896
validator-1  | INFO:__main__:Received notice status 201 body b'{"index":0}'
validator-1  | INFO:__main__:Sending finish
```

#### Analisando os outputs da aplicação:

_User Story 5_

_Interações passadas requeridas: Rodar e interagir com a aplicação._

##### Passo 1

Para isso basta acessar o explorer, uma aplicação web que está sendo servida na seguinte [rota](http://localhost:8080/explorer), mas especificamente: ```http://localhost:8080/explorer``` 
