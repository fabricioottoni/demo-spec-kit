# Constituição do Projeto Demo Spec Kit

## Instruções de Inicialização

```bash
specify init --here --offline --integration copilot
```

Após inicializar, execute sequencialmente:
1. `/speckit-specify` - Criar especificação de funcionalidade
2. `/speckit-clarify` - Esclarecer pontos ambíguos (após `/speckit-specify`)
3. `/speckit-plan` - Criar plano de implementação
4. `/speckit-tasks` - Gerar tarefas (após `/speckit-plan`)
5. `/speckit-analyze` - Analisar consistência (após `/speckit-tasks`)

---

## Princípios Não-Negociáveis (OBRIGATÓRIOS)

Estes princípios e premissas não devem ser violados e devem ser seguidos rigorosamente:

### I. Padrões de Linguagem

- **Português (pt-br) é OBRIGATÓRIO** para toda comunicação, documentação, mensagens de log e respostas de todos os agentes (humanos, IA, ferramentas)
- Para criação de código-fonte, configurações e testes, utilizar sempre inglês americano
- Todos os agentes, incluindo Claude e ferramentas de automação, DEVEM responder exclusivamente em português (pt-br), sem exceções

### II. Qualidade de Código

- **SOLID** - Princípios SOLID devem ser seguidos rigorosamente
- **Clean Code** - Código limpo e legível é obrigatório
- **TDD (Test-Driven Development)** - Testes devem ser escritos antes da implementação
- **Cobertura de Testes**: Sempre cobrir 100% dos testes
- **Arquitetura Hexagonal**: Utilizar arquitetura hexagonal para o projeto, inclusive na estrutura de pastas (adapter, application, domain, etc...), distribuição dos arquivos, etc...

### III. Padrões de Git

- Toda ramificação deve ter o prefixo obrigatório: `feature/<nome-da-funcionalidade>`
- Mensagens de commit devem ser claras e descritivas em inglês

### IV. Documentação

- Toda vez que forem feitas modificações no projeto, o README deve ser atualizado contendo:
  - Visão funcional do projeto
  - Diagramas de sequência ou fluxogramas em formato Mermaid
  - Exemplos de payloads de entrada e saída
- Ao final de toda implementação, execute a aplicação e garanta que o que foi implementado esteja funcional

### V. Padrões de Logs

- Utilizar idioma português (pt-br) para mensagens de log
- Em todos os logs, incluir o nome da classe e método no seguinte formato: `[<NomeDaClasse>::<nomeDometodo>]`

---

## Stack Tecnológico

- **Java**: Versão 21 da SDK ou superior
- **Framework**: Spring Boot (utilizando starter dependencies, testes e Maven/POM)
- **Documentação de API**: Swagger/OpenAPI para documentação dos endpoints
- **Build Tool**: Maven com configuração explícita de POM

---

## Fluxo de Processamento

Exemplo de funcionalidade inicial:
- Receber uma solicitação GET com uma palavra na URL
- Devolver a palavra escrita de trás para frente
- A resposta deve ser um JSON

---

## Estrutura do Projeto

```
<nome-do-projeto>/
├── app/                          # Código-fonte da aplicação
│   ├── src/main/java/           # Código principal
│   ├── src/test/java/           # Testes unitários
│   └── src/main/resources/      # Recursos da aplicação
│   └── pom.xml                  # Configuração Maven
│   └── Dockerfile               # Configuração Docker (container)
├── infra/                        # Infraestrutura da aplicação
│   ├── docker-compose.yml       # Configuração de contêineres
│   ├── kubernetes/              # Configurações do Kubernetes
│   └── config/                  # Arquivos de configuração
├── README.md                     # Visão funcional e documentação
```
