# Criando-seu-Primeiro-Projeto-de-Devops-com-GitLab

Viu criar um guia detalhado para o projeto "Criando seu Primeiro Projeto de DevOps com GitLab". Neste tutorial, abordarei os seguintes tópicos:

## 1. Configurando o Ambiente

Antes de começarmos, certifique-se de ter o GitLab instalado e uma conta criada. Se você ainda não tem uma conta, pode se cadastrar gratuitamente no [GitLab](https://gitlab.com/). Agora, vamos aos passos:

### 1.1. Instalando o Git

O primeiro passo é instalar o Git em seu ambiente de desenvolvimento. O Git é uma ferramenta essencial para controle de versão. Você pode baixá-lo gratuitamente no [site oficial](https://git-scm.com/). Após a instalação, verifique a versão do Git executando o comando:

```bash
git --version
```

### 1.2. Criando um Grupo no GitLab

1. Faça login no GitLab.
2. Clique em "Groups" no menu superior e selecione "New group".
3. Preencha as informações do grupo, como nome e descrição. Lembre-se de selecionar a opção "Private" para tornar os repositórios privados.
4. Clique em "Create group".

### 1.3. Adicionando Membros ao Grupo

1. No dashboard do grupo, clique em "Members" no lado esquerdo.
2. Adicione os membros que participarão do projeto. Eles precisam ter uma conta no GitLab.

## 2. Criando o Repositório

Agora, vamos criar o repositório para o nosso projeto:

1. Acesse o grupo que você criou.
2. Clique em "New project" e escolha um nome para o projeto.
3. Selecione a opção "Private" para manter o código seguro.
4. Crie o projeto.

## 3. Definindo o Pipeline com .gitlab-ci.yml

O arquivo `.gitlab-ci.yml` é onde definimos os jobs do pipeline. Vamos criar um exemplo simples:

```yaml
# .gitlab-ci.yml

build-job:
  stage: build
  script:
    - echo "Hello, $GITLAB_USER_LOGIN!"

test-job1:
  stage: test
  script:
    - echo "This job tests something"

test-job2:
  stage: test
  script:
    - echo "This job tests something, but takes more time than test-job1."
    - echo "After the echo commands complete, it runs the sleep command for 20 seconds"
    - echo "which simulates a test that runs 20 seconds longer than test-job1"
    - sleep 20

deploy-prod:
  stage: deploy
  script:
    - echo "This job deploys something from the $CI_COMMIT_BRANCH branch."
  environment: production
```

Neste exemplo, temos quatro jobs: `build-job`, `test-job1`, `test-job2` e `deploy-prod`. Os comentários nas mensagens `echo` são exibidos na interface do GitLab quando você visualiza os jobs. As variáveis predefinidas, como `$GITLAB_USER_LOGIN` e `$CI_COMMIT_BRANCH`, são preenchidas quando os jobs são executados.

## 4. Executando o Pipeline

Após criar o arquivo `.gitlab-ci.yml`, faça um commit no repositório. O GitLab executará automaticamente os jobs definidos no pipeline. Você pode acompanhar o progresso na seção "CI/CD > Pipelines" do seu projeto.

Agora já está pronto para explorar o mundo do DevOps com o GitLab!
