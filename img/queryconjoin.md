1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
------
SELECT 
`students`.*,
`degrees`.`name` `degree_name`

FROM 
`students`
JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id` 
WHERE `degrees`.`name` = "Corso di Laurea in Economia";



-------
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze
------
SELECT 
`courses`.*,
`degrees`.*,
`departments`.`name` `name_department`

 FROM `courses`
 JOIN `degrees`
 ON `courses`.`degree_id`= `degrees`.`id`
 JOIN `departments`
 ON `degrees`.`department_id`= `departments`.`id`
 WHERE `level`= "magistrale" AND
`departments`.`name`LIKE "%neuroscienze%";


------
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
------
SELECT * 
FROM `courses`
JOIN `teachers`
ON `courses`.`degree_id` = `teachers`.`id`
WHERE `teachers`.`id` = "44";



-----
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
------
SELECT * 
FROM 
    `students`
JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
ORDER BY 
    `students`.`name` ASC, 
    `students`.`surname` ASC;

-------
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
------
SELECT 
`degrees`.*,
`courses`.*,
`teachers`.* 
FROM `degrees`

JOIN `courses`
ON `courses`.`degree_id`=`degrees`.`id`

JOIN `course_teacher`
ON `course_teacher`.`course_id`=`courses`.`id`

JOIN `teachers`
ON `course_teacher`.`teacher_id`=`teachers`.`id`;


------
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
SELECT distinct
`departments`.*,

`teachers`.* 
FROM `degrees`

JOIN `courses`
ON `courses`.`degree_id`=`degrees`.`id`

JOIN `course_teacher`
ON `course_teacher`.`course_id`=`courses`.`id`

JOIN `teachers`
ON `course_teacher`.`teacher_id`=`teachers`.`id`
JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE departments.name LIKE "%matematica%"
;
