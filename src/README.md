![diagramm](ERD.png)


> Пациенты {```
id integer pk increments
firstname text
lastname text
surname text
date_of_birth date
adress text
phonenumber text
district integer > Участки.id
polyclinic integer > Поликлиники.id```
}
* пациент прикреплен к своему участку в поликлинике, поликлиники.id, участки.id
> диагнозы {```
    id integer pk increments
    name text
    treatment_example text```
}
* здесь у нас есть виды болезней и их примерное лечение
> Анализы {```
id integer pk increments
name text
price integer```
}
* здесь у указаны виды анализов и их стоимость
> Врачи {```
id integer pk increments
firstname text
lastname text
surname text
speciality text > Специальности.id
cabinet_number integer
shedule text
polyclinic integer > Поликлиники.id
distict integer```
}
* здесь у нас врачи, где каждый привязан к определенному учатку своей поликлиники
> Специальности {```
id integer pk increments > Doctor.id
type text```
}
* тут у нас специальности врачей
> Поликлиники {```
id integer pk increments
name text
adress text
city_code integer```
}
* тут у нас поликлиники города
> Города {```
id integer pk increments > Поликлиники.id
name text```
}
* тут города
> Участки {```
id integer pk increments *>* Врачи.distict
district_name text```
}
* тут участки поликилиники
> Приемы {```
id integer pk increments
desease text > диагнозы.id
doctorID integer > Врачи.id
patientID integer > Пациенты.id
treatment text
appointmentTime date > ВремяПриема.id```
}
* по результатам приема мы можем получить направление на анализы, диагноз и лечение
> Направлениенаанализы {```
id integer pk increments
visitID integer > Приемы.id
doctorID integer > Врачи.id
patientID integer > Пациенты.id
analizeID integer > Анализы.id
note text```
}
* врач может выдать пациенту направление на анализы
> РезультатАнализов {```
id integer pk increments
result text
idPatient integer > Пациенты.id
analizeType integer > Анализы.id```
}
* пациент может получить результат анализа
> ВремяПриема {```
id integer pk increments
DoctorID integer > Врачи.id
shedule text```
}
* у врача есть свое время приема