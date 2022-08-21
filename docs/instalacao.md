# Instalação do OABSP

Instru?es de instalação do Portal OABSP.

## 1. Ambiente de Desenvolvimento
Segue abaixo as instruções de instalação do Portal IDGX para avaliação e desenvolvimento.

Fiquem atentos as instruções para a versão de Python correta. Apesar do Objetivo do OABSP seja a utilização de Python 3, ainda seguimos utilizando python 2.7 no momento.

As instruções são para a instalação em um ambiente Linux Ubuntu 22.04 LTS.

### 1.1 Dependências
Atualize o sistema com as dependências necessárias. Na linha de comando rode:

```
$ sudo apt-get update && sudo apt install -y --no-install-recommends --no-install-suggests dpkg-dev gcc libbz2-dev libc6-dev libffi-dev libjpeg-turbo8-dev libjpeg-dev libldap2-dev libopenjp2-7-dev libpcre3-dev libpq-dev libsasl2-dev libssl-dev libtiff5-dev libxml2-dev libxslt1-dev zlib1g-dev build-essential git gosu libjpeg62 libopenjp2-7 libpq5 libtiff5 libxml2 libxslt1.1 lynx netcat poppler-utils rsync wv curl tzdata net-tools htop python2-setuptools-whl libpython2-dev virtualenv python2-pip-whl
```

### Adicionando um usuário Plone no sistema
```
sudo useradd --system -m -d /opt/plone -U -u 1001 plone -s /bin/bash
su - plone
```

### 1.2 Ambiente Virtual

Para evitar conflitos com o Python utilizado pelo sistema operacional, cria-se um ambiente virtual (virtualenv) apartado do restante do sistema. 

Para criar o ambiente virtual execute:

```
$ virtualenv -p python2.7 ./env27
```

### Ativando o ambiente virtual rec? criado

```
$ source env27/bin/activate
```

### Atualizando o PIP

```
$ wget -O - https://bootstrap.pypa.io/pip/2.7/get-pip.py | python
```

### O buildout

Agora clone o projeto:

```
$ git clone https://github.com/forcontent/oabsp.buildout.git
```



### 1.3 Buildout

Para terminar, vá para a pasta onde o código do projeto foi clonado, instale os requerimentos e rode o buildout:

```
$ cd oabsp.buildout
$ pip install -r requirements/install.txt
$ buildout -t 30 -c development.cfg
```

"Nada pode dar errado" (Santos, Cléber)

### 1.4 Subindo a instancia

Para subir a instancia e iniciar o Plone rode: 

```
$ bin/instance fg
```

Você poderá acessar o Plone pelo endereço http://localhost:8080 em seu navegador.

## 2. Ambiente de Avaliação

Para criar um ambiente de avaliação do OABSP você pode serguir os mesmos passos da seção anterior até o passo 1.2. A única mudança a ser feita será na hora de rodar o buildout e subir a instancia.

### 2.1 Buildout

Para avaliação, você irá rodar um arquivo de buildout diferente, o buildout.cfg:

```
$ cd oabsp.buildout
$ pip install -r requirements/install.txt
$ buildout -t 30 -c buildout.cfg
```

### 2.2 Subindo a instancia

Para subir a instancia, não será necessário subir em modo foreground. Entao para iniciar o Plone rode:

```
$ bin/instance start
```

Você poderá acessar o Plone pelo endereço http://localhost:8080 em seu navegador

## Ambiente de Produ?o

todo

## Container

todo
