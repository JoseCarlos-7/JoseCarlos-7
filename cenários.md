## Casos interessantes que tive a oportunidade de solucionar.

**Relação entre vendas e ações de vendas.**

Um dos clientes recentes não tinha ao certo o resultado das suas ações de venda, e para isso criei um pipeline que identifica a ocorrência de vendas para CPFs que foram acionados via SMS ou Discadora dentro de um período de 30 dias, considerando casos em que o agente que iniciou a venda é o mesmo que finalizou (ou da mesma hierarquia). Essa solução possibilitou a análise de retorno sobre o investimento em ações de venda. <br>

**Desempenho de vendedores após treinamento.**

Aplicando a mesma lógica, desenvolvi um pipeline que apurava a performance dos vendedores que participavam do treinamento de vendas, analisando resultados desde D0 [início do treinamento] até D+20 [pós término do treinamento]. Essa solução apresentada em Dashboard Power Bi possibilita compreender e eficácia do treinamento em seus diferentes modos [presencial, imersivo, ead].
Para essas duas soluções, utilizei arquiteturas parecidas. Extração dos dados -> Transformação e padronização -> Modelagem DW -> Apresentação Power Bi. <br>
Embora simples, o desafio maior foi experimentar formas de atualizar os dados de forma rápida no Power Bi. Nessa empresa era comum carregar os dados no Powe Query e transformá-los. Então apresentei a possibilidade de transformá-los de forma mais simples agregando colunas na tabela calendário que já apresentasse D+20, D-20, D+30 e D-30 como atributo da data. Essa abordagem otimizou o custo de processamento na atualização do modelo e consequentemente reduziu drásticamente o tempo de atualização do Dashboard.
Aviso de inconsistência nos dados. <br>
Em uma das empresas em que trabalhei, uma constante reclamação das áreas de negócio era a inconsistência nos relatórios apresentados. E sabendo que 90% dos dados tinham origem em cargas Batch D-1 que eram feitas de madrugada, mapeei o caminho desses dados, separando em instâncias [Fonte - ETL – indicadores - Apresentação] e criei um processo que apurava volumetria e qualidade dos dados atualizados em Batch D-1. Desta forma, já na primeira hora do dia, tínhamos um Dashboard que mostrava desvios de volume e ausência de entidades e atributos que causariam impactos nos relatórios. Portando essas informações era possível solicitar correção da carga Batch a tempo e quase zerar os erros de relatório.