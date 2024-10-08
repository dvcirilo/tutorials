---
size: 4:3
theme: default
paginate: true
_paginate: false
title: Minicurso Git
author: Diego Cirilo

---

# <!--fit--> Introdução ao Git
### Prof. Diego Cirilo

---

![bg width:90%](img/git.png)

---
# Git

- Sistema de controle de versionamento gratuito e de código livre

## Versionamento
- Gerenciamento das mudanças nos documentos, programas, sites e outras coleções de informação.
- Disponibiliza um ambiente isolado para experimentos, sem riscos para o que já funciona.
- Essencial para colaboração eficiente.

---
# Git

- Desenvolvido por Linus Torvalds (criador do Linux).
- Versão 1.0 lançada em 2005.
- Utilizado pelo kernel do Linux e outros inúmeros projetos.
- Repositórios locais e remotos.
- [Github](https://github.com) - [Gitlab](https://gitlab.com) - [BitBucket](https://bitbucket.org)

---
# Repositório
- Diretório onde as versões do código ficam armazenadas.
- Local/Remoto independentes

---
# Fluxo

![width:90%](img/git-flow.png)

---
# Instalação

- [Windows](https://git-for-windows.github.io/)
- [Demais sistemas](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git)

---
# Configuração de usuário

```sh
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@email.com"
```
- Verificando as configurações feitas:
```sh
git config --list
```

---
# Inicializando/clonando um repositório

- Em qualquer diretório de projeto (ou novo): `git init`

- Repositórios remotos existentes: 
`git clone https://github.com/exemplo/repositorio`

---
# Status

- Para verificar o status de um repositório:
`git status`

- Para verificar o histórico de um repositório
`git log`
- Há várias opções para visualização do log, ex.:
`git log --pretty=oneline --graph`

---
# Fluxo dos arquivos

![width:90%](img/git-file.png)

---
# Adicionando arquivos
- Podemos adicionar arquivos não acompanhados (untracked) e arquivos modificados.
`git add arquivo`

- Para adicionar todos os arquivos do diretório:
`git add *`

---
# *Commits*
- O commit é o momento onde *salvamos* o repositório.
- Após adicionar um arquivo para o index (git add) podemos fazer o commit.
- O commit precisa de uma mensagem descrevendo as modificações.
- O ideal é que os commits tenham um escopo bem definido, facilitando o entendimento da mensagem.
`git commit`
- Para já incluir a mensagem:
`git commit -m "Mensagem de commit"`

---
# Prática
- Inicialize um repositório em um diretório vazio.
- Crie um arquivo `exemplo.txt` no repositório criado anteriormente.
- Verifique o status do repositório `git status`
- Adicione o arquivo ao index:
`git add exemplo.txt`
- Verifique o status do repositório `git status`
- Faça o commit do arquivo: `git commit`
- Verifique o status do repositório `git status`

---
# Verificando diferenças
- Podemos verificar o que foi modificado no repositório com:
`git diff`
- Para um arquivo específico:
`git diff arquivo`
- Ou commits diferentes:
`git diff COMMIT`

---
# Removendo arquivos
- Para remover arquivos de um repositório:
`git rm arquivo`

---
# Desfazendo modificações
- Para modificar um commit recente (mensagem errada, esquecimento de arquivos)
`git commit --amend`
- Removendo do index:
`git reset HEAD arquivo`
- Desfazendo modificações em arquivo não comitado:
`git checkout -- arquivo`

---
# Gitignore
- Existem arquivos nos projetos que **não devem** ser versionados
- Ex. bancos de dados, configurações locais, ambientes virtuais, senhas, etc.
- Para garantir que esses arquivos não entrem no projeto, seu nome deve estar em um arquivo `.gitignore` na raiz no repositório.
- Ex.
```
venv
db.sqlite3
```

---
# Branches
- Os *branches* ou ramos, são versões alternativas de um projeto.
- Podem ser utilizados para implementação de novas funcionalidades sem arriscar o que já funciona.
- O branch padrão é o `master` ou `main`
- Para criar um novo branch:
`git branch nome`

---
# Navegando versões/branches
- Para mudar o branch:
`git checkout nome-do-branch`
- O mesmo funciona para commits:
`git checkout 7ab839a`

---
# Merge
- Quando o trabalho em um branch deve ser adicionado a outro branch, fazemos um `merge` no branch de destino:
`git merge branch-origem`

---
# Prática
- https://git-school.github.io/visualizing-git/

---
# Conflitos
- Quando arquivos são modificados em dois locais diferentes, é necessário mesclar essas modificações.
- O Git consegue fazer *quase* tudo automaticamente.
- Quando há um conflito, você será avisado no merge, e os arquivos com problema terão as seguintes indicações:
```
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```

---
# Conflitos
- Após resolver os conflitos (apagando as indicações `<<< === >>>` no código), devemos fazer um novo commit.

---
# Removendo branches
`git branch -d branch`

---
# Repositórios Remotos
- Para listar os remotos:
`git remote -v`
- Para adicionar um remoto:
`git remote add nome-do-remoto url`
- Para mudar a URL de um remoto:
`git remote set-url nome-do-remoto url`
- Normalmente o nome do remoto padrão é `origin`

---
# Pull/Push
- Para receber as modificações do repositório remoto:
`git pull nome-do-remoto nome-do-branch`

- Para enviar nossas modificações para o remoto:
`git push nome-do-remoto nome-do-branch`

- Convém sempre realizar um pull antes de um push para garantir o merge local.

---
# Criando um repositório no Github
- [Github](https://github.com/new)

---
# Forks
- Forks são cópias de repositório no Github.
- Aplicado no seu user.

---
# Fluxo de colaboração
- Devemos criar um fork de uma aplicação que queremos contribuir.
- No nosso repositório local, devemos criar um remote para o repositório original, normalmente chamando de `upstream`
- Fazemos o fluxo de desenvolvimento normal, e quando necessário realizamos um pull request no repositório original.

---
# Arquivos Indesejados
- Devemos ter cuidado para não fazer *commit* de arquivos indesejados/sensíveis.
- Ambientes virtuais, senhas, chaves, dados de configuração restritos, etc.
- É importante configurar o `gitignore` no início do projeto para evitar falhas.
- Caso senhas, chaves ou segredos tenham sido enviados para o Github, devem ser imediatamente alterados!

---
# Arquivos Indesejados
- Para remover os arquivos indesejados podemos usar o `git-filter-repo`
- É um *script* *Python* - [link](https://github.com/newren/git-filter-repo)
- [Guia de uso](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#using-git-filter-repo)

---
# Referências
- https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
- http://coral.ufsm.br/pet-si/wp-content/uploads/2017/02/Consult%C3%B3rio-de-Software-Git.pdf
- https://githowto.com/history
- https://rogerdudler.github.io/git-guide/index.pt_BR.html
- https://www.atlassian.com/git/tutorials/setting-up-a-repository
