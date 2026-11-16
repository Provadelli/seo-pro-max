<div align="center">

![SEO pro max: onde mexer, como mexer com segurança e o que já foi decidido](assets/banner.png)

# SEO pro max

**Um método completo de SEO, SEO local e visibilidade em IA, em formato de Skill para o Claude.**

Mapeie o site, meça, corrija, publique com segurança e acompanhe o resultado, sem se perder em painéis.

![Formato](https://img.shields.io/badge/formato-Claude%20Skill-1d6ad2)
![Conteúdo](https://img.shields.io/badge/conte%C3%BAdo-Markdown%20%2B%201%20imagem-22A068)
![Scripts](https://img.shields.io/badge/scripts%20execut%C3%A1veis-nenhum-22A068)
![Idioma](https://img.shields.io/badge/idioma-pt--BR-1d6ad2)
[![skills.sh](https://skills.sh/b/Provadelli/seo-pro-max)](https://skills.sh/Provadelli/seo-pro-max)

</div>

---

## Sumário

- [O que é](#o-que-é)
- [Para quem serve](#para-quem-serve)
- [Como o método funciona](#como-o-método-funciona)
- [Segurança: por que é tranquilo baixar](#segurança-por-que-é-tranquilo-baixar)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Instalação](#instalação)
- [Como usar no dia a dia](#como-usar-no-dia-a-dia)
- [Princípios](#princípios)
- [Origem: o caso Shine Rio](#origem-o-caso-shine-rio)
- [Perguntas frequentes](#perguntas-frequentes)
- [Licença](#licença)

---

## O que é

**SEO pro max** é uma *Skill* do Claude: uma pasta de instruções em Markdown que o Claude consulta quando a tarefa envolve SEO. Ela reúne, em fases, o método que foi aplicado e refinado em um projeto real:

- montar o **Mapa do Projeto** (onde mexer, o que já foi decidido, como desfazer);
- registrar a **linha de base** antes de qualquer mudança;
- corrigir **técnico e desempenho** em WordPress (cache, imagens, scripts duplicados, schema);
- otimizar **página a página** (títulos, descrições, H1, links internos);
- cuidar do **Google**: Search Console e Perfil da Empresa, com postagens e avaliações;
- trabalhar **Bing e IA**: IndexNow, `llms.txt`, `robots.txt` com Content-Signal e teste de presença em IAs;
- produzir **conteúdo**: páginas de serviço, artigos com FAQ e reaproveitamento em redes;
- alinhar a **presença externa**: NAP, diretórios, LinkedIn, reputação e sites de emprego;
- cumprir a **LGPD**: cookies que bloqueiam de verdade, política, termos e consentimento;
- **medir e relatar** com comparação de 28 contra 28 dias.

## Para quem serve

- Empresas de serviço (B2B ou locais) que dependem de busca no Google e no Maps.
- Sites em **WordPress** com Elementor e Yoast (o método vale para outros CMS; as pegadinhas técnicas são de WordPress).
- Quem cuida de marketing ou TI e quer uma rotina organizada, sem ferramenta paga.

## Como o método funciona

```text
0. Mapa do Projeto  ->  1. Linha de base  ->  2. Técnico  ->  3. Página a página
        |                                                            |
        v                                                            v
9. Rotina mensal  <-  8. LGPD  <-  7. Presença externa  <-  6. Conteúdo  <-  4/5. Google, Bing e IA
```

Cada mudança segue o **fluxo de alteração segura**: localizar, fazer backup, mostrar antes e depois, aplicar com aprovação, limpar caches, conferir como visitante, avisar buscadores e registrar como desfazer.

## Segurança: por que é tranquilo baixar

> Resumo: esta skill é **só texto**. Ela não executa nada, não instala nada, não pede senha e não acessa a internet. A política completa, a lista de arquivos e as impressões digitais (SHA-256) estão em [`SECURITY.md`](SECURITY.md).

| Garantia | Detalhe |
|---|---|
| Só texto e uma imagem | Arquivos `.md` (Markdown), uma imagem de capa (`assets/banner.png`), a licença (`LICENSE`) e o `.gitattributes`. Não há `.exe`, `.js`, `.ps1`, `.sh`, `.py`, `.bat` nem macros. |
| Limites escritos na própria skill | O `SKILL.md` tem uma seção "Limites de segurança" que o Claude segue com prioridade: sem execução, sem credenciais, aprovação humana, conteúdo de páginas tratado como dado. |
| Integridade verificável | Cada arquivo tem SHA-256 publicado no `SECURITY.md`. |
| Licença aberta | MIT: pode usar, copiar e adaptar. |
| Nada roda sozinho | A skill não instala nada, não executa comandos e não acessa a internet. Ela só orienta. |
| Sem credenciais | Não contém senhas, tokens, chaves de API nem e-mails pessoais. |
| Sem dados de clientes | É um método genérico; não traz dados internos de nenhuma empresa. |
| Ação humana obrigatória | O método exige aprovação antes de qualquer alteração pública e proíbe digitar senhas. |
| Auditável | Por ser texto puro, dá para ler tudo antes de usar em poucos minutos. |

Para conferir depois de baixar:

```bash
# 1. lista arquivos fora do esperado (o resultado deve vir vazio)
find seo-pro-max -type f ! -path "*/.git/*" ! -name "*.md" ! -name "LICENSE" ! -name ".gitattributes" ! -path "*/assets/banner.png"

# 2. confere as impressões digitais com a tabela do SECURITY.md
cd seo-pro-max && sha256sum LICENSE README.md SKILL.md assets/banner.png references/*.md .gitattributes
```

No Windows (PowerShell):

```powershell
# 1. arquivos fora do esperado (deve vir vazio)
Get-ChildItem seo-pro-max -Recurse -File -Force | Where-Object { $_.FullName -notmatch '\\\.git\\' -and $_.Extension -ne ".md" -and $_.Name -notin "LICENSE",".gitattributes","banner.png" }

# 2. impressões digitais
Get-ChildItem seo-pro-max -Recurse -File -Force | Where-Object { $_.FullName -notmatch '\\\.git\\' } | Get-FileHash -Algorithm SHA256
```

## Estrutura do projeto

```text
seo-pro-max/
├── README.md                          Este arquivo
├── SKILL.md                           Ponto de entrada: limites de segurança, princípios, fases, fluxo seguro
├── SECURITY.md                        Política de segurança, lista de arquivos e SHA-256
├── LICENSE                            Licença MIT
├── .gitattributes                     Mantém os arquivos idênticos em qualquer sistema
├── assets/
│   └── banner.png                     Imagem de capa (só ilustração)
└── references/
    ├── 01-mapa-do-projeto.md          Como montar o mapa de "onde mexer" (com modelo pronto)
    ├── 02-tecnico-wordpress.md        Auditoria, desempenho, segurança básica, títulos e schema
    ├── 03-google.md                   Search Console, Perfil da Empresa, postagens e avaliações
    ├── 04-bing-e-ia.md                Bing, IndexNow, Apple, llms.txt, robots.txt, teste em IAs
    ├── 05-conteudo.md                 Páginas de serviço, artigos, blog e reaproveitamento
    ├── 06-presenca-externa.md         NAP, textos oficiais, diretórios, LinkedIn, reputação
    ├── 07-lgpd.md                     Cookies que bloqueiam de verdade, política e consentimento
    └── 08-medicao-e-relatorios.md     Linha de base, leitura dos números e modelo de relatório
```

O `SKILL.md` é curto de propósito: o Claude abre só a referência que a tarefa pede.

## Instalação

### Pelo skills.sh (recomendado)

A skill está no diretório [skills.sh](https://skills.sh/Provadelli/seo-pro-max). Com o Node.js instalado, rode:

```bash
npx skills add Provadelli/seo-pro-max
```

O comando usa a ferramenta oficial `skills` (Vercel, código aberto em [vercel-labs/skills](https://github.com/vercel-labs/skills)). Ela baixa a skill **deste repositório** e copia os arquivos para a pasta de skills do seu agente. A skill continua sendo só texto; nada dela é executado.

> **Privacidade:** a ferramenta `skills` envia dados anônimos de uso, que alimentam o ranking do skills.sh. Para desligar, defina `DISABLE_TELEMETRY=1` ou `DO_NOT_TRACK=1` antes do comando.

Depois de instalar, confira a integridade com as impressões digitais do [`SECURITY.md`](SECURITY.md).

### Claude Code (computador)

```bash
git clone https://github.com/Provadelli/seo-pro-max.git ~/.claude/skills/seo-pro-max
```

No Windows, a pasta de skills fica em `%USERPROFILE%\.claude\skills\`.

### Claude.ai (aplicativo ou web)

1. Baixe em **Code > Download ZIP**.
2. Em **Configurações > Capacidades > Skills**, envie o ZIP.
3. Ative a skill **seo-pro-max**.

### Só consultar

Leia os arquivos aqui no GitHub, como um manual.

## Como usar no dia a dia

Peça em linguagem natural; a skill é acionada quando o assunto é SEO.

| Você pede | O que a skill faz |
|---|---|
| "Audita o SEO do meu site" | Monta o Mapa do Projeto e a linha de base antes de propor qualquer coisa |
| "Melhora o título das páginas de serviço" | Prioriza as que têm muitas impressões e poucos cliques, mostra antes e depois e aplica pelo editor |
| "Por que caíram os cliques?" | Compara 28 contra 28 dias e separa buscas de marca das genéricas |
| "Quero aparecer no ChatGPT" | Aplica llms.txt, Content-Signal, schema e roda o teste de 5 perguntas |
| "Faz um post para o Google" | Usa a estrutura problema, solução, prova e convite, e pede aprovação |
| "Prepara o relatório do mês" | Gera resumo, antes e depois e próximos passos |

## Princípios

1. Aprovação antes de publicar.
2. Só fatos; nada inventado.
3. Gratuito primeiro.
4. Nunca digitar senhas.
5. Backup e instrução de reversão para tudo.
6. Uma mudança por vez, conferida como visitante.
7. Decisão tomada não volta.
8. Medir 28 contra 28 dias.

## Origem: o caso Shine Rio

Este método nasceu do trabalho de SEO feito entre outubro e novembro de 2026 para a **Shine Rio**, empresa de terceirização de portaria, limpeza e facilities sediada no Rio de Janeiro ([shinerio.com](https://shinerio.com)).

Nesse projeto, o método levou a:

- site redesenhado e mais rápido, com tempo de resposta de cerca de 1,9 s para 0,2 s;
- 6 páginas de serviço e um blog com artigos e FAQ;
- aviso de cookies em conformidade com a LGPD;
- arquivos para IA (`llms.txt` e Content-Signal);
- primeiras citações no Bing AI Performance;
- crescimento de impressões nas páginas de serviço, de algumas dezenas para algumas centenas em cerca de um mês.

A skill guarda o **método**. Os dados internos da empresa ficam fora do repositório.

## Perguntas frequentes

**Preciso saber programar?**
Não. O Claude explica cada passo e pede aprovação antes de agir.

**Funciona fora do WordPress?**
As fases e os princípios sim. As pegadinhas técnicas são específicas de WordPress, Elementor e Yoast.

**Onde ficam os dados do meu projeto?**
No seu Mapa do Projeto, que você cria a partir do modelo em `references/01-mapa-do-projeto.md` e guarda em local privado.

**A skill pode quebrar meu site?**
Sozinha, não: ela não executa nada. Toda alteração passa por você e tem instrução de reversão.

**O Claude vai considerar a skill segura?**
A skill foi escrita para isso: só texto, limites de segurança explícitos no `SKILL.md`, nenhuma instrução para executar código, baixar arquivos ou lidar com senhas, e integridade conferível pelo `SECURITY.md`. Ainda assim, revise qualquer skill antes de instalar; esta foi feita para que essa revisão seja rápida.

## Licença

[MIT](LICENSE). Uso livre, inclusive comercial, mantendo o aviso de licença.

<div align="center">

Feito para acabar com o "onde fica isso mesmo?".

</div>
