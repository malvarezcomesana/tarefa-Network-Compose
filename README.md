# Tarefa 4: Network e Compose


Neste repositorio resolvemos o exercicio de Docker Network y Docker Compose, con explicacións claras de cada paso:


## 1. Crear unha rede en Docker

Para crear unha rede en Docker, usamos o comando:
```bash
docker network create minharede
```
Neste caso, creamos unha rede chamada minharede co driver predeterminado bridge.


## 2. Crear dous contenedores unidos a esa rede

Agora, creamos dous contenedores que estarán unidos á rede que acabamos de crear:
```bash
docker run -itd --name=cont1 --network=minharede ubuntu
docker run -itd --name=cont2 --network=minharede ubuntu
```
Aquí estamos lanzando dous contenedores (cont1 e cont2) e conectándoos á rede minharede usando a imaxe de ubuntu.


## 3. Comprobar que os contenedores están na rede

Para verificar que os contenedores están conectados á rede:
```bash
docker network inspect minharede
[
    {
        "Name": "minharede",
        "Id": "2e64a4d4f687d9ad1e7ef76bb9f3da2f0bce146b05b3bdcf1c69b56a752d5a1f",
        "Created": "2024-10-21T20:22:17.903753428+02:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "0844ca8a5f3d17e4ef09c946dcf96ee404e3bbe312d4f327f55e5c5b7f2da833": {
                "Name": "cont1",
                "EndpointID": "c15548fb53785be03c3db823a6ca8762ce3bb94836df1aaab65dfde0eb135bac",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "cbfb514ae1dae7e86334fa3fd57d9e4552ef7391f31c9103b2d4f35047ddec12": {
                "Name": "cont2",
                "EndpointID": "c438394fd296ae80e56153b2a72af5e5ed5662ef8a813b085e5ebe036aa69925",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```
