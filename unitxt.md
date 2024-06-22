# Metadados
* Unitxt :Flexible,Sharable and Reusable Data Preparation and Evaluation for Generative AI
* Elron Bandel,Ofir Arviv,Ariel Gera,Yotam Perlitz,Matan Orbach,Leshem Choshen,Elad Venezian,Roni * * * Friedman-Melamed,Shachar Don-Yehyia,Dafna Sheinwald,Michal Shmueli-Scheuer,Yoav Katz
* IBM Research	
* NAACL demo track
* 2024
* https://arxiv.org/abs/2401.14019

# Qual o problema?

Nos estudos de LLMs, é possível realizar diversas combinações entre componentes de prompts e a saída do modelo pode ser processada e avaliada de acordo com diferentes métodos. Nesse contexto, conforme mencionado no artigo, o processamento das entradas e saídas de um modelo sobre o mesmo conjunto de dados pode requerer a reescrita do código, levando a inconsistências nos resultados reportados, e bugs ocultos. Além disso, casos com demonstrações in-context não possuem uma API padronizada, o que dificulta a comparação entre estudos e desestimula a exploração de diferentes combinações.

Atualmente, já existem ferramentas que auxiliam em alguma parte desse pipeline. No entanto, o design não é modular, o que dificulta a adaptação e personalização para diferentes necessidades. Além disso, algumas dessas ferramentas apresentam dificuldade de integração com outros sistemas, o que limita a interoperabilidade.

# Qual a solução?
# Como os autores tentam resolver o problema? Criando um algoritmo novo? uma metodologia? uma ferramenta?
Os autores desenvolveram uma ferramenta modularizada e com API padronizada que auxilia no processamento de dados e facilita a experimentação de diferentes combinações de prompts.

## Quais são os detalhes técnicos dessa solução? O que chama mais atenção? Qual a ideia geral e o que deve ser discutido em mais detalhes?
A ferramenta foi desenvolvida em Python, suporta o processamento de texto em diferentes idiomas e seu design foi planejado para facilitar a integração com códigos pré-existentes.
Na prática, a Unitxt executa receitas (pipeline) que consistem na aplicação de uma sequência de operadores (ingredientes) para o processamento de dados. Esses operadores são responsáveis por carregar e pré-processar os dados, administrar o tratamento para diferentes partes de um prompt ou avaliar as predições do modelo.

A Unitxt possui um objeto chamado de catálogo, que contém receitas pré-definidas e possibilita a mistura ou adição de novos ingredientes a qualquer receita, promovendo flexibilidade. Os ingredientes são categorizados em:

* resources: dados
* task: tarefas normais de NLP (ex: classificação, sumarização, etc.)
* template: definem verbalizações a serem aplicadas aos inputs e desverbalização das predições do modelo
* format: tokens especiais ou prefixos user/agent e demonstrações in-context
* extensions: extensões, como input-augmentation (ex: acréscimo de espaço em branco, erros gramaticais, etc.)

# Como foi avaliado?
O artigo não apresenta métricas sobre a avaliação da ferramenta, apenas menciona que a Unitxt foi implantada na IBM para a avaliação e treinamento de LLMs

# Resenha crítica
Considerei a Unitxt uma ótima alternativa em comparação às outras ferramentas similares já existentes mencionadas no artigo, como a OpenCompass, HELM e LM-eval-harness. A Unitxt atende aos requisitos de flexibilidade e reprodutibilidade de forma prática e eficiente, impulsionando o avanço nos estudos de LLMs. Além disso, achei o design simples e intuitivo (achei a escolha da nomenclatura “recipe” e “ingredients” uma ótima analogia), facilitando a compreensão e uso. Por fim, a implementação concisa evita verbosidade excessiva, e a documentação da Unitxt é organizada e abrangente, cobrindo grande parte do código.

Ao realizar a execução do repositório disponível no GitHub a partir da branch main, alguns testes falharam, e acredito que a apresentação dos resultados dos testes poderia ser aprimorada para facilitar a identificação e resolução dos erros.

No artigo, são apresentados alguns pontos de melhoria sobre a ferramenta: o catálogo necessita de expansão para abranger mais datasets, idiomas e tasks específicas; as métricas de avaliação, principalmente no que tange a tasks generativas, podem ter uma cobertura maior; e, por fim, para facilitar a adição de datasets ou operadores, a curva de aprendizado da linguagem Unitxt precisa ser reduzida. Tutoriais ou documentação adicional podem ser úteis para auxiliar os usuários neste processo.
Os autores deste estudo se consolidam como especialistas nas áreas de Processamento de Linguagem Natural (NLP), Inteligência Artificial (IA) e Aprendizado de Máquina (ML), expertise comprovada por suas diversas publicações em periódicos de renome.

Yotam Perlitz se destaca por suas pesquisas em adaptação de domínios e avaliação semântica, áreas cruciais para o avanço da NLP. Elron Bandel também contribui significativamente para a área de adaptação de domínios, com ênfase no idioma hebraico, e possui trabalhos relevantes em Deep Learning. Os demais autores complementam o grupo com pesquisas em diversos temas dentro das áreas mencionadas.

# Replicação
* Onde estão os dados?
* Onde está o código? https://github.com/IBM/unitxt
* Conseguiu entender/rodar? sim
* Dá para replicar o experimento/estudo? sim
