![diagramm](ERD.png)

Patients {
id integer pk increments
firstname text
lastname text
surname text
date_of_birth date
adress text
phonenumber text
}

diseases {
id integer pk increments
name text
}

analizes {
id integer pk increments
name text
price integer
}

Doctor {
id integer pk increments
firstname text
lastname text
surname text
speciality text
cabinet_number integer
shedule text
}

Specialties {
id integer pk increments > Doctor.id
type text
}

Logbook {
id integer pk increments
idDoctors integer > Doctor.id
idPatients integer > Patients.id
date date
}