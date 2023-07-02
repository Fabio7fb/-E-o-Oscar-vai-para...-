# 🔹 E o-Oscar-vai-para...?
![oscars](https://github.com/Fabio7fb/-E-o-Oscar-vai-para...-/assets/125493191/dcc652a5-2e1c-4a19-9e57-dab27c797e04)

Prêmios têm sim o seu valor, mas que eles não são o único indicador de sucesso. É claro que é sempre bom ser reconhecido pelo nosso trabalho e ter um troféu ou uma placa para pendurar na parede, mas o mais importante mesmo é a satisfação pessoal que sentimos quando fizemos algo que amamos e que acreditamos ser importante. Então, sim, prêmios importam, mas não devemos deixar-los ser o único fator que determina o nosso sucesso e a nossa felicidade. Aqui você irá estudar enquanto trabalha com dados sobre os premiados do Oscar.
1. Quantas vezes Natalie Portman foi indicada ao Oscar?

 Natalie Portman foi indicada ao Oscar três vezes.
SELECT COUNT(*) from `movies` WHERE name LIKE "%Natalie Portman%";
2. Quantos carros Natelie Portman ganhou?
Natalie Portman ganhou um Oscar.
SELECT COUNT(*) from `movies` WHERE name LIKE "%Natalie Portman%" AND winner = 'True';
3. Amy Adams já ganhou algum Oscar?
Amy Adams nunca ganhou um Oscar.
SELECT COUNT(*) from `movies` WHERE name LIKE "%Amy Adams%" AND winner = 'True';
4. A série de filmes Toy Story ganhou um Oscar em quais anos?
A série Toy Story ganhou o Oscar em dois anos: 2011 e 2020.
SELECT year_ceremony from `movies` WHERE film LIKE "%Toy Story%" AND winner = 'True';
5. Quem tem mais Oscars: a categoria "Melhor Ator" ou "Melhor Filme"?
Melhor filme tem mais Oscars, com 74 contra 49 de melhor ator.
SELECT COUNT(category) from movies WHERE category = 'actor' AND winner = '1'; -- 49 

SELECT COUNT(category) from movies WHERE category = 'best picture' AND winner = '1'; -- 58

SELECT COUNT(category) from movies WHERE category = 'outstanding picture' AND winner = '1'; -- 2

SELECT COUNT(category) from movies WHERE category = 'outstanding production' AND winner = '1'; -- 11

SELECT COUNT(category) from movies WHERE category = 'outstanding motion picture' AND winner = '1'; -- 3
6. O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
Janet Gaynor foi a primeira atriz a ganhar o Oscar de melhor Atriz, em 1928.
SELECT * from movies WHERE category = 'actress' AND winner = 'True';
7. Na coluna/campo Winner, altere todos os valores com "True" para 1 e todos os valores "False" para 0.
UPDATE movies SET winner = 0 WHERE winner = 'False';
UPDATE movies SET winner = 1 WHERE winner = 'True';
8. Em qual edição do Oscar "Crash" ganhou o prêmio principal?
Na edição de 2006 do Oscar.
SELECT * from movies WHERE film LIKE "%Crash%" AND winner = 'True';
9. Bom... dê um Oscar para um filme que merece muito, mas não ganhou.
Sussurro do coração. Shizuku e Seiji, nossos queridos romances.
USE movies_data;
INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2002', '2003', '75', 'ANIMATED FEATURE FILM', 'Yoshifumi Kondō', 'Whisper of the Heart', 'True');
SELECT * from `movies` WHERE 'film' LIKE 'Whisper of the Heart';
10. O filme Central do Brasil aparece no Oscar?
Sim, ele concorreu ao Oscar de 1999.
SELECT * from `movies` WHERE name LIKE "%Brazil%";
11. Inclua no banco 3 filmes que nunca nem foram nomeados ao Oscar, mas que na sua opinião, merecem.
Vamos premiar os injustiçados: Toc Toc; O Castelo Animado; Barbie e as Doze Princesas Bailarinas.
USE ovies_data;
INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2018', '2018', '90', 'WRITING (Original Motion Picture Story)', 'Vicente Villanueva', 'Toc Toc', 'True');

ISERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2005', '2006', '78', 'ANIMATED FEATURE FILM', 'Hayao Miyazaki', 'O Castelo Animado', 'True');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2006', '2007', '79', 'ANIMATED FEATURE FILM', 'Greg Richardson, Terry Klassen', 'Barbie e as Doze Princesas Bailarinas', 'True');
12. Crie uma nova categoria de premiação. Qualquer prêmio que você queira dar. Agora vamos dar esses prêmios aos filmes que você cadastrou na questão acima.
Agora vamos dar esses prêmios aos filmes que você cadastrou na questão acima.

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2018', '2018', '90', 'BEST COMEDY MOVIE', 'Vicente Villanueva', 'Toc Toc', 'True');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2005', '2006', '78', 'BEST FILM EVER', 'Hayao Miyazaki', 'O Castelo Animado', 'True');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2006', '2007', '79', 'BEST FILM EVER', 'Greg Richardson, Terry Klassen', 'Barbie e as Doze Princesas Bailarinas', 'True');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2002', '2003', '75', 'BEST FILM EVER', 'Yoshifumi Kondō', 'Whisper of the Heart', 'True');
13. Qual foi o primeiro ano a ter um prêmio do Oscar?
1928 foi o primeiro ano a ter um prêmio do Oscar.
SELECT * from movies;
14. Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?
Em 2003, o melhor filme para Chicago, Adrien Brody ganhou o prêmio de Melhor Ator e Nicole Kidman o de Melhor Atriz.
melhor filme
SELECT * FROM movies where year_ceremony like '2003' and category like '%BEST PICTURE%' and winner = 1;
Melhor Atriz
SELECT * FROM movies where year_ceremony like '%2003%' and category like '%ACTRESS%' and winner = 1;
melhor diretor
SELECT * FROM movies where year_ceremony like '%2003%' and category like '%DIRECTING%' and winner = 1;
15. Agora procure 7 atrizes que não sejam americanas, europeias ou brasileiras. Vamos cadastrá-los no nosso banco, mas eles ainda não ganharam o Oscar. Só foram nomeados.
USE movies_data;

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner) 
VALUES ('2005', '2006', '79', 'ACTRESS IN A SUPPORTING ROLE', 'Zhang Ziyi', 'Memórias de uma Gueixa', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2006', '2007', '80', 'ACTRESS IN A SUPPORTING ROLE', 'Rinko Kikuchi', 'Babel', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2018', '2019', '91', 'ACTRESS IN A SUPPORTING ROLE', 'Yalitza Aparicio', 'Roma', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2003', '2004', '76', 'ACTRESS IN A SUPPORTING ROLE', 'Shohreh Aghdashloo', 'Casa de Areia e Névoa', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2004', '2005', '77', 'ACTRESS IN A SUPPORTING ROLE', 'Catalina Sandino Moreno', 'Maria Cheia de Graça', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2010', '2011', '83', 'ACTRESS IN A SUPPORTING ROLE', 'Hailee Steinfeld', 'Bravura Indômita', 'False');

INSERT INTO movies (year_film, year_ceremony, ceremony, category, `name`, film, winner)
VALUES ('2003', '2004', '75', 'ACTRESS IN A SUPPORTING ROLE', 'Keisha Castle-Hughes', 'A Encantadora de Baleias', 'False');
