1. Selezionare tutti gli studenti nati nel 1990

r-> 
SELECT * FROM `students` WHERE YEAR(date_of_birth) = `1990`;

2. Selezionare tutti i corsi che valgono più di 10 crediti

r->
SELECT * FROM `courses` WHERE `cfu` > 10;

3. Selezionare tutti gli studenti che hanno più di 30 anni

r->
SELECT * FROM `students` WHERE YEAR(date_of_birth) < 1992;


4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea 

r-> 
SELECT * FROM `courses` WHERE `period` = "I semestre" AND `year` = 1;
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 
6. Selezionare tutti i corsi di laurea magistrale 
7. Da quanti dipartimenti è composta l'università? 
8. Quanti sono gli insegnanti che non hanno un numero di telefono?
