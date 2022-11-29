# Tutorial Git

Esse tutorial fiz com base em um curso da Udemy. Todos os comandos estão mastigados.

- https://www.udemy.com/course/git-e-github-do-basico-ao-avancado-c-gist-e-github-pages/

# Fundamental

Aqui estarão os conceitos FUNDAMENTAIS, praticamente obrigatórios para um programador.

## Preparo

Para enviar um repositório, ele precisa de pelo menos 1 arquivo.

```bash
git init
```

- Inicia um reposítorio na pasta pro git funcionar. É criado um arquivo oculto .git dentro do projeto. É o começo de tudo. Sem esse comando, não dá pra trabalhar com nada no git.


```bash
git add <nome do arquivo incluindo formato>
git add .
```

- Prepara o arquivo escolhido pro git (seleção individual) ou prepara TODOS os arquivos da pasta pro git usando o ponto '.'. (seleção múltipla)

```bash
git commit (-a) -m "first commit"
```
- Envia os arquivos adicionados ou modificados para o repositório **LOCAL** do git. 
- -m é uma flag de mensagem. 
- -a envia todos do diretório, comando opcional.

## Linkagem do rep Local com rep Remoto

```bash
git branch -M main
git branch -M master
```

- Criação de uma branch (ramificação) main/master **LOCAL** e **REMOTO** ao mesmo tempo. É onde o código será commitado.
- branch *master* para definir a ramificação principal caiu em desuso por convenção. Usa-se *main* atualmente.

```bash
git remote add origin https://github.com/USUARIO/NOMEDOREPOSITORIO.git
```

- Linkagem e sincronização do repositório **Local** e **Remoto** e preparo para envio para o github (repositório remoto).
- *Origin* é um termo que a comunidade usa por convenção. Não é recomendada a sua alteração.

## Envio e Recebimento

```bash
git push -u origin main
git push
```
- Envio definitivo para o repositório remoto (github).
- O primeiro comando serve pra dizer pra qual branch vai o envio. No primeiro push, é obrigatório seu uso.
- O segundo comando se usa quando o primeiro já foi utilizado pelo menos 1 vez.
> Nota: se utilizar o comando --rebase, é interessante reutilizar o primeiro comando.

```bash
git pull
```

- Traz um repositório remoto para o repositório local com todos os dados do repositório remoto, incluindo ramificações, rollbacks e outros dados mais avançados.
- Também atualiza um repositório local.
> Nota: sempre antes de iniciar um projeto a partir de um repositório, evitar commitar algo. Dar um pull antes de programar qualquer coisa é uma boa prática.

## Resumo

- **OBRIGATÓRIO:** *git init* - inicia o git em uma pasta
- **OBRIGATÓRIO:** *git add .* - seleciona arquivos para preparo de envios pro git (intermediador)
- **OBRIGATÓRIO:** *git commit -m "alteração"* - envia pro git (intermediador)
- SITUACIONAL: *git branch -M main* - Cria uma ramificação main
- SITUACIONAL: *git remote add origin https://github.com/USUARIO/NOMEDOREPOSITORIO.git* - Sync com o github
- **OBRIGATÓRIO:** *git push -u origin main* - Envio definitivo do repositório local (intermediador) pro repositório do github (destinatário)
- **OBRIGATÓRIO:** *git pull* - TRazer repositório remoto pro local com dados importantes do projeto.


# Situacionais

Aqui estarão os conceitos SITUACIONAIS, geralmente usados para se trabalhar em equipe ou em projetos maiores de empresas.

## Diagnóstico

```bash
git status
```
- Verifica alterações e erros

```bash
git log
```
- É um git status com steroids. Ele mostra as últimas alterações do projeto.

## Manipulação de repositórios

```bash
git clone https://github.com/USUARIO/NOMEDOREPOSITORIO.git (.)
```

- Parecido com pull, mas "baixa" um repositório inteiro (clona) pra máquina.
- Usado para quando não sabemos a origem do repositório.
- Muito usado quando se está entrando em um projeto novo.
- '.' é usado pra clonar pro diretório atual do terminal.
> Nota: parece com pull, mas a diferença é que copia o repositório (clona) pra máquina, porém não traz consigo rollbacks, ramificações, dados avançados, etc.

```bash
git rm (.)
```
- Similar ao comando linux, deleta arquivos locais e não terá mais atualizações consideradas pelo git.
- O '.' é para deletar todos os arquivos do repositório local.

```bash
git mv <nome do arquivo> <diretório a ser movido/nome do arquivo>
```
- Similar ao comando linux, move ou muda o nome de um arquivo, e isso é monitorado pelo git
- O arquivo "anterior" é excluido. É como se fosse Ctrl+X.

```bash
git ignore
```
- Lista todos os arquivos e pastas que devem ser ignorados pelo git.

## Branch e commit

```bash
git checkout <diretório do arquivo/nome do arquivo>
```
- O arquivo modificado retoma ao estado original (onde está no repositório)

```bash
git checkout <branch>
```
- Muda a branch pra alguma que você quer. Esemplo: main e beta. Se você está na main e deseja ir pra beta, basta usar 'git checkout beta'

```bash
git merge <branch>
```
- Traz alterações de uma branch para a branch que você tá atualmente. Exemplo: main e beta. Se você estiver na main e der um 'git merge beta', tudo que estiver na beta vai pra main.

```bash
git branch -d <branch>
```
- Deleta uma branch a sua escolha **LOCAL**.

```bash
git push -d origin <branch>
```
- Deleta uma brnach a sua escolha **REMOTA**.


```bash
git reset (--hard)
```
- Todas as alterações commitadas e pendentes serão excluídas. A flag --hard origin/main


# TROUBLESHOOTING

```bash
git pull --rebase origin main
```
- Se esse erro aparecer após dar qualquer git push: **"error: failed to push some refs to [link do repositório]"**

```bash
git reset --hard
```
- Se esse erro aparecer após dar qualquer git pull: **"error: Your local changes to the following files would be overwritten by merge: [arquivos]"**

```bash
git clean -d -f
git pull origin main
```
- Se esse erro aparecer após dar qualquer git pull: **The following untracked working tree files would be overwritten by merge: [arquivos]. Please move or remove them before you merge.**
