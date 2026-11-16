# 02. Técnico, desempenho e página a página (WordPress)

## Auditoria técnica (somente leitura primeiro)
- Todas as URLs do sitemap respondem 200? Canonical aponta para a versão https sem variações?
- Redirecionamentos em cadeia (`http://www` > `https://www` > `https://`)? Se a cadeia vem da hospedagem, use sempre a URL canônica nos links externos.
- Páginas não indexadas no Search Console: separe as técnicas e inofensivas (wp-admin, feeds, parâmetros) das que importam.
- Meta description duplicada (tema e plugin de SEO imprimindo juntos).
- Scripts duplicados (Tag Manager inserido por dois plugins conta visitas em dobro).
- Imagens pesadas (PNG de 1 MB exibido em 236 px).
- Fontes e preloads quebrados, bibliotecas carregadas duas vezes (jQuery, ícones de CDN antigo).
- Vídeos incorporados carregando antes do clique.
- Hierarquia de títulos (H1 único, sem saltos) e contraste (axe-core).

## Desempenho
| Ação | Ganho típico | Cuidado |
|---|---|---|
| Cache de página | Tempo de resposta de ~2 s para ~0,2 s | Se houver aviso de cookies, o HTML deve ser igual para todos (decidir no navegador) |
| Imagens em WebP no tamanho exibido | Página interna de nota 55 para 80+ | Manter original na biblioteca |
| Minificar CSS e JS, fontes assíncronas | +5 a +10 na nota mobile | Testar menus e formulários |
| Combinar CSS | Muitos arquivos viram 1; LCP menor | Conferir visual de todas as páginas |
| YouTube com imagem e carregamento só no clique | Remove cookies de terceiros e peso | |
| Remover módulos sem uso (login social, eventos extras) | Menos JS e cookies | Perguntar se alguém usa |

O que normalmente **não** vale a pena: refazer uma imagem principal que já é leve e prioritária, trocar fonte variável por estáticas (fica maior), mexer no JS central do construtor.

Meça em **pagespeed.web.dev**; dados de campo (CrUX) levam 28 dias para refletir.

## Segurança básica (sem plugin pago)
- Backup da hospedagem antes de atualizar plugins e o WordPress.
- Desligar XML-RPC se não for usado, esconder a lista pública de usuários, remover cabeçalhos que revelam versões, cabeçalhos de segurança.
- Limitar tentativas de login.
- Revisar contas administradoras antigas.
- E-mail do site por SMTP autenticado; SPF no DNS; depois DKIM e DMARC.
- Documente essas medidas no Mapa privado, nunca em repositório público.

## Página a página

### Títulos e descrições
- Título até 60 caracteres, com o serviço e a marca: `Terceirização de portaria para condomínios | Marca`.
- Descrição até 155 caracteres: o que faz, para quem, onde, convite.
- Priorize páginas com **muitas impressões e poucos cliques** no Search Console.
- Modelo global do plugin: `%%title%% %%sep%% Marca` (evita o nome longo do site).

### Editar Yoast com segurança
```js
wp.data.dispatch('yoast-seo/editor').updateData({ title: '...', description: '...' });
wp.data.dispatch('core/editor').savePost();
```
Alterar só o meta no banco não muda a saída: o Yoast lê o registro "indexable".

### Dados estruturados
- Organization: razão social, CNPJ (ou equivalente), endereço, telefone, área atendida, redes (`sameAs`), serviços.
- Service nas páginas de serviço, FAQPage onde houver perguntas, Article nos posts.
- Arquivos de categoria e autor finos: `noindex` para não poluir o índice.
- Imagem padrão de compartilhamento 1200x630.

### Links internos
- Menu "Serviços" com todas as páginas de serviço.
- Bloco "Leia também" nas páginas de serviço apontando para artigos relacionados, e vice-versa.
- Rodapé com links legais e de contato.
