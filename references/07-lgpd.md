# 07. LGPD no site

## Aviso de cookies que realmente bloqueia
- Botões **Aceitar** e **Recusar** com o mesmo peso visual.
- Antes da escolha, scripts de rastreamento (Analytics, Tag Manager, Ads, AdSense) ficam desativados: troque o `type` para `text/plain` e reative só após o aceite.
- Compatível com cache: o servidor sempre entrega o HTML com rastreadores bloqueados e o banner oculto; o navegador decide pelo cookie de escolha.
- Recusar apaga cookies de medição já gravados.
- Link "Preferências de cookies" no rodapé para mudar de ideia.
- Teste: zero requisições de rastreamento antes do aceite; carregam depois do aceite; somem após recusar.

**Efeito esperado:** o Analytics passa a contar só quem aceita. Use o Search Console como número oficial de tráfego orgânico.

## Política de Privacidade e Termos de Uso
- Escreva só com fatos verificáveis do site: controlador, contato, ferramentas encontradas no HTML, finalidades.
- Liste ferramentas de terceiros (fontes externas, medição, mensageria).
- Marque para **revisão de advogado** antes de considerar definitivo (encarregado de dados, foro, compartilhamento).

## Formulários e comentários
- Caixa de consentimento obrigatória e desmarcada, com links para Política e Termos.
- Validação no servidor e registro da data do consentimento.
- Moderação manual de comentários e pingbacks desligados.

## Recursos com dados pessoais
- Contadores (curtidas etc.) com hash temporário, sem guardar IP; descrever na política.
- Fotos de pessoas só com termo de uso de imagem; retirar fotos de quem saiu da empresa.
