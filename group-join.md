# GROUP BY
```
1. Contare quanti iscritti ci sono stati ogni anno
SELECT 
    COUNT(*) AS 'enrolment_tot', YEAR(enrolment_date) AS 'enrolment_date'
FROM 
    students
GROUP BY
    YEAR(enrolment_date')
```
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```
SELECT 
    COUNT(*) AS 'teachers_per_address', office_address
FROM 
    teachers
GROUP BY
    office_address
```
3. Calcolare la media dei voti di ogni appello d'esame
```
SELECT 
    ROUND(AVG(vote)) AS 'average_vote', exam_id
FROM 
    exam_student
GROUP BY
    exam_id
```
4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```
SELECT 
    COUNT(*) AS 'course_per_degree', degree_id
FROM 
    courses
GROUP BY
    degree_id
```
  
# JOIN
```
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT
    *
FROM
    students
INNER JOIN
    degrees ON degrees.id = students.degree_id
WHERE
    degrees.name = 'Corso di Laurea in Economia'
```
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```
SELECT
    *
FROM
    degrees
INNER JOIN
    departments ON departments.id = degrees.department_id
WHERE
    level = 'magistrale' AND departments.name = 'Dipartimento di Neuroscienze'
```
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```
SELECT 
    *
FROM
    course_teacher
INNER JOIN
    courses ON courses.id = course_id
WHERE
    teacher_id = 44
```
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```
SELECT
    students.*,
    degrees.name AS degree_name,
    departments.name AS department_name
FROM
    students
INNER JOIN
    degrees ON degrees.id = students.degree_id
INNER JOIN
    departments ON departments.id = degrees.department_id
ORDER BY 
    students.surname, students.name
```
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```
SELECT
    degrees.name AS degree_name,
    courses.name AS course_name,
    teachers.name AS teacher_name,
    teachers.surname AS teacher_surname
FROM
    degrees
INNER JOIN
    courses ON courses.degree_id = degrees.id
INNER JOIN
    course_teacher ON course_teacher.course_id = courses.id
INNER JOIN
    teachers ON teachers.id = course_teacher.teacher_id
```
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
```
SELECT 
    teachers.*, departments.name
FROM
    course_teacher
INNER JOIN
    teachers ON teachers.id = course_teacher.teacher_id
INNER JOIN
    courses ON courses.id = course_teacher.course_id
INNER JOIN
    degrees ON degrees.id = courses.degree_id
INNER JOIN
    departments ON departments.id = degrees.department_id
WHERE
    departments.name = 'Dipartimento di Matematica'
```
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
