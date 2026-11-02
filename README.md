# OreFlow DEM

**Status:** concepção e definição de requisitos — ainda sem solver ou implementação DEM.

OreFlow DEM é o nome de trabalho de um software autoral de simulação DEM voltado a engenheiros e pesquisadores, com foco em aplicações de mineração. A visão é oferecer fluxos de trabalho e ferramentas de cálculo e análise adequados a problemas como dimensionamento de chutes e estudos de troca de calor.

## Direção atual

- Plataformas pretendidas: Windows e Linux; iOS fora do escopo atual.
- Fluxo geométrico preferido: modelar em CAD de terceiros e importar a geometria. Modelagem CAD interna não é prioridade e pode ser descartada.
- Capacidades-alvo incluem superfícies e geometrias móveis/controladas (free body, servo e atuador de força), múltiplos formatos de partículas (incluindo superquadráticas, clumps/superpartículas e partículas definidas por STL) e visualização/análise de resultados.
- GPU e uso eficiente de múltiplos núcleos de CPU são metas desde o início do planejamento; estratégia e escopo precisam de estudo técnico.
- CFD/OpenFOAM é etapa posterior. A visão contempla acoplamento unidirecional e bidirecional, reconhecendo o maior custo deste último.
- Comparação com LIGGGHTS, Rocky e EDEM deve fazer parte da validação, complementada por benchmarks e dados experimentais quando disponíveis.
- C++ é a direção inicial escolhida para avaliação do núcleo. Arquitetura, interface, bibliotecas e implementação ainda não foram decididas.
- Intenção de licença: software aberto, inspirada no modelo do LIGGGHTS. Licença exata e compatibilidade de dependências continuam pendentes de análise.

## Comece por aqui

Leia [`docs/PROJECT_CONTEXT.md`](docs/PROJECT_CONTEXT.md) e [`AGENTS.md`](AGENTS.md) antes de propor alterações. Este repositório é também o pacote de contexto para continuar o trabalho no Codex. Não tratar metas de longo prazo como requisitos já implementados nem iniciar a reescrita do solver antes da avaliação técnica e de licenças.
