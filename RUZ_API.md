Список методов, которые поддерживает RUZ
URL: `http://ruz.XXX.ru/RUZService.svc/<MethodName>`

Groups
------
Возвращает список групп.

Принимаемые параметры:

- `facultyOid` - ID образовательной программы
- `findText` - Текст для поиска

Возвращает массив объектов:
```
[{
   "chairOid":0,
   "course":2,
   "faculty":"Б 00.00.00 2010 очная XXXXXXXXXXXXXX",
   "facultyOid":0000,
   "formOfEducation":"очная форма обучения",
   "groupOid":0000,
   "number":"01",
   "speciality":""
}]
```


----------

StaffOfGroup
------
Возвращает список студентов в группе.

Принимаемые параметры:

 - `groupOid` - ID группы, можно получить через `Groups`, обязательный параметр
 - `findText` - Текст для поиска

Возвращает массив объектов:
```
[{
   "fio":"Иванов Иван Иванович",
   "shortFIO":"Иванов И.И.",
   "studentOid":00000
}]
```
----------

Streams
------
Возвращает список потоков.

Принимаемые параметры:

 - `findText` - Текст для поиска

Ответ:
```
[{
   "abbr":"БИИ100,БИИ101",
   "course":"0",
   "faculty":"Б 00.00.00 2010 очная XXXXXXXXXXXXXX",
   "facultyOid":0000,
   "formOfEducation":"очная форма обучения",
   "name":"БИИ100,БИИ101",
   "streamOid":0000,
   "yearOfEducation":2010
}]
```
----------

StaffOfStreams
------
Возвращает список групп в потоке.

Принимаемые параметры:

 - `streamOid` - ID группы, можно получить через `Groups`, обязательный параметр

Ответ:
```
[{
   "GroupNumber":"БИИ150",
   "GroupOid":0000,
   "SubgroupName":"БИИ150",
   "SubgroupOid":00000
}]
```
----------

Lecturers
------
Возвращает список преподавателей.

Принимаемые параметры:

 - `chairOid` - ID кафедры
 - `findText` - Текст для поиска

Ответ:
```
[{
   "chair":"!Не определена",
   "chairOid":1,
   "fio":"!Вакансия",
   "lecturerOid":1,
   "shortFIO":"!Вакансия "
}]
```
----------

Auditoriums
------
Возвращает список преподавателей.

Принимаемые параметры:

 - `buildingOid` - ID здания
 - `findText` - Текст для поиска

Ответ:
```
[{
   "auditoriumOid":000,
   "building":"ул. XXX NN",
   "buildingOid":00,
   "number":"001",
   "typeOfAuditorium":"Компьютерный класс"
}]
```

----------

TypeOfAuditoriums
------
Возвращает список типов аудиторий.

Ответ:
```
[{
   "abbr":"ЯА",
   "code":"",
   "name":"Языковая",
   "typeOfAuditoriumOid":0
}]
```
----------

KindOfWorks
------
Возвращает список типов занятий.

Ответ:
```
[{
   "abbr":"Контрольная работа",
   "code":"Контрольная работа",
   "complexity":0,
   "kindOfWorkOid":866,
   "name":"Контрольная работа",
   "unit":""
}]
```
----------

Buildings
------
Возвращает список зданий.

Принимаемые параметры:

- `findText` - Текст для поиска

Ответ:
```
[{
   "abbr":"XXXXXXXXXX",
   "address":"Москва, XXXXXXX, NN",
   "buildingOid":XX,
   "name":"XXXXXXXXXXX"
}]
```
----------

Faculties
------
Возвращает список образовательных программ.

Принимаемые параметры:

 - `findText` - Текст для поиска

Ответ:
```
[{
   "abbr":"XXX NNN",
   "code":"Б0X0X0XNNNN",
   "facultyOid":0000,
   "institute":"Факультет XXXXXXXXXX",
   "name":"Б 00.00.00 NNNN очная XXXXXXXXX"
}]
```
----------

Chairs
------
Возвращает список департаментов.

Принимаемые параметры:

 - `facultyOid` - ID образовательной программы
 - `findText` - Текст для поиска

Ответ:
```
[{
   "abbr":"XXXXXXXXXXXX",
   "chairOid":NNN,
   "code":"00",
   "faculty":"",
   "facultyOid":0,
   "name":"XXXXXX XXXXXX XXXXXX"
}]
```
----------

SubGroups
------
Возвращает список подгрупп. Подгруппой считается не только привычные всем 1/2, так же подгруппой будет считаться любой факультатив на который ходят студенты с данной группы.

Принимаемые параметры:

 - `findText` - Текст для поиска

Ответ:
```
[{
   "abbr":"XXXNNN_1",
   "group":"XXXNNN",
   "groupOid":0000,
   "name":"XXXNNN_1#",
   "subGroupOid":00000
}]
```
----------

PersonLessons
------
Возвращает расписание.

Принимаемые параметры:

 - `fromDate` - Начало периода в формате YYYY.MM.DD, обязательный параметр
 - `toDate` - Конец периода в формате YYYY.MM.DD, обязательный параметр
 - `receiverType` - Тип расписания(1 - для преподавателя, 2 - для аудитории, 3 - для студента)
 - `groupOid` - ID группы
 - `lecturerOid` - ID преподавателя
 - `auditoriumOid` - ID аудитории
 - `studentOid` - ID студента
 - `email` - e-mail
 - `UNS` - UNS???

Необходимо указать минимум один из параметров - `lecturerOid`, `groupOid`, `auditoriumOid`, `studentOid`, `email`. Для надежности лучше указывать группа + email.

Ответ:
```
[{
   "auditorium":"XXX",
   "auditoriumOid":NNNN,
   "beginLesson":"XX:XX",
   "building":"XXXXXXXXX ул., д. XX",
   "date":"NNNN.NN.NN",
   "dateOfNest":"\/Date(NNNNNNNNNNNNN+NN00)\/",
   "dayOfWeek":N,
   "dayOfWeekString":"Пн",
   "discipline":"XXXXXXXXX (рус)",
   "endLesson":"NN:NN",
   "group":null,
   "groupOid":0,
   "kindOfWork":"Лекция",
   "lecturer":"XXXXXXXXX X.X.",
   "lecturerOid":XXXXXX,
   "stream":"XXXNNN;XXXNNN;XXXNNN#XXXXXXXXXX",
   "streamOid":XXXXXXX,
   "subGroup":null,
   "subGroupOid":0
}]
```
