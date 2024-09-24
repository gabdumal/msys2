# Configuração de ambiente Windows para desenvolvimento em C e C++ utilizando MSYS2

> [Gabriel Malosto](https://github.com/gabdumal), 2024

Este guia pretende auxiliar a configurar uma máquina Windows para desenvolvimento de software em C e C++.

## Sumário

- [Instalação do Visual Studio Code](/chapters/installing_vscode/text.md)
- [MSYS2](/chapters/msys2/text.md)
  - [Mintty](/chapters/msys2/text.md/#mintty)
  - [Atualização dos pacotes](/chapters/msys2/text.md/#atualização-dos-pacotes)
  - [Estrutura de diretórios](/chapters/msys2/text.md/#estrutura-de-diretórios)
  - [Link simbólico](/chapters/msys2/text.md/#link-simbólico)
- [Instalação do shell Zsh](/chapters/zsh/text.md)
- [Configuração do Windows Terminal](/chapters/windows_terminal/text.md)
- [Instalação do Git](/chapters/git/text.md)
  - [MSYS2 e Git](/chapters/git/text.md/#msys2-e-git)
- [Instalação do Oh My Zsh](/chapters/oh_my_zsh/text.md)
- [Compilando um programa em C](/chapters/compiling_c_code/text.md)
  - [Instalando o compilador](/chapters/compiling_c_code/text.md/#instalando-o-compilador)
  - [Compilando o programa](/chapters/compiling_c_code/text.md/#compilando-o-programa)
- [Adicionando o Visual Studio Code à Path](/chapters/vscode_to_path/text.md)
- [Compilando um projeto em C](/chapters/compiling_c_project/text.md)
- [Adicionando o MSYS2 à Path](/chapters/msys2_to_path/text.md)
- [Criando um projeto em C no Visual Studio Code](/chapters/c_project_vscode/text.md)
  - [Extensões](/chapters/c_project_vscode/text.md/#extensões)
  - [Compilando o projeto](/chapters/c_project_vscode/text.md/#compilando-o-projeto)
  - [Depurando o projeto](/chapters/c_project_vscode/text.md/#depurando-o-projeto)
    - [Compilando pela interface gráfica](/chapters/c_project_vscode/text.md/#compilando-pela-interface-gráfica)
    - [Rodando o programa pela interface gráfica](/chapters/c_project_vscode/text.md/#rodando-o-programa-pela-interface-gráfica)
    - [Configurações globais](/chapters/c_project_vscode/text.md/#configurações-globais)
- [Compilando um projeto em C++](/chapters/compiling_cpp_project/text.md)
  - [Compilando um único arquivo](/chapters/compiling_cpp_project/text.md/#compilando-um-único-arquivo)
  - [Compilando um projeto com vários arquivos](/chapters/compiling_cpp_project/text.md/#compilando-um-projeto-com-vários-arquivos)
  - [Configurando tarefa de compilação](/chapters/compiling_cpp_project/text.md/#configurando-tarefa-de-compilação)
  - [Depurando o projeto](/chapters/compiling_cpp_project/text.md/#depurando-o-projeto)
  - [Configurações globais](/chapters/compiling_cpp_project/text.md/#configurações-globais)
- [Usando o CMake](/chapters/cmake/text.md)
  - [Instalando o CMake](/chapters/cmake/text.md/#instalando-o-cmake)
  - [Extensões](/chapters/cmake/text.md/#extensões)
  - [Criando o projeto](/chapters/cmake/text.md/#criando-o-projeto)
  - [Configurando o CMake](/chapters/cmake/text.md/#configurando-o-cmake)
    - [Criando o arquivo `CMakeLists.txt`](/chapters/cmake/text.md/#criando-o-arquivo-cmakeliststxt)
    - [Versões](/chapters/cmake/text.md/#versões)
    - [Definições do projeto](/chapters/cmake/text.md/#definições-do-projeto)
    - [Configurações do ambiente](/chapters/cmake/text.md/#configurações-do-ambiente)
    - [Flags de compilação](/chapters/cmake/text.md/#flags-de-compilação)
    - [Diretórios](/chapters/cmake/text.md/#diretórios)
    - [Executável](/chapters/cmake/text.md/#executável)
    - [Incluindo o módulo](/chapters/cmake/text.md/#incluindo-o-módulo)
  - [Configurando os diretórios](/chapters/cmake/text.md/#configurando-os-diretórios)
    - [Módulo `node`](/chapters/cmake/text.md/#módulo-node)
    - [Módulo `edge`](/chapters/cmake/text.md/#módulo-edge)
    - [Módulo `graph`](/chapters/cmake/text.md/#módulo-graph)
    - [Ligando os módulos ao executável](/chapters/cmake/text.md/#ligando-os-módulos-ao-executável)
  - [Compilando o projeto](/chapters/cmake/text.md/#compilando-o-projeto)
    - [Configuração de compilação](/chapters/cmake/text.md/#configuração-de-compilação)
    - [Compilação](/chapters/cmake/text.md/#compilação)
    - [Ignorando arquivos gerados](/chapters/cmake/text.md/#ignorando-arquivos-gerados)
    - [Snippets para os arquivos `CMakeLists.txt`](/chapters/cmake/text.md/#snippets-para-os-arquivos-cmakeliststxt)
- [CMake Tools no VsCode](/chapters/cmake_tools/text.md)
  - [Compilando o projeto](/chapters/cmake_tools/text.md/#compilando-o-projeto)
  - [Executando o projeto](/chapters/cmake_tools/text.md/#executando-o-projeto)
  - [Depurando o projeto](/chapters/cmake_tools/text.md/#depurando-o-projeto)
