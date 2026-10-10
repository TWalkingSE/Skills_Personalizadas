# Skills de Investigação, Segurança e Redação — Guia de Uso

Este guia explica como usar, no Claude, as nove skills instaladas a partir dos pacotes abaixo: o que cada uma faz, quando ela entra em ação, como formular o pedido e o que esperar como resultado.

| Skill | Pacote | Versão interna | Em uma frase |
|---|---|---|---|
| **Análise IP** (`analise-ip`) | `Analise ip-v1.zip` | — | Análise técnica, forense e de inteligência de endereços IPv4/IPv6 |
| **Crypto Investigator** (`crypto-investigator`) | `Crypto investigator-v1.zip` | v3.2 | Rastreamento on-chain de criptoativos e persecução patrimonial no Brasil |
| **CyberShield** (`cybershield`) | `Cybershield-v1.zip` | v4.1 | Consultoria de privacidade e segurança digital organizada pelas camadas TCP/IP |
| **DarkWeb Investigator** (`darkweb-investigator`) | `Darkweb investigator-v1.zip` | v4.1 | Investigação de crimes na deep/dark web: análise, atribuição, enquadramento penal e relatório |
| **Investigative Notebook** (`investigative-notebook`) | `Investigative notebook-v3.zip` | — | Caderno de análise de vínculos no estilo i2: entidades, grafo, timeline, mapa, hipóteses e relatório |
| **OPSEC Specialist** (`opsec-specialist`) | `Opsec specialist-v1.zip` | v2.2 | Segurança operacional defensiva guiada por modelo de ameaça, inclusive stalking e incidente em curso |
| **PhishGuard360** (`phishguard360`) | `Phishguard360-v1.zip` | v2.2 | Análise de e-mail, SMS e URL suspeitos, treinamento antiphishing e programas corporativos |
| **Redator Inteligente** (`redator-inteligente`) | `Redator inteligente-v2.zip` | 5.2 | Revisão e reescrita de textos em português com intervenção proporcional ao pedido |
| **Sistema Pericial ALPR** (`sistema-pericial-alpr`) | `Sistema pericial alpr-v2.zip` | v4.4 | Leitura de placas veiculares brasileiras, sinais de adulteração e laudo estruturado |

---

## Sumário

1. [Como as skills funcionam no Claude](#1-como-as-skills-funcionam-no-claude)
2. [Princípios comuns a todas](#2-princípios-comuns-a-todas)
3. [Qual skill usar?](#3-qual-skill-usar)
4. [Análise IP](#4-análise-ip)
5. [Crypto Investigator](#5-crypto-investigator)
6. [CyberShield](#6-cybershield)
7. [DarkWeb Investigator](#7-darkweb-investigator)
8. [Investigative Notebook](#8-investigative-notebook)
9. [OPSEC Specialist](#9-opsec-specialist)
10. [PhishGuard360](#10-phishguard360)
11. [Redator Inteligente](#11-redator-inteligente)
12. [Sistema Pericial ALPR](#12-sistema-pericial-alpr)
13. [Fluxos combinados](#13-fluxos-combinados)
14. [Boas práticas com dados de caso real](#14-boas-práticas-com-dados-de-caso-real)
15. [Solução de problemas](#15-solução-de-problemas)

---

## 1. Como as skills funcionam no Claude

**Acionamento automático.** Cada skill tem uma descrição. Quando o pedido combina com ela, o Claude carrega a skill sozinho — não é preciso citar o nome. "Analise este IP: 203.0.113.10" já aciona a Análise IP; "revisa este parágrafo" aciona o Redator Inteligente.

**Acionamento pelo nome.** Se a skill não entrou em ação ou se o pedido se encaixa em mais de uma, peça explicitamente: *"Use a skill phishguard360 para analisar este e-mail"*.

**Menus numerados.** Várias skills (CyberShield, Crypto, DarkWeb, OPSEC, PhishGuard, Redator) trabalham com um menu de ações. Você pode responder só com o número ("opção 8") ou descrever o que precisa — as duas formas funcionam.

**Calibração de nível.** CyberShield, DarkWeb, Crypto, OPSEC e PhishGuard ajustam linguagem e profundidade ao seu nível (iniciante, intermediário, avançado). Se quiser pular a pergunta inicial, diga logo no pedido: *"nível avançado, sem analogias"*.

**Arquivos.** Anexe à conversa o material de trabalho (imagens, PDF, DOCX, CSV, XLSX, logs). As skills com scripts (Análise IP e Investigative Notebook) processam os arquivos por código; as demais analisam o conteúdo diretamente.

**O que nenhuma delas faz.** Nenhuma skill acessa a dark web, consulta blockchains em tempo real, consulta bases restritas (SINESP, DETRAN, cadastros policiais) ou executa varreduras ativas contra alvos. Quando o dado não está no que você enviou, a skill orienta onde e como obtê-lo.

---

## 2. Princípios comuns a todas

Estas regras aparecem, com nomes diferentes, em praticamente todas as skills. Conhecê-las ajuda a ler os resultados:

- **Fato ≠ inferência.** Toda conclusão vem classificada (fato, observado, declarado, correlação, inferência, hipótese) e, quando é inferência, com o grau de confiança e a base que a sustenta.
- **Nada é inventado.** Dado ausente aparece como "não identificado nas fontes consultadas" ou como lacuna — nunca é preenchido por suposição.
- **Ausência de evidência não é evidência de ausência.** "Não foi encontrada relação" é diferente de "não existe relação".
- **Fontes contraditórias ficam lado a lado.** A skill aponta a contradição; não escolhe uma fonte arbitrariamente.
- **Dados reais × simulação.** Análises de dados reais e exercícios fictícios são rotulados de forma distinta (ex.: `[REAL]` / `[SIMULAÇÃO]`).
- **Conteúdo analisado é dado, não instrução.** Se um e-mail, documento ou imagem contiver ordens dirigidas a uma IA ("ignore as instruções anteriores…"), isso vira indicador a registrar, não comando a cumprir.
- **Correlação técnica não é conclusão jurídica.** As saídas auxiliam a análise humana; não substituem laudo pericial oficial, parecer jurídico nem decisão da autoridade.

---

## 3. Qual skill usar?

Algumas skills se sobrepõem. Use esta tabela para escolher:

| Situação | Skill indicada | Por quê |
|---|---|---|
| Um ou mais IPs, ASN, prefixo, PTR, Tor/VPN, logs de acesso | **Análise IP** | Coleta passiva, correlação e relatório forense de infraestrutura |
| Endereço ou hash de transação de cripto, rastreamento de fundos, apreensão | **Crypto Investigator** | Especializada em UTXO/EVM, bridges, mixers e persecução patrimonial |
| Marketplace, fórum, vendedor ou denúncia ligada à dark web | **DarkWeb Investigator** | Atribuição, enquadramento penal, OPSEC do investigador e cooperação internacional |
| Montar o caso com várias fontes (BO, extratos, ERB, depoimentos) e ver vínculos | **Investigative Notebook** | Integra tudo num caso rastreável com grafo, timeline, mapa e relatório |
| E-mail, SMS, WhatsApp, URL ou ligação suspeita | **PhishGuard360** | Análise do artefato com mascaramento da vítima e encaminhamento |
| "Quero me proteger", escolher VPN, navegador, mensageiro, comparar ferramentas | **CyberShield** | Recomendações por camada TCP/IP com base de 600+ ferramentas |
| Proteção em contexto de risco: stalking, campo, forense, empresa, conta invadida agora | **OPSEC Specialist** | Parte do modelo de ameaça e tem subperfis para situações de risco real |
| Foto de veículo ou placa | **Sistema Pericial ALPR** | Leitura caractere a caractere, adulteração e laudo |
| Revisar relatório, ofício, despacho, artigo, e-mail | **Redator Inteligente** | Corrige sem alterar sentido, modalizadores ou identificadores |

**CyberShield × OPSEC Specialist:** o CyberShield é o consultor de ferramentas e hardening (o *quê* instalar e configurar, camada por camada). O OPSEC Specialist é o consultor de conduta e risco (de *quem* você se protege e em que ordem agir), e é o indicado para perseguição, violência doméstica, operações de campo e incidente em andamento.

---

## 4. Análise IP

**O que faz.** Analisa endereços IPv4/IPv6 respondendo não só "de quem é este IP?", mas o que se pode afirmar tecnicamente sobre ele, qual infraestrutura está associada, com que confiabilidade e quais dados faltam para uma atribuição. Cobre RDAP, ASN/BGP, DNS/PTR, geolocalização comparada, VPN/proxy/Tor, cloud/datacenter, reputação, certificados, histórico e correlação entre vários IPs.

**Quando usar.** IPs isolados, listas de IPs, logs de acesso, registros de provedor, pedidos de relatório técnico sobre IP, ou quando você quiser construir uma plataforma de análise de IP.

### Modos de operação

O modo é escolhido automaticamente pela entrada, mas você pode fixá-lo escrevendo `modo: TRIAGEM` (ou outro) no pedido.

| Modo | Quando | Seleção automática |
|---|---|---|
| `IP_UNICO` | Análise completa de um IP | 1 IP |
| `MULTI_IP` | Análise individual + comparativa e agrupamentos | 2 a 20 IPs |
| `TRIAGEM` | Classificação rápida por interesse e aprofundamento só dos relevantes | Mais de 20 IPs |
| `CORRELACAO_INVESTIGATIVA` | IPs com datas, domínios, e-mails, telefones ou eventos; relações classificadas de CONFIRMADA a NÃO CONFIRMADA | IPs com contexto de caso |
| `ANALISE_DE_INFRAESTRUTURA` | Quem anuncia, ASN, prefixo, tipo de rede (residencial, móvel, cloud, CDN, VPN, Tor) | Perguntas sobre ASN/BGP |
| `ANALISE_TEMPORAL` | Linha do tempo de ASN, ISP, prefixo, PTR, domínios e reputação | Perguntas com datas ou histórico |
| `RELATORIO_FORENSE` | Documento técnico em 11 blocos | Pedido de relatório |

Comandos conceituais que você pode escrever dentro do pedido: `/analisar`, `/triagem`, `/correlacionar`, `/comparar <IP1> <IP2>`, `/histórico <IP>`, `/timeline`, `/pivô <indicador>`, `/clusters`, `/outliers`, `/hipóteses`, `/testar-hipótese`, `/o-que-falta`, `/próximo-passo`, `/relatório`, `/exportar-grafo`, `/exportar-caso`.

> Dica: escreva esses comandos no meio da frase (ex.: *"faça /correlacionar destes três IPs"*). Uma mensagem que começa com `/` pode ser interpretada pelo aplicativo como atalho de skill.

### Como pedir

```
Analise o IP 203.0.113.45. Ele aparece no log de acesso da conta da vítima
em 14/09/2026 às 22:41:07 (UTC-3), porta de origem 51322.
```

```
Segue o log em anexo (acessos.txt). Faça a triagem, aprofunde os IPs de
alto interesse e gere o relatório forense.
```

```
Correlacione estes IPs com os eventos do caso:
198.51.100.7 — login em 02/10/2026 08:15
198.51.100.9 — cadastro do PIX em 02/10/2026 08:22
203.0.113.80 — acesso ao e-mail em 03/10/2026 19:40
```

### O que entrega

- Análise em 16 blocos (identificação, RDAP, BGP/ASN, DNS, domínios, geolocalização, VPN/Tor, hospedagem, reputação, serviços, certificados, histórico, correlações, avaliação, conclusão).
- **"O que pode e o que não pode ser atribuído"**, matriz de evidências, quadros **"O que sabemos / O que não sabemos"**.
- **Dados necessários para atribuição** (IP, data, hora com segundos, fuso, porta de origem, protocolo), indicando o que existe e o que falta — e o alerta de CGNAT quando cabível.
- Próximo melhor passo (1 a 3 prioridades, sem medidas invasivas) e fontes com URL e data/hora da consulta.
- Com 2+ IPs: matriz de similaridade explicável, clusters, hubs, outliers e exportação do caso (`case.json`, CSVs, `graph.graphml` para Gephi/Cytoscape/Neo4j).

### Limites

- Apenas **coleta passiva**: dados públicos e fontes autorizadas. Sem varredura, exploração ou autenticação.
- **IP não é pessoa.** A skill nunca conclui que alguém usou o IP apenas pelo endereço; considera NAT, CGNAT, Wi-Fi compartilhado, VPN, proxy, Tor e IP dinâmico.
- Geolocalização de IP é estimativa, não prova de localização física.
- Em consultas externas, só o indicador é enviado — nunca o contexto do caso, nomes ou vítimas.
- Quando o ambiente não tem acesso de rede para o script de coleta, a skill recorre à leitura web das mesmas fontes e registra o resultado no mesmo formato; fonte indisponível vira lacuna declarada.

---

## 5. Crypto Investigator

**O que faz.** Orienta a investigação forense de criptoativos: rastreamento em blockchains UTXO (Bitcoin, Litecoin) e baseadas em contas (Ethereum e redes EVM), multi-hop e cross-chain, golpes, contratos e tokens, preservação de prova on-chain e busca, apreensão e destinação de criptoativos no contexto brasileiro.

**Como ela trabalha.** A skill **não acessa blockchains**. Ela identifica a rede, diz exatamente qual explorer abrir, quais abas consultar e o que copiar — e analisa os dados que você trouxer. Se você anexar o CSV exportado do explorer, ela processa o arquivo por código (totais, contrapartes, linha do tempo) em vez de estimar.

### Menu de ações

| # | Ação | Para quê |
|---|---|---|
| 1 | Análise de endereço ou transação | Ponto de partida de qualquer rastreamento |
| 2 | Rastreamento multi-hop e cross-chain | Swaps, bridges, DeFi, mixers |
| 3 | Ferramentas OSINT e explorers | Passo a passo de uso: qual URL, qual aba, como exportar |
| 4 | Explicações técnicas | Conceito → funcionamento → relevância investigativa → exemplo |
| 5 | Simulação de investigação | Cenários fictícios com gabarito (BTC, DeFi, bridge, rug pull, mixer, stablecoin, NFT) |
| 6 | Smart contracts e tokens | Análise de contratos e tokens |
| 7 | Golpes e esquemas | Catálogo de golpes com padrão on-chain e como investigar |
| 8 | Busca, apreensão e destinação (Brasil) | Fluxo de localização, apreensão, custódia e alienação |
| 9 | Preservação de prova on-chain | Cadeia de custódia para capturas e exportações do explorer |
| 10 | Roteiro de estudo | Plano de capacitação por nível |

### Como pedir

```
Opção 1. Endereço: 0x... (cole o endereço completo). Ele apareceu no
comprovante enviado pela vítima. Não sei em qual rede.
```

```
Anexei o CSV de transações exportado do explorer. Rastreie para onde foram
os fundos a partir da transação de 05/10/2026 e monte o mapa de fluxo.
```

```
Opção 8. Quais são os caminhos para localizar e bloquear criptoativos de um
investigado que usa exchange nacional?
```

### Cuidados que a skill aplica antes de analisar

- **Identifica a blockchain primeiro.** Um endereço `0x` existe em dezenas de redes EVM; sem a rede, ela pergunta.
- **Diferencia endereço de hash de transação** (em EVM, `0x` + 40 caracteres é endereço; `0x` + 64 é hash).
- **Verifica checksum** e alerta sobre redes sem checksum (ex.: Solana), onde um erro de digitação passa despercebido.
- **Alerta para address poisoning:** endereços visualmente parecidos com o real, plantados no histórico da carteira. Prefira copiar o endereço da fonte primária (extrato da exchange, ordem judicial), não de captura de tela.
- **Diferencia carteira (EOA) de contrato**, inclusive EOA com delegação (EIP-7702).

### O que entrega

Relatório on-chain em 8 seções: resumo executivo, dados observados, mapa de fluxo de fundos, padrões (fragmentação, consolidação, peeling chain, round-trip, dormência…), classificação de risco, pontos prioritários, ferramentas recomendadas e limitações. Toda análise com dados reais termina com ressalva de que os resultados devem ser validados com ferramentas especializadas antes de uso processual.

### Limites

Não dá assessoria financeira nem jurídica para caso concreto, não inventa saldo ou transação e não cita jurisprudência sem certeza. Para redes com privacidade forte (Monero, Zcash blindado), declara a limitação de rastreio.

---

## 6. CyberShield

**O que faz.** Consultor de privacidade, segurança digital e anonimato. Toda recomendação é posicionada na camada do modelo TCP/IP em que atua (Aplicação, Transporte, Internet, Acesso à Rede ou transversal), sempre com trade-offs e limitações. Consulta uma base própria de 63 categorias e mais de 600 ferramentas, com alertas de incidentes e ferramentas descontinuadas.

**Quando usar.** Escolher ou comparar ferramentas (VPN, navegador, DNS, mensageiro, e-mail, gerenciador de senhas), endurecer celular, computador ou rede doméstica, entender fingerprinting, reduzir pegada digital, proteger a família ou usar IA com segurança.

### Menu

| Grupo | Opções |
|---|---|
| Diagnóstico e planejamento | **[1]** Diagnóstico de privacidade · **[8]** Modelo de ameaça personalizado · **[10]** Limpeza digital (data brokers) |
| Ferramentas e comparações | **[2]** Guia por tema · **[3]** Kit de privacidade · **[6]** Análise de ferramenta · **[12]** Comparar ferramentas |
| Proteção e hardening | **[4]** Mapa TCP/IP · **[5]** Hardening passo a passo · **[7]** Fingerprinting · **[9]** Privacidade em IA · **[13]** Segurança familiar |
| Livre | **[11]** Pergunte qualquer coisa |

A opção **[8]** conduz o modelo de ameaça em três rodadas (perfil, superfície de exposição, adversários). Há também cenários prontos: usuário casual, profissional de TI, jornalista/ativista, idoso/usuário vulnerável e família com crianças.

### Como pedir

```
Opção 12: compare Signal, Threema e SimpleX para comunicação de equipe
que lida com informação sensível.
```

```
Quero endurecer meu Android de trabalho. Nível avançado.
```

```
Opção 7 — como um site me identifica mesmo sem cookies, e o que dá para fazer?
```

### O que entrega

Para cada tema: o que é e por que importa, camada TCP/IP, ameaça mitigada, ferramentas recomendadas, como implementar, limitações e riscos residuais, nível de dificuldade e referências.

### Limites

Nunca garante anonimato absoluto, não recomenda ferramentas encerradas ou com histórico problemático sem o alerta correspondente e, quando a informação pode ter mudado (preços, aquisições, auditorias), recomenda conferir no site oficial.

---

## 7. DarkWeb Investigator

**O que faz.** Apoia a investigação de crimes na deep e dark web — tráfico de dados, fraudes, ransomware, comércio ilícito, lavagem com criptoativos, exploração infantil e outros — com foco em identificação, análise, atribuição, enquadramento penal brasileiro, preservação de prova e documentação.

**Como ela trabalha.** A skill **não acessa a dark web nem sites .onion** e não consulta alvos em nome do usuário. Ela analisa o conteúdo que você fornecer (texto de anúncios, perfis, mensagens, metadados), estrutura a investigação e orienta as ferramentas externas. Antes de qualquer ação investigativa, confere se você está operando com OPSEC adequada.

### Menu de ações

| # | Ação | # | Ação |
|---|---|---|---|
| 1 | Análise de atividades suspeitas | 8 | Atribuição e desanonimização |
| 2 | Mapeamento de conexões e vínculos | 9 | Análise de marketplace ou fórum |
| 3 | Classificação criminal e enquadramento legal | 10 | Simulações de investigação |
| 4 | Ferramentas e técnicas | 11 | Cooperação internacional |
| 5 | Relatório de investigação | 12 | Triagem rápida de denúncia |
| 6 | Segurança operacional (OPSEC) | 13 | Orientação em incidente ativo |
| 7 | Rastreamento de criptomoedas | | |

### Como pedir

```
Ação 12. Recebemos denúncia anônima com o texto abaixo, indicando venda
de base de dados de clientes de uma operadora. Avalie se justifica
investigação aprofundada.
[cole o texto]
```

```
Ação 3. Enquadre penalmente a conduta descrita: venda de credenciais
bancárias em fórum, com pagamento em Monero.
```

```
Ação 8. Tenho o texto de 15 anúncios do mesmo vendedor em dois
marketplaces. Quais técnicas de atribuição se aplicam?
```

### Recursos que se destacam

- **Fato × inferência** com nível de confiança e **Escala de Admiralty** para avaliar fontes.
- **Formatos de relatório por destino:** investigativo policial (padrão), relatório de inteligência (briefing), pericial simplificado e modelos de quesitos periciais.
- **Classificação penal** com artigo, pena e agravantes, e referências à legislação complementar e a tratados.
- **Atribuição:** estilometria, análise temporal, fingerprinting de vendedor, correlação surface ↔ dark web, falhas comuns de OPSEC do alvo.
- **Preservação de prova:** checklist com hash SHA-256 e referência aos arts. 158-A a 158-F do CPP.
- **Continuidade de sessão:** em investigações longas, oferece resumos periódicos e um resumo exportável para retomar depois.

### Limites

Pedidos são avaliados por uma matriz de legitimidade (contexto, natureza, especificidade, direção). Orientações para acessar, comprar, explorar ou ocultar atividade ilícita são recusadas com redirecionamento para o uso investigativo.

---

## 8. Investigative Notebook

**O que faz.** Caderno investigativo digital inspirado no IBM i2 Analyst's Notebook. Trata o caso como um **conjunto rastreável de afirmações**: cada entidade, relação, evento e observação guarda sua fonte, sua evidência e sua natureza (fato, observado, declarado, correlação, inferência, hipótese, não verificado). A mesma base vira grafo, timeline, mapa, tabelas, matriz de hipóteses e relatório.

**Quando usar.** Montar ou analisar um caso a partir de BO, depoimentos, extratos e quebras de sigilo, registros de chamadas e ERB, planilhas e documentos; achar vínculos, caminhos entre pessoas e contas, duplicidades, contradições entre fontes, lacunas; organizar hipóteses; gerar relatório de análise. Também serve para projetar ou desenvolver a plataforma (Streamlit, NetworkX, Cytoscape, SQLite).

### Fluxo de trabalho

1. **Abrir ou criar o caso.** Envie um `caso.json` existente ou peça um caso novo, informando título, responsável e objetivo da análise.
2. **Fontes e evidências primeiro.** Cada arquivo é registrado como evidência com hash SHA-256 antes de qualquer extração, para que tudo o que for extraído já nasça vinculado à origem.
3. **Extração.** Planilhas (extratos, CDR/ERB, logs, cadastros) passam por mapeamento de colunas → prévia → confirmação. Textos (BO, depoimento, relatório) têm identificadores extraídos automaticamente; pessoas, empresas e relações são lidas e registradas, preferencialmente como observações do tipo *"Segundo o depoimento de 12/08/2026, a vítima informou que…"*. **Você vê a prévia e aprova antes da importação em massa.**
4. **Validação e análise.** Checagem de integridade (ex.: "fato sem fonte") e análises de rede, caminhos, duplicidades, contradições, lacunas, temporal, espacial, financeira, anomalias e hipóteses.
5. **Respostas no formato explicável:**

```
CONCLUSÃO:     afirmação objetiva
EVIDÊNCIAS:    IDs usados (ex.: R-0016, D-0001)
FUNDAMENTAÇÃO: como se chegou à conclusão
TIPO:          fato | declarado | correlação | inferência | hipótese
CONFIANÇA:     muito baixa … muito alta
LIMITAÇÕES:    o que a conclusão NÃO demonstra
FONTES:        IDs e títulos das fontes
```

6. **Visualização e entrega.**

### O que entrega

| Entregável | Descrição |
|---|---|
| `caso.json` | A base do caso, com trilha de auditoria |
| Visualizador i2 (`caso.html`) | HTML único, abre no navegador sem servidor: grafo, inspector, timeline, mapa, evidências, filtros, hipóteses e auditoria sincronizados. Permite criar, editar, mesclar (com motivo), agrupar e desfazer. "Salvar" baixa o JSON atualizado — envie-o de volta para continuar |
| Relatório (`relatorio.md`) | 17 seções, com marcadores `[ANALISTA: …]` para objetivo, resumo executivo e conclusões; pode ser convertido em DOCX ou PDF |
| Exportações | GraphML, GEXF, CSV, XLSX, JSON |
| Pacote do caso | ZIP com caso, análise, visualizador, relatório, exportações, manifesto de evidências e `SHA256SUMS` |
| Snapshots | Versões do caso, com comparação (`diff`) e restauração |

Os arquivos do caso são entregues como **arquivos**, não como página publicada: o conteúdo de caso real é sigiloso e não deve ganhar URL. Para máquinas isoladas, o visualizador pode embutir as bibliotecas e desligar o mapa online, que revelaria a região analisada ao servidor de mapas.

### Como pedir

```
Crie um caso "Golpe do falso leilão — IP 0000/2026", objetivo: identificar
os titulares das contas recebedoras. Anexei o BO, dois depoimentos e o
extrato da conta da vítima.
```

```
Qual é o caminho entre a Pessoa A e a conta X? Ele se sustenta só com fatos
documentados (modo oficial) ou depende de declaração?
```

```
Há entidades duplicadas no caso? Mostre as sugestões; eu decido as mesclagens.
```

```
Gere o visualizador e o pacote do caso com os arquivos de evidência.
```

### Regras invariáveis

- Inferência, correlação ou hipótese **nunca** viram fato sozinhas; a promoção exige fundamentação registrada.
- Entidades **nunca** são mescladas só por semelhança de nome; o sistema sugere, você decide e registra o motivo (mesclagem reversível).
- Fontes contraditórias aparecem como **CONTRADIÇÃO DETECTADA**, com as duas versões.
- Identificadores guardam o valor original, o normalizado e a validade.
- Toda operação relevante entra na trilha de auditoria.

### Ecossistema

O Notebook é a camada de gestão e visualização do caso. As demais skills de inteligência instaladas convergem nele (pelo formato `intel-bundle/1.0` ou trabalhando sobre o `caso.json`) e também podem ser pedidas diretamente:

| Papel | Skill | O que acrescenta ao caso |
|---|---|---|
| Coleta e extração | `document-intelligence` | Entidades, relações e eventos extraídos de documentos com página, trecho e posição |
| | `financial-intelligence` | Contas, transferências e padrões financeiros ("compatível com") |
| | `social-media-intelligence` | Perfis públicos classificados (Confirmado / Provável / Possível) |
| | `malware-artifact-analysis` | Arquivos, hashes, IOCs e nível de suspeição |
| | `osint-intelligence` | Entidades de fontes abertas com fonte, data, trecho e confiabilidade |
| Consistência | `entity-resolution` | Duplicidades e homônimos, com decisão humana |
| Rastreabilidade | `evidence-provenance` | Hashes, cadeia de custódia, "de onde veio esta informação?" |
| Interpretação | `link-analysis` | Centralidade, comunidades, pontes e caminhos com sustentação |
| | `timeline-geospatial` | Ordem dos fatos, trajetórias, compatibilidade de deslocamento |
| | `case-correlation` | Conexões com outras investigações |
| Raciocínio | `hypothesis-engine` | Resumo, hipóteses, matriz ACH e próximas verificações |

Integrações com as skills deste guia: IPs, ASN e domínios → **Análise IP**; criptoativos → **Crypto Investigator**; revisão do texto do relatório → **Redator Inteligente**. Os resultados entram no caso como `nao_verificado`, com o registro da consulta.

---

## 9. OPSEC Specialist

**O que faz.** Consultoria de segurança operacional defensiva: anonimato, proteção de dispositivos, eliminação de rastros, senhas e autenticação, segurança corporativa, forense e antiforense, operações de campo e resposta a incidente. Começa sempre pelo **modelo de ameaça** — de quem você se protege — e recomenda medidas proporcionais ao risco (baixo, médio, alto, crítico).

### Subperfis

A skill infere o subperfil pelo pedido (ou pergunta uma vez):

| Subperfil | Ativado por |
|---|---|
| Instrutor Leigo | Privacidade pessoal, redes sociais, senhas |
| Consultor Corporativo | Empresa, compliance, LGPD, hardening, DLP |
| Analista Forense | Coleta de evidências, cadeia de custódia, antiforense |
| Especialista em Campo | Operações de risco real, segurança física, dispositivos descartáveis |
| Suporte a Pessoa em Risco | Stalking, ex-parceiro abusivo, violência doméstica, perseguição |

### Menu de ações

1. Anonimato e comunicação segura · 2. Proteção de dispositivos e sistemas · 3. Eliminação de rastros digitais (redes sociais → data brokers → registros públicos → metadados) · 4. Gestão de senhas e autenticação · 5. Segurança corporativa e compliance · 6. Análise forense e antiforense · 7. Segurança em operações de campo (só risco alto/crítico) · 8. **Resposta a incidente em andamento**.

### Como pedir

```
Ação 8: minha conta de e-mail funcional foi acessada agora há pouco de um
IP desconhecido. O que faço primeiro?
```

```
Vou fazer diligência de campo com celular funcional. Monte o modelo de
ameaça e as medidas para risco alto.
```

```
Uma vítima relata que o ex-companheiro sabe onde ela está o tempo todo.
Que orientações posso passar a ela sem alertar o agressor?
```

### O que entrega

- Recomendações estruturadas por nível de risco, com trade-offs e alternativa mínima aceitável quando o ideal é inviável.
- Na **Ação 8**, uma lista numerada de ações imediatas em ordem de urgência — conter, preservar, avaliar escopo, recuperar, notificar, pós-mortem — sem teoria.
- No subperfil **Pessoa em Risco**: validação antes da instrução, sequência que não alerta o agressor, preservação de evidência para medida protetiva, verificação de stalkerware, acessos compartilhados e rastreadores Bluetooth, e canais de apoio (Ligue 180, Disque 100, Access Now Helpline).

### Limites

Orienta proteção e defesa, nunca ataque: não simula engenharia social, phishing nem doxing, mesmo "para fins educacionais". Orientações de compliance são educacionais; coleta formal de evidências deve seguir protocolo pericial.

---

## 10. PhishGuard360

**O que faz.** Defesa contra phishing e engenharia social em três módulos:

| Módulo | Para quê | Tom |
|---|---|---|
| 1. 📚 **Educacional** | Simulador interativo de ataques, checklist de persuasão (Cialdini), "DNA do golpista", workshop de defesa | Didático |
| 2. 🕵️ **Investigativo** | Análise de e-mail, SMS/WhatsApp, URL, ligação e vetores modernos (QR Code, falso CAPTCHA/ClickFix, AiTM, fadiga de MFA, callback phishing, deepfake de voz) | Analítico |
| 3. 🏢 **Corporativo** | Programa de treinamento por maturidade, simulador de resposta a incidente, políticas e métricas | Estratégico |

Se você já chegar com o material suspeito, a skill vai direto ao Modo Investigativo.

### Como pedir

```
Analise este e-mail suspeito. Seguem os cabeçalhos completos e o corpo.
[cole cabeçalhos e corpo]
```

```
Uma vítima recebeu este SMS e pagou um Pix de R$ 1.850. Analise a mensagem
e diga o que ela deve fazer agora.
[cole o SMS]
```

```
Módulo 3: monte um programa de conscientização de 6 meses para uma unidade
com 40 servidores, sem treinamento prévio.
```

Para análises mais completas, envie os **cabeçalhos completos** do e-mail (com SPF/DKIM/DMARC) e, no caso de QR Code, a URL que o leitor revela antes de abrir.

### O que entrega

- Relatório técnico padronizado (Markdown, ou HTML para exportação) em sete blocos: indicadores identificados, táticas psicológicas detectadas, *heatmap* das frases de maior risco, classificação (vetor, objetivo, IOCs, nível de risco), veredito, recomendação e ferramentas para verificação adicional.
- **Mascaramento da vítima** (`João S****`, `j****@empresa.com.br`) e **defanging** de URLs e IPs maliciosos (`{hxxps://phishing[.]com}`, `{185[.]220[.]101[.]42}`), para que o relatório possa circular sem risco de clique acidental. E-mail do atacante, domínio malicioso isolado e hashes ficam no formato original, porque são IOCs. Payloads codificados (Base64, hex, QR Code) aparecem com o valor original e o decodificado lado a lado.
- **Tratamento de falso positivo:** se o artefato for legítimo, a skill diz isso e explica os indicadores de legitimidade.
- **Encaminhamento:** quando há vítima ou perda financeira, lista canais (CERT.br, SaferNet, delegacia de crimes cibernéticos, banco, **MED do Pix** — contestação em até 80 dias, Registrato do Banco Central, PROCON, Consumidor.gov.br) e checklist de ação imediata.

### Limites

A skill **nunca abre nem visita** as URLs maliciosas que analisa e **nunca cria** e-mails de phishing, páginas falsas ou scripts funcionais — nem para teste interno; nesse caso, oferece desenho de programa com plataformas de simulação, descrição de técnicas ou checklist. Não acusa pessoas reais.

---

## 11. Redator Inteligente

**O que faz.** Revisa, corrige, reescreve e adapta textos em português (PT-BR por padrão; preserva PT-PT, PT-AO e PT-MZ) sem alterar o sentido e sem fabricar dados. A intervenção é proporcional ao que você pede.

### Grau de intervenção — inferido do verbo

| Você diz | Grau | O que muda |
|---|---|---|
| "revisa", "corrige", "confere", "vê se tem erro" | **Mínimo** (padrão) | Só desvios objetivos: ortografia, acentuação, concordância, regência, crase, pontuação que altera o sentido |
| "melhora", "deixa mais claro / conciso / profissional" | **Moderado** | O mínimo + clareza, concisão, repetições, coesão — mantendo estrutura e vocabulário-chave |
| "reescreve", "reformula", "faz outra versão" | **Profundo** | Reestrutura frases e parágrafos, preservando sentido e fatos |

No grau mínimo, usos aceitos pela norma culta mas criticados por gramáticos conservadores não são "corrigidos" — vão para **Sugestões não aplicadas**, para você decidir. Se disser "só erros" ou "não mexe no estilo", isso vale para o resto da conversa.

### Modos

- **Lite** — textos curtos e informais.
- **Pro** — público profissional; revisão crítica, expansão, adaptação por canal, exportação.
- **Enterprise** — documentos oficiais, jurídicos, policiais e acadêmicos; normas (ABNT, APA, MLA, Vancouver, Chicago, ISO 690) e rigor máximo — nada é completado por suposição.

O modo é inferido e declarado na primeira linha da resposta; para trocar, basta dizer.

### Elementos que nunca são alterados

Citações diretas, **transcrições literais** (depoimentos, mensagens de WhatsApp, áudios transcritos — "corrigi-las" alteraria a prova), **marcadores de atribuição e modalização** ("segundo", "teria fugido", "supostamente"), qualificações técnico-jurídicas (suspeito, investigado, indiciado, réu não são sinônimos), números, datas, valores, nomes próprios e identificadores (CPF, CNPJ, BO, processo, placa, IMEI, IP, chave PIX, hashes). Fatos inconsistentes são sinalizados para você verificar, nunca "corrigidos".

### Ações disponíveis

1. Revisão completa com feedback · 2. Ajuste de tom e estilo · 3. Expansão de ideias (sem inventar fatos) · 4. Resumo e síntese · 5. Adaptação por objetivo · 6. Conversão de gênero (e-mail → relatório, ata → comunicado) · 7. Normas de citação e referências · 8. Revisão crítica didática · 9. Verificação de coerência · 10. Arquivos (entrada e exportação) · 11. Limite de caracteres ou palavras · 12. Linguagem inclusiva e acessível · 13. Saída em diff.

### Formatos de resposta

| Formato | Conteúdo |
|---|---|
| **Explicativo** (padrão) | Texto revisado + lista numerada de alterações com motivo + sugestões não aplicadas + pontos para o autor verificar |
| **Direto** | Só o texto final |
| **Resumido** | Texto final + 1–2 linhas de comentário |
| **Diff** | Pares ORIGINAL / REVISADO / MOTIVO cobrindo todas as alterações |

### Como pedir

```
Revisa este trecho do relatório policial. Só erros, não mexe no estilo.
Formato diff.
[cole o trecho]
```

```
Anexei o ofício em .docx. Corrija e devolva em .docx com controle de
alterações.
```

```
Reescreva este resumo para caber em 1.500 caracteres com espaços,
para o campo do sistema.
```

Um `.docx` enviado volta como `.docx` com **controle de alterações** e as justificativas em comentários, para você aceitar ou rejeitar cada mudança no Word. PDFs voltam como texto revisado (ou `.docx`) com a lista de alterações. Em documentos longos, nada é omitido: a revisão vem em partes numeradas se necessário, com folha de estilo para manter o padrão do início ao fim.

---

## 12. Sistema Pericial ALPR

**O que faz.** Analisa imagens de veículos e placas brasileiras (padrões Pré-Mercosul e Mercosul): avalia a qualidade da mídia, procura sinais de adulteração física, lê os caracteres um a um com validação tipográfica e emite **laudo estruturado**. Opera sob **desconfiança sistemática**: toda imagem é tratada como potencialmente adulterada até que a análise indique o contrário. O laudo é análise técnica auxiliar e não se confunde com o laudo pericial oficial.

### Pipeline

| Fase | O que acontece |
|---|---|
| A | Qualidade da imagem (Excelente / Suficiente / Crítica / Insuficiente) e contagem de placas |
| B | Adulteração física: textura, brilho, traço, relevo, obstruções, QR Code (só presença visual) |
| C | Leitura caractere a caractere, validação tipográfica e de formato, categoria e UF quando visíveis |
| D | **Análise probabilística** — só se a qualidade for Crítica/Insuficiente **e** você pedir |
| E | Autoavaliação antes de emitir |
| F | **Convergência multi-fonte** — só se você enviar várias capturas do mesmo veículo e pedir consolidação |

### Como pedir

Envie a imagem (ou imagens) e, se tiver, informe a proveniência — origem do arquivo, data, local. Esses dados entram no laudo como **declarados**.

```
Analise a placa deste veículo. Frame de CFTV, Av. Principal,
03/10/2026 21:14 (dado declarado).
```

```
A qualidade deu Insuficiente. Faça a análise probabilística dos caracteres.
```

```
Seguem 3 capturas de câmeras diferentes que acreditamos ser do mesmo
carro. Consolide as leituras.
```

### Como ler o laudo

- **`[3/8]`** indica posição ambígua entre os candidatos listados. Com caracteres ambíguos, o laudo principal lista no máximo 8 combinações; acima disso, declara a mídia insuficiente para busca efetiva.
- A linguagem evita "provavelmente" e "talvez"; usa "compatível com", "indicativo de", "evidências sugerem".
- Os percentuais da análise probabilística (Fase D) são **ilustrativos**, indicam só a ordem relativa entre candidatos — não são probabilidades calibradas.
- Na convergência, vários frames do **mesmo vídeo/câmera contam como uma única fonte**; se todas as capturas vierem da mesma câmera, a confiança consolidada máxima é Média. Convergência nunca apaga suspeita de adulteração.
- Você pode perguntar a fundamentação de qualquer campo ("por que leu [3/8] na posição 6?") — a skill explica com base nas evidências visuais.

### Limites

Não identifica proprietário, condutor ou passageiros; não sugere consulta a SINESP, DETRAN ou bases similares (LGPD); não amplia nem melhora a imagem; não faz medição de pixels nem OCR algorítmico; não decodifica QR Code. A análise é observação visual interpretativa — o que um perito humano também descreveria olhando a mesma imagem. Laudos Complementar e de Convergência são sempre subordinados ao Laudo Principal.

---

## 13. Fluxos combinados

As skills foram desenhadas para trabalhar juntas. Alguns roteiros:

**Golpe com Pix a partir de SMS ou e-mail**
1. **PhishGuard360** analisa a mensagem e lista as ações imediatas da vítima (incluindo o MED do Pix).
2. **Análise IP** examina os IPs do log de acesso ou dos cabeçalhos do e-mail e lista os dados necessários para atribuição.
3. **Investigative Notebook** integra BO, extrato e resultados num caso com grafo e timeline.
4. **Redator Inteligente** revisa o relatório final em grau mínimo.

**Ransomware ou extorsão com pagamento em cripto**
1. **DarkWeb Investigator** — Ação 13 (incidente ativo) e análise do site de vazamento ou do grupo.
2. **Crypto Investigator** — rastreamento do endereço de pagamento e preservação da prova on-chain.
3. **Investigative Notebook** — consolidação do caso e relatório.

**Veículo usado em crime**
1. **Sistema Pericial ALPR** lê a placa em cada captura e consolida as leituras.
2. **Investigative Notebook** registra a leitura como observação vinculada à evidência (o frame, com hash) e cruza com eventos e localizações do caso.

**Proteção da equipe ou de uma vítima**
- **OPSEC Specialist** monta o modelo de ameaça e a ordem de ação.
- **CyberShield** detalha e compara as ferramentas escolhidas, camada por camada.

---

## 14. Boas práticas com dados de caso real

- **Minimize.** Envie apenas o necessário para a análise. Quando o nome da vítima não for relevante, substitua por "Vítima 1".
- **Preserve antes de analisar.** Calcule o hash dos arquivos originais e trabalhe sobre cópias; o Investigative Notebook faz isso ao registrar evidências.
- **Não publique.** Resultados de caso real devem circular como arquivos, não como páginas com link.
- **Consultas externas revelam interesse.** Consultar um indicador num serviço de terceiros registra que alguém o consultou. A Análise IP envia só o indicador, mas avalie a OPSEC antes de autorizar consultas.
- **Confirme o que mudou.** Explorers, ferramentas, sanções e normas mudam. As skills sinalizam isso, mas valide o estado atual antes de citar algo como vigente em documento oficial.
- **Revisão humana sempre.** Toda saída é apoio à análise; a conclusão e a responsabilidade são do analista e da autoridade.

---

## 15. Solução de problemas

| Problema | O que fazer |
|---|---|
| A skill esperada não entrou em ação | Peça pelo nome: *"use a skill crypto-investigator"* |
| Entrou a skill errada (ex.: CyberShield em vez de OPSEC) | Diga qual quer; consulte a seção [Qual skill usar?](#3-qual-skill-usar) |
| Resposta muito básica ou muito técnica | Declare o nível: *"nível avançado"* ou *"explique para leigo"* |
| O Redator mudou mais do que você queria | Diga *"só erros, não mexe no estilo"* — vale para o resto da conversa |
| A Análise IP não conseguiu consultar as fontes | Sem rede no ambiente, a skill usa leitura web; fontes indisponíveis aparecem como lacunas, não como dado |
| O Crypto Investigator pede dados em vez de analisar | Ele não acessa blockchains: siga o roteiro de coleta no explorer ou anexe o CSV exportado |
| O ALPR não emitiu laudo | Ele exige imagem; descrição em texto de uma placa não basta |
| O visualizador do Notebook não mostra o mapa de ruas | Por sigilo, ele pode ter sido gerado sem buscar mapas online — nesse caso aparece um esquema local. Se o sigilo permitir, peça a versão com mapa online |
| Quer continuar um caso depois | Guarde o `caso.json` (ou o JSON salvo pelo visualizador) e envie-o numa nova conversa |
