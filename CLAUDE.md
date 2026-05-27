# Imersão Hora de Decolar — Contexto do Projeto

Projeto interno de acompanhamento do lançamento da imersão **Hora de Decolar** da Bruna Araujo (@eujuntomilhas). Dashboard HTML puro hospedado no Vercel, repositório no GitHub.

## URLs

- **Dashboard (produção):** https://imersao-hora-de-decolar.vercel.app
- **Repositório:** https://github.com/eujuntomilhas-bit/imersao-hora-de-decolar
- **Página de vendas:** https://imersao-hora-de-decolar.vercel.app/pages/vendas.html

## Estrutura de Arquivos

```
index.html              ← Dashboard principal (hero + faixa + pendências + metas)
assets/
  page.css              ← CSS compartilhado por todas as páginas internas
  logo.png
  logo-verde.png
  mockup.png
pages/
  conteudo.html         ← 01 Conteúdo da imersão
  dia-horario.html      ← 02 Data e horário
  funil.html            ← 03 Funil de vendas (com steps clicáveis)
  captacao.html         ← 04 Prazo de captação e ManyChat
  trafego.html          ← 05 Verba de tráfego
  criativos.html        ← 06 Criativos
  valores.html          ← 08 Lotes, preços e investimento em tráfego
  ex-alunos.html        ← 09 Ex-alunos
  identidade-visual.html← 10 Identidade visual
  cronograma.html       ← 11 Cronograma
  formulario.html       ← 12 Formulário de pesquisa
  publico-dores.html    ← 13 Público e dores
  vendas.html           ← Página de vendas pública
```

## Identidade Visual

Paleta (definida em `assets/page.css` como variáveis CSS):

| Variável         | Hex       | Uso                          |
|------------------|-----------|------------------------------|
| `--musgo`        | `#4F6F52` | Cor principal, headers, CTAs |
| `--salvia`       | `#8FAF9A` | Destaques suaves, barras     |
| `--terracota`    | `#D97A3A` | CTAs de ação, urgência       |
| `--ambar`        | `#E6A15A` | Alertas, pendências          |
| `--offwhite`     | `#F4F1EC` | Background geral             |
| `--creme`        | `#EDE8DF` | Footer, separadores          |
| `--texto`        | `#2C2C2C` | Texto principal              |
| `--texto-suave`  | `#6B6560` | Texto secundário             |

Fontes (Google Fonts):
- **Cormorant Garamond** — títulos elegantes no index
- **Gabriela** — títulos nas páginas internas
- **Caveat** — destaques manuscritos, eyebrows
- **Roboto** — texto corrido

> No `index.html` as variáveis CSS usam nomes curtos (`--musgo`, `--salvia`).  
> No `assets/page.css` usam nomes longos (`--verde-musgo`, `--verde-salvia`).  
> São a mesma paleta — apenas naming diferente entre os dois escopos.

## Dados do Lançamento

| Campo                | Valor                        |
|----------------------|------------------------------|
| Data da imersão      | 20 de junho de 2026          |
| Horário              | 09h00                        |
| Plataforma           | Zoom (ao vivo)               |
| Duração              | ~3h30                        |
| Plataforma de vendas | Kiwify                       |
| Meta de inscritos    | 300 pessoas                  |

### Lotes

| Lote   | Período         | Preço  | Meta acumulada |
|--------|-----------------|--------|----------------|
| Lote 1 | 27/05 – 05/06   | R$ 37  | 80 inscritos   |
| Lote 2 | 05/06 – 12/06   | R$ 57  | 150 inscritos  |
| Lote 3 | 12/06 – 20/06   | R$ 77  | 300 inscritos  |

### Verba de Tráfego (atrelada a inscritos)

| Fase   | Período         | Verba          | Gatilho de liberação         |
|--------|-----------------|----------------|------------------------------|
| Fase 1 | 27/05 – 05/06   | R$ 500         | Início                       |
| Fase 2 | 05/06 – 12/06   | + R$ 1.500     | Se Fase 1 atingir 80 inscritos  |
| Fase 3 | 12/06 – 20/06   | + R$ 6.000     | Se Fase 2 atingir 150 inscritos |
| **Total** |              | **R$ 8.000**   |                              |

## Funcionalidades do Dashboard (index.html)

### Seções
1. **Hero** — logo, descrição, badges de data/hora, grid de mini-cards linkando para as 13 páginas
2. **Faixa verde** — data, horário, plataforma, Lote 1, Lote 2, Lote 3, Kiwify
3. **Próximos passos** — checklist clicável (estado salvo em `localStorage` chave `imersao_proximos_v2`)
4. **Metas de Vendas:**
   - Resumo geral (meta, data, dias de captação)
   - Barra de progresso com marcadores de fase
   - **Histórico diário** — tabela editável + gráfico de barras (chave `imersao_historico_v1`)
   - Cards das 3 fases (Aquecimento / Prova e Desejo / Urgência Final)
   - Simulador de receita com slider (ticket médio R$ 57, conv. CEP 10%, R$ 1.997/aluna)

### localStorage — Chaves usadas
| Chave                    | Conteúdo                                    |
|--------------------------|---------------------------------------------|
| `imersao_proximos_v2`    | Estado das pendências (checklist)           |
| `imersao_inscritos_v1`   | Total de inscritos atual                    |
| `imersao_historico_v1`   | Array `[{data: "YYYY-MM-DD", qtd: N}, ...]` |

## ManyChat — Gatilho de Captação

- **Palavra-chave:** `PLANO DE VOO`
- **Plataforma:** Instagram Direct (via ManyChat)
- **Ação:** Envia automaticamente o link da página de vendas no Direct
- **Uso:** Colocar "Comenta PLANO DE VOO" nos posts de feed, Reels e Stories

## Equipe

| Pessoa   | Papel                                      |
|----------|--------------------------------------------|
| Bruna    | Conteúdo, criativos, pitch, mentoria       |
| Carol    | Envio de convites WhatsApp para ex-alunas  |
| Luis G.  | Tráfego pago (Meta Ads), criativos pagos   |

## Deploy

- Repositório GitHub: `eujuntomilhas-bit/imersao-hora-de-decolar`
- Branch principal: `master`
- Deploy automático via Vercel ao fazer push no `master`
- HTML/CSS/JS puro — sem build, sem dependências, sem framework

## Convenções do Projeto

- Todo HTML é puro — sem framework, sem npm
- Estilos das páginas internas ficam em `assets/page.css`
- Estilos específicos do index ficam inline no `<style>` do `index.html`
- Estado interativo salvo sempre em `localStorage`
- Commit messages em português descrevendo o que mudou por seção
