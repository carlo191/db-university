

1. Selezionare tutti gli studenti nati nel 1990 (160)
---------
SELECT SELECT COUNT(*) AS totale_studenti90
FROM `students`
WHERE YEAR(date_of_birth) = 1990;
--------

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
------
SELECT COUNT(*) AS totale_corsi
FROM university.courses
WHERE `cfu` > 10;



-------
3. Selezionare tutti gli studenti che hanno più di 30 anni
------
SELECT * 
FROM students
WHERE date_of_birth <= '1994-12-31';


------
4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
-------

SELECT COUNT(*) AS totale_primo_semestre_primo_anno
FROM `courses`
WHERE anno = 1  -- Primo anno
AND semestre = 1;


--------
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
-----
SELECT COUNT(*) AS totale_appelli_pomeriggio
FROM `exams`
WHERE DATE(`date`) = '2020-06-20'
AND TIME(`hour`) > '14:00:00';
-------



6. Selezionare tutti i corsi di laurea magistrale (38)
-----
SELECT COUNT(*) AS corsi_magistrali 
FROM university.degrees
WHERE(`level`) = "magistrale";


------
7. Da quanti dipartimenti è composta l'università? (12)
-------
SELECT COUNT(*) AS totale_dipartimenti
FROM university.departments;

-----
8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
-----
SELECT COUNT(*) AS totale_insegnanti_senza_telefono
FROM teachers
WHERE phone IS NULL;


-----
9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo
degree_id, inserire un valore casuale)
-----

INSERT INTO students (name, surname, date_of_birth, degree_id, fiscal_code, enrolment_date, registration_number,email)
VALUES ('Carlo', 'Elvisi', '2001-08-23', 1, 'XYZ123456789', '2025-01-07', 'REG123456',"carlo109@hotmail.it");

----
10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126
-----
UPDATE teachers
SET office_number = 126
WHERE id = 58;

-----

11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9
-----

DELETE FROM students
WHERE id = 5003; 

----
