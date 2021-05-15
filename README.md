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

3. Criar o arquivo `cypress.env.json` com o conteúdo abaixo:

```json
{
    "user_name": "root",
    "user_password": "password-do-usuario-root",
    "gitlab_access_token": "access-token"
}
```
4. Acessar `http://localhost`, criar senha e logar como `root` com a senha criada

5. Substituir o valor `password-do-usuario-root` de `user_password` do arquivo `cypress.env.json` com a senha criada
    > Este arquivo não é versionado

6. Criar *access token* (`http://localhost/profile/personal_access_tokens`) com as configurações:
    - Nome: `curso-cypress-intermediario`
    - Escopo: api

7. Copiar o token e substituir o valor `access-token` de `gitlab_access_token` do arquivo `cypress.env.json` pelo token

8. Crie chave ssh com `ssh-keygen -t ed25519 -C "root@example.com"`, seguido de `~/.ssh/ead_tat_cypress_intermediario` para o nome da chave, <kbd>enter</kbd> para senha em branco e <kbd>enter</kbd> para confirmar senha em branco
    - O local da chave no windows deve ser `C:\Users\SEUNOMEDEUSUARIO\.ssh\ead_tat_cypress_intermediario`
    - `ssh-keygen` é instalado no windows junto com git

9. Copiar o output do comando `cat $HOME/.ssh/ead_tat_cypress_intermediario.pub`, acessar `http://localhost/profile/keys`, colar em `Key` e clicar em `Add Key`

## Execução dos testes

- Iniciar aplicação

```sh
docker run --publish 80:80 --publish 22:22 --hostname localhost wlsf82/gitlab-ce
```

- Executar comando de teste
    - `npm run cy:open` e escolher arquivo
    - `npm run cy:test:spec cypress/integration/path/para/arquivo.spec.js`
    - `npm run cy:test`

## Anotações do curso

### App Actions

- Comandos criados para executar ações que criam o ambiente para teste. Exemplo: para testar uma issue é necessário possuir um projeto.
- App Actions que dependem da GUI (simulam usuário):
    - Tornam os testes mais lentos
    - Acabam "testando" a GUI mesmo que não seja esse o propósito, tornando os testes que os chamam mais frágeis. Exemplo: caso a interface de criar um projeto mude vai gerar erro no teste de issue. Não que o erro seja incoerente, mas o erro não está na issue! Ao ver todos os testes quebrarem é mais difícil de identificar a causa real do erro e - pela criação de projeto ser uma funcionalidade - existe a possibilidade da frequência de modificações ser alta.
