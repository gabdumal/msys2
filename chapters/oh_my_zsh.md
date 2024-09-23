# Instalação do Oh My Zsh

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

O Oh My Zsh instalará vários plugins e temas por padrão.
Após a instalação, você verá uma mensagem de boas-vindas do Oh My Zsh.

Infelizmente, ele substituirá o arquivo `.zshrc` dentro da pasta `/home/[username]`, que nós editamos anteriormente.
Mas não se preocupe, o conteúdo do arquivo original será salvo em um arquivo chamado `.zshrc.pre-oh-my-zsh`.

Edite o arquivo `.zshrc` com um editor de texto qualquer.
Copie a seguinte linha e a coloque no **INÍCIO** do arquivo:

```bash
export PATH=$PATH:"/c/Program Files/Git/cmd":"/c/Program Files/Git/bin"
```

O Oh My Zsh depende do Git para funcionar corretamente, então é importante que você o defina no Path logo na **primeira** linha do arquivo.
Caso contrário, você poderá ter problemas ao abrir o terminal.

Como sempre, para atualizar as definições, feche o terminal atual e abra um novo.

---

> ➡️ [**Próximo capítulo**](/chapters/compiling_c_code.md)\
> ⬅️ [**Capítulo anterior**](/chapters/git.md)\
> 🏠 [**Página inicial**](/README.md)
