# Meu Projeto

**Descrição curta:**  
Projeto exemplo com foco em boas práticas: fluxo de branching (GitFlow), histórico de commits semântico, releases com versionamento semântico, acessibilidade (WCAG 2.1 AA) e otimização para produção.

---

## Sumário
- [Status](#status)
- [Visão geral](#visão-geral)
- [Como começar (dev)](#como-começar-dev)
- [Estratégia de branching (GitFlow)](#estratégia-de-branching-gitflow)
- [Commits semânticos](#commits-semânticos)
- [Releases e versionamento semântico](#releases-e-versionamento-semântico)
- [Acessibilidade (WCAG 2.1 AA)](#acessibilidade-wcag-21-aa)
- [Otimização para produção](#otimização-para-produção)
- [CI/CD e automações](#cicd-e-automações)
- [Checklist de PR / Code Review](#checklist-de-pr--code-review)
- [Contato](#contato)

---

## Status
- Código: **Esqueleto e exemplos**
- Acessibilidade: **Padrões implementados nos exemplos**
- Otimização: **Scripts e workflow para minificação e compressão configurados como exemplo**

---

## Visão geral
Este repositório serve como um template inicial com:
- Estrutura semântica HTML e componentes acessíveis
- Templates e documentação para GitFlow, commits semânticos e releases
- Workflows GitHub Actions para build (minificar CSS/JS/HTML) e compressão de imagens
- Versões de alto contraste e modo escuro prontas

---

## Como começar (dev)
Requisitos:
- Node.js (>=14) e npm ou yarn
- Git

Instalação (exemplo):

```bash
# clonar
git clone https://github.com/SEU_USUARIO/meu-projeto.git
cd meu-projeto

# instalar dependências (exemplo)
npm install
```

Comandos úteis:

```bash
# rodar servidor de dev (se implementado)
npm run dev

# build de produção
npm run build
```

---

## Estratégia de branching (GitFlow)
Adotamos uma versão simplificada do **GitFlow**:

- `main` — ramo estável, pronto para produção.
- `develop` — desenvolvimento integrado (base para features).
- `feature/*` — novas funcionalidades (criar a partir de `develop`).
- `release/*` — preparação para release (criar a partir de `develop`, mesclar em `main` e `develop`).
- `hotfix/*` — correções críticas em produção (criar a partir de `main`, mesclar em `main` e `develop`).

Fluxo rápido:

```bash
# criar feature
git checkout develop
git checkout -b feature/minha-feature

# quando pronta, push e PR para develop
git push origin feature/minha-feature
```

---

## Commits semânticos
Usar mensagens no formato: `<tipo>(escopo?): descrição`  

Tipos comuns:
- `feat` — nova funcionalidade
- `fix` — correção de bug
- `docs` — documentação
- `style` — formatação, semântica no código
- `refactor` — refatoração
- `perf` — melhoria de performance
- `test` — adicionar testes
- `chore` — tarefas auxiliares

Exemplo:

```
feat(auth): adicionar login por token
fix(ui): corrigir foco do botão enviar
```

Para automatizar, considere usar `commitlint` e `husky`.

---

## Releases e versionamento semântico
Usamos **SemVer**: `MAJOR.MINOR.PATCH`

- MAJOR — mudanças incompatíveis
- MINOR — novas funcionalidades compatíveis
- PATCH — correções e melhorias pequenas

Exemplo de fluxo de release:

```bash
# criar release branch
git checkout develop
git checkout -b release/1.2.0

# após testes e PR, mesclar em main
git checkout main
git merge --no-ff release/1.2.0
git tag -a v1.2.0 -m "v1.2.0"
git push origin main --tags

# também mesclar release em develop
git checkout develop
git merge --no-ff release/1.2.0
git push origin develop
```

Para automação, usar `semantic-release` no CI.

---

## Acessibilidade (WCAG 2.1 AA)
Princípios aplicados nos exemplos:
- Estrutura semântica com `<header>`, `<nav>`, `<main>`, `<footer>`.
- Navegação por teclado: todos os controles são alcançáveis com Tab; foco visível.
- Uso de `aria-*` quando necessário.
- Contraste mínimo de **4.5:1** para texto normal.
- Suporte a leitores de tela: labels, roles e landmarks.
- Versão de alto contraste e modo escuro com alternativas de CSS e `prefers-color-scheme`.

Veja `ACCESSIBILITY.md` para checklist e detalhes.

---

## Otimização para produção
Inclui configuração de build para:
- Minificar CSS, JS e HTML
- Comprimir imagens (lossy e lossless)
- Gerar sourcemaps opcionalmente

Exemplo (scripts em package.json):

```json
{
  "scripts": {
    "build": "node build-scripts/build.js",
    "compress-images": "node build-scripts/compress-images.js"
  }
}
```

Fornecemos um workflow GitHub Actions (`.github/workflows/ci.yml`) que instala dependências, executa lint, testes e build.

---

## CI/CD e automações
Workflows:
- CI: testes, lint, build e report de acessibilidade.
- Release: ao criar tag `v*.*.*`, agendar build e publish (ex.: criar release draft no GitHub).

---

## Checklist de PR / Code Review
- [ ] Mensagens de commit semânticas
- [ ] PR com descrição e linked issue
- [ ] Testes adicionados / atualizados
- [ ] Testes passando no CI
- [ ] Checklist de acessibilidade verificado

---

## Contato
Mantenedor: Ivandro — jardimivandro6@gmail.com
