# Configuração de ambiente

Este guia pretende auxiliar a configurar uma máquina Windows para desenvolvimento de software em C e C++.

## Editor de texto

A fim de escrever código, você precisará de um editor de texto apropriado.
É interessante que ele seja voltado para o desenvolvimento de software, com funcionalidades como _syntax highlighting_, _code completion_, _debugging_, etc.

O **Visual Studio Code** é um editor de texto muito popular entre desenvolvedores.
Ele é leve, rápido e possui uma grande quantidade de extensões que facilitam o desenvolvimento de software.
Você pode fazer seu download em [https://code.visualstudio.com/](https://code.visualstudio.com/).
Execute o instalador e siga as instruções.

## Compilador

O **MSYS2** é um ambiente de desenvolvimento que fornece um shell tipo bash, pacotes de software e ferramentas de compilação.

Ele habilita um ambiente Unix-like no Windows.
O Linux é um exemplo de sistema operacional Unix-like, que é muito utilizado para desenvolvimento de software.
Mas perceba que o MSYS2 não é um emulador de Linux, ele apenas oferece um ambiente de desenvolvimento similar ao Linux, que facilita a instalação de ferramentas.

Faça o download do instalador do MSYS2 em [https://www.msys2.org/](https://www.msys2.org/).\
Execute o instalador e siga as instruções.
Durante a instalação, você pode escolher o diretório de instalação, mas o padrão é `C:\msys64`.

O MSYS fornece vários ambientes de desenvolvimento, como explicado pela [documentação oficial](https://www.msys2.org/docs/environments/).
O que vamos usar é o MSYS2 **Clang64**, que é um ambiente de desenvolvimento baseado no Clang e no LLVM.

**Clang** é um compilador C, C++, Objective-C e Objective-C++ de código aberto, que é parte do projeto LLVM. Outro compilador muito conhecido é o _GCC_.
Já **LLVM** é uma infraestrutura de compilador que é usada para construir compiladores para várias linguagens de programação.

## Configurações iniciais

Após a instalação, abra o programa **MSYS2 CLANG64**, disponível no menu Iniciar.

Ele abre o emulador de **terminal** padrão do MSYS2, que é o **Mintty**, que é baseado no terminal _xterm_.
Um emulador de terminal é um programa que permite que você interaja com o computador por meio de comandos de texto.

Essa interação é feita por meio de um **shell**, que é um programa que interpreta comandos e executa programas.
O shell padrão do MSYS2 é o **bash**, que é muito popular no Linux.

Dentro do Mintty, nós podemos executar comandos específicos do MSYS2.
Ele é um ambiente **Unix-like**, então muitos comandos são similares aos do Linux.
Por exemplo, para listar os arquivos de um diretório, usamos o comando `ls`.

## Atualização dos pacotes

O MSYS2 disponibiliza um gerenciador de pacotes chamado **pacman**.
Ele é usado para instalar, atualizar e remover pacotes de software.

Primeiramente, vamos atualizar o banco de dados de **pacotes** do MSYS2.
Execute o comando abaixo no terminal Mintty:

```bash
pacman -Syu
```

O shell perguntará se você deseja proceder com o processo.
Digite `Y` e pressione `Enter`.

Ao concluir, ele o pedirá para reiniciar o MSYS2.
Novamente, digite `Y` e pressione `Enter`.

Abra o MSYS2 CLANG64 novamente.
Agora vamos de fato **baixar** os pacotes atualizados.
Antes, havíamos apenas buscado as informações sobre os pacotes disponíveis.
Digite o comando abaixo:

```bash
pacman -Su
```

Confirme a instalação dos pacotes digitando `Y` e pressionando `Enter`.

## Estrutura de diretórios

O MSYS2 cria uma pasta no seu disco `C:` chamada `msys64`.
Ela simula um ambiente Unix-like, com diretórios como `/bin`, `/home`, `/usr`, etc.

Além disso, é neste diretório que você encontrará os executáveis de cada ambiente disponibilizado pelo MSYS2.
Lembre-se: estamos utilizando o CLANG64, mas há outros ambientes disponíveis, caso você precise.

O diretório `/home` cria uma pasta para cada usuário do subsistema MSYS2.
Inicialmente, você verá apenas uma pasta dentro dela, que é o seu usuário do Windows.
Vamos nos referir a ele como `[username]`.
Então, o caminho completo para a pasta do seu usuário é `C:\msys64\home\[username]`.

Dentro dessa pasta, ficarão todos os arquivos de configuração do shell e de outros programas que você virá a instalar no MSYS2.

Além disso, todos os arquivos que você queira usar dentro do MSYS2, incluindo projetos que você queira desenvolver, devem ser colocados dentro de `/home/[username]`.

Todas vez que você inicia o MSYS2 CLANG64, ele abre o terminal Mintty no diretório `/home/[username]`.
Por enquanto, há apenas os arquivos de configuração do shell.
Você pode listá-los com o comando `ls --all`.

Para ajudar na organização, vamos criar um diretório chamado `dev` dentro de `/home/[username]`.
Dentro dele, você pode colocar todos os seus projetos de desenvolvimento.

```bash
mkdir ~/dev
```

Esse `~` é um atalho de linha de comando, que representa o caminho até seu diretório `/home/[username]`.
Você pode usá-lo para se referir a este diretório em qualquer lugar do subsistema MSYS2.

Se você listar o conteúdo do diretório novamente, verá que o diretório `dev` foi criado.
O comando `ls` lista o conteúdo de um diretório, e o argumento `--all` (executado como `ls --all`) faz com que ele liste todos os arquivos, incluindo os ocultos.

## Instalação de pacotes

Vamos trocar o shell do MSYS2 para o **zsh**, que é um shell mais moderno e poderoso que o bash.

Para isso, execute o comando abaixo no terminal do MSYS2:

```bash
pacman -S zsh
```

Agora precisamos definir o **zsh** como o shell padrão.
Para isso, precisamos definir uma nova variável de ambiente, chamada `SHELL`.
Uma variável de ambiente é um valor que contém alguma informação sobre o ambiente do sistema, e que frequentemente é utilizada por programas.

- Pesquise no menu Iniciar por **Editar as variáveis de ambiente do sistema**.
- Clique em **Variáveis de ambiente**.
- Na janela que abrir, há duas tabelas: `Variáveis de usuário para [username]` e `Variáveis do sistema`.
  - Na tabela de `Variáveis de usuário`, clique em **Novo...**.
    - No campo **Nome da variável**, digite `SHELL`.
    - No campo **Valor da variável**, digite o caminho do executável do zsh, que é `C:\msys64\usr\bin\zsh.exe`.
    - Clique em **OK**.

Aproveitando que estamos aqui, vamos adicionar o diretório do executável do MSYS2 ao **Path**.
O Path é uma variável de ambiente que contém uma lista de diretórios onde o sistema procura por executáveis.

Para que você possa rodar qualquer comando do MSYS2 de qualquer diretório, é necessário adicionar o diretório do executável ao PATH.

- Na tabela de `Variáveis de usuário`, clique em **Path** e depois em **Editar...**.
- Clique em **Novo** e adicione o caminho `C:\msys64\usr\bin`.
- Clique em **OK**.

Agora, feche o terminal atual e abra um novo, ainda do MSYS2 CLANG64.

Você verá uma mensagem de boas-vindas do zsh.
Ele te guiará por um processo de configuração inicial.
Sinta-se à vontade para configurar como desejar.

![alt text](zsh-welcome.png)

Para navegar pelas opções, você deve digitar o número ou letra correspondente à opção desejada e pressionar `Enter`.
A fim de configurar, pressione `1` e `Enter`.

A seguinte sequência de teclas pode ser usada para fazer uma configuração padrão: `10213041u2s00`.

## Windows Terminal

Nós podemos configurar o **Windows Terminal** para abrir no ambiente MSYS2 CLANG64, como mostrado na [documentação oficial](https://www.msys2.org/docs/terminals/).

Para isso, abra o Windows Terminal e acesse as **configurações**.
Na barra inferior, clique em **Abrir o arquivo JSON**.
Este arquivo define todas as configurações do Windows Terminal.
Nós desejamos adicionar um novo perfil para o MSYS2 Clang64.

Encontre a chave `"profiles"`.
Ela contém duas chaves:

- `"defaults"`: define as configurações padrão para todos os perfis.
- `"list"`: contém a lista de perfis, definida pelos colchetes `[]`.
  Cada perfil dentro deles é um objeto JSON que contém várias configurações, como nome, ícone, fonte, esquema de cores, etc.

Abaixo definimos um novo perfil, chamado `CLANG64 / MSYS2`, que abre o MSYS2 Clang64 no diretório do usuário.
Copie **APENAS** o objeto JSON abaixo e cole dentro do array `"list"`.

```json
{
  "guid": "{07b52e3e-de2c-5db4-bd2d-ba144ed6c273}",
  "name": "CLANG64 / MSYS2",
  "commandline": "C:/msys64/msys2_shell.cmd -defterm -here -no-start -clang64 -shell zsh",
  "icon": "C:\\msys64\\clang64.ico",
  "startingDirectory": "C:/msys64/home/%USERNAME%"
}
```

Salve o arquivo e feche o Windows Terminal.

Agora, abra o Windows Terminal novamente e você verá um novo perfil chamado `CLANG64 / MSYS2`.
Clique nele e você abrirá o MSYS2 Clang64 no diretório do usuário.

Você pode definir este perfil como padrão,.
Acesse as **Configurações** do Windows Terminal, clique em **Inicialização** e, no campo **Perfis padrão**, selecione o perfil `CLANG64 / MSYS2`.

Sinta-se à vontade para personalizar o perfil como desejar.

## Git

O **Git** é um sistema de controle de versão distribuído.
Ele é muito utilizado para controle de versão de código fonte e colaboração em projetos de software.

O Git é focado em sistemas Unix-like.
Para usá-lo no Windows, é necessário instalar uma versão específica chamada, veja só, **Git for Windows**.
Você pode baixar o instalador pelo site [https://gitforwindows.org/](https://gitforwindows.org/).

Execute o instalador e siga as instruções.
Durante a instalação, você pode escolher o diretório de instalação, mas o padrão é `C:\Program Files\Git`.
Quando perguntado sobre o editor de texto padrão, você pode escolher o **Visual Studio Code**, caso o tenha instalado.

Na sessão **Adjusting the name of the initial branch in new repositories**, você pode escolher o nome da branch padrão.
Recomendo selecionar a opção **Override the default branch name for new repositories** e digitar `main`, uma vez que este é o padrão adotado pelo _GitHub_.

Nas próximas sessões, pode manter as opções padrão, até a **Configuring extra options**, em que recomendo marcar também a caixa **Enable symbolic links**.

O Git for Windows configura automaticamente a Path para seu executável.
De todo modo, caso você tenha problemas, você pode adicionar o diretório do executável do Git ao Path, como fizemos com o MSYS2.

Clique em **Editar...** a variável **Path**.
Dessa vez, adicione duas novas entradas a ela: `C:\Program Files\Git\cmd`, e `C:\Program Files\Git\bin\git.exe`.

Para testar se a instalação foi bem-sucedida, abra o PowerShell e execute o comando:

```bash
git --version
```

Se tudo estiver correto, você verá a versão do Git instalada, como `git version 2.46.0.windows.1`, por exemplo.

### MSYS2 e Git

A Path do Git for Windows não é reconhecida por padrão pelo terminal do MSYS2.
Para resolver isso, nós teremos que editar o arquivo de configuração do zsh.
Ele é um arquivo chamado `.zshrc` e fica no diretório do usuário dentro do subsistema MSYS2. Seu caminho é `C:\msys64\home\[username]`.

Essa pasta guardará vários arquivos de configuração de programas que você utilizará no MSYS2.
Caso você encontre algum problema, é possível que a solução esteja em um desses arquivos.

Abra o arquivo `C:\msys64\home\[username]\.zshrc` com um editor de texto qualquer.
Adicione a linha abaixo ao **final** do arquivo:

```bash
export PATH=$PATH:"/c/Program Files/Git/cmd":"/c/Program Files/Git/bin"
```

Note que o caminho está escrito com barras normais (`/`), e não invertidas (`\`).
A forma de escrever o caminho de arquivos é diferente em sistemas Windows e Unix-like.

Salve o arquivo e feche o editor.
**Feche** o terminal atual e abra um novo.
Agora faça o teste do Git novamente.
Se tudo estiver correto, você verá a versão do Git instalada.

O que nós fizemos foi dizer para o shell zsh que ele deve procurar os executáveis do Git nos diretórios `C:\Program Files\Git\cmd` e `C:\Program Files\Git\bin`.
Você pode precisar fazer isso para outros programas que você instalar no MSYS2 no futuro.

## Oh My Zsh

Eu disse que o zsh é um shell mais moderno e poderoso que o bash.
Mas ainda não expliquei por quê.
A resposta é que ele é altamente _customizável_ e _extensível_, graças a uma grande quantidade de _plugins_ e _temas_ disponíveis.

O **Oh My Zsh** é um framework para gerenciar a configuração do zsh.
Suas instruções de instalação estão disponíveis no seu [repositório no GitHub](https://github.com/ohmyzsh/ohmyzsh).

Neste link, você encontrará o comando de instalação.
Execute-o no terminal do MSYS2.

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Depois

Ensinar link simbólico

```bash
ln -s /c/Users/[username]/dev ~/dev
```
