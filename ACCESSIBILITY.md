# Acessibilidade (WCAG 2.1 AA) — Checklist e Implementação

Este documento descreve as ações implementadas e a checklist a seguir para garantir conformidade com WCAG 2.1 Nível AA.

## Estrutura semântica
- Usar elementos: header, nav, main, aside, footer.
- Usar headings (h1..h6) em ordem lógica.

## Navegação por teclado
- Todos os controles são alcançáveis via teclado (Tab / Shift+Tab).
- Indicar estado de foco com outline visível.
- Elementos personalizados devem possuir `tabindex="0"` e tratar `keydown` para Enter/Space.

## Suporte a leitores de tela
- Fornecer labels e `aria-label` quando necessário.
- Usar `role="navigation"`, `role="main"` quando o elemento não for nativo.

## Contraste
- Garantir contraste mínimo 4.5:1 para texto normal e 3:1 para texto grande.
- Fornecer tema de alto contraste.

## Modo escuro
- Respeitar `prefers-color-scheme` e fornecer variáveis CSS para cores acessíveis.

## Ferramentas sugeridas
- axe-core, pa11y, Lighthouse

## Verificações
- [ ] Teste com leitor de tela (NVDA/VoiceOver)
- [ ] Teste com teclado apenas
- [ ] Teste de contraste (axe / contrast checker)
