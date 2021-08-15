---
title: Data Analysis of Public Telephones on Brazil using R
date: 2021-08-15 05:25:00 -0300
categories: [Data Analysis, R]
tags: [data, data analysis, data visualization, R, programming, orelhao, tup]     # TAG names should always be lowercase
---

To begin to learn the basics of R and plot data, I searched online for publicly available data on the Brazilian government site when I founded a dataset of TUP's - [Telefone de Uso Público](https://dados.gov.br/dataset/tuptelefoneusopublico) - (Public Use Telephones). Since nowadays almost everybody has a smartphone, they should be unused now, right?

![Orelhão]({{ site.baseurl }}/images/orelhao/orelhao.jpg)
_Image from [Gustavo Ferreira Gustavo](https://pixabay.com/pt/users/gustavofer74-791316/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=664968)_

## A little bit of history ##
In Brazil, we name the telephones "Orelhão" because of their format capable of reducing the noise from 40 to 90 dB. Designed by the architect Chu Ming Silveira in 1971, released in 1972, and exported in 1973, the fiberglass protective shell officially called Chu I and II, received nicknames like "Tulipa" (tulip), "Capacete de Astronauta" (astronaut helmet), but "Orelhão" is popular until nowadays. 

The Chu I model - nicknamed "Orelhinha" (small ear) - developed by the CTB (Companhia Telefônica Brasileira), the Brazilian Telephone Company, had a transparent design and was made for indoor use. After a successful test on the company building, a larger and more robust model Chu II was designed and put on the streets.

### The companies ###
In 1970, the Brazilian telecom sector changed to expand and facilitate communication in the country. From the military dictatorship, the creation of the state-owned holding TELEBRAS for all kind of telecom companies that lasted until 1997, when the laws changes to set rules and inspect the sector in 1998, making room for private companies.

Now under the ANATEL inspection, lots of changes happened to the companies. So, on the dataset, we have five companies:
- CTBC:  Companhia de Telecomunicações do Brasil Central, now Algar Telecom, with is head office on Uberlândia, Minas Gerais. There was another CTBC, called Companhia Telefônica da Borda do Campo S/A, but it acted in São Paulo and now is part of TELEFÔNICA
- EMBRATEL: Empresa Brasileira de Telecomunicações, now owned by Claro S.A.
- OI: previously named Telemar Norte Leste S/A - Telemar, changed its name to OI in 2007
- SERCOMTEL: Serviço de Comunicações Telefônicas de Londrina has its headquarters in Londrina, Paraná
- TELEFÔNICA: Telefónica S/A is an Spanish companie that holds the control of Vivo.

I had a hard time finding good images, but let's see how they look.

| CTBC | EMBRATEL | OI | SERCOMTEL | TELEFÔNICA |
|:----:|:--------:|:--:|:---------:|:----------:|
| ![Orelhao ALGAR]({{ site.baseurl }}/images/orelhao/orelhao-algar.jpg) | ![Orelhao EMBRATEL]({{ site.baseurl }}/images/orelhao/orelhao-embratel.jpg) | ![Orelhao ALGAR]({{ site.baseurl }}/images/orelhao/orelhao-oi.jpeg) | ![Orelhao SERCOMTEL]({{ site.baseurl }}/images/orelhao/orelhao-sercomtel.jpg) |![Orelhao TELEFÔNICA]({{ site.baseurl }}/images/orelhao/orelhao-telefonica.jpg)|
| _Image from [G1.com](http://g1.globo.com/minas-gerais/triangulo-mineiro/noticia/2014/03/com-pouca-utilizacao-mais-de-1-mil-orelhoes-sao-retirados-de-uberlandia.html)_ | _Image from [Gazeta do Povo](https://www.gazetadopovo.com.br/economia/dois-orelhoes-para-se-falar-a-vontade-25k7cyk7ntljbkgia6i5jv58u/)_ | _Image from [Alv/Wikipédia](https://commons.wikimedia.org/wiki/File:3orelhoesoi.JPG)_ | _Image from [Adam Esteves/Wikipedia](https://pt.wikipedia.org/wiki/Ficheiro:Telefone_Público_da_Sercomtel.jpg)_ | _Image from [Orelhões do Brasil/Guarulhos Web](http://orelhoes.blogspot.com/2012/04/encontrado-mais-alguns-orelhoes-da-vivo.html)_ |

## The numbers ##
Brazil today have 169214 public phones, with the following distribution:
![Phones by company]({{ site.baseurl }}/images/orelhao/phones-by-company.jpg)
![Phones by status]({{ site.baseurl }}/images/orelhao/phones-status.jpg)

Plotting this phones on the map:
![Phones map - Brazil]({{ site.baseurl }}/images/orelhao/phones-map-full.jpg)

During the data cleanup, I faced a few problems. A bunch of phones coordinates is way out. So, I had to keep some of them outside the plot. To be precise, 5400 phones (which corresponds to 3.2% of the dataset) are outside the plot area, most of them from Salvador (1045), Belém (659), Rio de Janeiro (586), Florianópolis (359), Niterói (190), Guarujá (161), Santos (111) and Vila Velha (108). Those cities are on the coast, so the coordinates landed on the sea. Florianópolis and Fernando de Noronha are cities located on islands. And a few phones had 0,0 coordinates, which probably is the standard coordinate to put instead of NA or NULL.
![Phones map - Fernando de Noronha]({{ site.baseurl }}/images/orelhao/phones-map-noronha.jpg)


After that, I tried to see the distribution by quantity per city. 13 cities do not have phones on the database, and one small city doesn't have coordinates and was left behind. The result is:
![Phones map - city]({{ site.baseurl }}/images/orelhao/phones-map-city.jpg)

---
## Understanding the distribution by company ##

- ### CTBC ##
The company is from Uberlândia - Minas Gerais, but have his services expanded to other neighboring states (São Paulo, Goiás e Mato Grosso do Sul). It was affiliated but not part of the TELEBRAS group. We had 19 phones from the database outside the plot from 12667 total. 
![Phones map - CBTC]({{ site.baseurl }}/images/orelhao/phones-map-ctbc.jpg)

- ### EMBRATEL ###
The company acts at the whole country, but have fewer phones. This company came from the privatization of TELEBRAS with its focus was on satellite communications, having a branch called EMBRATEL Star One. 5 phones outside the plot, 584 total. 
![Phones map - EMBRATEL]({{ site.baseurl }}/images/orelhao/phones-map-embratel.jpg)

- ### OI ###
In 1972, the military president changed the law and created a company called TELEBRAS, which acted as a holding for the telecom companies (EMBRATEL included). Then during the privatization process previously said, part of the TELEBRAS structure sold became Brasil Telecom S/A (including the center-west and south region states) and TELEMAR (north, northeast, and southeast region states). 

|TELEMAR Area | Brasil Telecom Area|
|:-----------:|:------------------:|
|![TELEMAR Area]({{ site.baseurl }}/images/orelhao/telemar-area.png) | ![Brasil Telecom Area]({{ site.baseurl }}/images/orelhao/brasil-telecom-area.png)|
|_Image from [Arthur Jacob/Wikipédia](https://pt.wikipedia.org/wiki/Ficheiro:Mapa_de_cobertura_da_Oi_Fixo.svg)_ | _Image from [Arthur Jacob/Wikipédia](https://pt.wikipedia.org/wiki/Ficheiro:Mapa_de_cobertura_da_Brasil_Telecom.svg)_|

Then, the 16 TELEMAR companies merged under the OI name in 2001, and in 2007 OI bought Brasil Telecom and became one large company covering the whole country, explaining the number of phones they have. 4925 phones are outside the map from 120356 total
![Phones map - OI]({{ site.baseurl }}/images/orelhao/phones-map-oi.jpg)

- ### SERCOMTEL ###
Founded in 1964 by the Londrina mayor named Serviço de Comunicações Telefônicas de Londrina the company was afilliate but not part of the TELEBRAS group. Since it covers only one city with its 669 phones, the map shows only the Paraná state.
![Phones map - SERCOMTEL]({{ site.baseurl }}/images/orelhao/phones-map-sercomtel.jpg)

- ### TELEFÔNICA ###
Telefónica is a Spanish telecom conglomerate that bought three companies at the privatization in 1998. TELESP and his subsidiary CTBC (the Companhia Telefônica da Borda do Campo, not the first of this list) and CETERP (Centrais Telefônicas de Ribeirão Preto). TELESP was part of TELEBRAS, CETERP was another affiliate but was not part. In 2011 Telefónica changed TELESP name to Telefônica Brazil and bought Portugal Telecom participation on their joint-venture named Vivo, changing the control to Telefônica Brazil. Then in 2012, all the services changed to Vivo, justifying why Telefônica paints its phones with the purple color of Vivo. 

Since all the phones concentrate in the São Paulo state, the plot is only from that state. They have 34938 phones and 451 outside this plot. Since São Paulo is the most populous state in the country, they hold lots of phones to supply the demand.
![Phones map - TELEFÔNICA]({{ site.baseurl }}/images/orelhao/phones-map-telefonica.jpg)

## Installation date ##
When we look at the installation dates, 351 phones had it before 1970, which does not make sense, excluding them.
![Phones install date]({{ site.baseurl }}/images/orelhao/phones-by-install.jpg)

The peak was reached in 2001 when Brazil had 1.38 million phones installed. But in the early 2000s became easier to get a private phone line, making the number of TUPs fall to almost 10% of this value 21 years later.

## Last time used ##
The dataset provides the last used time from each phone.
![Phones last used]({{ site.baseurl }}/images/orelhao/phones-last-use.jpg)

## Acessibility ##
Some phones are different, separated into two groups that can overlap:

### For wheelchair users ###
Those phones are mounted lower, as we can see on the first pic of this page: the purple phone is lower mounted to provide accessibility. 
![Phones wheelchair]({{ site.baseurl }}/images/orelhao/phones-by-wheelchair.jpg)

_Side note: all EMBRATEL phones reported as adapted for wheelchair users, which is probably not true._

### For hearing impaired ###
Those phones have a text terminal attached to them like this
![Hearing impaired phone]({{ site.baseurl }}/images/orelhao/hearing-impaired-phone.jpg)
_Image from [Sem Barreiras](https://www.sembarreiras.jor.br/2018/02/01/o-telefone-como-ferramenta-de-comunicacao-para-surdos/)_

Again, plotting the graphs:

![Phones hearing impaired]({{ site.baseurl }}/images/orelhao/phones-by-hearing-impaired.jpg)

_Side note: again, the EMBRATEL data probably is distorted._

## Conclusions ##

We can conclude that:
- CTBC all phones stop at 2018 at the database probably they stopped updating.
- EMBRATEL probably stopped updating the database too.
- Most of the phones uses are from this year! Brazil is a continental country with laws where telecom companies need to keep a minimum amount of phones available for the population, especially in small cities in the countryside.

## Sources ##

### Dataset ###
[Cities dataset](https://github.com/kelvins/Municipios-Brasileiros) \\
[IBGE API to city info](https://servicodados.ibge.gov.br/api/docs/localidades) \\
[TUP](https://dados.gov.br/dataset/tuptelefoneusopublico) - _Dataset last update: 2021-02-11, 09:29 AM (UTC-03:00)_

### Information ###
[TELECOMUNICAÇÃO NO BRASIL: O GUIA COMPLETO SOBRE O ASSUNTO](https://itc.com.br/telecomunicacao-no-brasil/)\\
[Telecomunicações Brasileiras - TELEBRAS - Wikipedia](https://pt.wikipedia.org/wiki/Telecomunicações_Brasileiras_S.A.)
[Companhia Telefônica Brasileira](https://pt.wikipedia.org/wiki/Companhia_Telefônica_Brasileira)\\
[Algar Telecom - Wikipedia](https://pt.wikipedia.org/wiki/Algar_Telecom)\\
[Algar Telecom](https://www.algartelecom.com.br/para-voce/telefonia-fixa/telefones-publicos.html)\\
[EMBRATEL - Wikipedia](https://pt.wikipedia.org/wiki/Embratel)\\
[TELEMAR - Wikipedia](https://pt.wikipedia.org/wiki/Telemar)\\
[OI - Wikipedia](https://pt.wikipedia.org/wiki/Oi_(empresa))\\
[Brasil Telecom - Wikipedia](https://pt.wikipedia.org/wiki/Brasil_Telecom)\\
[Sercomtel - Wikipedia](https://pt.wikipedia.org/wiki/Sercomtel)\\
[Telefônica Brasil - Wikipedia](https://pt.wikipedia.org/wiki/Telefônica_Brasil)\\
[Vivo - Wikipedia](https://pt.wikipedia.org/wiki/Vivo)