# ✅ CHECKLIST COMPLETA — Fluxo de trabalho com MkDocs, VS Code e GitHub Pages (Mac)

## 🟢 1. Ativar o MkDocs no Mac
1. Abra o Terminal.
2. Acesse a pasta onde você criou o ambiente virtual:
   cd ~
3. Ative o ambiente virtual:
   source Ambiente_Virtual_MkDocs/bin/activate
   IMPORTANTE: Sempre que for usar o MkDocs, ative o ambiente virtual primeiro!

## 🟣 2. Abrir o projeto do GDD no Visual Studio Code
1. Acesse o diretório do seu projeto:
   cd ~/GDD_Cozy_Neko_World
2. Abra o Visual Studio Code:
   code .

## 🟡 3. Editar e salvar alterações no GDD
1. Dentro do VS Code, edite os arquivos .md dentro da pasta:
   ~/GDD_Cozy_Neko_World/docs/
2. Sempre que terminar uma alteração, salve o arquivo (Cmd + S).

## 🟠 4. Visualizar alterações localmente com MkDocs
1. No terminal, execute:
   mkdocs serve
2. Abra o navegador e acesse:
   http://127.0.0.1:8000/
3. Se aparecer mensagem sobre páginas não incluídas na "nav", edite o mkdocs.yml:
   nav:
     - Início: index.md
     - Checklist: other/checklist.md

## 🔵 5. Encerrar o MkDocs
1. Para parar o servidor local, pressione Ctrl + C no terminal.
2. Depois, se quiser, desative o ambiente virtual:
   deactivate

## 🟤 6. Atualizar o GDD na sua página do GitHub Pages
1. Com o ambiente virtual ativo e na pasta do projeto, execute:
   mkdocs gh-deploy
2. Após alguns minutos, acesse sua página do GitHub Pages:
   https://seu-usuario.github.io/GDD_Cozy_Neko_World/
