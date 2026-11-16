# 04. Bing e visibilidade em IA

## Bing Webmaster Tools
- Verificar o site e enviar o sitemap do plugin de SEO. Se aparecer "Erro", reenviar: o arquivo costuma estar certo.
- Instalar o plugin oficial **IndexNow**: avisa o Bing a cada publicação.
- Relatório **AI Performance**: mostra citações do site em respostas do Copilot. Anote a linha de base (normalmente 0).

## Bing Places
- Importar do Google. Para atualizar depois: edite o Google e clique em **Sincronizar** no Bing Places.

## Apple Business Connect
- Gratuito. Cadastrar com os mesmos dados do Google para aparecer no Apple Mapas e na Siri.

## Arquivos para IA
| Arquivo | Para que serve | Como fazer |
|---|---|---|
| `/llms.txt` | Resumo da empresa, serviços e principais páginas para modelos de IA | Snippet que monta o texto e lista os posts automaticamente |
| `/llms-full.txt` | Texto completo dos artigos | Snippet com `noindex` no cabeçalho |
| `/robots.txt` | Sinalizar uso permitido | Acrescentar `Content-Signal: search=yes, ai-input=yes, ai-train=yes` dentro do grupo `User-agent: *` |

Pegadinha do robots.txt: o snippet precisa rodar **depois** do plugin de SEO (prioridade alta no filtro `robots_txt`), senão surge um grupo `User-agent` duplicado.

## Robôs de IA
- Confira no painel da hospedagem se robôs como GPTBot, ClaudeBot, PerplexityBot e OAI-SearchBot estão liberados.
- Testes com user-agent falso a partir de IP comum recebem 403 ou 429 por proteção contra robôs falsos. **Não é bloqueio real.**
- Ferramentas de "nota de visibilidade em IA" de hospedagens podem procurar palavras em inglês (contact, terms). Não renomeie páginas em português por causa disso.

## Teste de presença em IA (mensal)
Pergunte no ChatGPT, Gemini e Copilot:
1. "O que é a <empresa>?"
2. "Empresas de <serviço> em <cidade>"
3. "<Serviço> para <público> em <cidade>"
4. "A <empresa> é confiável?"
5. "Onde a <empresa> atua?"

Anote se o site é citado, se a descrição está certa e quais fontes aparecem. Quando a IA usa diretórios de terceiros em vez do site, priorize: descrição única em todo lugar, schema completo, fichas sem duplicatas e FAQ visível em HTML.
