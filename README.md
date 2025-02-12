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

## Merge

Fazer o merge de uma branch na branch principal de desenvolvimento de forma segura usando o Visual Studio Code envolve alguns passos importantes. Segue o guia completo:

### Passo 1: Abra o projeto no VS Code
Certifique-se de que o repositório Git do projeto está corretamente configurado no VS Code.

### Passo 2: Garanta que você está na branch principal de desenvolvimento
1. No terminal do VS Code ou pela interface gráfica:
   - Abra o terminal.
   - Confira qual branch você está usando o comando:
     ```bash
     git branch
     ```
   - Certifique-se de que você está na branch `dev` (ou a branch principal de desenvolvimento). Caso contrário, troque para ela com:
     ```bash
     git checkout dev
     ```
     
### Passo 3: Atualize a branch `dev`
É importante ter certeza de que sua branch principal está atualizada antes de aplicar o merge:
```bash
git pull origin dev
```

### Passo 4: Faça o merge da sua branch na branch `dev`
Agora, aplique o merge da sua branch de forma segura:
1. No terminal:
   ```bash
   git merge nome-da-sua-branch
   ```
   Substitua `nome-da-sua-branch` pelo nome da branch que deseja integrar.

2. Resolva possíveis conflitos:
   - Caso ocorram conflitos, o VS Code destacará os arquivos com conflitos.
   - Na interface, você verá opções para escolher **"Aceitar mudança atual"**, **"Aceitar mudança da entrada"** ou até mesmo **"Aceitar ambas"**.
   - Após resolver os conflitos, salve os arquivos e marque-os como resolvidos com:
     ```bash
     git add <arquivo>
     ```
   - Finalize o merge com:
     ```bash
     git commit
     ```

### Passo 6: Envie as alterações para o repositório remoto
Após confirmar que o merge foi bem-sucedido e os testes estão OK, envie as alterações:
```bash
git push origin dev
```

Seguindo esses passos, você garante que o merge será feito de forma segura e rastreável. Se algo der errado, você pode sempre desfazer com:
```bash
git merge --abort
```

## Atualizar listagem de repositórios remotos

Se o VS Code ainda estiver listando branches que já foram deletadas no repositório remoto, às vezes, o Git mantém referências a branches remotos que não existem mais. Para limpar isso, execute:

```sh
git fetch --prune
```
Isso remove referências a branches que foram deletados no repositório remoto.

Se `git fetch --prune` não resolver, pode ser necessário limpar as referências armazenadas:
```sh
git remote prune origin
```
Ou, para remover referências específicas:
```sh
git remote set-url --delete origin nome-da-branch
```

## Atualizar listagem de repoisitórios locais

Se houver branches locais que foram deletadas manualmente, mas ainda aparecem na lista do VS Code, verifique se ainda há referências a eles:
```sh
git branch --list
```
Se aparecerem branches que você quer remover, exclua com:
```sh
git branch -d nome-da-branch
```
Se a branch ainda não tiver sido mesclada e quiser forçar a exclusão, use:
```sh
git branch -D nome-da-branch
```

Se você quiser excluir **todas** as branches locais do repositório (exceto a branch ativa), siga estas opções:

###*1. Excluir todas as branches locais mescladas
Se você deseja excluir apenas as branches **já mescladas**, use:
```sh
git branch --merged | grep -v '\*' | xargs git branch -d
```
- `git branch --merged` lista branches já mescladas.
- `grep -v '\*'` exclui a branch atual da lista.
- `xargs git branch -d` executa a exclusão.

### 2. Excluir todas as branches locais (mesmo as não mescladas)
Se quiser excluir **todas as branches locais**, mesmo as não mescladas, use:
```sh
git branch | grep -v '\*' | xargs git branch -D
```
- Isso **força** a exclusão das branches sem verificação de merge.

### 3. Excluir todas as branches locais, exceto 'main' ou 'master'
Caso queira manter a `main` ou `master`, use:
```sh
git branch | grep -v "main" | grep -v "master" | grep -v '\*' | xargs git branch -D
```
Isso protege a `main` e `master`, excluindo todas as outras.

> **Atenção:** Esses comandos são irreversíveis! Se houver algo importante, garanta que está commitado antes de deletar.

Por fim, exista a possibilidade do VS Code manter um cache das branches. Para forçar a atualização:

1. Feche o VS Code.
2. Execute:
   ```sh
   git status
   ```
   para garantir que o repositório está atualizado.
3. Reabra o VS Code e tente abrir a aba **Source Control (CTRL + Shift + G)** para verificar se a lista foi atualizada.

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

```bash
git stash
```
- Se esse erro aparecer após dar qualquer git pull: **Your local changes to the following files would be overwritten by merge: [arquivos]. Please commit your changes or stash them before you merge.**
