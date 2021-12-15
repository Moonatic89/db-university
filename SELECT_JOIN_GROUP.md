Query con Group by
- Contare quanti iscritti ci sono stati ogni anno
r-> SELECT COUNT(id) AS students_enroled, enrolment_date FROM students GROUP BY enrolment_date;

- Contare gli insegnanti che hanno l'ufficio nello stesso edificio
r-> SELECT COUNT(id) AS teacher_same_address, office_address FROM teachers GROUP BY office_address;

- Calcolare la media dei voti di ogni appello d'esame
r-> SELECT exam_id, AVG(vote) AS vote_average FROM exam_student GROUP BY exam_id;

- Contare quanti corsi di laurea ci sono per ogni dipartimento
r-> SELECT department_id, COUNT(department_id) AS `department_number` FROM degrees GROUP BY department_id


Query con Join
- Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
r-> SELECT students.name, students.surname, degrees.name FROM students JOIN degrees ON students.degree_id = degrees.id WHERE degrees.name = "Corso di Laurea in Economia"

- Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
r-> SELECT degrees.name FROM degrees JOIN departments ON degrees.department_id = departments.id WHERE departments.name = "Dipartimento di Neuroscienze"

- Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
r-> SELECT courses.name FROM courses JOIN course_teacher ON courses.id = course_teacher.course_id JOIN teachers ON course_teacher.teacher_id = teachers.id WHERE teachers.name = 'Fulvio' AND teachers.surname = "Amato";

- Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
r-> SELECT students.surname, students.name, degrees.name, departments.name FROM students JOIN degrees ON degrees.id = students.degree_id JOIN departments ON departments.id = degrees.department_id ORDER BY students.surname ASC;

- Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
r-> SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname FROM courses JOIN course_teacher ON courses.id = course_teacher.course_id JOIN teachers ON course_teacher.teacher_id = teachers.id JOIN degrees ON courses.degree_id = degrees.id;


- Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
r-> SELECT DISTINCT teachers.name, teachers.surname FROM teachers JOIN course_teacher ON teachers.id = course_teacher.teacher_id JOIN courses ON course_teacher.course_id = courses.id JOIN degrees ON courses.degree_id = degrees.id JOIN departments ON degrees.department_id = departments.id WHERE departments.name = "Dipartimento di Matematica";


- BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
r-> 