# Instruções de Inicialização

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

### I. Padrões de Linguagem (OBRIGATÓRIO)

**Português (pt-br) é OBRIGATÓRIO** para toda comunicação, documentação, mensagens de log e respostas de todos os agentes (humanos, IA, ferramentas). Para criação de código-fonte, configurações e testes, utilizar sempre inglês americano. Todos os agentes, incluindo Claude e ferramentas de automação, DEVEM responder exclusivamente em português (pt-br), sem exceções.

**Clarificação - Escopo de Linguagem**:

| Escopo | Idioma | Exemplos |
|--------|--------|----------|
| **Documentação formal** | Português (pt-br) | `/specs/` (spec.md, plan.md, tasks.md, research.md, data-model.md), `/docs/`, README.md, CLAUDE.md, constituição |
| **Código-fonte e configuração** | Inglês americano | `src/main/java/`, `src/test/java/`, `pom.xml`, `application.yml`, nomes de variáveis, comentários de código |
| **Comunicação e logs** | Português (pt-br) | Mensagens de log em runtime, PRs, issues, commits (descrição), Slack, reuniões |
| **Git history** | Inglês americano | Mensagens de commit (`git commit -m`), branch names, commit hashes |

**Rationale**: Coesão cultural e acessibilidade à equipe brasileira; código em inglês segue convenção da indústria e facilita contribuições externas; especificações em português garantem que requisitos sejam claros para stakeholders brasileiros.

### II. Qualidade de Código

Aplicação rigorosa de **SOLID**, **Clean Code**, **TDD**, **100% cobertura de testes** e **Arquitetura Hexagonal**:
- Princípios SOLID devem ser seguidos rigorosamente em todas as classes e módulos
- Código limpo e legível é obrigatório; refatoração contínua sem acúmulo de débito técnico
- Testes DEVEM ser escritos ANTES da implementação (Red-Green-Refactor)
- Cobertura de testes: obrigatoriamente 100% do código produzido
- Arquitetura Hexagonal obrigatória para separação clara entre negócio, ports e adapters

**Rationale**: Manutenibilidade de longo prazo, confiabilidade e redução de bugs em produção; TDD força clareza de requisitos antes de implementação.


### III. Padrões de Git

Toda ramificação DEVE ter prefixo obrigatório: `feature/<nome-da-funcionalidade>`. Mensagens de commit DEVEM ser claras, descritivas e em inglês. Histórico de commits será usado para rastreabilidade de funcionalidades e debugging.

**Rationale**: Organização visual do repositório; commits em inglês facilitam integração com ferramentas e busca; rastreabilidade de decisões.

### IV. Documentação

Toda modificação no projeto OBRIGA atualização do README com:
- Visão funcional do projeto (o que faz, para quem, por quê)
- Diagramas de sequência ou fluxogramas em formato Mermaid
- Exemplos de payloads de entrada e saída (para APIs/serviços)

Ao final de toda implementação, a aplicação DEVE ser executada e validada para garantir que o implementado seja funcional conforme especificado.

**Rationale**: Documentação viva reduz curva de aprendizado; exemplos práticos evitam ambiguidade; validação em execução real previne surpresas em deploy.

### V. Padrões de Logs

Mensagens de log DEVEM utilizar português (pt-br) e incluir OBRIGATORIAMENTE o nome da classe e método no formato: `[<NomeDaClasse>::<nomeDoMetodo>]` em todos os eventos registrados.

**Rationale**: Rastreabilidade em produção em idioma conhecido da equipe; formato estruturado acelera debug de issues em produção.

---

## Stack Tecnológico

- **Java**: Versão 21 da SDK ou superior (JDK 21+)
- **Framework**: Spring Boot com starter dependencies, testes integrados e Maven/POM explícito
- **Documentação de API**: Swagger/OpenAPI obrigatório para todos os endpoints REST
- **Build Tool**: Maven com configuração explícita em pom.xml (sem defaults implícitos)
- **Infraestrutura**: Docker Compose, Kubernetes configs, arquivos de configuração centralizados em `infra/`

---

## Fluxo de Processamento

Exemplo de funcionalidade inicial (e padrão mínimo para validação):
1. Receber uma solicitação GET com uma palavra na URL
2. Devolver a palavra escrita de trás para frente
3. Resposta em formato JSON estruturado

Este fluxo simples valida: routing HTTP, processamento básico, serialização JSON, testes unitários e integração com Spring Boot.

---

## Governance

**Autoridade e Precedência**: Esta constituição é o documento supremo de governança do projeto. Todos os PRs, reviews, testes e deploys DEVEM verificar conformidade com estes princípios antes de merge. Quando uma prática existente conflitar com um princípio aqui declarado, o princípio prevalece.

**Emendas e Mudanças**:
1. Toda mudança de princípio REQUER documentação clara do motivo (contexto que mudou)
2. Mudanças DEVEM ser aprovadas e rastreadas via commit separado com prefixo `docs: amend constitution to vX.Y.Z`
3. Versão DEVE ser bumped semanticamente:
   - **MAJOR**: Remoção ou redefinição de princípio existente
   - **MINOR**: Novo princípio ou seção, ou extensão material de orientação
   - **PATCH**: Clarificações, correções de linguagem, refinamentos não-semânticos

**Compliance Review**: Sprints deverão incluir revisão de conformidade (especialmente TDD, cobertura 100%, padrão de logs). Débito técnico contra a constituição DEVE ser rastreado como issue com label `constitution-violation`.

**Rationale Guidance**: Para contexto de decisões em runtime (ambiguidades não contempladas aqui), consulte `CLAUDE.md` (instruções de inicialização) e `README.md` (visão funcional e diagramas Mermaid).

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

