---
title: "Falemos de Poetry"
date: 2023-02-11
tags: ["python","poetry","dependencias","galego"]
draft: False
---

Cando nos enfrontamos a un desenvolvemento dun proxecto existen tres variables fundamentais:

## 💡️ Idea

Ter unha idea quizáis é o punto máis importe, xa que sen ela pouco ou nada poderemos facer.

## 🛠 Traballo

Calquera idea xa sexa boa ou mala non se levará a cabo sen realizar un traballo.

## ⏱ Tempo

Para realizar o traballo e facer realidade a idea do noso proxecto tamén fara falla adicarlle un tempo.

Posto que para ter unha idea non podemos recurrir a unha ferramenta que nos poida axudar pouco podemos optimazar neste punto. Sen embargo, sobre os outros dous puntos si que podemos actuar e así optimizar tanto o traballo como o tempo adicado ó noso proxecto.

En Python existen milleiros de paquetes e frameworks que nos fan máis sinxelo o proceso de desenvolvemento. Esto nun primeiro momento é algo excelente posto que tarefas básicas ou repetivas xa están implementadas e probadas pola comunidade e nós só temos que preocuparnos e sacarlle todo o proveito que poidamos.

Unha vez que escollemos que ferramentas nos axudarán a levar a cabo a nosa idea, atopámonos co dilema de que versión escoller. Nun primeiro momemento podemos tomar a decisión de escoller a última versión estable dispoñible. Esta adoita ser a opción máis cómada e sinxela xa que teremos as últimas características dos paquetes ou framework.

Sen embargo, co paso do tempo as versións que escollimos nun primeiro momento comezarán a quedarse obsoletas e quereremos actualizar á última versión o noso framework ou os paquetes que nos axudaron a levar a cabo a nosa idea. Este proceso pode parecer sinxelo pero en ocasións pode chegar a ser un verdadeiro quebradeiro de cabeza polas dependencias que adoita haber entre paquetes en Python.

Para resolver este último punto e facer o proceso de actualización de versións algo moito máis sinxelo e levadeiro ven **Poetry**.

**Poetry** é un xestor de dependencias e empaquetador de Python e axudanos a manter un control preciso das dependencias no noso proxecto, facilitando a instalación e desplegue de aplicacións.

Segundo a súa web oficial, **Poetry** ten tres características principais:

### Resolvedor de dependencias
>Poetry ven cun exaustivo resolvedor de dependencias, o cal sempre atopara una solución se esta existe.

### Illamento
>Poetry emprega os teus entornos virtuais configurados ou ben crea os seus propios para que estar sempre illado do teu sistema.

### Liña de comandos intuitiva
>Os comandos de Poetry son intuitivos e fáciles de usar, con valores predeterminados razoables aínda que tamén se poden configurar.


## Instalación
Para [instalar](https://python-poetry.org/docs/#installation) **Poetry** é moi sinxelo, chega con executar o seguinte comando na túa:

```bash
$ curl -sSL https://install.python-poetry.org | python3 -
```

## Crear un novo proxecto
Para crear un novo proxecto con **Poetry**, simplemente tes que executar o seguinte comando:

```
$ poetry new my-project
```

Esto creará unha nova carpeta chamada *my-project* coa estructura básica dun proyecto Python.

```bash
├── my_project
│   └── __init__.py
├── pyproject.toml
├── README.md
└── tests
    └── __init__.py
```

## Comezar a usar **Poetry** nun proxecto existente
No desenvolvemento de software o máis común e traballar con proxectos xa creados con anterioridade. Este feito non é un problema xa que **Poetry** pódese engadir a un proxecto existente. Para facer isto simplemente colocámonos no directirio raíz do noso proxecto e executamos o seguinte comando:

```bash
$ cd my-existing-project
$ poetry init
```

Cando executemos o comando anterior mostrarásenos un wizard que no axudará coa configuración inicial básica do noso proxecto tal e como se ve a continuación

```bash
This command will guide you through creating your pyproject.toml config.

Package name [my-existing-project]:  
Version [0.1.0]:  
Description []:  
Author [Mateo C.P. <mateo.cp.dev@gmail.com>, n to skip]:  
License []:  
Compatible Python versions [^3.9]:  

Would you like to define your main dependencies interactively? (yes/no) [yes] no
Would you like to define your development dependencies interactively? (yes/no) [yes] no
Generated file

[tool.poetry]
name = "my-existing-project"
version = "0.1.0"
description = ""
authors = ["Mateo C.P. <mateo.cp.dev@gmail.com>"]
readme = "README.md"
packages = [{include = "my_existing_project"}]

[tool.poetry.dependencies]
python = "^3.9"


[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"


Do you confirm generation? (yes/no) [yes] yes
``` 

Para engadir as dependencias necesarias ó noso proxecto podemos facelo no momento de configurar por primeira vez o proxecto ou a posteriori.

## Engadir dependencias
Cando precisemos engadir ó noso proxecto unha nova librería ou framework, empregaremos o comando `add` de **Poetry**. Por exemplo, para agregar a librería requests, executaremos:

```bash
$ poetry add requests
```
**Poetry** actualizará automáticamente o arquivo `pyproject.toml` coa nova dependencia e agregaraa ó arquivo `poetry.lock`, que rexistra aa versión exacta de cada dependencia.

## Instalar dependencias
Outro xeito de engadir novas librerías ó noso projecto é modificar o arquivo `project.toml`. Cando estemos listos para instalar as dependencias do proyecto, executaremos o seguinte comando:

{{< notice warning >}}
Teremos que borrar o arquivo `poetry.lock` antes de proceder a instalar as novas dependencias.
{{< /notice >}}

```bash
$ poetry install
```
Esto instalará e resolverá todas as novas dependencias listadas no arquivo `pyproject.toml`.

## Empaquetar e distribuir o teu proxecto
**Poetry** tamén serve para empaquetar o teu proxecto, se executamos:

```
poetry build
```

Esto creará unha carpeta, no raíz do noso proxecto, chamada `dist` con dous ficheiros no seu interior. Estes arquivos terán o nome do noso proxecto e un terá a extención `.whl` e outro terá a extensión `.tar.gz`

Ámboslos dous arquivos poderanse compartir ou publicar en [PyPI](https://www.pypi.org)

Para publicar o teu proxecto en PyPI, primeiro debes configurar a túa conta e despois executar o seguinte comando:

```bash
$ poetry publish
```
Con isto, o noso proxecto estará dispoñiible para ser instalado empregando `pip`


[Presentación en pdf](/pdf/poetry/Poetry.pdf)