# Fixação Unidade 01

* O que é um alfabeto Σ;
  É um conjunto finito de sìmbolos.

* O que é uma cadeia;
  Uma sequência de símbolos pertencentes ao alfabeto.

* O que significa ε; 
  Palavra vazia.

* Por que |ε| = 0; 
  Porque representa uma cadeia que não contém nenhum símbolo.

* O que é um prefixo; 
  É um elemento adicionado no início da palavra

* O que é um sufixo; 
  É um elemento adicionado no fim da palavra

* O que significa Σ*; 
  Representa o conjunto de todas as cadeias finadas que podem ser formadas a partir dos símbolos de um alfabeto.

* Se Σ* possui limite de tamanho; 
  Não possui limite de tamanho.

* O que é uma linguagem formal L; 
  É um conjunto de palavras construídas a partir de um alfabeto.

* O que significa L ⊆ Σ*; 
  Significa que L (linguagem formal) é um subconjunto de Σ* (Sigma - alfabeto).

* O que é uma gramática formal; 
    A gramática formal fonece as regras que utilizamos para gerar as palavras.

* O que são terminais e não terminais; 
  ** Não Terminais (ou Variáveis): São os símbolos que representam "categorias" estruturais. Eles podem (e devem) ser substituídos ou expandidos por outros símbolos. Pense neles como caixas ou moldes que guardam outras coisas dentro e que ainda não chegaram à sua forma final.

  ** Terminais: São os símbolos, caracteres ou palavras definitivas da linguagem. Eles não podem ser substituídos nem expandidos. Eles encerram a regra, sendo o "ponto final" de estrutura.

* O que é uma regra de produção; 
  Se trada do conjunto de instruções lógicas que definem como os símbolos de uma gramática podem ser combinados ou substituídos para gerar as "palavras" válidas de uma linguagem.

* Como ler S → aS | ε; 
  S produz aS ou ε.

* Como gerar palavras usando uma gramática.
  A geração de palavras em uma gramática formal ocorre por meio de um processo algorítmico de sucessivas substituições, chamadas de derivações.
    
  1.Iniciar pelo símbolo inicial:
  Toda derivação começa obrigatoriamente pela variável principal da gramática, geralmente representada pela letra $S$.
    
  2.Identificar um não terminal:
  Observe a sua sequência atual e identifique qual variável (representada por letras maiúsculas, conhecidas como não terminais) precisa ser desenvolvida.
    
  3.Aplicar uma regra de produção:
  Consulte o conjunto de produções da gramática e escolha uma regra cujo lado esquerdo corresponda à variável que você está analisando. Substitua a variável pelo conteúdo exato que está do lado direito da seta ($\rightarrow$). Utilizamos o símbolo $\Rightarrow$ para registrar esse passo de derivação.
    
  4.Repetir até o fechamento:
  Continue substituindo os não terminais que surgirem na sequência. A geração da palavra termina apenas quando a cadeia resultante for composta exclusivamente por símbolos terminais (elementos do alfabeto) ou pela palavra vazia ($\varepsilon$).
    
Exemplo Prático
Considere uma gramática com o seguinte conjunto de produções:
    $S \rightarrow 0A$
    $A \rightarrow 1A$
    $A \rightarrow 1$
    
Para gerar a palavra 011, a execução obedece à seguinte ordem lógica:Início:
    $S$ (Símbolo inicial)
    1ª Derivação: $S \Rightarrow 0A$ (Substituímos $S$ aplicando a regra 1)
    2ª Derivação: $0A \Rightarrow 01A$ (Substituímos o $A$ aplicando a regra 2)
    3ª Derivação: $01A \Rightarrow 011$ (Substituímos o $A$ aplicando a regra 3)
    
Como a cadeia final 011 não possui mais nenhuma letra maiúscula (não terminais), a derivação está oficialmente concluída.
