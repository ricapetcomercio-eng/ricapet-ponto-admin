# Painel de Ponto — Administração

Site separado (só HTML/JS, sem build) pra gestão do ponto. Acesso restrito aos
funcionários marcados como `admin` no backend (hoje: Geisyanne, Jennifer,
Ricardo, Nivaldo — mude com `scripts/configurar_ponto_admin.py` no
PortalRicapetApp ou a rota `ponto-definir-admins`).

## O que dá pra fazer

- **Solicitações**: ver os pedidos de correção pendentes (funcionário só manda o
  motivo), abrir o dia da pessoa pra ajustar, marcar como aprovada/recusada.
- **Por funcionário**: folha de ponto do período, editar/adicionar/remover
  qualquer batida de qualquer dia (motivo obrigatório, tudo fica auditado),
  **Imprimir** (→ salvar PDF) e baixar **CSV**.
- **Visão geral**: resumo do período por pessoa (dias com ponto, extras,
  faltas, saldo).

## Backend

Tudo bate em `painel-entrega-turbo` (`/api/debug?tipo=ponto-admin-*`), com o
`PONTO_PUBLIC_SECRET` na porta + um token de login de admin (o gate real).
Jornada diária considerada: 8h (constante `JORNADA` no index.html).

## Publicar

```
cd C:\RobotOmie\PainelPontoAdmin
npx vercel deploy --prod
```

Na 1ª vez a Vercel pergunta se cria um projeto novo — responda sim, nome
sugerido `ricapet-ponto-admin`. Depois é só rodar o mesmo comando pra
atualizar.
