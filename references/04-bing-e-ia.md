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

## Markdown sob demanda para agentes (Accept: text/markdown)
Ideia: quando um agente de IA pede a página com o cabeçalho `Accept: text/markdown`, o site responde a mesma página em Markdown, com `Content-Type: text/markdown`, `Vary: Accept` e `X-Robots-Tag: noindex`. Visitantes e buscadores continuam recebendo o HTML normal.

O ponto que engana: **o cache de página responde antes do PHP.** O snippet sozinho parece não funcionar, porque o pedido nem chega ao WordPress. A solução tem duas camadas, e as duas são necessárias:

1. **Regra no servidor** que desliga o cache só para pedidos com `text/markdown` no `Accept`. Vai no topo do `.htaccess`, **fora** dos blocos que o plugin de cache gerencia (eles são reescritos). Exemplo ilustrativo para LiteSpeed:
```
# BEGIN MarkdownAgentes
<IfModule LiteSpeed>
RewriteEngine On
RewriteCond %{HTTP:Accept} text/markdown [NC]
RewriteRule .* - [E=Cache-Control:no-cache]
</IfModule>
# END MarkdownAgentes
```
2. **Aviso no código da resposta** para o cache não guardá-la: o snippet deve enviar `X-LiteSpeed-Cache-Control: no-cache` (e acionar o filtro de "não cachear" do plugin). Sem isso, a primeira resposta em Markdown é armazenada e **entregue a visitantes comuns**. Isso aconteceu em teste e só foi desfeito com a limpeza total do cache.

Procedimento seguro (com aprovação humana a cada passo):
- Faça backup do `.htaccess` no próprio servidor antes de mexer e confira que a cópia é idêntica.
- Aplique primeiro a camada 2 (inofensiva, pois hoje nenhum pedido Markdown chega ao PHP) e só depois a regra.
- Teste **sem login** (navegador logado ignora o cache e engana o teste), por exemplo com `curl`:
  - com `Accept: text/markdown`: deve vir `text/markdown` e nenhum `hit` de cache;
  - sem o cabeçalho, duas vezes seguidas: deve vir `text/html` e `hit` na segunda;
  - repita em várias páginas (início, institucional, serviço, blog).
- Tenha a reversão pronta: restaurar o backup e usar "Limpar tudo" do plugin de cache. Confira de novo que o HTML voltou.
- Valor real baixo: serve a pontuação de "preparo para IA" e a leitura limpa por agentes. Faça depois do que mexe com busca e reputação.

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
