## BigHomework-NN_Java.1Q20-

===================

### Введение:
Вы можете выполнять задание в любом порядке, но прежеде чем приступить, подумайте как модули будут взаимодействовать между собой.  
Рекомендуется реализовывать приложение в порядке:
 - web -> модели -> сервисы -> репозитории
 - модели -> репозитории -> сервисы -> web  

[Кроме того, мы настоятельно рекомендуем сдавать это задание по частям, итеративно наращивая функциональность. Пожалуйста убедитесь что вы сдаёте на проверку более или менее завершённые модули, которые возможно запустить и протестировать]

***
#### __Пример: приложение Каталог музыки__ 

>База данных H2  
>Spring Boot  
>lombok  
>orika mapper  

REST endpoints

api/songs: 
- `GET /songs` 
- `GET /songs/{songId}` 
- `POST /songs`
- `PUT /songs/{songId}`
- `DELETE /songs/{songId}`

 api/albums:
- `GET /albums`
- `GET /albums/{albumId}`
- `POST /album`
- `PUT /album/{albumId}`
- `DELETE /album/{albumId}`

 api/author:
- `GET /authors`
- `GET /authors/{authorId}`
- `POST /authors`
- `PUT /authors/{authorId}`
- `DELETE /authors/{authorId}`


Приложение должно иметь три доменные сущности:  
`Song {Long id, String name, Duration duration, List<Author> authors, Album album}`  
`Album {Long id, String name, Duration duration, List<Author> authors, List<Song> songs, Instant createdDate}`  
`Author {Long id, String firstname, String lastname, Instant birthdate, List<Song> songs, List<Album> albums}`

Приложение должно иметь следующую структуру:  
- Слой Repository - взаимодействие с базой данных
  > - Поробовать разные инструменты (JdbcTemplate, NativeQuery, JPQL, Jpa repository)
  > - Обратить внимание на CriteriaApi и Specification
- Слой Service - слой бизнес логики  
- Слой Web - слой rest контроллеров
  > - Использовать Orika mapper ( https://orika-mapper.github.io/orika-docs/ )
  > - Добавить Swagger

Структура каталогов будет примерно следующая:
```
app:  
  src:  
    main:  
      java:  
        com.example.app:  
          config
          model  
          repository  
          service  
          web
    test
```  

Тесты:  
- написать интеграционные тесты (MockMvc)

Опционально: Создать Dockerfile
***

### Repository: 
Необходимо реализовать классы DAO, которые будет обеспечивать работу c БД. DAO должен работать через Entity объекты предметной области.
Entity должны описывать варианты взаимодействия: One-To-One, One-To-Many.  
Реализовать CRUD операции. На каждую сущность своя таблица. Например, вы выбрали "Медиатека", значит нужно создать три таблицы "песни", "альбомы" и "авторы".
* DAO использует NamedQuery, NativeQuery. (По желанию)
* Entity должны описывать варианты взаимодействия: Many-To-Many. (По желанию)

### Markup languages: 
База данных заполняется при старте приложения из JSON файла

## Evaluation and Feedback Process

Запрос проверки осуществляется через отправку ссылки на git репозиторий с выполненной задачей.
* https://forms.office.com/Pages/ResponsePage.aspx?id=0HIbtJ9OJkyKaflJ82fJHaeWqIB3x9VNuKBJnf-qcwdURDVJSlFGU0VGMDJJUlBFUjM0NDRDVVlHNy4u
* Других домашних заданий больше не планируем в тренинге, поэтому dead line середина мая (или завершение тренинга)
