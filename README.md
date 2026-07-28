# Carrega a base de dados
> data(mtcars)

# Exibe toda a tabela

> mtcars
                     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
# Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

 # Características de cada coluna:
 # mpg  -> Consumo de combustível (milhas por galão)
 # cyl  -> Número de cilindros do motor
 # disp -> Cilindrada do motor
 # hp   -> Potência do motor (Horse Power)
 # drat -> Relação do eixo traseiro
 # wt   -> Peso do veículo (milhares de libras)
 # qsec -> Tempo para percorrer 1/4 de milha (segundos)
 # vs   -> Tipo do motor (0 = V, 1 = em linha)
 # am   -> Tipo de transmissão (0 = automática, 1 = manual)
 # gear -> Número de marchas
 # carb -> Número de carburadores
 
 
 # Estrutura da base
 # Quantidade de observações;
 # Quantidade de variáveis;
 # Tipo de cada variável.

 str(mtcars)
'data.frame':	32 obs. of  11 variables:
 $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
 $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
 $ disp: num  160 160 108 258 360 ...
 $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
 $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
 $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
 $ qsec: num  16.5 17 18.6 19.4 17 ...
 $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
 $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
 $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
 $ carb: num  4 4 1 1 2 1 4 2 2 4 ...

 #Escolhemos a variável cyl para formar os estratos porque ela divide naturalmente a população em três grupos distintos: 11 veículos com 4 cilindros, 7 com 6 cilindros e 14 com 8 cilindros. A partir dessa divisão, realizaremos a Amostragem Estratificada e compararemos seus resultados com a Amostragem Aleatória Simples.
 

 table(mtcars$cyl)

 4  6  8 
11  7 14 

 variaveis <- data.frame(
     Variavel = c("mpg","cyl","disp","hp","drat","wt","qsec","vs","am","gear","carb"),
     Descricao = c(
         "Consumo",
         "Nº de cilindros",
         "Cilindrada",
         "Potência",
         "Relação do eixo",
         "Peso",
         "Tempo 1/4 de milha",
         "Tipo do motor",
         "Transmissão",
         "Nº de marchas",
         "Nº de carburadores"
     )
 )
 
 variaveis
   Variavel          Descricao
1       mpg            Consumo
2       cyl    Nº de cilindros
3      disp         Cilindrada
4        hp           Potência
5      drat    Relação do eixo
6        wt               Peso
7      qsec Tempo 1/4 de milha
8        vs      Tipo do motor
9        am        Transmissão
10     gear      Nº de marchas
11     carb Nº de carburadores
 View(variaveis)
 
 
 # Separando os veículos por número de cilindros
 estrato4 <- subset(mtcars, cyl == 4)
 
 estrato6 <- subset(mtcars, cyl == 6)
 
 estrato8 <- subset(mtcars, cyl == 8)
 View(estrato4)
 View(estrato4)
 
 
 # A função subset() cria subconjuntos da base.
 
 # cyl == 4 → seleciona apenas veículos de 4 cilindros.
 # cyl == 6 → seleciona apenas veículos de 6 cilindros.
 # cyl == 8 → seleciona apenas veículos de 8 cilindros.
 
 # Ao final dessa etapa, a população está dividida em três estratos.
 
 
 # Reprodutibilidade do sorteio
 
 set.seed(123)
 
 # Sorteio dentro de cada estrato
 
 amostra4 <- estrato4[sample(nrow(estrato4), 5), ]
 
> amostra6 <- estrato6[sample(nrow(estrato6), 3), ]
> 
> amostra8 <- estrato8[sample(nrow(estrato8), 6), ]
> 
> 
> # Reprodutibilidade do sorteio
> 
> set.seed(123)
> 
> # Sorteio dentro de cada estrato
> 
> amostra4 <- estrato4[sample(nrow(estrato4), 5), ]
> 
> amostra6 <- estrato6[sample(nrow(estrato6), 3), ]
> 
> amostra8 <- estrato8[sample(nrow(estrato8), 6), ]
> 
> 
> # Unindo os estratos sorteados
> 
> amostra_estratificada <- rbind(amostra4, amostra6, amostra8)
> 
> # Exibir a amostra
> 
> amostra_estratificada
                  mpg cyl  disp  hp drat    wt  qsec vs am gear carb
Merc 230         22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
Volvo 142E       21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
Merc 240D        24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
Toyota Corolla   33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
Lotus Europa     30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
Merc 280         19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
Valiant          18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
Mazda RX4        21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
AMC Javelin      15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
Camaro Z28       13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
Merc 450SLC      15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
Merc 450SE       16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
Dodge Challenger 15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
Maserati Bora    15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
> 
> 
> # rbind() une as três amostras em uma única tabela.
> 
> # O resultado é a amostra estratificada, composta por 14 veículos, mantendo representantes de todos os estratos.
> 
> 
> # Média da potência em cada estrato
> 
> tapply(mtcars$hp, mtcars$cyl, mean)
        4         6         8 
 82.63636 122.28571 209.21429 
> 
> 
> # tapply()
> 
> # É uma função que aplica um cálculo em grupos.
> 
> # No nosso caso:
> 
> # mtcars$hp → variável que será analisada (potência).
> 
> # mtcars$cyl → variável que define os estratos.
> 
> # mean → função utilizada para calcular a média.
> 
> 
> # Desvio-padrão da potência em cada estrato
> 
> tapply(mtcars$hp, mtcars$cyl, sd) 
       4        6        8 
20.93453 24.26049 50.97689 
> 
> 
> # Desvio-padrão da potência em cada estrato
> 
> tapply(mtcars$hp, mtcars$cyl, sd)
       4        6        8 
20.93453 24.26049 50.97689 
> 
> 
> # Ela mede o quanto os valores estão dispersos em torno da média.
> 
> # Quanto menor o desvio-padrão, mais homogêneo é o estrato.
> 
> 
> # Variância da potência em cada estrato
> 
> tapply(mtcars$hp, mtcars$cyl, var)
        4         6         8 
 438.2545  588.5714 2598.6429 
> 
> 
> #Calcula a variância. Ela mede a variabilidade dos dados.
> 
> #Quanto maior a variância, mais diferentes são os veículos daquele estrato.
> 
> # Resumo da potência por estrato
> 
> by(mtcars$hp, mtcars$cyl, summary)
mtcars$cyl: 4
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  52.00   65.50   91.00   82.64   96.00  113.00 
------------------------------------------------------------------ 
mtcars$cyl: 6
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  105.0   110.0   110.0   122.3   123.0   175.0 
------------------------------------------------------------------ 
mtcars$cyl: 8
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  150.0   176.2   192.5   209.2   241.2   335.0 
> 
> 
> # A função 'by()' divide a variável hp pelos estratos definidos em cyl e aplica a função 'summary()' 
> 
> # O resultado apresenta:
> 
> # Valor mínimo
> # Primeiro quartil (25%)
> # Mediana
> # Média
> # Terceiro quartil (75%)
> # Valor máximo
> 
> # Isso fornece uma visão completa da distribuição da potência em cada estrato.
> 
> 
> # Comparação entre a Amostragem Estratificada e a AAS
> 
> # Definir a mesma semente
> 
> set.seed(123)
> 
> # Selecionar uma amostra aleatória simples com 14 veículos
> 
> AAS <- mtcars[sample(nrow(mtcars), 14), ]
> 
> # Exibir a amostra
> 
> AAS
                    mpg cyl  disp  hp drat    wt  qsec vs am gear carb
Maserati Bora      15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
Cadillac Fleetwood 10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
Honda Civic        30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
Merc 450SLC        15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
Datsun 710         22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
Merc 280           19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
Fiat 128           32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
Dodge Challenger   15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
Merc 280C          17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
Hornet Sportabout  18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
Toyota Corolla     33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
Ford Pantera L     15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
AMC Javelin        15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
Ferrari Dino       19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
> 
> 
> ## Explicação
> 
> # sample(nrow(mtcars), 14) sorteia 14 veículos da população de 32 automóveis.
> 
> # Diferentemente da Amostragem Estratificada, aqui não existe separação por estratos.
> 
> # Todos os veículos possuem a mesma probabilidade de serem selecionados.
> 
> # Comparar as médias 
> 
> # Média da potência na população
> 
> mean(mtcars$hp)
[1] 146.6875
> 
> # Média da potência na AAS
> 
> mean(AAS$hp)
[1] 154
> 
> # Média da potência na amostra estratificada
> 
> mean(amostra_estratificada$hp)
[1] 144.4286
> 
> A função mean() calcula a média da potência (hp).
Erro: unexpected symbol em "A função"

> ## A função mean() calcula a média da potência (hp).
> 
> # Serão comparadas três médias:
>     
> # População;
> # AAS;
> # Amostragem estratificada.
> 
> # A técnica cuja média ficar mais próxima da média da população tende a fornecer uma estimativa mais precisa.
> 
> 
> ## Comparar o desvio-padrão
> 
> # Desvio-padrão da AAS
> 
> sd(AAS$hp)
[1] 78.82015
> 
> # Desvio-padrão da Amostragem Estratificada
> 
> sd(amostra_estratificada$hp)
[1] 73.38698
> 
> # O desvio-padrão mede a dispersão dos valores. Uma amostra com menor dispersão costuma produzir estimativas mais estáveis.
> 
> # Comparar o erro padrão
> 
> # Erro padrão da AAS
> 
> sd(AAS$hp) / sqrt(nrow(AAS))
[1] 21.06557
> 
> # Erro padrão da Amostragem Estratificada
> 
> sd(amostra_estratificada$hp)/sqrt(nrow(amostra_estratificada))
[1] 19.61349
> 
> # O erro padrão é calculado pela divisão do desvio padrão da amostra pela raiz quadrada do tamanho da amostra.
> # Quanto menor o erro padrão , maior a precisão da estimativa da média. 
> 
> ## Comparar o erro absoluto em relação à população 
> 
> # Média populacional
> 
> media_pop <- mean(mtcars$hp)
> 
> # Erro da AAS
> 
> abs(mean(AAS$hp) - media_pop)
[1] 7.3125
> 
> # Erro da Estratificada
> 
> abs(mean(amostra_estratificada$hp) - media_pop)
[1] 2.258929
> 
> 
> # abs() calcula o valor absoluto da diferença entre a média da amostra e a média da população.
> # Quanto menor essa diferença, mais próxima a amostra está da realidade da população.
> 
> ## Conclusão 
> 
> # Na base mtcars, a Amostragem Estratificada tende a apresentar maior precisão, pois garante que os três grupos de veículos (4, 6 e 8 cilindros) estejam representados na amostra. Já a Amostragem Aleatória Simples pode, por acaso, selecionar mais veículos de um grupo e menos de outro, o que pode aumentar a variabilidade das estimativas. Assim, quando a população possui grupos naturalmente distintos, como ocorre na variável cyl, a Amostragem Estratificada geralmente produz estimativas mais representativas e precisas do que a AAS.
