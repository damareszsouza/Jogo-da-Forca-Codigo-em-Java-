# Jogo-da-Forca-Codigo-em-Java-

Ir para o conteúdo principal
Damares Costa de Souza 
Moodle - IFRS

Programação Básica com Java III - Turma 2022B
Painel Meus cursos  PBJIII2022B 4. Procedimentos, Funções e Métodos  4.11. Jogo da Forca
4.11. Jogo da Forca
Vamos encerrar o capitulo construindo um programa que implementa um jogo clássico: o Jogo da Forca. Neste jogo, o jogador deve tentar adivinhar uma palavra escolhida por outra pessoa (que em nosso caso será o próprio computador). O jogador deve mencionar uma letra de cada vez, e poderá cometer, no máximo, 7 erros.

Podemos organizar a lógica do jogo em passos usando descrição narrativa como segue:
Sortear palavra a ser descoberta pelo jogador.
Mostrar a palavra, escondendo letras ainda não descobertas pelo jogador.
O jogador deve informar uma letra.
Se a letra estiver na palavra, marcar as posições onde ela se encontra. Caso contrário, somar mais um no número de erros do jogador.
Se o jogador ainda não cometeu 7 erros ou não acertou a palavra, voltar ao passo 2.
Caso contrário, encerrar o jogo.
Nesta altura, você já deve ter experiência em programação suficiente para pularmos o pseudocódigo e tentarmos escrever o código para este problema diretamente em Java. Para este problema, vamos utilizar uma abordagem top-down, como já fizemos anteriormente. Assim, vamos montar o código do método main utilizando chamadas de métodos que implementaremos a seguir. Com base nos passos em descrição narrativa que elaboramos, podemos construir o código em Java mostrado abaixo.



1      public class JogoDaForca {

2            public static void main(String[] args) {

3                   char[] palavra = sorteiaPalavra();

4                   char[] tabuleiro = montaTabuleiro(palavra);

5                   int erros = 0;

6

7                   while(erros <= 7 && !Arrays.equals(tabuleiro, palavra)) {

8                          mostraTabuleiro(tabuleiro);

9                         

10                         System.out.print(“Informe uma letra: ”);

11                         char letra = System.console().readLine().charAt(0);

12

13                         if(acertou(palavra, letra))

14                                atualizaTabuleiro(tabuleiro, palavra, letra);

15                         else

16                                erros++;

17                  }

18                  if(erros > 7)

19                         System.out.println(“Você perdeu :(”);

20                  else

21                         System.out.println(“Você venceu :)”);

22           }

23     }


Vamos tentar entender o código mostrado, linha a linha. A linha 3 mostra a declaração da variável palavra, que irá conter a palavra a ser adivinhada pelo jogador. Armazenaremos a palavra como um vetor de caracteres, onde cada letra ocupará uma posição do vetor. Por exemplo, a palavra UVA será representada como um vetor de três posições, onde a letra U estará na primeira posição, V na segunda e A na terceira. Essa variável será inicializada com um vetor retornado pelo método sorteiaPalavra que implementaremos em breve.Veja que nenhum vetor é criado no método main, através do comando new, para preencher essa variável. O vetor em questão será criado dentro do método sorteiaPalavra e retornado por ele.

A linha 4 mostra a declaração da variável tabuleiro que será usada para armazenar o que será mostrado ao jogador a cada rodada do jogo. O método montaTabuleiro irá gerar um vetor para esta variável com base na palavra que foi sorteada.  Na linha 5, encontramos a declaração da variável erros, que será utilizada para contar o número de erros cometidos pelo jogador.

A linha 7 contém uma estrutura while que controla o loop principal do jogo.  O jogo será executado enquanto o número de erros for menor ou igual a sete e enquanto o jogador não acertar a palavra. Definimos que o jogador acertará a palavra quando o vetor tabuleiro for igual ao vetor palavra. Utilizamos o método equals da classe Arrays, que é um método da API Java que retorna true caso os vetores informados sejam iguais, ou false caso contrário. Dois vetores serão iguais quando tiverem o mesmo tamanho e os mesmos valores nas mesmas posições. Incluímos um operador de negação (!) antes da chamada do método equals, pois o jogo deve continuar enquanto o usuário NÃO acertar a palavra.

A linha 8 contém a chamada ao método mostraTabuleiro, que deverá mostrar na tela o conteúdo do vetor tabuleiro. As linhas 10 e 11 contém o código que realiza a leitura da letra desejada pelo usuário, armazenando a letra digitada na variável letra.

As linhas 13 a 16 contém uma estrutura if que verifica se o usuário acertou uma letra da palavra. O método acertou deverá verificar se a letra está no vetor palavra, retornando true em caso positivo e false em caso negativo. O método atualizaTabuleiro deverá preencher as posições do tabuleiro onde a letra for encontrada na palavra. Caso o usuário não tenha acertado a letra, a variável erros é incrementada.

Por fim, as linhas 18 a 21 contém uma estrutura if que verifica se o jogador venceu ou perdeu, mostrando uma mensagem apropriada na tela.


Última atualização: domingo, 1 nov 2020, 20:51
Seguir para...
Academi
Dúvidas? 
Perguntas frequentes

Fale conosco | Suporte | Contato

Informação
Termos e Condições de Uso
Aviso de Privacidade e Proteção de Dados Pessoais
Contato
Rua Gen. Osório, 348, Bento Gonçalves/RS
Siga-nos
Copyright © 2017 - Desenvolvido por LMSACE.com. Distribuído por Moodle
