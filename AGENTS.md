# Instruções para agentes de código

## Contexto e escopo
- Antes de agir, leia `README.md`, `docs/PROJECT_CONTEXT.md` e `docs/DECISIONS.md`.
- O projeto está em concepção. Não alegue que o solver, GPU, CFD, pós-processamento ou funcionalidades listadas já existem.
- Henrique tem experiência em DEM, mas não em programação. Conduza decisões técnicas com análise e recomendação fundamentadas; explique escolhas em português claro e deixe explícitas as decisões de produto que dependem dele.
- O objetivo é um produto autoral para engenharia e pesquisa em mineração, não uma cópia de Rocky, EDEM ou LIGGGHTS.
- Trate Rust como linguagem escolhida para o projeto inteiro, conforme decisão atual do usuário; a motivação é robustez. Não substitua por C++ sem autorização explícita. Avalie a viabilidade do ecossistema e explique que a linguagem não garante sozinha a robustez do produto.

## Antes de implementar
1. Transforme a visão em requisitos testáveis e fases; diferencie confirmado, hipótese, recomendação e questão em aberto.
2. Inspecione a fonte e a licença de qualquer código/dependência a reutilizar. Não copiar código ou documentação de concorrentes sem permissão. Não escolher licença do OreFlow até avaliar obrigações e compatibilidade; solicite revisão jurídica quando apropriado.
3. Proponha opções com vantagens, riscos, custo e recomendação. Não transferir escolhas de baixo nível ao usuário sem contextualizá-las.
4. Para DEM, especificar benchmarks reproduzíveis e critérios de convergência/validação; comparar com códigos comerciais não substitui validação experimental.
5. GPU, multicore, Windows/Linux, importação CAD e CFD são metas sujeitas a desenho técnico e fases, não promessa de disponibilidade imediata.

## Fluxo de trabalho
- Faça alterações pequenas, explique o propósito, rode testes reais disponíveis e registre resultados.
- Não introduza credenciais, dados pessoais ou arquivos locais não relacionados.
- Atualize `docs/PROJECT_CONTEXT.md` e/ou `docs/DECISIONS.md` quando houver novas decisões verificadas.
- Comece cada sessão reportando brevemente o contexto lido, o estado atual, a recomendação/questão principal e o próximo passo; não reabra decisões já registradas sem motivo.
