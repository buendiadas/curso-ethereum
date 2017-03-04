# Introducción a ethereum

Curso Introducción a Ethereum para desarrolladores

## Contenido

      1. Introducción
      2. Clientes
         - Arquitectura
         - [Geth](#)
            - Instalación
            - Inicialización de parámetros
            - Creación de una blockchain privada
            - Comienzos con la blockchain pública
         - testRPC
      3. [Web3](web3.html)
      3. [Solidity](solidity.html#2)
      4. Ejemplos Smart Contracts
          -Token
         -DAO
         -Crowdfunding

      5. Ejercicio con Token

# Arquitectura de una DApp

  ![image](img/arch-dapp.png)


---

# Clientes

#### Interfaz con la blockchain capaz de recuperar y verificar información de la Blockchain

  - Clientes oficiales
      - [geth](https://github.com/ethereum/go-ethereum): Cliente en Go Lang
      - [eth](https://github.com/ethereum/webthree-umbrella): Cliente C++
      - [pyethapp](https://github.com/ethereum/pyethapp): Cliente en Python

  - Clientes no oficiales:

      - [Parity](https://github.com/ethcore/parity): Cliente escrito por ethcore
      - [Ethereumj](https://github.com/ethereum/ethereumj): Cliente en Java
      - [Ruby-Ethereum](https://github.com/janx/ruby-ethereum): Cliente de Ruby
      -Etc..

##### Todos los clientes deberían tener las mismas funcionalidades

Diferentes implementaciones puede dar lugar a [problemas](https://blog.ethereum.org/2016/11/25/security-alert-11242016-consensus-bug-geth-v1-4-19-v1-5-2/)

---

# Geth
### ¿Por qué Geth?
  - Cliente más popular
  - Compatibilidad multiplaforma

### 3 interfaces:
  - Linea de sub-comandos
  - Un servidor en JSON-RPC
  - Una consola integrada (Web3.js)

El cliente de Ethereum es válido tanto para la red principal (Main net), como para diferentes implementaciónes (Ropsten, Private chain...)

---

# Geth
### Instalación

```sh
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository -y ppa:ethereum/ethereum
$ sudo apt-get update
$ sudo apt-get install ethereum

```
Con solo esto, ya somos capaces de interactuar con Ethereum!

---

# Geth
### Flags
La ejecución de Geth admite numerosos "flags", algunos de los más importantes:

|     Flag             | Descripción                        | Por defecto              |
 ----------------- | ---------------------------- | ------------------
| `--networkid`           | Selecciona el id de blockchain sobre la que se ejecutará |0 (main net)  |
|`--rpc`  |       Permiso a la interfaz RPC     | true |
|`--rpcapi`          |    APIs abiertas vía RPC        | web3
|`--rpcport`          |   Puerto de acceso a RPC        | 8545
| `--rpccorsdomain`| Dominios de acceso a RPC | localhost|
| `--port`           | Puerto de conexión para otros nodos | 30303 |

---
# Geth
### Blockchain privada

#### Inicialización

````json
{
    "nonce": "0x0000000000000042",
    "timestamp": "0x0",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x0",
    "gasLimit": "0x8000000",
    "difficulty": "0x400",
    "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0x3333333333333333333333333333333333333333",
    "alloc": {
    }
}
````
```sh
$ geth init genesis.json
```
  Abrir ahora el archivo datadir
---

# Geth
### Blockchain privada

#### Ejecución

```bash
$ geth --networkid 03032017 --rpccorsdomain "*" --datadir "/home/satoshi/chain" --port "30303"  "db,eth,net,web3"

```

En otra terminal

```bash
$ geth attach
```

#### Blockchain pública

```bash
$ geth
$ geth attach
```
---

#TestRPC

 - Incluso las blockchain privadas son demasiado **lentas/ineficientes a la hora de desarrollar**
 - [testRPC](https://github.com/ethereumjs/testrpc) es una Librería en JS que simula un nodo completo de una blockchain privada, o una blockchain real a partir de determinado punto
 - Para el desarrollo de aplicaciones del curso, se utilizará esta librería.

Ejemplo
``` sh
 $ testrpc
```

---
#TestRPC


Options (From the Docs):

  * `-a` or `--accounts`: Specify the number of accounts to generate at startup.
  * `-b` or `--blocktime`: Specify blocktime in seconds for automatic mining. Default is 0 and no auto-mining.
  * `-d` or `--deterministic`: Generate deterministic addresses based on a pre-defined mnemonic.
  * `-m` or `--mnemonic`: Use a specific HD wallet mnemonic to generate initial addresses.
  * `-p` or `--port`: Port number to listen on. Defaults to 8545.
  * `-h` or `--hostname`: Hostname to listen on. Defaults to Node's `server.listen()` [default](https://nodejs.org/api/http.html#http_server_listen_port_hostname_backlog_callback).
  * `-s` or `--seed`: Use arbitrary data to generate the HD wallet mnemonic to be used.
  * `-g` or `--gasPrice`: Use a custom Gas Price (defaults to 20000000000)
  * `-l` or `--gasLimit`: Use a custom Gas Limit (defaults to 0x47E7C4)
  * `-f` or `--fork`: Fork from another currently running Ethereum client at a given block. Input should be the HTTP location and port of the other client, e.g. `http://localhost:8545`. You can optionally specify the block to fork from using an `@` sign: `http://localhost:8545@1599200`.

---

#Ejemplo: Fork de blockchain para development

####Ejecutar:

``` sh
 $ geth --networkid.... Port, ? rcpport?
```
``` sh
 $ testrpc -p 8545
```

Links a las presentaciones: 

  - [Introducción a Ethereum](http://buendiadas.github.io/ethereum.html)
  - [Introducción a Web3] (http://buendiadas.github.io/web3.html)
  - [Introducción a Solidity] (http://buendiadas.github.io/solidity.html)

