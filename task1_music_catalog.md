
# Каталог музыки

***

## Components

>База данных H2  
>Spring Boot  
>lombok  
>orika mapper  
>свои варианты  

## REST endpoints  

### **authors**  

- `GET /authors`  
>
> возращает всех авторов, pageable response  
>
- `GET /authors/{authorId}`  
>
> возвращает автора по id  
>
- `POST /authors`  
>
> добавляет автора  
>
- `PUT /authors/{authorId}`  
>
> обновляет информацию об авторе  
>
- `DELETE /authors/{authorId}`  
>
> удаляет автора по id  

### albums  

- `GET /albums`  
>
> возвращает все альбомы, pageable response  
>
- `GET /albums/{albumId}`  
>
> возвращает альбом по id  
>
- `POST /albums`  
>
> добавляет альбом  
>
- `PUT /albums/{albumId}`  
>
> обновляет информацию об альбоме  
>
- `DELETE /albums/{albumId}`  
>
> удаляет альбом и все песни которые к нему относятся  

### songs  

- `GET /albums/songs`  
>
> возвращает все песни  
>
- `GET /albums/{albumId}/songs/{songId}`  
>
> возвращает песню по id  
>
- `POST /albums/{albumId}/songs`  
>
> добавляет песню в альбом  
>
- `PUT /albums/{albumId}/songs/{songId}`  
>
> обновляет информацию о песне  
>
- `DELETE /albums/{albumId}/songs/{songId}`  
>
> удаляет песню  

Опционально:  

- Добавить поиск песен по названию (по части названия)  
- Добавить поиск альбома по году выхода  

## Models

Приложение должно иметь три доменные сущности:  
`Song {Long id, String name, Duration duration, List<Author> authors, Album album}`  
`Album {Long id, String name, Duration duration, List<Song> songs, LocalDate createdDate}`  
`Author {Long id, String firstname, String lastname, LocalDate birthdate, List<Song> albums}`  

## Structure

Приложение должно иметь следующую структуру:  

- Слой Repository - взаимодействие с базой данных  
  >
  > Поробовать разные инструменты (NativeQuery, JPQL, Jpa repository)  
  > Обратить внимание на CriteriaApi и Specification  
  >
- Слой Service - слой бизнес логики  
- Слой Web - слой rest контроллеров  
  >
  > Использовать Orika mapper ( <https://orika-mapper.github.io/orika-docs/> )  
  > Добавить Swagger  

Структура каталогов будет примерно следующая:  

```yml
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
