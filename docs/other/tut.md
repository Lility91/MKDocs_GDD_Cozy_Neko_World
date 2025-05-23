# Como editar o documento

O mkdocs utiliza a sintaxe markdown para criação e edição das páginas. Para criar uma nova página basta criar um arquivo, através do Visual Studio Code, com a extensão md (botão direito na pasta da estrutura de arquivos, new, file e dê o nome e coloque a extensão .md).

Para saber mais sobre a formatação markdown, [clique aqui](https://www.markdownguide.org/basic-syntax/). 

Para consultar a documentação oficial do mkdocs, [clique aqui](https://www.mkdocs.org/)

## Título

Os títulos são escritos com o cerquilho (#) sendo que:

```md
# para título 1
## para título 2
### para título 3
#### para título 4
##### para título 5
```

## Parágrafos

Todos os parágrafos devem ter uma linha entre eles, entre listas e imagens, por exemplo, o texto abaixo:

```md
Este é o primeiro parágrafo.
Este é o segundo parágrafo.
```

Será impresso assim:

Este é o primeiro parágrafo.
Este é o segundo parágrafo.

## Listas

Listas não ordenadas são criadas utilizando o hífen. O exemplo abaixo é formatado desta forma:

```md
- Item 1
- Item 2
- Item 3
```

É exibido desta forma:

- Item 1
- Item 2
- Item 3

Listas ordenadas podem ser criadas utilizando o número na frente do elemento:

```md
1. Item 1
2. Item 2
3. Item 3
```

Exibe:

1. Item 1
2. Item 2
3. Item 3

## Tabelas

Sintace:

```md
| Head 1 | Head 2 | Head 3 |
| ------ | ------ | ------ |
| Item 1 | Item 2 | Item 3 |
| Item 4 | Item 5 | Item 6 |
| Item 7 | Item 8 | Item 9 |
```

Sendo exibida assim:

| Head 1 | Head 2 | Head 3 |
| ------ | ------ | ------ |
| Item 1 | Item 2 | Item 3 |
| Item 4 | Item 5 | Item 6 |
| Item 7 | Item 8 | Item 9 |

## Links (âncoras)

Links são criados com a seguinte sintaxe:

```md
[Texto de exibição](url do caminho)
```

Por exemplo, para acessar o site do Senac ficaria:

```md
[Senac](https://www.sp.senac.br/)
```

Seria exibido:

[Senac](https://www.sp.senac.br/)

## Imagens

Sintaxe:

```md
![Alt da imagem](url do caminho local ou externa)
```

Exemplo:

```md
![Exemplo de imagem local](../img/sonic_feio.jpg | 200px)

![Exemplo de imagem externa](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbkiAGkj63gvkYUlAJGE-fSnqax1zIIW1QPatBouVPQrKMAU79Vqq7YvA7Wpu5Xng2nWgHPFdgwBRR1f7FMXrnmOjWgGzRTzn4Q26UfYzs5OdoiaSSexOXr85TcYdEdeio9GIu7YrmVCsZ/s1600/super+mario+real.jpg)
```

Resultado:

![Exemplo de imagem local](../img/sonic_feio.jpg)

![Exemplo de imagem externa](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbkiAGkj63gvkYUlAJGE-fSnqax1zIIW1QPatBouVPQrKMAU79Vqq7YvA7Wpu5Xng2nWgHPFdgwBRR1f7FMXrnmOjWgGzRTzn4Q26UfYzs5OdoiaSSexOXr85TcYdEdeio9GIu7YrmVCsZ/s1600/super+mario+real.jpg)

O problema dessa abordagem é que Markdown não suporta ajuste de tamanho de imagem, sendo necessário utilizar html no lugar:

```html
<img src="/img/sonic_feio.jpg" width="200">
```

Resultando em:

<img src="/img/sonic_feio.jpg" width="200" alt="Exemplo de imagem local com HTML">

O problema de usar a sintaxe HTML é que essa informação não é transmitida para o mkdocs quando está convertendo para PDF com mkdoks-to-pdf. Quando precisar que a imagem vá para o PDF, recomenda-se trabalhar a imagem no tamanho correto antes de inserir no documento e, se necessário, considerar deixar bordas transparêntes nas laterais.

Para ajustar o tamanho de imagem diretamente pelo Markdown, é necessário instalar alguns plugins. Por exemplo, o Pandoc, ou o Krandown, que permitem ajustar a figura com a sintaxe abaixo:

```md
Pandoc: ![Exemplo de imagem local](../img/sonic_feio.jpg){width=250}
Krandown: ![Exemplo de imagem local](../img/sonic_feio.jpg){: width=250}
```

## Transformando em um projeto HTML

Se desejar, após a construção do documento, é possível transformar o projeto em um projeto HTML.

Navegue, via terminal, até a pasta onde está o arquivo mkdocs.yml. Digite ```mkdocs build``` e uma pasta chamada ```site``` será gerada. Nessa pasta todo o conteúdo me foi convertido em HTML + CSS + JavaScript.

## Criando um PDF a partir de um mkdocs

Para criar um PDF são necessários alguns passos mais avançados, mas uma vez configurados, pode-se gerar quantos PDFs quiser para qualquer projeto novo do mkdocs na mesma instalação da máquina.

As dependências necessárias são:

- mintty (através do msys2)
- cairo
- pango
- gdk-pixbuf2
- glib2
- weasyprint
- mkdocs-to-pdf

#### Instalando o mintty:
- Baixe o msy2 do site [https://www.msys2.org/](https://www.msys2.org/)
- Instale a versão correta para o sistema operacional (estará na opção 1: Download the installer)
- Faça a instalação padrão dele.


#### Instalando o cairo, pango, gdk-pixbuf2 e glib2
Abra o terminal do mintty (MSYS2 MINGW64) e entre com os comandos:

Atualizar o mintty:

```
pacman -Syu
```

Instalar o cairo:

```
pacman -S mingw-w64-x86-cairo
```

Instalar o pango:

```
pacman -S mingw-w64-x86-pango
```

Instalar o gdk-pixbuf2

```
pacman -S mingw-w64-x86-gdk-pixbuf2
```

Instalar o glib2

```
pacman -S mingw-w64-x86-glib2
```

Após a instalação dos pacotes, feche a janela do mintty.

#### Configurando as variáveis de ambiente
Configure as variáveis de ambiente para que essas bibliotecas fiquem acessíveis ao weasyprint. Os passos para o Windows estão abaixo:

- Abra as variáveis de ambiente e, em variáveis do sistema, crie uma nova variável.
- Para o nome da variável digite: ```WEASYPRINT_DLL_DIRECTORIES```
- Para o valor, será incluída a pasta bin da instalação do mintty. Geralmente ela fica em: ```C:\msys64\mingw64\bin```.

Feito isso, clique em ok e feche a janela.

#### Instalando o weasyprint

Abra o terminal no modo de administrador e digite:

```python
pip install weasyprint --upgrade
```

#### Instalando o mkdocs-to-pdf

Ainda no terminal com o modo de administrador:

```python
pip install mkdocs-to-pdf
```

No seu projeto mkdocs, abra, no Visual Studio Code, o arquivo ```mkdocs.yml``` e adicione a dependência do plugin:

```
plugins:
    - to-pdf:
```

Agora, quando rodar o ```mkdocs build```, um PDF será criado junto com o site.
