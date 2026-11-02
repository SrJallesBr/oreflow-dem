# OreFlow DEM — contexto e requisitos iniciais

**Estado do documento:** consolidação da conversa de concepção; não é especificação final nem compromisso de implementação.
**Nome:** OreFlow DEM é nome de trabalho; marca/disponibilidade não verificada.

## 1. Visão e público

Criar um software DEM autoral, aberto ao público conforme licença ainda a definir, para engenheiros e pesquisadores. A ambição é alcançar capacidades de engenharia e análise comparáveis às ferramentas de referência, sem assumir que uma paridade abrangente caiba na primeira versão.

Aplicações citadas explicitamente:
- Dimensionamento de chutes.
- Processos de troca de calor.
- Outras aplicações de mineração a identificar com base nos manuais e casos que Henrique fornecerá.

Gás foi mencionado e corrigido durante a conversa; não registrar como requisito específico já confirmado, além do futuro interesse de acoplamento CFD.

## 2. Requisitos/intenções registrados

### Produto e plataformas
- Plataforma-alvo: Windows e Linux.
- iOS não é prioridade e fica fora do escopo atual.
- Engenheiros e pesquisadores são públicos-alvo.
- Incluir visualização dos resultados e ferramentas de cálculo/análise comparáveis às referências, definindo quais e em que fase após levantamento funcional.

### Geometria e workflow
- Usuário prefere criar/modelar a geometria em CAD de terceiros e importá-la.
- Modelagem CAD dentro do OreFlow pode ser expansão futura, mas a preferência atual é que não seja necessária, possivelmente nem incluída.
- Objetos geométricos precisam contemplar superfícies, sólidos e elementos com movimento/controle, incluindo free body, servo e atuador de força. Definir significado operacional, graus de liberdade e interfaces de controle na especificação.
- Identificar formatos de importação/exportação e tratamento de malha em levantamento futuro; nenhum formato de CAD específico está fechado.

### Partículas e física
- Interesse em esferas superquadráticas e outros formatos disponíveis nas ferramentas de referência.
- Investigar suporte a partículas STL/mesh como forma de partícula; Henrique mencionou isso como capacidade desejada ausente no LIGGGHTS de seu fluxo conhecido. Tratar como requisito a avaliar, incluindo custo/algoritmos e não assumir implementação simples.
- Considerar superpartículas/clumps nos moldes funcionais do LIGGGHTS, definindo terminologia e comportamento com exemplos.
- Troca de calor é aplicação desejada; modelos térmicos, contatos, condições de contorno e critérios ainda não foram especificados.

### Desempenho e computação
- GPU deve entrar desde cedo na estratégia do projeto, mas a extensão de suporte (quais algoritmos/solvers, dispositivos e precisão) precisa de estudo e benchmark.
- Usar inteligentemente múltiplos núcleos da CPU; definir paralelismo e escalabilidade com medições reproduzíveis.
- Evitar prometer desempenho ou compatibilidade de hardware antes dos protótipos e medições.

### CFD
- CFD/OpenFOAM é fase posterior ao núcleo DEM inicial.
- Objetivo futuro: oferecer acoplamento unidirecional e bidirecional, com o modo bidirecional reconhecido como mais custoso computacionalmente.
- Definir versões, campos trocados, sincronização, estratégias de acoplamento e plataformas suportadas numa fase própria.

### Linguagem e arquitetura
- Decisão de direção inicial: avaliar/desenvolver o núcleo em C++.
- Isso não fecha toda a arquitetura; interface, bibliotecas, formatos internos, solver-base e módulos auxiliares ainda precisam de análise fundamentada.
- O assistente deve apresentar recomendações técnicas, alternativas e consequências; Henrique decide questões de produto e escolhas que exijam sua preferência. Henrique tem experiência em DEM, não em programação.

### Licença e validação
- Intenção: licença aberta/pública com reciprocidade semelhante à associada pelo usuário ao LIGGGHTS.
- Licença exata ainda NÃO escolhida. Verificar a licença e versão exatas do código considerado, dependências e implicações de combinação/distribuição; buscar revisão jurídica antes de publicar decisão.
- Comparar física/comportamento com LIGGGHTS, Rocky, EDEM e outras referências indicadas, além de validar contra literatura e experimentos quando possíveis. Comparação não prova por si só acurácia.
- Henrique pretende fornecer manuais dos softwares de referência para extrair e organizar capacidades. Materiais ainda não anexados neste repositório.

## 3. Princípios de planejamento

1. Separar visão aspiracional, requisito confirmado, hipótese técnica e item adiado.
2. Construir matriz de funcionalidades com fonte (manual/caso de uso), valor ao usuário, complexidade, dependências, fase e critério de aceitação.
3. Converter casos de uso em especificações e benchmarks verificáveis antes de escolher/reutilizar um solver.
4. Definir primeiro um MVP coerente, mas não reduzir o produto a um único tipo de problema sem avaliar o conjunto de aplicações desejadas.
5. Fazer estudo de arquitetura, desempenho e licença antes de código derivado ou promessa de paridade com concorrentes.
6. Proteger independência/autoria: não copiar implementação ou texto protegido de produtos concorrentes.

## 4. Questões de trabalho em aberto

- Quais casos de uso de mineração e quais cálculos/resultados são essenciais por fase? Quais manuais/casos serão fornecidos primeiro?
- Que modelos de contato, coesão, atrito, rolamento, amortecimento, quebra/desgaste e térmicos entram no escopo?
- Qual definição prática de partículas STL e “superpartículas” atende às necessidades e que limites geométricos/escala são aceitáveis?
- Quais tipos de movimento/controle e condições de contorno de geometria são necessários? Como interpretar “todas as superfícies” dos softwares de referência em requisitos próprios?
- Quais formatos CAD/malha, projeto e resultados devem ser suportados no MVP?
- Quais plataformas GPU são prioritárias e quais cargas serão aceleradas? Como será o modo CPU-only?
- Qual estratégia de paralelismo atende Windows e Linux? Como testar escalabilidade e reprodutibilidade?
- Qual licença (por exemplo, família GPL ou outra) combina com a intenção do produto e com possíveis dependências/integrações? Necessária análise técnica e jurídica.
- Qual software/base será implementado ou integrado, se algum, após verificar licença, arquitetura, manutenção e compatibilidade?
- Quando e com qual versão do OpenFOAM desenvolver o acoplamento DEM–CFD?
- Quais dados experimentais ou casos publicados serão referência independente para validação?

## 5. Próximos passos sugeridos

1. Reunir os manuais prometidos e criar uma matriz rastreável de funcionalidades (requisito → página/seção de fonte → caso de uso → fase → critério de aceitação).
2. Elaborar casos de uso de mineração e resultados esperados, priorizando chute e troca de calor.
3. Produzir estudo comparativo de bases/arquiteturas C++, paralelismo CPU, GPU, interface Windows/Linux, importação geométrica e licenças.
4. Propor escopo de MVP e roadmap para aprovação do usuário.
5. Só então criar protótipo técnico mínimo com benchmark e testes verificáveis.

## 6. Continuação com Codex

Este repositório é a fonte de contexto versionada para as próximas conversas de desenvolvimento. Instruções do agente em `AGENTS.md`. Ao iniciar Codex, peça que leia `AGENTS.md`, este documento, `docs/DECISIONS.md` e `README.md`; confirme o estado do Git e resuma fatos confirmados, pendências e recomendação do próximo passo antes de editar. Manter o trabalho em português, salvo quando nomes técnicos/código exigirem inglês.
