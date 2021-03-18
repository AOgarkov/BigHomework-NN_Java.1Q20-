## BigHomework-NN_Java.1Q20-

===================

### Введение:
Вы можете выполнять задание в любом порядке, но прежеде чем приступить, подумайте как модули будут взаимодействовать между собой.  
Рекомендуется реализовывать приложение в порядке:
 - web -> модели -> сервисы -> репозитории
 - модели -> репозитории -> сервисы -> web  

[Кроме того, мы настоятельно рекомендуем сдавать это задание по частям, итеративно наращивая функциональность. Пожалуйста убедитесь что вы сдаёте на проверку более или менее завершённые модули, которые возможно запустить и протестировать]

***
#### __Пример: приложение Сервис заказа билетов__ 

>База данных H2  
>Spring Boot  
>lombok  
>orika mapper  

REST endpoints

__planes__:
- `GET /planes`  
> - возвращает рейсы от текущей даты и позднее
> - возвращает Pageable response
- `GET /planes/{planeId}`  
> - возвращает рейс по id
- `POST /planes` 
> - добавляет рейс, при добавлении рейса создаются билеты в нужном кол-ве  
- `PUT /planes/{planeId}` 
> - изменяет информацию о существующем рейсе    
- `DELETE /planes/{planeId}`  
> - помечает рейс как удаленный, помечает все билеты на рейс как удаленные    


__tickets__: 
- `GET /planes/{plainId}/tickets` 
> - {Query params: Boolean isSold} - возращает все билеты/ только проданные / билеты в продаже 
- `GET /plains/{plainId}/tickets/{ticketId}`  
> - возвращает билет по id
- `POST /tickets`  
> - добавляет билет в продажу
> - билетов на рейс не должно быть больше чем мест в самолете
- `PUT /tickets/{ticketId}`  
> - продажа билета, назначает билет юзеру
- `DELETE /tickets/{ticketId}`  
> - помечает билет как удаленный


__users__:
- `GET /users`  
> - возвращает всех пользователей
- `GET /users/{userId}`  
> - возвращает пользователя по id
- `POST /users`  
> - добавляет нового пользователя
- `PUT /users/{userId}`  
> - изменяет информацию о пользователе 
- `DELETE /users/{userId}`  
> - помечает пользователя как удаленного


Приложение должно иметь три доменные сущности:  
`Ticket {Long id, Plane plane, User user, BigDecimal price, boolean isDeleted}`  
`Plane {Long id, String name, Integer places, Instant depart, Duration duration, String from, String to, boolean isDeleted}`  
`User {Long id, String firstname, String lastname, String passport, List<Tickets> tickets, boolean isDeleted}`


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
