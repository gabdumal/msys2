# Configuração de ambiente

O **MSYS2** é um ambiente de desenvolvimento que fornece um shell tipo bash, pacotes de software e ferramentas de compilação.\
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
