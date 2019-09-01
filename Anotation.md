# Comands linux

```bash
$ which python                      #exibe qual o PATH que esta rodando o python
```

# How to use pip

```bash
$ pip install <nome pacote>         #instala o pacote
$ pip freeze                        #lista os pacotes do  ambiente
$ pip freeze > requeriments.txt     #coloca no requerimenrs os pacotes do ambiete
$ pip install -r requeriments.txt   #instala os pacotes listados dentro do requeriments

```

# How to use virtualenv

```bash
$ virtualenv env                    #cria o ambiente virtual env
$ source env/bin/activate           #ativa o ambiente virtual env
$ deactive                          #sai do ambiente virtual

```

# how to use conda
```bash
$ conda create --name envConda      #cria o ambiente virtual env
$ conda deactive                    #sai do ambiente virtual
$ conda env list                    #lista os ambientes virtuais do conda
$ conda install <nome do pacote>    #instala o pacote
$ conda activate envConda           #ativa o ambiente virtual env

```

#Python

##Compilando pacotes
Encapsular os projeto s criados para sererem distribuidos para terceiros

Com o codigo abaixo, em um arquivo chamado setup.py
```python
from setuptools import setup


setup(
    name="hello",
    version="0.0.1",
    description="Meu novo pacote",
    author="Lincoln Schreiber",
    author_email="lincolnschreiber at gmail",
    packages=["01-example"],
    install_requires=["numpy"]
)
```

Pode-se exportar as aplicações feitas, exemplos
```bash
$ python setup.py build             #builda todo projeto e armazena/organiza em pastas
$ python setup.py sdist             #compila o projeto e adiciona a um arquivo compact
$ python setup.py install           #istala o projeto especificado no setup.py

```

# Docker

exemplo de um arquivo docker
```dockerfile
FROM python:3.7-alpine

COPY ./requirements.txt /requeriments.txt

RUN pip install -r requeriments.txt

RUN mkdir /statsapi
RUN mkdir /logs

COPY ./02-apiRest/app.py /app.py
COPY ./02-apiRest/statsapi/data_store.py /statsapi/data_store.py
COPY ./02-apiRest/statsapi/operation.py /statsapi/operation.py

EXPOSE 5000

CMD python app.py
```

Os arquivos criados dentro de um container são deletados juntamente com ele, se ele for deletado. Entao é nescessario apontar o arquivo do container para um arquivo da maquina host.




```bash
$ docker build -t statsapi:0.0.1 .                   # builda a imagem com nome statsapi com a tag 0.0.1 
$ docker image ls                                    # lista as imagens instaladas
$ docker container ls -a                             # lista os containers criados, se nao usar a flag -a mostra somente os que estao rodando 
$ docker run -p 5000:5000 -ti statsapi:0.0.1         # roda a imagem statsapi:0.0.1, comando -p indica que a porta 5000 do container é a mesma que a porta da maquina
$ docker container rm <id>                           # passando o id do container é possivel remover ele
$ docker exec -ti <id> sh                            # abre um bash dentro do container, o comando exec responsavel por executar comandos dentro do container
$ docker run -p 5000:5000 -v ~/statsAPI/logs:logs -ti statsapi:0.0.1  # rodando o container e o parametro -v ~/statsAPI/logs:/logs aponta o uma pasta do computador (~/statsAPI/logs) para salvar os arquivos de uma pasta do container (/logs)  
$ docker container ls -a -q                          # lista os id de todos containers
$ docker container rm $(docker container -a -q)      # remove todos os containers
$ docker container stop <id>                         # para de rodar o container de determinado id
# docker run -d nameImg roda o container, porem nao fica no terminal em que tu esta, ou seja roda em background
# docker run -rm nameImg roda o container, porem qd terminar o processo / parar o processo ele é removido pq da flag -rm


```


# Neoway DataScience Template

Dentro da pasta [template](00-Introduction/03-modelNeoWay/data-science-template) ao rodar o comando "./create-model <nome>" cria um projeto seguindo o template da neoway no caminho/nome passado por parametro.

A seguir seram apresentados alguns comandos que podem ser executados dentro da pasta de um projeto criado seguindo o template da neoway.
```bash
$ make docs     # gerara um site de documentação do projeto
$ make jupyter-notebook # criara um container do docker com um jupyter notebook e coloca pra rodar
$ make jupyter # criara um container do docker com todas as funções do jupyter lab 

```

dentro do makefile que se encontra na pasta, se encontra outras funções q o template possui