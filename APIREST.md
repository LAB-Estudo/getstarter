# Guia de Design da API

Trata-se de um guia para o desenvolvimento de APIs REST

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