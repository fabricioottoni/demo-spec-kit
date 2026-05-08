# Exemplo para inicializar o repositorio
specify init --here --offline --integration copilot

# executar o /specify.clarify após o /specify.specify
# executar o /specify.analyse após o /specify.tasks

# Modelo de constituição
Princípios e premissas que não devem ser violados e devem ser seguidos a risca:

- SOLID
- Clean Code
- TDD
- Sempre cobrir 100% dos testes
- Utilizar arquitetura hexagonal para o projeto
- Toda branch obrigatoriamente deve ter o prefixo 'feature/<nome-da-funcionalidade>'
- Toda vez que forem feitas modificações no projeto seja atualizado o readme contendo a visão funcional do projeto, diagramas de sequência ou fluxogramas no formato mermaid e exemplos de payloads de entrada e saída.
- Ao final de toda implementação execute a aplicação e garanta que o que foi implementado esteja funcional.

# Stack a ser utilizada
- Java versão 21 da sdk ou superior
- Spring boot (Utilizando: starter, tests e maven:POM)
- Swagger/OpenAPI para documentação dos endpoints

# Padrões de logs a serem seguidos
- Utilizar idioma pt-br para as mensagens
- Em todos os loggings logar o nome do método da seguinte forma '[<nome-da-classe>::<nome-do-metodo>]'

# Fluxo de processamento
- receber uma requisição get com uma palava na url e devolvela escrita de traz para frente. A resposta deve ser um json

# Estrutura do projeto
<nome-do-projeto>
- app (local do código fonte da aplicação)
-- tests (local dos testes unitários)
- infra (local da infraestrutura da aplicação)

# Modelos e exemplos
abc...

