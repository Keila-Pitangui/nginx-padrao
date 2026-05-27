# padrao-instance
Repositório criado para padronizar a criação de instância na Oracle.

# Servidor Nginx com Proxy

Este projeto utiliza **Nginx** rodando em um container Docker para servir arquivos estáticos e atuar como um **Proxy Reverso** para um container de gerenciamento de firmware.

## Como iniciar o projeto

### Pré-requisitos
* Docker instalado
* Docker Compose instalado


### Passos

1. Instalar o Docker (caso não tenha):

```bash
curl -fsSL https://get.docker.com/ | sh
```

2. Clone este repositório e certifique-se de que os arquivos de configuração .conf estejam dentro da pasta ./conf.d.

3. Configuração das Aplicações:

    Para cada nova aplicação, crie um **arquivo.conf** em **conf.d/.** Lembre-se de substituir as variáveis nos arquivos:
    
    **server_name:** Defina o seu domínio (ex: jimibrasil.com.br).

    **set $upstream_aplication:** Nome do container de destino (deve estar na mesma rede Docker).

    **<porta>:** Porta interna do serviço que está rodando.
        
    Exemplo de substituição:

```
server_name <dns-do-seu-site>;

server_name jimibrasil.com.br;

```


4. Acesse o diretório do **/nginx** e inicie o container do nginx:

```bash
docker compose up -d
```

5. Comandos Úteis

```bash
docker compose logs -f nginx

docker compose exec nginx nginx -t
```

7. para derrubar o container: 

```bash
docker compose down
```

## Se precisar alterar configurações de rede ou portas, edite o arquivo docker-compose.yml.
