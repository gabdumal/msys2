# Configuração de ambiente

O **MSYS2** é um ambiente de desenvolvimento que fornece um shell tipo bash, pacotes de software e ferramentas de compilação.

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
