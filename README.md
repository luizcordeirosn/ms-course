# Microsserviços com Java e Spring

Este repositório contém o código-fonte de um projeto de microsserviços desenvolvido em Java com o ecossistema Spring. O objetivo é demonstrar a comunicação entre serviços, balanceamento de carga, descoberta de serviços, tolerância a falhas e roteamento de requisições.

## Tecnologias Utilizadas

* Java 11+
* Spring Boot
* Spring Cloud
* Maven
* Feign (para comunicação síncrona)
* Ribbon (para balanceamento de carga)
* Eureka (para descoberta de serviços)
* Hystrix (para tolerância a falhas)
* Zuul (para API Gateway)
* H2 (banco de dados em memória)

## Estrutura do Projeto

O projeto é dividido nos seguintes microsserviços:

* **hr-worker:** Um microsserviço simples para gerenciar trabalhadores.
* **hr-payroll:** Um microsserviço que consome o `hr-worker` para calcular a folha de pagamento.
* **hr-eureka-server:** Servidor de descoberta de serviços (Service Discovery).
* **hr-zuul-server:** API Gateway para rotear as requisições para os outros microsserviços.

## Como Executar o Projeto

Para executar o projeto, siga os passos abaixo na ordem indicada:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/luizcordeirosn/ms-course.git](https://github.com/luizcordeirosn/ms-course.git)
    cd ms-course
    ```

2.  **Execute o Eureka Server (`hr-eureka-server`):**
    * Navegue até o diretório `hr-eureka-server` e execute a aplicação Spring Boot.
    * Acesse o dashboard do Eureka em `http://localhost:8761`.

3.  **Execute o Worker (`hr-worker`):**
    * Navegue até o diretório `hr-worker` e execute a aplicação.
    * Você pode executar múltiplas instâncias em portas diferentes para testar o balanceamento de carga. Por exemplo, na porta 8001 e 8002.

4.  **Execute o Payroll (`hr-payroll`):**
    * Navegue até o diretório `hr-payroll` e execute a aplicação.

5.  **Execute o Zuul Server (`hr-zuul-server`):**
    * Navegue até o diretório `hr-zuul-server` e execute a aplicação.
    * Todas as requisições para os microsserviços devem ser feitas através do Zuul na porta `8765`.

## Fases do Projeto

O projeto foi desenvolvido em fases, cada uma introduzindo novos conceitos de microsserviços.

### Fase 1: Comunicação Simples, Feign e Ribbon

* Criação dos projetos `hr-worker` e `hr-payroll`.
* Implementação da comunicação entre `hr-payroll` e `hr-worker` utilizando `RestTemplate` e `Feign`.
* Configuração do `Ribbon` para balanceamento de carga ao executar múltiplas instâncias do `hr-worker`.

### Fase 2: Eureka, Hystrix e Zuul

* Criação e configuração do `hr-eureka-server` para descoberta de serviços.
* Configuração dos microsserviços como clientes do Eureka.
* Implementação de tolerância a falhas com o `Hystrix` no `hr-payroll`.
* Criação e configuração do `hr-zuul-server` como API Gateway do projeto.
