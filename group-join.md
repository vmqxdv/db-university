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
```
