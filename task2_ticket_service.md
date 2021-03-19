
***
#### __приложение Сервис заказа билетов__ 

>База данных H2  
>Spring Boot  
>lombok  
>orika mapper  
>свои варианты

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
> - обновляет информацию о существующем рейсе    
- `PATCH /planes/{planeId}`  
> - помечает рейс как удаленный, помечает все билеты на рейс как удаленные    


__tickets__: 
- `GET /planes/{plainId}/tickets` 
> - {Query params: Boolean isSold} - возращает все билеты/ только проданные / билеты в продаже 
- `GET /plains/{plainId}/tickets/{ticketId}`  
> - возвращает билет по id
- `PUT /tickets/{ticketId}`  
> - обновляет информацию о билете
- `PATCH /tickets/{ticketId}`  
> - помечает билет как удаленный


__users__:
- `GET /users`  
> - возвращает всех пользователей
- `GET /users/{userId}`  
> - возвращает пользователя по id
- `POST /users`  
> - добавляет нового пользователя
- `PUT /users/{userId}`  
> - обновляет информацию о пользователе 
- `PATCH /users/{userId}`  
> - помечает пользователя как удаленного

Опционально:
- Добавить поиск самолетов, которые в данный момент в воздухе
- Добавить поиск самолетов, которые заходят на посадку через 10 минут
- Сделать так, чтобы нельзя было изменить информацию о билете, если до вылета меньше 10 минут

Приложение должно иметь три доменные сущности:  
`Ticket {Long id, Plane plane, User user, BigDecimal price, boolean isDeleted}`  
`Plane {Long id, String name, Integer places, LocalDate depart, Duration duration, String from, String to, boolean isDeleted}`  
`User {Long id, String firstname, String lastname, String passport, List<Tickets> tickets, boolean isDeleted}`


Приложение должно иметь следующую структуру:  
- Слой Repository - взаимодействие с базой данных
  > - Поробовать разные инструменты (NativeQuery, JPQL, Jpa repository)
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
