# Instala��o do OABSP

Instru��es de instala��o do Portal OABSP.

## 1. Ambiente de Desenvolvimento
Segue abaixo as instru��es de instala��o do Portal OABSP para avalia��o e desenvolvimento.

Fiquem atentos as instru��es para a vers�o de Python correta. Apesar do Objetivo do OABSP seja a utiliza��o de Python 3, ainda seguimos utilizando python 2.7 no momento.

As instru��es s�o para a instala��o em um ambiente Linux Ubuntu 22.04i LTS.

### 1.1 Depend�ncias
Atualize o sistema com as depend�ncias necess�rias. Na linha de comando rode:

```
$ sudo apt-get update && sudo apt install -y --no-install-recommends --no-install-suggests dpkg-dev gcc libbz2-dev libc6-dev libffi-dev libjpeg-turbo8-dev libjpeg-dev libldap2-dev libopenjp2-7-dev libpcre3-dev libpq-dev libsasl2-dev libssl-dev libtiff5-dev libxml2-dev libxslt1-dev zlib1g-dev build-essential git gosu libjpeg62 libopenjp2-7 libpq5 libtiff5 libxml2 libxslt1.1 lynx netcat poppler-utils rsync wv curl tzdata net-tools htop python2-setuptools-whl libpython2-dev virtualenv python2-pip-whl
```

### Adicionando um usu�rio Plone no sistema
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

### Ativando o ambiente virtual rec�m criado

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

Para terminar, v� para a pasta onde o c�digo do projeto foi clonado, instale os requerimentos e rode o buildout:

```
$ cd oabsp.buildout
$ pip install -r requirements/install.txt
$ buildout -t 30 -c development.cfg
```

"Nada pode dar errado" (Santos, Cl�ber)

### 1.4 Subindo a instancia

Para subir a instancia e iniciar o Plone rode: 

```
$ bin/instance fg
```

Voc� poder� acessar o Plone pelo endere�o http://localhost:8080 em seu navegador.

## 2. Ambiente de Avalia��o

Para criar um ambiente de avalia��o do OABSP voc� pode serguir os mesmos passos da se��o anterior at� o passo 1.2. A �nica mudan�a a ser feita ser� na hora de rodar o buildout e subir a instancia.

### 2.1 Buildout

Para avalia��o, voc� ir� rodar um arquivo de buildout diferente, o buildout.cfg:

```
$ cd oabsp.buildout
$ pip install -r requirements/install.txt
$ buildout -t 30 -c buildout.cfg
```

### 2.2 Subindo a instancia

Para subir a instancia, n�o ser� necess�rio subir em modo foreground. Entao para iniciar o Plone rode: 

```
$ bin/instance start
```

Voc� poder� acessar o Plone pelo endere�o http://localhost:8080 em seu navegador

## Ambiente de Produ��o

todo

## Container

todo
