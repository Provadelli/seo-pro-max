# 01. Mapa do Projeto

O Mapa do Projeto é o primeiro entregável de qualquer trabalho de SEO. Ele evita a pergunta "onde fica isso mesmo?" e impede que decisões antigas sejam desfeitas. Guarde-o junto do projeto (privado, se tiver dados internos).

## Como montar (1 a 2 horas)

1. **Stack**: CMS, tema, construtor, plugin de SEO, plugin de código, cache, CDN, hospedagem, DNS, e-mail, medição.
2. **Inventário de páginas**: ID, URL, título atual, descrição atual, H1, indexada ou não.
3. **Inventário de código**: cada snippet ou trecho customizado com número, função e como desativar.
4. **Peças do construtor**: cabeçalho, rodapé, menus, widgets importantes (IDs).
5. **Painéis externos**: Search Console, Perfil da Empresa, Bing, diretórios, redes, reputação. Anote só o caminho, nunca senhas.
6. **Identidade oficial**: razão social, nome fantasia, endereço, telefone, site, área de atuação, serviços oferecidos e não oferecidos.
7. **Decisões do responsável**: o que foi aprovado, recusado e não deve voltar.
8. **Regras de estilo**: tom, palavras proibidas, pontuação, emojis.

## Modelo

```markdown
# Mapa do Projeto: <empresa>

## Stack
| Camada | Ferramenta | Observação |
|---|---|---|

## Onde mexer
| Quero mexer em... | Onde fica | Como desfazer |
|---|---|---|
| Título e descrição de página | Editor da página > painel SEO | Restaurar texto do backup |
| Dados estruturados da empresa | Snippet N | Desativar snippet |
| llms.txt | Snippet N | Desativar snippet |
| robots.txt | Plugin SEO + snippet N | Desativar snippet |
| Redirecionamentos | Snippet N / plugin | Remover regra |
| Rodapé | Template N | Restaurar widget do backup |
| Menu | Menu N | Remover item |
| Cache | Plugin de cache + CDN | Desligar opção + limpar |

## Páginas
| Página | ID | URL | Indexada |
|---|---|---|---|

## Identidade oficial (NAP)
- Nome:
- Endereço:
- Telefone:
- Site (sempre https, sem www se for o canônico):
- Área de atuação:
- Serviços oferecidos:
- Serviços NÃO oferecidos:

## Decisões (não reabrir)
| Data | Decisão | Motivo |
|---|---|---|

## Regras de estilo
-

## Histórico
| Data | O que mudou | Onde | Como desfazer |
|---|---|---|---|
```

## Dica de organização do código

Concentre customizações em **snippets numerados com nome descritivo** (ex.: "Schema da empresa", "llms.txt", "Aviso de cookies"), em vez de espalhar código no tema. Assim cada mudança tem um único lugar e um único botão de desligar.
