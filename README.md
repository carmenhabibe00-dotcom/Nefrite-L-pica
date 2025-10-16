Artigo 
Introdução
A nefrite lúpica (NL) é um tipo de glomerulonefrite considerada uma das manifestações orgânicas mais graves do lúpus eritematoso sistêmico (LES). 1 Enquanto a osteoporose é uma condição comum que resulta na perda progressiva de massa óssea e deterioração da microarquitetura em todo o corpo, aumentando assim o risco de fraturas. 2 A redução da massa óssea e as fraturas são complicações significativas observadas em doenças inflamatórias crônicas , incluindo o LES. 3 Vários estudos epidemiológicos mostraram que pacientes com LES têm maior risco de fraturas e osteoporose. 4 5 Em pacientes com LES, em comparação com a população em geral, o risco de fratura de quadril é 1,86-1,99 vezes maior, e o risco de fratura de quadril é 2,97 vezes maior. 6
Inflamação sistêmica , queixas musculoesqueléticas e o uso de glicocorticoides são fatores adicionais que afetam a perda óssea no LES, além de fatores mais comuns, como idade e estilo de vida. 7 No LES, sabe-se que a perda óssea é agravada pela alta atividade da doença , crises recorrentes, insuficiência renal e níveis inadequados de complemento. Como resultado, as fraturas por fragilidade são contabilizadas no índice de danos do LES como consequências graves da doença. Resultados recentes mostraram uma maior probabilidade de fraturas osteoporóticas, apesar dos esforços para reduzir a dose cumulativa de glicocorticoides por meio de abordagens de tratamento. 8 Para pessoas com LES, as fraturas não apenas diminuem seu padrão de vida, mas podem causar incapacidade. As fraturas osteoporóticas podem ser evitadas identificando a perda óssea precocemente e tomando as medidas adequadas. A avaliação da densidade mineral óssea (DMO), avaliada por meio de absorciometria de raios X de dupla energia (DXA), é uma abordagem frequentemente utilizada para caracterizar a osteoporose 9 .
No geral, a nefrite-osteoporose é uma doença multifatorial crônica , que é determinada pela presença de nefrite e osteoporose, caracterizada pela diminuição da massa óssea e pelo aumento do risco de fraturas. 10 A nefrite-osteoporose é uma condição muito complexa e diversa que apresenta muitas dificuldades em seu diagnóstico, tratamento e gerenciamento. A coexistência dessas duas condições é bastante desafiadora tanto em ambientes clínicos quanto de pesquisa, porque requer uma compreensão dos aspectos moleculares da doença. A ligação exata entre essas duas condições no nível molecular ainda não é totalmente compreendida. 11 Nos últimos anos, estratégias de bioinformática foram identificadas como eficazes no exame de distúrbios multifatoriais, utilizando múltiplas fontes de dados ômicos e análise computacional. Assim, empregando esses métodos, podemos identificar genes significativos e revelar os mecanismos moleculares subjacentes das doenças, bem como potenciais alvos terapêuticos. 12 Em relação à nefrite-osteoporose, a bioinformática pode ser uma ferramenta valiosa para identificar a complexa relação entre inflamação renal e remodelação óssea . Uma análise bioinformática abrangente baseada em dados de microarray disponíveis forneceria informações detalhadas sobre os genes e as vias moleculares associadas à nefrite-osteoporose.
Neste estudo, conduzimos uma análise bioinformática abrangente de dados de microarray facilmente acessíveis no domínio público para determinar os genes e vias moleculares envolvidas na nefrite-osteoporose. Do banco de dados GEO , baixamos seis conjuntos de dados de microarray, três deles eram sobre LES e os outros três eram sobre osteoporose. Após o pré-processamento dos dados, conduzimos uma análise de expressão gênica diferencial em cada conjunto de dados de microarray independentemente usando o pacote limma na ferramenta estatística R. Essa análise nos permitiu determinar os genes superexpressos no grupo nefrite em comparação com o grupo osteoporose. Com base em um valor de p limiar menor que 0,05 e uma mudança de log-fold (log-FC) maior que 0,75, identificamos 44 genes diferencialmente expressos (DEGs) comuns associados à nefrite-osteoporose. Para entender melhor as funções biológicas desses DEGs, realizamos análises de via GO , KEGG, Wiki Pathways e Reactome . Para obter insights sobre as implicações biológicas desses DEGs, conduzimos análises abrangentes de ontologia genética (GO), análises de vias da Enciclopédia de Genes e Genomas de Kyoto (KEGG), bem como análises de vias Wiki e vias Reactome. Para explorar as potenciais interações entre os 44 DEGs, construímos uma rede de interação proteína-proteína (PPI) usando o plug-in StringApp do software Cytoscape . 13 Por fim, utilizando o plug-in cytoHubba do Cytoscape , identificamos alguns genes centrais dos conjuntos de dados.
A identificação desses genes centrais proporcionou maior compreensão das vias moleculares da nefrite-osteoporose. Além disso, esses genes centrais podem auxiliar na identificação de biomarcadores e alvos terapêuticos para o desenvolvimento de novas estratégias terapêuticas para essa doença multifacetada. Os resultados deste estudo podem ser considerados um avanço na elucidação da intrincada relação entre nefrite e osteoporose em nível molecular. A compreensão dos genes potenciais e de suas vias de sinalização relacionadas pode fornecer uma base para o desenvolvimento de novos métodos diagnósticos, planos de tratamento e tratamentos para pacientes com nefrite-osteoporose.
Materiais e métodos
Recuperação e pré-processamento de dados
As etapas de download e pré-processamento de dados foram conduzidas usando o software estatístico R. Para obter os conjuntos de dados relevantes, uma busca completa foi realizada no repositório público GEO do National Centre for Biotechnology Information (NCBI) . 14 Especificamente, os conjuntos de dados GEO com números de acesso GSE32591, GSE144390, GSE50772, GSE56815, GSE7158 e GSE35958 foram selecionados para a análise. Para recuperar esses conjuntos de dados, o pacote GEOquery R 15 foi empregado, permitindo o download dos perfis de expressão gênica do repositório GEO. Posteriormente, uma sequência de procedimentos de pré-processamento foi executada em cada perfil de expressão para garantir a qualidade e a consistência dos dados antes de realizar a análise diferencial. Esse pré-processamento incluiu correção de fundo, normalização, transformação log2, mapeamento de ID de sonda e remoção de amostras discrepantes. Para mapeamento de ID de sonda, os IDs de sonda foram associados aos IDs Entrez correspondentes, símbolos de genes e nomes de genes utilizando pacotes de anotação disponíveis no Bioconductor . 16 Às vezes, o mesmo símbolo de gene pode ser mapeado com múltiplas sondas. Nesses casos, esses mapeamentos foram considerados como observações separadas durante a análise, e estatísticas padronizadas como valor de p foram usadas para quantificá-los. Para melhorar a comparação subsequente, os símbolos de genes correspondentes às sondas com o menor valor de p para cada símbolo de gene foram escolhidos. Esse processo de seleção levou à identificação das associações mais relevantes entre os símbolos de genes e as sondas que correspondem a eles. Além disso, quando os IDs de genes de sonda não foram mapeados, eles foram excluídos da matriz de contagem para reter apenas os dados importantes e mapeados para as próximas etapas da análise.
Análise estatística
A análise estatística é essencial para extrair insights significativos de dados de microarray e gerar hipóteses para validação e exploração posteriores. Os perfis de expressão gênica dos conjuntos de dados escolhidos foram submetidos à análise de expressão diferencial usando o pacote "limma" do software estatístico R. 17 O pacote "limma" pode ser usado em várias funções para realizar análises de expressão diferencial, incluindo testes t e ANOVA, projetados especificamente para dados de microarray. Para iniciar a análise, um modelo linear foi ajustado aos dados de expressão de cada gene usando o método "lmFit()" em "limma". 17 Este modelo linear considera o delineamento experimental e calcula os níveis médios de expressão nas amostras controle e experimental. Esta etapa é essencial para comparar os níveis médios de expressão entre os dois grupos para cada gene. Para definir as comparações específicas de interesse, uma matriz de contraste foi criada usando o método "makeContrasts()". Neste caso, como comparamos dois grupos, um teste t foi realizado. O "limma" se aplica a uma estatística t moderada com um desvio padrão reduzido para cada gene. Essa redução é alcançada por meio de um método Bayesiano empírico, que reduz a influência de desvios-padrão extremamente baixos ou altos no teste t. Ao combinar informações de todos os genes, o teste t moderado melhora o desempenho por meio da redução em todo o genoma. A comparação das diferenças de expressão gênica entre as amostras experimentais e de controle foi avaliada por meio do método "eBayes()" do pacote "limma". Este método aplica um teste t moderado para calcular as estatísticas Bayesianas empíricas moderadas. Para controlar múltiplos testes, a abordagem da Taxa de Descoberta Falsa (FDR) baseada no método Benjamini-Hochberg (BH) foi empregada para ajustar os valores de p resultantes. 18
Meta-análise de conjuntos de dados de microarray
A meta-análise de conjuntos de dados de microarray envolve a combinação e análise de dados de múltiplos estudos independentes para identificar padrões de expressão gênica robustos e reprodutíveis. Os seis conjuntos de dados GSE32591, GSE144390, GSE50772, GSE56815, GSE7158 e GSE35958 estão associados a diferentes países e foram baixados. GSE32591, GSE50772 e GSE56815 – esses três conjuntos de dados são dos EUA, GSE144390 e GSE7158 são da China, e o conjunto de dados GSE35958 é da Alemanha. Para determinar os genes-chave que exibem expressão diferencial, a etapa subsequente envolve o emprego do teste de probabilidade combinada de Fisher em R para combinar os valores de p dos genes comuns em todos os conjuntos de dados. Essa amalgamação facilita a identificação de DEGs estatisticamente significativos. Este método funciona somando o logaritmo dos valores de p ajustados em todos os conjuntos de dados para cada gene. Essa soma é então comparada a um
Unknown node type: font
Unknown node type: font
distribuição com 2
Unknown node type: font
graus de liberdade, onde
Unknown node type: font
representa o número de conjuntos de dados utilizados na análise. Os valores de p são ajustados usando o método BH para controlar o FDR. Para obter um único log-FC para cada gene, os seis log-FCs derivados dos conjuntos de dados são calculados em média. Os DEGs foram selecionados com base em critérios específicos: valores de p menores que 0,05 e valores absolutos de log-FC maiores ou iguais a 0,75.
Análise de enriquecimento funcional e de via
Após realizar uma meta-análise e identificar DEGs, conduzir análises de enriquecimento funcional e de via pode fornecer insights valiosos sobre os processos biológicos e vias associadas a esses genes. Portanto, análises de enriquecimento funcional e de via dos DEGs identificados foram conduzidas. Isso envolveu a realização de análises de enriquecimento de GO e via utilizando o pacote gprofiler2 R. As análises de enriquecimento foram realizadas em vários bancos de dados, incluindo KEGG, 19 REACTOME, 20 e WikiPathways. 21 A anotação funcional em KEGG envolve a associação de um grupo de genes dentro de um genoma a uma rede de moléculas celulares interagentes, como vias ou complexos, ilustrando assim uma função biológica de nível superior . O REACTOME é um banco de dados de código aberto disponível publicamente que fornece informações abrangentes sobre vias biológicas humanas. Essas vias são construídas a partir de uma rede de 'reações' biológicas interconectadas ou etapas da via, que incluem vários processos biológicos , como ligação, fosforilação e transporte, além de eventos bioquímicos tradicionais. Cada reação é obtida da literatura científica com citações que oferecem validação experimental dos eventos descritos. O WikiPathways é um banco de dados de código aberto dedicado a vias biológicas. Seu sucesso depende fortemente da colaboração e dos princípios da ciência aberta. O limiar de significância para a análise de enriquecimento foi estabelecido em um valor de p inferior a 0,05.
Construção de rede PPI e análise de genes centrais
A construção de redes PPI e a análise de genes centrais fornecem insights adicionais sobre os mecanismos moleculares subjacentes às condições ou doenças estudadas. O estudo das interações proteicas, que leva à formação de redes extensas e densamente interconectadas, é uma área significativa de pesquisa. As redes de interação proteica são valiosas tanto para a pesquisa científica básica quanto para os avanços em aplicações biológicas e biomédicas. Ao elucidar os papéis das proteínas em várias funções biológicas, essas redes revelam os mecanismos moleculares e celulares que regulam os estados saudáveis ​​e patológicos nos organismos. Consequentemente, a compreensão dessas redes aumenta nossa compreensão dos mecanismos patogênicos e fisiológicos subjacentes ao início e à progressão da doença. Os PPIs foram adquiridos do banco de dados STRING ( https://stringdb.org/ ) usando o plugin StringApp 22 integrado ao Cytoscape . Para gerar as redes para os 10 principais DEGs, o plugin cytoHubba 23 para Cytoscape foi empregado. Especificamente, os algoritmos Degree, MNC (Maximum Neighborhood Component), Betweenness e Closeness no plugin cytoHubba foram utilizados. No geral, a metodologia passo a passo usada neste estudo é mostrada na Fig. S1 Suplementar .
Resultados
Conjunto de dados e análise exploratória
Os seis conjuntos de dados brutos foram selecionados de acordo com seus números de acesso GEO GSE32591, GSE144390, GSE50772, GSE56815, GSE7158 e GSE35958 do GEO usando o pacote GEOquery R. Os detalhes desses conjuntos de dados são apresentados na Tabela 1. Esses conjuntos de dados foram então preparados para meta-análise usando técnicas estatísticas. O pré-processamento Robust Multi-Array Average (RMA) foi usado para cada conjunto de dados de microarray, incluindo correção de fundo, normalização e transformação log2. A correção de fundo é uma etapa crucial do pré-processamento na análise de dados de microarray, visando ajustar os dados para a intensidade ambiental ao redor de cada característica. 24 A normalização é o processo de retornar os dados a uma condição ou estado padrão. Na análise ômica de todo o sistema , a normalização aborda vieses ou erros sistemáticos ou não para melhorar a comparabilidade das amostras e garantir que as diferenças observadas na abundância molecular sejam devidas a mudanças biológicas em vez de artefatos. A transformação log2 é frequentemente aplicada a dados de microarray, pois estabiliza a variância em altas intensidades, embora possa aumentar a variância em baixas intensidades. Para garantir que os níveis de expressão dos genes nos conjuntos de dados recuperados do GEO sejam comparáveis, um boxplot foi criado e inspecionado antes e depois da normalização ( Fig. Suplementar 2 ). Essa avaliação permitiu identificar se os níveis de expressão precisavam de normalização para o nível apropriado. Quando as amostras tinham valores de expressão baixos ou não uniformes, a normalização era feita como um pré-requisito antes de análises posteriores. A normalização e o pré-processamento de dados são muito importantes na análise de expressão porque podem afetar o resultado da meta-análise.
Tabela 1. Informações detalhadas de conjuntos de dados GEO recuperados para análise DEG.

S. Não.	Adesão GEO	Tamanho da amostra	Características	Plataforma
1	GSE32591	64	Nefrite Lúpica	GPL14663
30	Controlar
2	GSE144390	3	Lúpus Eritematoso Sistêmico	GPL6244
3	Controlar
3	GSE50772	60	Lúpus Eritematoso Sistêmico	GPL570
20	Controlar
4	GSE56815	40	DMO alta	GPL96
40	Baixa DMO
5	GSE7158	14	PBM alto	GPL570
12	Baixo PBM
6	GSE35958	5	Osteoporose	GPL570
4	Não osteoporótico
Meta-análise e triagem de DEGs
Um total de 44 genes demonstrou expressão diferencial significativa em todos os seis conjuntos de dados. Esses DEGs foram identificados com base em seu enriquecimento de mais de 0,75 vezes a mudança (FC) em comparação à expectativa aleatória, com uma significância estatística de valor de p menor que 0,05. Utilizando os mesmos critérios de triagem de valor de p corrigido de Benjamini-Hochberg menor que 0,05 e um logFC maior que 0,75, observamos que 42 DEGs exibiram consistentemente regulação positiva, enquanto 2 DEGs foram regulados negativamente neste nível de significância ( Tabela Suplementar ). A Tabela 2 fornece uma lista dos DEGs identificados, onde os genes são empilhados com base em seus valores de p corrigidos por BH. Além disso, para representar visualmente os DEGs regulados positivamente e negativamente, um gráfico de vulcão foi criado ( Fig. 1 ). Além disso, um mapa de calor foi gerado usando R para visualizar os DEGs ( Fig. 2 ).
Tabela 2. Genes diferencialmente expressos (DEGs) classificados por valores de p corrigidos por Benjamini-Hochberg (BH).

S. Não.	Gene	valor-p	BH-valor p	LogFC
1	IFI6	1.46E-31	8.73E-28	0,884795
2	IFI44L	1,51E-30	4.50E-27	1.559439
3	IFI27	5.95E-27	7.12E-24	1.437318
4	MX1	6.42E-26	6.40E-23	1,054625
5	IFI44	2.48E-24	2.12E-21	1.204604
6	HERC5	7.72E-24	6.16E-21	0,767662
7	IFIT3	5.81E-21	2.33E-18	0,94474
8	IFIT1	1.37E-20	4.51E-18	0,931464
9	ISG15	7.85E-19	1.24E-16	0,765778
10	OAS1	7.79E-18	7.90E-16	0,881404
11	C1QB	1.86E-16	1.22E-14	0,78905
12	CHI3L1	3.91E-16	2.22E-14	0,765244
13	MS4A4A	1.24E-15	5.69E-14	0,757455
14	COL1A1	1,49E-15	6.53E-14	0,859182
15	LY6E	1.92E-15	8.12E-14	0,955919
16	SERPING1	1.07E-14	3.46E-13	0,763199
17	RSAD2	1.13E-14	3.62E-13	0,976844
18	IL1R2	2.39E-14	6.83E-13	0,75539
19	RNASE2	2.61E-14	7.31E-13	0,880859
20	LTF	5.44E-14	1.35E-12	1.740923
21	HP	1.16E-13	2.61E-12	0,915143
22	ARG1	1.63E-13	3.45E-12	0,937886
23	CXCL8	1.14E-12	1.90E-11	1.183969
24	ANXA3	1.71E-12	2.69E-11	1.158545
25	SLPI	1.33E-11	1,52E-10	0,91513
26	NAMPT	2.79E-11	2.91E-10	0,798328
27	CRISP3	3.54E-11	3,58E-10	1.240898
28	MMP8	2.16E-10	1.71E-09	1.428165
29	MMP9	2.20E-10	1.75E-09	0,819494
30	LCN2	3.86E-10	2.84E-09	1.398353
31	RNASE3	3.86E-10	2.84E-09	0,949308
32	OLFM4	9.32E-10	6.16E-09	1.453739
33	ACAMPAR	1.79E-09	1.09E-08	1,05834
34	DEFA4	2.05E-09	1.22E-08	1.367233
35	CEACAM6	3.47E-09	1.92E-08	0,967833
36	DDX3Y	5.04E-09	2.66E-08	-0,93597
37	RPS4Y1	3.10E-08	1.29E-07	-1,0486
38	CD24	3,99E-08	1.62E-07	1.016559
39	CEACAM8	5.78E-08	2.23E-07	1.452076
40	HBB	1.64E-07	5.61E-07	0,855432
41	BPI	2.54E-07	8.29E-07	1.082915
42	TCN1	2.89E-07	9.31E-07	0,778123
43	ELANE	9.78E-07	2.78E-06	0,819914
44	CA1	3.40E-05	6.69E-05	0,755398
Figura 1
Download: Baixe a imagem em alta resolução (315 KB)
Download: Baixar imagem em tamanho real
Fig. 1. Gráfico de Vulcão mostrando 42 DEGs com regulação positiva e 2 DEGs com regulação negativa. Pontos ciano, vermelho e cinza mostraram genes com regulação positiva, regulação negativa e não significativos, respectivamente.

Figura 2
Download: Baixe a imagem em alta resolução (1 MB)
Download: Baixar imagem em tamanho real
Fig. 2. Mapa de calor de 44 graus em seis conjuntos de dados. A figura foi gerada em R por meio da função heatmap().

Análise de enriquecimento funcional e de vias
Para entender melhor a função biológica dos DEGs, a análise de enriquecimento de via e função foi realizada usando os bancos de dados GO, KEGG pathway, WikiPathways e Reactome . Essas análises buscaram determinar os papéis e as redes relacionadas dos DEGs. O pacote gprofiler2 R que pode ser acessado através do Bioconductor foi usado para esses propósitos. Para processos biológicos , os três primeiros termos GO mais significativos foram 'resposta de defesa', 'processos biológicos de interações organismo-em-organismo' e 'resposta a outros organismos'. Em relação às funções moleculares, os DEGs identificados foram significativamente enriquecidos nos termos GO: ligação de lipopolissacarídeo , atividade de peptidase do tipo serina e atividade de hidrolasede serina. Os termos mais representativos dos componentes celulares foram 'lúmen de grânulo específico', 'grânulo específico' e 'grânulo secretor'. O exame das vias mostrou que os DEGs estavam implicados em diferentes vias, como "Desregulação transcricional no câncer" e "por Staphylococcus aureus". Além disso, os termos aprimorados do Reactome e do WikiPathways envolviam "Sistema Imunológico", "Degranulação de Neutrófilos", "Sistema Imunológico Inato" e "Resposta Imunológica à Tuberculose". Esses achados são ilustrados nasFiguras 3e4.
Figura 3
Download: Baixe a imagem em alta resolução (1 MB)
Download: Baixar imagem em tamanho real
Fig. 3. Análise de enriquecimento gênico (A) Gráfico de barras mostrando os 10 principais termos de via enriquecidos (B) Gráfico de pontos mostrando os 10 principais termos GO enriquecidos em cada categoria.

Figura 4
Download: Baixe a imagem em alta resolução (335 KB)
Download: Baixar imagem em tamanho real
Fig. 4. Análise de enriquecimento gênico. Gráfico de Manhattan dos cinco principais termos GO e da via enriquecidos.

Análise de interação proteína-proteína (PPI)
O uso da rede PPI é particularmente importante na identificação de genes reguladores que são importantes para o funcionamento de um organismo. O banco de dados STRING ( https://stringdb.org/ ) serve como um recurso valioso para explorar interações proteicas conhecidas e previstas. Por esse motivo, o plugin StringApp do Cytoscape foi usado para criar a rede PPI dos 44 DEGs. Essa rede também foi avaliada usando o software Cytoscape; isso oferece uma visão clara da interação dos DEGs, como mostrado na Fig. 5. Esses nós são geralmente considerados os "centros" da rede e podem estar envolvidos na regulação das vias biológicas de interesse. Por meio da representação visual e da análise computacional pelo Cytoscape, as interações funcionais entre os DEGs foram elucidadas, permitindo a identificação de potenciais genes e vias reguladoras.
Figura 5
Download: Baixe a imagem em alta resolução (805 KB)
Download: Baixar imagem em tamanho real
Fig. 5. Rede de interação proteína-proteína (PPI) de DEGs identificados. A rede continha 42 nós representando cada DEG e 192 arestas representando sua interação.

Detecção de genes centrais
Para explorar mais a fundo o mecanismo molecular subjacente dos 44 DEGs, a rede PPI dos 44 DEGs foi construída, e os 10 principais genes centrais foram analisados ​​( Fig. 6 A–D). Isso foi possível graças ao plugin cytoHubba para Cytoscape que empregou algoritmos de grau, MNC (Componente Máximo de Vizinhança), Betweenness e Closeness. Com base nessa análise, sete genes foram encontrados como significativamente envolvidos na construção da rede de genes. Esses genes são o ligante 8 da quimiocina do motivo CXC ( CXCL8 ), a elastase neutrofílica ( ELANE ), a lipocalina 2 ( LCN2 ), a metalopeptidase de matriz 8 ( MMP8 ), a proteína induzida por interferon com repetições de tetratricopeptídeo 1 ( IFIT1 ), a resistência ao mixovírus 1 ( MX1 ) e o gene 15 estimulado por interferon ( ISG15 ) ( Fig. 6 E). Esses genes centrais são os nós mais cruciais e centrais na rede PPI dos 44 DEGs.
Figura 6
Download: Baixe a imagem em alta resolução (678 KB)
Download: Baixar imagem em tamanho real
Fig. 6. Identificação do gene hub. (A) A rede PPI dos genes hub plotada com o algoritmo Closeness; (B) um diagrama da rede PPI dos genes hub gerada com o algoritmo Degree; (C) um diagrama da rede PPI dos genes hub gerada com o algoritmo Betweenness; (D) Rede PPI dos genes hub gerada com o algoritmo MNC; (E) o diagrama de Venn de identificação dos genes hub.

Discussão
A nefrite e a osteoporose são duas doenças crônicas que afetam muito a saúde humana e diminuem a qualidade de vida . 11 Para elaborar estratégias de prognóstico ou diagnóstico para esses distúrbios, é necessária uma compreensão clara da genética e molecular desses distúrbios. Nesta análise in silico , identificamos genes-chave e vias moleculares relevantes que desempenham papéis importantes na comorbidade de nefrite-osteoporose. Identificamos 44 genes diferencialmente expressos analisando seis conjuntos de dados de microarray usando o pacote LIMMA recuperado do banco de dados NCBI GEO e identificamos genes que exibem diferenças significativas em todos os seis conjuntos de dados. A ontologia genética de 44 genes nos permitiu obter insights sobre as implicações biológicas, descobrindo sua associação com resposta de defesa, interações do organismo e resposta a estímulos externos.
O termo ontologia de função molecular revela suas associações em diferentes atividades, incluindo a ligação a lipopolissacarídeos e funções de peptidase e hidrolase . Uma compreensão detalhada das atividades biológicas dos genes e seus papéis contribui para o nosso conhecimento dos mecanismos moleculares subjacentes à nefrite-osteoporose. Além disso, a análise de enriquecimento da via KEGG mostrou vias significativas, como a desregulação transcricional no câncer, infecção por Staphylococcus aureus e via de sinalização do receptor semelhante a NOD . A análise de enriquecimento de vias Reactome e Wiki destacou associações significativas de vias, como o sistema imunológico . degranulação de neutrófilos ,respostas imunes inatase a resposta imune à tuberculose. Essa análise associada a vias recomendou o envolvimento de processos e vias relacionados ao sistema imunológico no desenvolvimento e progressão da nefrite-osteoporose.
Para examinar como os genes interagem entre si, construímos uma rede PPI complexa, analisando a rede PPI posteriormente, encontramos sete genes centrais, a saber: CXCL8, ELANE, LCN2, MMP8, IFIT1, MX1 e ISG15 . O gene CXCL8 foi relatado como envolvido no processo patogênico da síndrome nefrótica pela modulação do estresse oxidativo e da resposta inflamatória . 25 O gene ELANE foi relatado como associado ao LES . 26 A correlação de LCN2 como regulada positivamente em pacientes com nefrite lúpica foi encontrada. 27 O gene MMP8 pode estar envolvido na nefrite lúpica por meio de uma via de matriz mediada. 28 O gene IFIT1 foi agrupado proporcionalmente na nefrite lúpica. 29 O gene MX1 revelou um alto valor diagnóstico na nefrite lúpica. 27 Relatórios mostraram que o gene ISG15 também foi encontrado anteriormente na patogênese do LES . 30 genes centrais identificados são considerados os genes mais conectados que regulam toda a rede e são considerados cruciais nos processos de doenças.
A identificação dos genes centrais é útil para a compreensão do possível tratamento da nefrite-osteoporose, uma vez que fornece informações sobre os genes que podem ser afetados. Esses genes podem ser alvos envolvidos na comorbidade da nefrite-osteoporose. Intervenções que visem os genes centrais podem ser um caminho potencial para melhorar a saúde e a qualidade de vida em pacientes com essas doenças. Coletivamente, os resultados deste estudo ajudam a elucidar a base genética e molecular da comorbidade entre nefrite e osteoporose. Posteriormente, ao analisar os dados e identificar os genes-chave e suas vias associadas, abrimos as portas para o desenvolvimento de novos métodos diagnósticos e prognósticos, bem como para o desenho de intervenções terapêuticas e direcionadas para pessoas com nefrite-osteoporose. No entanto, estudos experimentais adicionais são necessários para determinar os papéis funcionais desses genes e seu potencial como alvos de intervenção terapêutica. 


Resumo do artigo
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





