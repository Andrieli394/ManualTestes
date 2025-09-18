# Roteiro passo-a-passo: de iniciante a especialista em testes manuais

---

## Visão geral (níveis)

1. **Fundamentos** — entender o que é teste, ciclo de vida, tipos básicos.
2. **Básico (manual)** — escrever casos de teste, executar, reportar bugs com clareza.
3. **Intermediário** — técnicas de design, testes exploratórios, APIs, DB, DevTools.
4. **Avançado** — estratégia de testes, integração com automação/CI, performance e segurança básicos.
5. **Especialista / Líder** — arquitetura de qualidade, métricas, governança, compliance (LGPD), chaos/reliability mindset.

---

## Nível 1 — Fundamentos

**Tópicos-chave**

- O que é qualidade vs. teste vs. QA vs. QC.
- SDLC (Waterfall, Agile/Scrum) e STLC (phases de teste).
- Níveis de teste: unit, integração, sistema, aceitação.
- Tipos de teste: funcional, regressão, smoke, sanity, usabilidade, performance, segurança (conceito).
- Bug lifecycle (aberto → triagem → resolvido → verificado → fechado).

**Prática**

- Mapear o fluxo de uma funcionalidade simples (ex.: login).
- Anotar 10 cenários de teste (pelo menos 1 positivo e 1 negativo por fluxo).

**Evidência**

- Documento simples: “Fluxo de Login + 10 cenários”.

---

## Nível 2 — Básico prático (escrever e executar)

**Tópicos-chave**

- Como escrever um caso de teste claro e reproduzível.
- Test plan básico e matriz de rastreabilidade (requirements → casos).
- Critérios de aceitação e definição de pronto.
- Gravidade vs prioridade.

**Ferramentas para aprender**

- Planilha / Google Sheets (comece aqui).
- Jira (ou equivalente) para criar issues/bugs.
- TestRail / Zephyr (opcional) — entender conceito de gerenciamento de casos.

**Templates (use e adapte)**

Teste (exemplo):

```
Test Case ID: TC-001
Título: Login com usuário válido
Pré-condição: Usuário cadastrado e ativado
Passos:
  1. Acessar /login
  2. Informar email e senha válidos
  3. Clicar em Entrar
Resultado esperado: Redireciona para /dashboard e mostra nome do usuário
Ambiente: staging
Status: (Pass/Fail)
Observações/Anexos: print, logs

```

Bug (exemplo):

```
Título: ERRO - Login falha com credenciais válidas
Resumo: Usuário não é autenticado apesar de credenciais corretas
Ambiente: staging
Passos para reproduzir:
  1. Acessar /login
  2. Inserir email x@x.com / senha 1234
  3. Clicar Entrar
Resultado esperado: Acesso concedido e redirecionamento para /dashboard
Resultado atual: Página recarrega e mostra erro genérico
Gravidade: Alta
Prioridade: Alta
Logs/Anexos: print + console log

```

**Prática**

- Escrever 20 casos de teste para um fluxo simples (cadastro, login, recuperação de senha).
- Reportar 5 bugs bem descritos (mesmo que sejam “intencionais” em apps de teste).

**Evidência**

- Repositório com planilha/tickets exportados.

---

## Nível 3 — Intermediário (técnicas e investigação)

**Tópicos-chave**

- Técnicas de design de testes: Equivalence Partitioning, Boundary Value Analysis, Decision Tables, State Transition, Pairwise.
- Testes exploratórios: charters, sessões, heurísticas (ex.: SFDPOT — Structure, Function, Data, Platform, Operations, Time).
- Testes de API: HTTP (GET/POST/PUT/DELETE), status codes, headers, payloads JSON.
- Validação em banco de dados: SELECT, joins básicos, checar dados de backend.
- Uso de DevTools: network, console, elements, performance (básico).

**Ferramentas**

- Postman (ou Insomnia) para APIs.
- Um client DB (DBeaver, TablePlus, psql) ou até sqlite local.
- Chrome DevTools.
- Ferramentas de captura de tela & gravação de bugs.

**Prática**

- Testar uma API pública (ou endpoint da sua aplicação): criar coleções no Postman com testes (asserts simples).
- Fazer sessão de testing exploratório guiada: 3 charters diferentes para mesma funcionalidade e documentar o que encontrou.
- Criar decision table para regras de desconto/validação.

**Evidência**

- Coleção Postman + relatório de sessão exploratória + 10 queries SQL usadas para validação.

---

## Nível 4 — Avançado (estratégia & integração)

**Tópicos-chave**

- Test strategy: cobertura, critérios de entrada/saída, prioridade de funcionalidades por risco.
- Integração manual ↔ automação: quando automatizar, quem automação resolve.
- Noções de CI/CD e como testes se encaixam (pipelines).
- Testes não-funcionais básicos: performance (carga simples), segurança (OWASP Top 10 awareness).
- Testability e observability: logs, traces, métricas que facilitam testes.

**Ferramentas**

- Familiaridade conceitual com Jenkins / GitHub Actions (saber onde os testes são executados).
- JMeter ou k6 (para entender testes de carga simples).
- Ferramentas de SAST/DAST (conceito, não precisa dominar todas).

**Prática**

- Definir estratégia de testes para um MVP (quais tipos testar, quais deixar para automação).
- Rodar um teste de carga simples contra um endpoint (coletar RPS, latência) — interpretar resultados.
- Fazer checklist de segurança básico baseado em OWASP (ex.: input validation, auth).

**Evidência**

- Documento “Estratégia de QA” para um projeto fictício + relatório de carga simples.

---

## Nível 5 — Especialista / líder técnico

**Tópicos-chave**

- Projetar política de qualidade na organização, indicadores (ex.: taxa de regressão, defect escape, tempo médio de resolução).
- Gestão de riscos e alinhamento com produto/negócio.
- Privacidade e compliance (LGPD no Brasil): impacto no teste de dados.
- Arquitetura de testes: dados, ambientes, geração de dados de teste seguros.
- Cultura de qualidade: shift-left, testes em pipeline, pair testing, mentoring.

**Atividades**

- Liderar uma campanha de qualidade, priorizar o backlog de bugs com product owners.
- Projetar e revisar políticas de dados de teste para conformidade com LGPD.
- Mentorar outros QAs e revisar test plans.

**Evidência**

- Portfolio com 3+ estratégias de QA aplicadas, métricas antes/depois, cases de problemas evitados.

---

## Projetos práticos sugeridos (faça e documente)

1. **E-commerce mini**: test plan + 50 casos (cadastro, busca, carrinho, checkout), 10 bugs reportados.
2. **API public**: coleção Postman com 20 requests + asserts + doc sobre edge cases.
3. **Exploratory challenge**: 5 sessões exploratórias diferentes em um app grátis (ex.: todo app) com relatório por sessão.
4. **Relatório de performance**: cenário simples de carga e recomendações.
5. **Case compliance**: plano para anonimizar dados de teste (LGPD).

Para cada projeto: gere um PDF/markdown com objetivo, escopo, artefatos (test cases), evidências (prints, logs), e poste no GitHub/Drive.

---

## Habilidades técnicas essenciais (checklist)

- Escrever casos bem-estruturados e bugs claros.
- Usar JIRA (criar, etiquetar, linkar PRs/issues).
- Postman + entendimento de JSON/HTTP.
- SQL básico (SELECT, WHERE, JOIN simples).
- Chrome DevTools uso para investigar erros.
- Noções de testes não-funcionais (performance, segurança básica).
- Boas práticas de testes exploratórios.

## Soft skills

- Comunicação escrita (reportar bugs com clareza).
- Curiosidade investigativa e pensamento crítico.
- Colaboração com devs e product owners.
- Priorizar com base em risco/impacto.
- Documentação eficiente e objetiva.

---

## Como provar que você evoluiu (portfólio)

- Repositório com: test plans, casos de teste, coleções Postman, relatórios de sessão exploratória, prints de bugs no Jira.
- Blog curto (ou LinkedIn) com 2-3 posts: “Como eu testei X” (mostre raciocínio).
- Apresente um case em entrevista: o problema, sua abordagem de teste, evidências e resultado.

---

## Dicas práticas imediatas (o que fazer agora)

1. Escolha um app simples (site ou web app) e escreva 20 casos de teste cobrindo fluxos principais.
2. Faça 3 sessões de teste exploratório com um objetivo definido e documente achados.
3. Aprenda o básico de Postman: crie 5 requests e valide respostas.
4. Aprenda SELECT simples: `SELECT * FROM users WHERE email = 'x@x.com';` e pratique com dados fictícios.

---

## Checklist de tópicos para entrevistas

- Explique diferença entre severity e priority.
- Descreva como você escreve um caso de teste.
- Dê exemplos de testes exploratórios e como documentá-los.
- Como validar dados no banco (quais queries você usaria).
- Como priorizar testes quando o tempo é curto.
- Como medir sucesso/risco de qualidade.

# Roteiro passo-a-passo: de iniciante a especialista em testes manuais

Beleza — abaixo tem um roteiro prático e progressivo pra você subir do zero até nível avançado em testes manuais. Cada “nível” traz tópicos-chave, ferramentas a praticar, tarefas práticas (o que você deve *fazer*) e evidências que provam sua evolução. Vá seguindo em sequência — foco na prática, não só em teoria.

---

## Visão geral (níveis)

1. **Fundamentos** — entender o que é teste, ciclo de vida, tipos básicos.
2. **Básico (manual)** — escrever casos de teste, executar, reportar bugs com clareza.
3. **Intermediário** — técnicas de design, testes exploratórios, APIs, DB, DevTools.
4. **Avançado** — estratégia de testes, integração com automação/CI, performance e segurança básicos.
5. **Especialista / Líder** — arquitetura de qualidade, métricas, governança, compliance (LGPD), chaos/reliability mindset.

---

## Nível 1 — Fundamentos

**Tópicos-chave**

- O que é qualidade vs. teste vs. QA vs. QC.
- SDLC (Waterfall, Agile/Scrum) e STLC (phases de teste).
- Níveis de teste: unit, integração, sistema, aceitação.
- Tipos de teste: funcional, regressão, smoke, sanity, usabilidade, performance, segurança (conceito).
- Bug lifecycle (aberto → triagem → resolvido → verificado → fechado).

**Prática**

- Mapear o fluxo de uma funcionalidade simples (ex.: login).
- Anotar 10 cenários de teste (pelo menos 1 positivo e 1 negativo por fluxo).

**Evidência**

- Documento simples: “Fluxo de Login + 10 cenários”.

---

## Nível 2 — Básico prático (escrever e executar)

**Tópicos-chave**

- Como escrever um caso de teste claro e reproduzível.
- Test plan básico e matriz de rastreabilidade (requirements → casos).
- Critérios de aceitação e definição de pronto.
- Gravidade vs prioridade.

**Ferramentas para aprender**

- Planilha / Google Sheets (comece aqui).
- Jira (ou equivalente) para criar issues/bugs.
- TestRail / Zephyr (opcional) — entender conceito de gerenciamento de casos.

**Templates (use e adapte)**

Teste (exemplo):

```
Test Case ID: TC-001
Título: Login com usuário válido
Pré-condição: Usuário cadastrado e ativado
Passos:
  1. Acessar /login
  2. Informar email e senha válidos
  3. Clicar em Entrar
Resultado esperado: Redireciona para /dashboard e mostra nome do usuário
Ambiente: staging
Status: (Pass/Fail)
Observações/Anexos: print, logs

```

Bug (exemplo):

```
Título: ERRO - Login falha com credenciais válidas
Resumo: Usuário não é autenticado apesar de credenciais corretas
Ambiente: staging
Passos para reproduzir:
  1. Acessar /login
  2. Inserir email x@x.com / senha 1234
  3. Clicar Entrar
Resultado esperado: Acesso concedido e redirecionamento para /dashboard
Resultado atual: Página recarrega e mostra erro genérico
Gravidade: Alta
Prioridade: Alta
Logs/Anexos: print + console log

```

**Prática**

- Escrever 20 casos de teste para um fluxo simples (cadastro, login, recuperação de senha).
- Reportar 5 bugs bem descritos (mesmo que sejam “intencionais” em apps de teste).

**Evidência**

- Repositório com planilha/tickets exportados.

---

## Nível 3 — Intermediário (técnicas e investigação)

**Tópicos-chave**

- Técnicas de design de testes: Equivalence Partitioning, Boundary Value Analysis, Decision Tables, State Transition, Pairwise.
- Testes exploratórios: charters, sessões, heurísticas (ex.: SFDPOT — Structure, Function, Data, Platform, Operations, Time).
- Testes de API: HTTP (GET/POST/PUT/DELETE), status codes, headers, payloads JSON.
- Validação em banco de dados: SELECT, joins básicos, checar dados de backend.
- Uso de DevTools: network, console, elements, performance (básico).

**Ferramentas**

- Postman (ou Insomnia) para APIs.
- Um client DB (DBeaver, TablePlus, psql) ou até sqlite local.
- Chrome DevTools.
- Ferramentas de captura de tela & gravação de bugs.

**Prática**

- Testar uma API pública (ou endpoint da sua aplicação): criar coleções no Postman com testes (asserts simples).
- Fazer sessão de testing exploratório guiada: 3 charters diferentes para mesma funcionalidade e documentar o que encontrou.
- Criar decision table para regras de desconto/validação.

**Evidência**

- Coleção Postman + relatório de sessão exploratória + 10 queries SQL usadas para validação.

---

## Nível 4 — Avançado (estratégia & integração)

**Tópicos-chave**

- Test strategy: cobertura, critérios de entrada/saída, prioridade de funcionalidades por risco.
- Integração manual ↔ automação: quando automatizar, quem automação resolve.
- Noções de CI/CD e como testes se encaixam (pipelines).
- Testes não-funcionais básicos: performance (carga simples), segurança (OWASP Top 10 awareness).
- Testability e observability: logs, traces, métricas que facilitam testes.

**Ferramentas**

- Familiaridade conceitual com Jenkins / GitHub Actions (saber onde os testes são executados).
- JMeter ou k6 (para entender testes de carga simples).
- Ferramentas de SAST/DAST (conceito, não precisa dominar todas).

**Prática**

- Definir estratégia de testes para um MVP (quais tipos testar, quais deixar para automação).
- Rodar um teste de carga simples contra um endpoint (coletar RPS, latência) — interpretar resultados.
- Fazer checklist de segurança básico baseado em OWASP (ex.: input validation, auth).

**Evidência**

- Documento “Estratégia de QA” para um projeto fictício + relatório de carga simples.

---

## Nível 5 — Especialista / líder técnico

**Tópicos-chave**

- Projetar política de qualidade na organização, indicadores (ex.: taxa de regressão, defect escape, tempo médio de resolução).
- Gestão de riscos e alinhamento com produto/negócio.
- Privacidade e compliance (LGPD no Brasil): impacto no teste de dados.
- Arquitetura de testes: dados, ambientes, geração de dados de teste seguros.
- Cultura de qualidade: shift-left, testes em pipeline, pair testing, mentoring.

**Atividades**

- Liderar uma campanha de qualidade, priorizar o backlog de bugs com product owners.
- Projetar e revisar políticas de dados de teste para conformidade com LGPD.
- Mentorar outros QAs e revisar test plans.

**Evidência**

- Portfolio com 3+ estratégias de QA aplicadas, métricas antes/depois, cases de problemas evitados.

---

## Projetos práticos sugeridos (faça e documente)

1. **E-commerce mini**: test plan + 50 casos (cadastro, busca, carrinho, checkout), 10 bugs reportados.
2. **API public**: coleção Postman com 20 requests + asserts + doc sobre edge cases.
3. **Exploratory challenge**: 5 sessões exploratórias diferentes em um app grátis (ex.: todo app) com relatório por sessão.
4. **Relatório de performance**: cenário simples de carga e recomendações.
5. **Case compliance**: plano para anonimizar dados de teste (LGPD).

Para cada projeto: gere um PDF/markdown com objetivo, escopo, artefatos (test cases), evidências (prints, logs), e poste no GitHub/Drive.

---

## Habilidades técnicas essenciais (checklist)

- Escrever casos bem-estruturados e bugs claros.
- Usar JIRA (criar, etiquetar, linkar PRs/issues).
- Postman + entendimento de JSON/HTTP.
- SQL básico (SELECT, WHERE, JOIN simples).
- Chrome DevTools uso para investigar erros.
- Noções de testes não-funcionais (performance, segurança básica).
- Boas práticas de testes exploratórios.

## Soft skills

- Comunicação escrita (reportar bugs com clareza).
- Curiosidade investigativa e pensamento crítico.
- Colaboração com devs e product owners.
- Priorizar com base em risco/impacto.
- Documentação eficiente e objetiva.

---

## Como provar que você evoluiu (portfólio)

- Repositório com: test plans, casos de teste, coleções Postman, relatórios de sessão exploratória, prints de bugs no Jira.
- Blog curto (ou LinkedIn) com 2-3 posts: “Como eu testei X” (mostre raciocínio).
- Apresente um case em entrevista: o problema, sua abordagem de teste, evidências e resultado.

---

## Dicas práticas imediatas (o que fazer agora)

1. Escolha um app simples (site ou web app) e escreva 20 casos de teste cobrindo fluxos principais.
2. Faça 3 sessões de teste exploratório com um objetivo definido e documente achados.
3. Aprenda o básico de Postman: crie 5 requests e valide respostas.
4. Aprenda SELECT simples: `SELECT * FROM users WHERE email = 'x@x.com';` e pratique com dados fictícios.

---

## Checklist de tópicos para entrevistas

- Explique diferença entre severity e priority.
- Descreva como você escreve um caso de teste.
- Dê exemplos de testes exploratórios e como documentá-los.
- Como validar dados no banco (quais queries você usaria).
- Como priorizar testes quando o tempo é curto.
- Como medir sucesso/risco de qualidade.
