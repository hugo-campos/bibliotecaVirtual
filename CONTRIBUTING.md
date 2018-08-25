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

    $ mkdir -p ~/desenv/ide/android-studio; # Local de descompactação do Android Studio
    $ mkdir -p ~/desenv/ide/vscode; # Local de descompactação do Visual Code
    $ mkdir -p ~/desenv/sdk/flutter; # Local de descompactação do Flutter v0.7.0
    $ mkdir -p ~/desenv/sdk/android; # Local de descompactação do Android SDK
    $ mkdir -p ~/desenv/sdk/jdk; # Local de descompactação do JDK 1.8
    $ mkdir -p ~/desenv/projects/biblioteca-virtual/android; # Workspace do Android Studio (validação da instalação do Android Studio)
    $ mkdir -p ~/desenv/projects/biblioteca-virtual/flutter; # Local do nosso projeto

## Instalação do SDK do Java

Você vai precisar para o funcionamento do Android Studio e outras ferramentas!

### Ambiente Linux

Descompactar a versão 1.8.0_181 do java no diretório indicado abaixo: 

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

    cd ~/desenv/sdk/jdk/
    unzip jdk1.8.0_181.zip
    
Obs: Certifique-se que o diretório do java ficou assim ~/desenv/sdk/jdk/jdk1.8.0_181

E no final do arquivo ~/.bash_profile ou ~/.profile (vai depender de sua distro linux), colocar os trechos abaixo: (após edição do arquivo refazer login no linux)

    JAVA_HOME=~/desenv/sdk/jdk/jdk1.8.0_181
    export JAVA_HOME
    
    PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

## Instalação do SDK Flutter

Para essa aplicação de apredizagem iremos trabalhar com a versão DEV do Flutter, que está na versão v0.7.0.

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

#### 1 - Andriod Studio

Bom, vou começar pelo Android Studio! 

Como solicitado pelo comando 'flutter doctor', vamos no [link](https://developer.android.com/studio/index.html) fazer o download do Android Studio para começar nossa instalação.

Baixe a versão _**3.1.4 for Linux 64-bit (856 MB)**_ e comece a instalação conforme comandos abaixo.

    cd ~/desenv/ide/android-studio
    unzip ~/Downloads/android-studio-ide-173.4907809-linux.zip
    mv android-studio android-studio-ide-173.4907809-linux; # Costumo fazer isso para ter o rastro da versão do binário que eu instalei
    cd android-studio-ide-173.4907809-linux
    ./bin/studio.sh
    
Ao executar este último comando, o Android irá iniciar um wizard de instalação.

Meus passos foram:

    - Não importar nada de configurações e projetos outras versões priviamente instaladas.
    - Next
    - Custom
    - Theme: Darcula (minha prferência)
    - Marquei os componentes Android SDK, Android SDK Platform, API 28 e Android Virtual Device e por fim coloquei o diretório customizado para instalação do Android SDK em _**~/desenv/sdk/android**_.
    - Next 2x
    - Antes de finalizar ele informa que detectou que meu SO pode rodar o emulador em modo de performance acelerada e que meu linux tem suporte aceleração de maquina virtual sobre o KVM, e que mais questões sobre performance ou posso consultar a página do [link](https://developer.android.com/studio/run/emulator-acceleration?utm_source=android-studio#vm-linux).
    - Finish... wait... wait... wait... coffee.. wait... wait... coffee.. 

Após a instalação, fui testar meu ambiente Android criando uma aplicação de exemplo.
Siga-me os bons... já dizia Chapolin Colorado

    - Start a new Android Studio project
    - Application Name: "My Application", Company domain: "foo.example.com", Project location: "~/desenv/projects/biblioteca-virtual/android/MyApplication" e Next
    - Check apenas "Phone and tablet" e selecione a API 23 (Android 6.0) - (Lembre-se que só estou validando a instalação, não tenho pretenções neste momento de fazer a aplicação funcionar em vários dispositivos) e Next
    - Template: Navigaion Drawer Activity e Next
    - Activity Name: "MainActivity", Layout Name: "activity_main", Title: "MainActivity" e Next e Finish

Após a criação do projeto, e ao iniciar o Android Studio receberá o seguinte erro:

    _**Failed to find Build Tools revision 27.0.3**_
    _**Install Build Tools 27.0.3 and sync project**_

Click sobre esse link de instalação do Build Tools e siga os passo do wizard.

    - Aceite a licença, Next e Finish
    - Aguarde um pouco enquanto o Gradle baixa uns componentes do repositório e o Android Studio fazer build do seu projeto.
    - Feche o arquivo content_main.xml e reabra logo em seguida. Verá que o Android Studio vai renderizar sua seu app inicial.

Agora vamos tentar executar nosso App.

    - Click em "Run App" (no canto superior direito)
    - O android pedirá pra selecionar o dispositivo, no meu caso vou usar o emulador, pois não tenho celular conectado no USB.
    - No meu caso já veio um Virtual Device chamado "Nexus 5X API 28 x86", selecione e click em Ok
    - E foi!!! O emulador iniciou e apresentou o App.

Opa!!! Menos um erro no flutter doctor -v

    ! Doctor found issues in 4 categories.

E para saber se você pode executar seu emulador com uma perfomance melhor, click sobre o icone "AVD Manager" no canto superior direito de seu Visual Studio e edite as configurações do emulador que já veio instalado para usar o modo "Hardware - GLES 2.0" na opção Emulated Performance Graphics.

Se seu emulardor iniciar normalmente, sucesso! Você já está com uma boa performance no seu emulador.. e deve estar iniciando bem rápido. Caso contrário, será necessário configurar algumas coisas no seu SO para poder habilitar essa função! Siga esses links para tentar identificar [link1](https://developer.android.com/studio/run/emulator-acceleration?utm_source=android-studio#vm-linux) e [link2](https://www.google.com.br/search?q=android+studio+emulator+performance&oq=emulate+android+performan&aqs=chrome.1.69i57j0l2.7512j0j7&sourceid=chrome&ie=UTF-8) .

#### 2 - Android Toolchain

Eu comecei pela instalação do Android Studio porque eu já sabia que ia precisar instalar o Android SDK e que esse passo ia ser fácil de configurar em seguida.

Se observaram a mensagem de erro do flutter doctor, ele diz justamente que não achou a variárial de ambiente chamada ANDROID_HOME. Para configurar, segue:

E no final do arquivo ~/.bash_profile ou ~/.profile (vai depender de sua distro linux), coloque os trechos abaixo: (após edição do arquivo refazer login no linux)

    ANDROID_HOME=~/desenv/sdk/android
    export ANDROID_HOME

Depois de fazer logout do Linux, rode o **flutter doctor -v** novamente.

Agora ele só pede pra rodar um comamndo pra aceitar as licenças do android.

    [!] Android toolchain - develop for Android devices (Android SDK 28.0.2)
        • Android SDK at /home/hendi/desenv/sdk/android
        • Android NDK location not configured (optional; useful for native profiling support)
        • Platform android-28, build-tools 28.0.2
        • ANDROID_HOME = /home/hendi/desenv/sdk/android
        • Java binary at: /home/hendi/desenv/ide/android-studio/android-studio-ide-173.4907809-linux/jre/bin/java
        • Java version OpenJDK Runtime Environment (build 1.8.0_152-release-1024-b01)
        ! Some Android licenses not accepted.  To resolve this, run: flutter doctor --android-licenses

Execute no terminal então o comando solicitado e (y) pra tudo.

    flutter doctor --android-licenses


Logo mais vou explicar como resolver cada pendências dessas.

Se no seu ambiente você encontrou outros problemas, nos informe e mostre também como às resolver... Ah! Ajude a criar uma seção de intalaçao em Mac e Windows (Deus me livre! :P).


### Criando uma App Flutter pra validar nossa instalação

Você pode usar seu editor preferido pra criar a aplicação... Provavelmente, daqui pra frente usarei o VisualCode, mas pra validar nossa instalação vou fazer a aplicação de teste usando o Android Studio.

#### Instalando o plugin Flutter e Dart no Android Studio

    Vá no item de menu File > Settings > Plugins.
    Click em Browse repositories…, selecione o plugin Flutter e Flutter i18n e click em install.
    Também procure o plugin Dart e instale-o.
    Depois reinicie o Android Studio.

#### New project Flutter

Chagamos no ponto de criar nosso primeiro App Flutter!!!!

Acesse o menu File > New > New Flutter Project > Flutter Application e Next

    Project name: flutter_app
    Flutter SDK Path: ~/desenv/sdk/flutter/v0.7.0
    Project Location: ~/desenv/projetos/biblioteca-virtual
    Description: A new Flutter application.
    Next
    Company domain: example.com
    Finish
    Logo em seguida, pede para abrir o projeto na mesma janela ou em outra, selecionei mesma janela.
    Selecione o device emulado no canto superor direito do Android Studio e dois em Run App.
    Vair demorar um pouco a primeira vez, pois vai baixar umas dependências.

Pronto, nosso Hello World saiu!!!

--------------------------------------------------

Se não funcionou pra você, conte-nos para que possamos te ajudar.

E sinta-se a vontade para corrigir quaisquer passo deste guia!


