# Guia do colaborador

Este guia visa descrever como você pode colaborar com o projeto, desde o download dos fontes, passando pelo processo de build e depois execução do sistema no seu ambiente local. Incluirá também o precesso de administração e commits no repositório.

_**ATENÇÃO:**_ Se você é iniciante em flutter, siga o roteiro escrito no [**link**](GET-STARTED.md) para montagem do seu ambiente de desenvolvimento.


# Pré-requisitos

- Conhecimentos:
  - Linux (desejável)
  - Docker
  - Git
  - Dart
  - Aplicações Mobile
  - Material Design
  - Html5, css e javascript
- Softwares
  - Linux (desejável)
  - Oh My Zsh - Shell linux integrado com o git, outras linguagens e ferramentas - https://ohmyz.sh/ (desejável)
  - Docker e Docker Compose (Fedora : https://docs.docker.com/install/linux/docker-ce/fedora/ e https://docs.docker.com/compose/install/#prerequisites)
  - Git (deve estar na central de pacotes de sua distribução Linux - git e git-core)
  - Visual Studio Code
  - SDK Flutter


# Passo a passo da configuração do ambiente local

Para facilitar o desenvolvimento, vou sugerir criar alguns diretórios para melhor organização do ambiente local de desenvolvimento. Vou usar essa convenção nos comandos abaixo, se não quiser seguir essa convenção faça adaptações nos comandos a serem executado.

    $ mkdir -p ~/desenv/ide/android-studio; # Local de descompactação do Android Studio
    $ mkdir -p ~/desenv/ide/vscode; # Local de descompactação do Visual Code
    $ mkdir -p ~/desenv/sdk/flutter; # Local de descompactação do Flutter v0.7.0
    $ mkdir -p ~/desenv/sdk/android; # Local de descompactação do Android SDK
    $ mkdir -p ~/desenv/sdk/jdk; # Local de descompactação do JDK 1.8
    $ mkdir -p ~/desenv/projects; # Local do nosso projeto

_**ATENÇÃO:**_ 
- Todos os passos para configuração destes diretório acima, estão descritos no [**link**](GET-STARTED.md)
- Se você seguiu os passos descritos no [**link**](GET-STARTED.md), limpe todo o conteúdo do diretório ~/desenv/projects/


## Clone dos fontes

Vamos fazer o clone conforme comandos abaixo:

    cd ~/desenv/projects
    git clone git@github.com:hugofields/bibliotecaVirtual.git biblioteca-virtual
    cd biblioteca-virtual


## Iniciando o emulador

    cd ~/desenv/projects/biblioteca_virtual
    flutter emulators; # para ver os emuladores que você tem.
    flutter emulators --launch Nexus_5X_API_28_x86; # para iniciar o emulador


## Testando projeto

    cd ~/desenv/projects/biblioteca_virtual
    flutter run --build --hot


# Visual Code 

Bom, minha preferência por editor é o vscode, mas pode ser utilizado qualquer outro. 

Só tome cuidado com os commit para não subir arquivos específicos de cada editor. Quando mais limpo os diretórios do projeto, mas fácil vai ser a assimilação por parte dos novatos!


    cd ~/desenv/projects/biblioteca_virtual
    code .


Volto já pra complementar!!!!