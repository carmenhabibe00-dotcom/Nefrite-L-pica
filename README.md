Artigo 


Resumo do Estudo: Análise de Bioinformática em Nefrite-Osteoporose
Este estudo utilizou uma abordagem de bioinformática para investigar a relação molecular entre nefrite lúpica e osteoporose.

Materiais e Métodos
A pesquisa começou com a recuperação de seis conjuntos de dados de microarray do banco de dados público GEO do NCBI. Os conjuntos utilizados foram: GSE32591, GSE144390, GSE50772, GSE56815, GSE7158 e GSE35958. Três deles eram de estudos sobre lúpus eritematoso sistêmico (LES) e os outros três, sobre osteoporose.

O primeiro passo metodológico foi o pré-processamento dos dados. Isso incluiu a correção de fundo, normalização, transformação log2 e mapeamento de IDs de sondas para genes, garantindo a qualidade e consistência dos dados para as próximas etapas. A normalização foi visualmente inspecionada usando boxplots para confirmar que os níveis de expressão eram comparáveis entre as amostras.

Em seguida, foi realizada a análise de expressão gênica diferencial (DEG). Usando o pacote "limma" no software R, um modelo linear foi ajustado para comparar os níveis de expressão entre os grupos de nefrite e osteoporose. Foi aplicado um teste t moderado com desvio padrão reduzido por meio de um método Bayesiano empírico. Os valores de p resultantes foram ajustados usando o método de Taxa de Descoberta Falsa (FDR) de Benjamini-Hochberg (BH) para controlar múltiplos testes.

A etapa seguinte consistiu em uma meta-análise dos seis conjuntos de dados. O teste de probabilidade combinada de Fisher foi utilizado para combinar os valores de p dos genes comuns em todos os conjuntos, facilitando a identificação de DEGs robustos e estatisticamente significativos. A seleção final dos DEGs se baseou em critérios de valores de p menores que 0,05 e valores absolutos de log-FC maiores ou iguais a 0,75. Um total de 44 DEGs foi identificado. A visualização desses genes foi feita com um gráfico de vulcão e um mapa de calor.

Para obter insights sobre a função biológica dos DEGs, foi conduzida uma análise de enriquecimento funcional e de vias. O pacote gprofiler2 R foi usado para analisar os genes nos bancos de dados GO (Ontologia Genética), KEGG, WikiPathways e Reactome. A análise buscou determinar os processos biológicos, funções moleculares e vias moleculares associadas a esses genes, com um limiar de significância de p < 0,05.

Por fim, foi construída uma rede de interação proteína-proteína (PPI) usando o banco de dados STRING e o plugin StringApp do software Cytoscape. A análise dessa rede permitiu identificar os genes mais interconectados. O plugin cytoHubba do Cytoscape foi empregado para identificar os genes centrais (hub genes), considerados os nós mais cruciais na rede. Os algoritmos Degree, MNC, Betweenness e Closeness foram utilizados para a detecção desses genes, que foram identificados como CXCL8, ELANE, LCN2, MMP8, IFIT1, MX1 e ISG15.

https://www.sciencedirect.com/science/article/pii/S1094695024000593





