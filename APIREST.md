# Guia de Design da API

Guia para o contrução de APIs REST seguindo as melhores práticas de desenvolvimento de software e com cobertura de testes, utilizando Node.js e seguindo os princípios do TDD.

Temos aqui como objetivos gerais:

+ Orientar a construção de aplicações modularizadas e desacopladas
+ Orientar a integração com banco de dados NoSQL
+ Orientar o desenvolvimento guiado por testes com TDD
+ Orientar o desenho de APIs seguindo o padrão REST
+ Orientar a autenticação e segurança de APIs

## Desenvolvimento guiado por testes

Seguir um modelo conhecido como TDD (Test Driven Development ou Desenvolvimento Guiado por Testes).

## Ambiente de Testes JavaScript

Componentes que fazem parte de uma suíte de testes em javascript:

## Test runners

Test runners são responsáveis por importar os arquivos de testes e executar os casos de teste.

+ Utilizamos o [Mocha](https://github.com/mochajs/mocha) como nosso test runners.

Vale destacar ainda o uso de bibliotecas de assert que verificam se o teste está cumprindo com o determinado fazendo a afirmação e
respondendo com true ou false para o runner.

+ Utilizamos o [chai](https://github.com/chaijs/chai) como nossa biblioteca assert.

Destacamos ainda as bibliotecas de suporte que se separam em diversas responsabilidades, como por exemplo:

+ Para fazer mocks e spys temos o [SinonJS](http://sinonjs.org/)
+ Para emular servidores existe o [supertest](https://github.com/visionmedia/supertest)

## Estrutura de diretórios e arquivos

Utilizamos essa estrutura de diretórios em que o código da aplicação é isolado em um diretório deixando a raiz do projeto mais
limpa e acabando com a mistura de diretórios de código com diretórios de testes e arquivos de configuração.

```javascript
├── package.json
├── server.js
├── src
│   ├── app.js
│   ├── controllers
│   ├── config
│   │   └── database.js
│   ├── middlewares
│   ├── models
│   └── routes
│       └── index.js
└── tests
```

## Dentro do diretório source

Ao movermos o código para o diretório src, criamos um arquivo chamado app.js e mantemos o server.js no diretório raiz, dessa maneira deixamos o server.js com a responsabilidade de chamar o app.js e inicializar a aplicação.

Assim isolamos a aplicação da execução e deixamos que ela seja executada por quem chamar, nesse caso o server.js, mas também poderia ser um módulo.

```javascript
├── src
│   ├── app.js
│   ├── controllers
│   ├── middlewares
│   ├── models
│   └── routes

```

Essa estrutura que utilizamos aqui, ela é clara e separa as responsabilidades de cada componente, além de permitir o carregamento dinâmico.

## Separação por funcionalidade

Adotamos um padrão que promove a separação por funcionalidade. Nele abstraímos os diretórios baseado nas funcionalidades e não nas responsabilidades, como no exemplo abaixo:

```javascript
└── src
    ├── controllers
    │   └── users.js
    └── routes
        └── users.js
```

## Rotas com o express router

O express possui um middleware nativo para lidar com rotas, o Router. O Router é responsável por administrar as rotas da aplicação e pode ser passado como parâmetro para o app.use(). Utilizando o Router é possível desacoplar as rotas e remover a necessidade de usar o app (instância do express)
em outros lugares da aplicação.

Para isso temos um diretório chamado routes dentro de src. Os diretórios devem ficar assim:

```javascript
├── package.json
├── server.js
├── src
│   ├── app.js
│   └── routes
```

## O padrão MVC

MVC é um design pattern de arquitetura que foca na separação de responsabilidades. O MVC separa os dados de negócio (Models) da interface do usuário (Views) e usa um componente para ligá-los (Controllers), normalmente os controllers são responsáveis por receber a entrada do usuário e coordenar Models e Views.

## Vantagens de utilizar MVC

A separação de responsabilidades facilita a modularizaçãoMVS das funcionalidades da aplicação e possibilita:

+ Manutenibilidade: Quando uma modificação precisa ser feita é mais fácil de descobrir onde é e também onde vai causar impacto.
+ Desacoplar models e views facilita os testes em ambos isoladamente. Testando a lógica de negócio em models e a usabilidade em views.
+ Reutilização de código

## MVC em API

Nota-se que para APIs, a parte da view não é aplicada. Assim mm APIs o controller recebe a requisição da rota, faz a chamada para o model realizar a lógica de negócio e retorna a resposta para o usuário.
## Models

Os models são responsáveis pelos dados, persistência e validação na aplicação.

## Controllers

Lançamos mão da implementação de um controller para administrar as requisições e conversar com o model. O próprio gerador de código do Express
já cria o diretório para controllers separadamente.

## Leituras

+ [Netflix Scaling Node](https://medium.com/@nodejs/netflixandchill-how-netflix-scales-with-node-js-and-containers-cf63c0b92e57#.9bzn8wm4u)
+ [Building Microservices with OpenSource Technologies](http://www.developer.com/open/building-microservices-with-open-source-technologies.html)
+ [Docker Micro-services with Node](http://anandmanisankar.com/posts/docker-container-nginx-node-redis-example/)
