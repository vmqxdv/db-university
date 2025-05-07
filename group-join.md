# GROUP BY

1. Contare quanti iscritti ci sono stati ogni anno
```
SELECT 
	COUNT(*) AS 'enrolment_tot', YEAR(`enrolment_date`) AS 'enrolment_date'
FROM 
	`students`
GROUP BY
	YEAR(`enrolment_date`)
```
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```
SELECT 
	COUNT(*) AS 'teachers_per_address', `office_address`
FROM 
	`teachers`
GROUP BY
	`office_address`
```
3. Calcolare la media dei voti di ogni appello d'esame
```
SELECT 
	ROUND(AVG(`vote`)) AS 'average_vote', `exam_id`
FROM 
	`exam_student`
GROUP BY
	`exam_id`
```
4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```
SELECT 
	COUNT(*) AS 'course_per_degree', `degree_id`
FROM 
	`courses`
GROUP BY
	`degree_id`
```  
# JOIN
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```
SELECT
	*
FROM
	`students`
INNER JOIN
	`degrees` ON `degrees`.`id` = `students`.`degree_id`
WHERE
	`degrees`.`name` = 'Corso di Laurea in Economia'
```
3. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```
```
4. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```
```
5. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```
```
6. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```
```
7. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
```
```
8. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
```
```
