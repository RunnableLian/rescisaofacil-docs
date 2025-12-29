# 🚀 Rescisão Fácil (Technical Showcase)

> **Live Demo / Production:** [https://www.rescisaofacil.com.br](https://www.rescisaofacil.com.br)

## ⚡ Engineering Overview
Este repositório documenta a arquitetura e as decisões técnicas por trás do **Rescisão Fácil**, uma plataforma de cálculo trabalhista (Tool) projetada para alta performance e escalabilidade via SEO Programático (pSEO).

O objetivo do projeto foi desafiar a stack moderna do **Next.js 14 (App Router)** para entregar cálculos complexos (CLT) com renderização instantânea, superando soluções legadas do mercado em UX e atualização legislativa.

## 🏗️ Arquitetura & Desafios Técnicos

### 1. SEO Programático (pSEO) em Escala
Ao invés de criar páginas genéricas, utilizei a **Static Site Generation (SSG)** para pré-renderizar mais de **500 rotas estáticas** focadas em intenção de busca específica (Long Tail Keywords).
- **Implementação:** Uso de `generateStaticParams` lendo uma base normalizada da CBO (Classificação Brasileira de Ocupações).
- **Resultado:** 500+ páginas indexadas (ex: `/calcular-rescisao-motorista`, `/calcular-rescisao-vendedor`) com load time < 100ms (Edge Cached).

### 2. Lógica Fiscal "Future-Proof" (Regras 2026)
A engine de cálculo foi isolada do framework para permitir testes unitários rigorosos e versionamento de regras fiscais.
- **Diferencial:** Implementação antecipada das tabelas de **Isenção de IRRF (até R$ 5.000,00)** e novas faixas progressivas do INSS, previstas para o Orçamento 2026.
- **Fallback:** O sistema detecta a data de saída (`dataRescisao`) e aplica dinamicamente a regra vigente (2025 legacy vs 2026 projected).

### 3. Performance Mobile & DOM Virtualization
Um dos maiores desafios foi renderizar a árvore de links internos (500+ profissões) sem bloquear a Main Thread em dispositivos móveis.
- **Solução:** Implementação de propriedade CSS `content-visibility: auto` e `contain-intrinsic-size` nos containers de listagem.
- **Impacto:** Redução do DOM Depth inicial e **Score 98+ no PageSpeed Insights (Mobile)**, eliminando penalidades de TBT (Total Blocking Time).

## 🛠️ Tech Stack

| Camada | Tecnologia | Motivação |
| :--- | :--- | :--- |
| **Core** | Next.js 14 (App Router) | Server Components por padrão, zero-bundle-size para lógica de servidor. |
| **Styling** | Tailwind CSS + Shadcn/UI | Design System leve e acessível, fácil manutenção. |
| **Deploy** | Vercel Edge Network | Distribuição global e invalidação de cache inteligente. |
| **Analytics** | GA4 + Server-side Events | Tracking de conversão (`calculate_rescission`) sem impactar o client-side. |
| **Database** | Prisma ORM | Tipagem forte e segurança no acesso aos dados de blog/pSEO. |

## 🔗 Links Oficiais
* [Calculadora CLT 2026 (App)](https://www.rescisaofacil.com.br)
* [Blog Técnico & Notícias](https://www.rescisaofacil.com.br/blog)

---
*Disclaimer: Este repositório serve como documentação pública da arquitetura do projeto. O código-fonte da aplicação comercial é proprietário.*
