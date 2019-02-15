# DevOpsLab-Pipeline
Demo para a criação de uma Pipeline DevOps usando uma aplicação "Hello World" Python/Flask fazendo deploy no Heroku.

## Pré-Requisitos

Para fazer o laboratório você precisará ter:
- Conta no GitHub - https://github.com
- Conta no PythonAnywhere  caso você não tenha git na máquina -  https://www.pythonanywhere.com
- Conta no Travis-CI - https://travis-ci.com
- Conta no Heroku - https://dashboard.heroku.com/apps
- Conta no SonarCloud - https://sonarcloud.io

## Fluxo do Lab 

1. Vamos criar um Repositório no GitHub e subir uma aplicação "Hello World" em Python/Flask
2. Vamos criar uma Pipeline no Travis-CI para fazer o Teste, Build e Deploy da nossa aplicação no Heroku
3. Vamos criar uma APP no Heroku para hospedar nossa aplicação "Hello World"

## Roteiro

**Pré-Lab** 

1) Clone o Repositório do Laboratório com todos os arquivos que iremos usar:
```
$ git clone https://github.com/gabydias/lab-campusparty2019.git
```

**GitHub** 

2) Criar um Repositório para sua aplicação "Hello World" no GitHub
3) Opcional: Criar um Projeto no GitHub padrão Kanban para planejar seu Projeto
4) Opcional: Colocar os Cards do que faremos no Lab 

	a) Criar App Python
	
	b) Criar Teste Unitário
	
	c) Criar Pipeline no Travis
	
	d) Fazer Deploy no Heroku
	
	e) Criar Integração com o Sonar

5) Clonar o Repositório da sua aplicação "Hello World" para começar a programar. 

** Vamos considerar aqui que após clonar você tem uma pasta chamada   *helloworld* , ou seja, toda vez que ver a pasta *helloworld* nos comandos troque para o nome do seu repositório.

6) Copiar os arquivos da App Python para dentro do seu repositório

```
$ cp -a lab-campusparty2019/app/*  helloworld
```

7) Realizar um Commit e enviar os novos arquivos para o GitHub

```
$ git status
$ git add .
$ git commit -m "First Commit - Python App"
$ git push origin master
```

**Travis-CI**

8) Acessar o Travis-CI e conectar ao Repositório do Lab
9) Criar o Arquivo Travis.yml usando o modelo travis.yml.0

```
$ cp -a lab-campusparty2019/travis/travis.yml.0  helloworld/.travis.yml
```

10) Fazer o commit e push do novo arquivo e acompanhar o build no Travis-CI (*é esperado dar erro*)
```
$ git status
$ git add .
$ git commit -m "Add Travis-ci Pipeline"
$ git push origin master
```

**Teste Unitário** 

11) Inserir o arquivo test.py na raiz do seu repositório 
```
$ cp -a lab-campusparty2019/test.py  helloworld/
```
12) Substituir o arquivo do travis com o travis.yml.1 inserindo a seção de teste na hora do build

```
$ cp -a lab-campusparty2019/travis/travis.yml.1  helloworld/.travis.yml
```

13) Fazer o commit e  push e acompanhar o build no Travis (*é esperado dar sucesso*)

```
$ git status
$ git add .
$ git commit -m "Add Unittest"
$ git push origin master
```

**Heroku**

14) Acesse sua conta no Heroku e crie um APP. Lembrando que o nome do APP tem que ser único.

15) Copiar os arquivos Procfile e runtime.txt necessários para realizar o deploy no Heroku na raiz do seu repositório.

```
$ cp -a lab-campusparty2019/heroku/*  helloworld/
```

16) Configurar o Travis-CI para fazer deploy no Heroku após build com sucesso. Para isso:

a) Substituir o arquivo do travis com o travis.yml.2 inserindo a seção de deploy após o build
```
$ cp -a lab-campusparty2019/travis/travis.yml.2  helloworld/.travis.yml
```

b) Alterar o nome da APP no arquivo .travis.yml com o nome da APP criada no passo 12
```
$ vim helloworld/.travis.yml
  app: COLOQUE_AQUI_SUA_APP_DO_HEROKU
```

c) Pegar a Key no Settings do Usuário do Heroku para configurar no Travis-CI

d) Colocar a key do Heroku no Travis por variável HEROKU_API_KEY

17) Fazer o commit e  push e acompanhar o build no Travis (*é esperado dar sucesso*)

```
$ git status
$ git add .
$ git commit -m "Add Heroku Deploy"
$ git push origin master
```

18) Acesse sua aplicação através da URL que o Heroku irá informar após deploy concluído.


**Opcional SonarCloud**

19) Acessa sua conta do SonarCloud e crie um Projeto
20) Copiar o arquivo do Sonar necessário para realizar scan na raiz do seu repositório.

```
$ cp -a lab-campusparty2019/sonar/sonar-project.properties  helloworld/
```
21) Preencha as informações do arquivo conforme o seu projeto no Sonar
```
$ vim sonar-project.properties
sonar.projectKey=COLOQUE_SUA_CHAVE
sonar.projectName=COLOQUE_O_NOME_DO_PROJETO
sonar.projectVersion=1.0
sonar.sources=.
sonar.language=py
sonar.sourceEncoding=UTF-8
```

22) Substituir o arquivo do travis com o travis.yml.3 inserindo a seção de deploy após o build

$ cp -a lab-campusparty2019/travis/travis.yml.3  helloworld/.travis.yml


23) Fazer o commit e  push e acompanhar o build no Travis (*é esperado dar sucesso*)

```
$ git status
$ git add .
$ git commit -m "Add SonarCloud Scanner"
$ git push origin master
```

24) Acesse o Dashboard do SonarCloud para analisar seu código.
