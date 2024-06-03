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
| --- | ---------------------------------------------------------------------------------------------------------------- |
| 0   | Como desenvolvedor, quero fazer o setup das ferramentas necessárias para cumprir o ciclo de vida de uma aplicação Cartesi. |
| 1   | Como desenvolvedor, eu quero criar um projeto cartesi utilizando a cli.                                           |
| 2   | Como desenvolvedor, eu quero dar "build" na minha aplicação, utilizando a cli.                                   |
| 3   | Como desenvolvedor, eu quero interagir com o meu dApp utilizando a cli em modo de produção.                      |
| 4   | Como desenvolvedor, eu quero personalizar o meu backend para alterar o ouputs.                                   |
| 5   | Como desenvolvedor, eu quero interagir com a minha aplicação, utilizando o Nonodo.                               |
| 5   | Como desenvolvedor, quero analisar os outputs do meu dApp, i.e., Notificações e Relatórios.                      |
 

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
> **_Command:_**
> 
> ```bash
> $ cartesi doctor
> ```
>
> **_Output_**
>
> ```bash
> 
> ```

#### Nonodo:
NoNodo é um nó de desenvolvimento para Cartesi Rollups que foi projetado para funcionar com aplicações que rodam na máquina hospedeira em vez da máquina Cartesi.

```bash
$ npm i -g nonodo
```

> [!WARNING]
> Novamente, rode o seguinte comando para verificar se instalação foi reaizada com sucesso e a sua máquina está pronta, antes de seguir em frente:
>
> **_Command:_**
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

### _"Talk is cheap, show me the code"_:



_User story number 1_

_Required past interactions: No past interactions._

##### Step 1:

###### Command:

```shell
sunodo send ether --amount=1000
```

###### Output:

```shell
? Chain Foundry
? RPC URL http://127.0.0.1:8545
? Wallet Mnemonic
? Mnemonic test test test test test test test test test test test junk
? Account 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 9999.969240420387558666 ETH
? DApp address 0x70ac08179605AF2D9e75782b8DEcDD3c22aA4D0C
✔ Input sent: 0x748c08e26d4898384ab0a0cdea7a41bfc7fe0138300133e6cdcf8733b245acf7
```

> [!NOTE]
> - Request Type: Advance State
> - Contract Name: EtherPortal
> - Contract Function: "depositEther(address app, bytes calldata execLayerData)"
> - Contract Address: 0xFfdbe43d4c855BF7e0f105c400A50857f53AB044


