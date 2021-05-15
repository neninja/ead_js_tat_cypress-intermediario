# ead_js_tat_cypress-intermediario

> Projeto referente a [este](https://www.udemy.com/course/testes-automatizados-com-cypress-intermediario/) curso.

## Setup inicial

1. Instalar as dependências

```sh
npm i
```

2. Iniciar aplicação

```sh
docker run --publish 80:80 --publish 22:22 --hostname localhost wlsf82/gitlab-ce
```

3. Acessar `http://localhost`, criar senha e logar como `root` com a senha criada

4. Criar *access token* (`http://localhost/profile/personal_access_tokens`) com as configurações:
    - Nome: `curso-cypress-intermediario`
    - Escopo: api
5. Copiar e salvar o token em algum arquivo temporário para depois colá-lo no lugar correto
6. Crie chave ssh com `ssh-keygen -t ed25519 -C "root@example.com"`, seguido de `~/.ssh/ead_tat_cypress_intermediario` para o nome da chave, <kbd>enter</kbd> para senha em branco e <kbd>enter</kbd> para confirmar senha em branco
    - O local da chave no windows deve ser `C:\Users\SEUNOMEDEUSUARIO\.ssh\ead_tat_cypress_intermediario`
    - `ssh-keygen` é instalado no windows junto com git
7. Copiar o output do comando `cat $HOME/.ssh/ead_tat_cypress_intermediario.pub`, acessar `http://localhost/profile/keys`, colar em `Key` e clicar em `Add Key`

## Execução dos testes

- Iniciar aplicação

```sh
docker run --publish 80:80 --publish 22:22 --hostname localhost wlsf82/gitlab-ce
```

- Abrir cypress

```sh
# usar cypress
npm run cy:open # interativo
# ou
npm run test # headless
```
