# Memória do projeto — Conteúdo e SEO dos sites H2G

Leia este arquivo antes de qualquer tarefa. Ele resume o que já foi feito e decidido, para a conversa começar sabendo de tudo.

## Quem e o quê

- **Fernando** (Luis Fernando) gerencia os sites da H2G: **HigiClear** (higiclear.com), **HyGiBras** (hygibras.com) e **Instituto da Limpeza**. Setor: limpeza profissional B2B.
- **Objetivo único:** fazer **empresas** (indústrias, cozinhas industriais, hospitais, escolas, condomínios, facilities) **entrarem em contato com intenção de compra**. Tráfego por si só não interessa.
- Idioma de trabalho: português do Brasil. Fernando não é técnico — explicar sem jargão (nada de "push", "canonical", "CLAUDE.md" sem traduzir).

## Ferramentas prontas neste repositório

- **Skill `artigo-humanizado`** em `.claude/skills/artigo-humanizado/` — escreve e revisa artigos/páginas no estilo editorial da HigiClear. Acionar com `/artigo-humanizado tema`. Ela lê:
  - `exemplos/rdc216.md` — artigo real de referência de voz
  - `higiclear-fatos.md` e `hygibras-fatos.md` — dados confirmados de cada empresa (endereços, telefones, linhas de produto, serviços). **Nunca inventar dado; o que não estiver ali vai como `[confirmar]`.**
- Artigos produzidos ficam em `artigos/` (ex.: `produtos-de-limpeza-jundiai.md`).

## O que o Search Console mostrou (nov/2026, hygibras.com, 16 meses)

- Tráfego caiu **–56% em um ano** (jul–out/2025: 39 mil cliques → jul–out/2026: 17 mil). Duas causas:
  1. **Respostas de IA do Google** (nov/2025–jan/2026): impressões subiram, posição melhorou, cliques caíram. O conteúdo informativo ("o que é hipoclorito", "flotador") é lido pela IA e não gera clique. **Esse tráfego não volta. Não investir mais em artigo "o que é".**
  2. **Migração www → sem www** (fev–mar/2026): dois meses de buraco e as mesmas buscas ficaram ~1 posição pior. Redirecionamentos estão corretos (301). Verificar se foi feita a "Mudança de endereço" no Search Console.
- **90% do tráfego não tem intenção de compra.** Só ~1% é transacional, ~0,2% local.
- Buscas pelas **marcas próprias** (Optigerm, Freeco, Nobby, Garra) têm ~9 mil impressões e CTR < 1% — as páginas de produto não estão em 1º lugar. Corrigir é barato e urgente.
- **Páginas de segmento** (hospitalar, condomínio, escolas, hotéis, industrial, distribuidora) estão entre a posição 9 e 35. São as landing pages B2B e precisam de conteúdo.
- **Unidades físicas:** Ribeirão Preto (Recreio Anhanguera) e Campinas (Vila Nova). A página de Ribeirão tinha **0 cliques** (texto sobre a cidade, sem orçamento, título "como escolher"). **Campinas não tem página.**
- Em todas as páginas, o botão "WhatsApp" no meio do texto é de **compartilhar**, não de contato. O contato real (`hygibras.com/whats`, 0800-505-2888) só está no cabeçalho/rodapé. **Toda página comercial precisa de bloco de contato no corpo.**

## O que o Analytics mostrou (sessão do terminal, nov/2026)

Taxa de lead por página de entrada (90 dias):
- `/reducao-de-despesas-com-produtos-de-limpeza` — **8,1% (258 leads)**, a que mais converte no site; tráfego vem de fora do Google (RD Station/direto). A promessa "reduza suas despesas" é a que faz o comprador agir.
- `/comodato/` 8,5% · `/segmentos/cozinha-industrial` 10,5% · `/segmentos/distribuidora` 16,7% · Rio Preto 10,5% · São Carlos 6,2% · hospitalar 5,9%
- Artigos gigantes: RDC 216 2,2% · diluição 1,3% · DDS 0,6% · cloro 0,8%
- Ribeirão Preto: 1 sessão em 90 dias. `/lista-de-produtos-de-limpeza/`: 2 sessões.
- Cronograma de limpeza (material para baixar) converte 7,6% — melhor artigo; modelo para lead magnet.

### Cuidados ao ler o Analytics (medição distorcida)

- **Robôs em 18–31/out/2026:** ~15 mil usuários estrangeiros (EUA, Singapura, Hong Kong, Indonésia, Vietnã…), canal "Direto", sem retorno, caindo em `/carrinho` (0,3 s) e "(não definido)". Infla o canal Direto; o **Google orgânico é o canal real principal**. Analisar só Brasil ou excluir esse período.
- **`generate_lead` está inflado:** 1.845 no trimestre, mas `form_submit` = 230 e "RD Popup e WhatsApp" = 37. Dispara várias vezes por visita e também para cliente logado (`/minha-conta`, `/central`, `/onboarding`). **Contatos reais: entre 37 e 230 por trimestre (provável ~100).** Usar a taxa só para comparar páginas, nunca como número de contatos.
- Falta descobrir a **origem do tráfego de `/reducao-de-despesas`** (Aquisição de tráfego → Página de destino + Origem/mídia). Se for Google Ads, ampliar essa campanha.

## Prioridades decididas (ordem)

1. **Medição primeiro**: evento `generate_lead` por envio de formulário, `click_whatsapp_contato`, `click_0800` no Google Tag Manager. Sem isso não dá pra medir melhoria.
2. **Blocos de CTA "Reduza suas despesas" + comodato** dentro dos artigos RDC 216 e diluição (4.100 sessões/trimestre a 1,7% → potencial +150–250 leads).
3. **Reescrever Ribeirão Preto** e **criar Campinas** no padrão da página de Rio Preto (que funciona).
4. **Página `/lista-de-produtos-de-limpeza/`** virar checklist por segmento para baixar (captura de lead).
5. **Páginas de produto das marcas próprias** em 1º lugar no Google.
6. **Expandir `/comodato/`** (hoje 225 palavras) e **reescrever a página de segmento "distribuidora"** (H1 restringe a comércio/varejo).
7. Google Perfil da Empresa para as duas unidades.

**Não fazer:** otimizar CTR de artigo informativo; escrever novos artigos "o que é X".

## Como trabalhar

- Branch de trabalho: `claude/skill-creation-text-iztJ5`. Salvar e enviar sempre que concluir algo, para outras conversas enxergarem.
- Entregas para o Fernando: texto no chat + arquivo em `artigos/` + e-mail para `luis.fernando.alves68@gmail.com` quando ele pedir.
- O site hygibras.com bloqueia robôs sem User-Agent de navegador; usar UA de Chrome ao ler páginas.
