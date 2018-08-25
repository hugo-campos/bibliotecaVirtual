# Guia do colaborador

Este guia visa descrever todo o processo de criação do ambiente de desenvolvimento, desde o download dos fontes, passando pelo processo de build e depois execução do sistema no seu ambiente local.

# Pré-requisitos

- Conhecimentos:
  - Linux (desejável)
  - Docker
  - Git
  - Dart
  - Aplicações Mobile
  - Bootstrap
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

    $ mkdir -p ~/desenv/ide/vscode/eclipse-jee-photon; # Local de descompactação do Eclipse
    $ mkdir -p ~/desenv/sdk/flutter; # Local de descompactação do JDK 1.8
    $ mkdir -p ~/desenv/projects/biblioteca-virtual; # Workspace do eclipse
    $ mkdir -p ~/desenv/server/wildfly; # Local de descompactação do wildfly
    $ mkdir -p ~/desenv/tools/maven; # Local de descompactação do maven


## Instalação do SDK Flutter

Iremos trabalhar com a versão DEV do Flutter, que está na versão v0.7.0.

### Ambiente Linux

No endereço [https://flutter.io/setup-linux/](https://flutter.io/setup-linux/) você vai encontrar o "Get Started" para fazer todas fua configuraçã, mais vamos fazer um resumo aqui.. :P.

Acesse o endereço https://flutter.io/sdk-archive/#linux, baixe o arquivo no diretório informado abaixo e depois descompacte-o.

    $ mv ~/Downloads/flutter_linux_v0.7.0-dev.tar.xz ~/desenv/sdk/flutter/
    $ cd ~/desenv/sdk/flutter/
    $ tar -xvf flutter_linux_v0.7.0-dev.tar.xz
    $ mv flutter v0.7.0
    
Obs: Certifique-se que o diretório do java ficou assim ~/desenv/sdk/flutter/v0.7.0

E no final do arquivo ~/.bash_profile ou ~/.profile (vai depender de sua distro linux), coloque os trechos abaixo: (após edição do arquivo refazer login no linux)

    FLUTTER_HOME=/home/hendi/desenv/sdk/flutter/v0.7.0
    export FLUTTER_HOME

    PATH=$FLUTTER_HOME/bin:$PATH

### Dependencias para o funcionamento do Flutter

Provavelmente você deve ter entrado no site do flutter e visto que ele é uma SDK (Software Development Kit), ou seja um conjunto de blibliotecas e ferramentas pra você criar aplicações nativas para Andriod e IOS. 

E basicamente você só precisa criar seu app utilizando apenas uma única linguagem de programação, que no final ele converte praticamente tudo em código nativo da plataforma em que você fizer o build.

Então ele vai precisar de algumas dependências para que funcione, e inclusive ele oferece um utilitário para você verificar o que está faltando do seu sistema operacional pra você começar a codificar. Rode o comando abaixo n seu terminal...

    $ flutter doctor -v

No meu caso a saída do comando foi essa aqui:

```
  ➜  v0.7.0 git:(dev) flutter doctor -v
  [!] Flutter (Channel dev, v0.7.0, on Linux, locale pt_BR.UTF-8)
      • Flutter version 0.7.0 at /home/hendi/desenv/sdk/flutter/v0.7.0
      • Framework revision 09fe34708f (2 days ago), 2018-08-22 10:20:51 -0700
      • Engine revision 4b271b2e02
      • Dart version 2.1.0-dev.1.0.flutter-69fce633b7
      ✗ Downloaded executables cannot execute on host.
        See https://github.com/flutter/flutter/issues/6207 for more information
        On Debian/Ubuntu/Mint: sudo apt-get install lib32stdc++6
        On Fedora: dnf install libstdc++.i686
        On Arch: pacman -S lib32-libstdc++5


  [✗] Android toolchain - develop for Android devices
      ✗ Unable to locate Android SDK.
        Install Android Studio from: https://developer.android.com/studio/index.html
        On first launch it will assist you in installing the Android SDK components.
        (or visit https://flutter.io/setup/#android-setup for detailed instructions).
        If Android SDK has been installed to a custom location, set $ANDROID_HOME to that location.

  [✗] Android Studio (not installed)
      • Android Studio not found; download from https://developer.android.com/studio/index.html
        (or visit https://flutter.io/setup/#android-setup for detailed instructions).

  [!] VS Code (version 1.26.1)
      • VS Code at /usr/share/code
      • Flutter extension not installed; install from
        https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter

  [!] Connected devices
      ! No devices available

  ! Doctor found issues in 5 categories.

```

Ou seja, foram encontrado problemas em 5 categorias.

Logo mais vou esplicar como resolver cada pendências dessas.

Se no seu ambiente você encontrou outros problemas, nos informe e mostre também como às resolver... Ah! Ajude a criar uma seção de intalaçao em Mac e Windows (Deus me livre! :P).


Volto já...
