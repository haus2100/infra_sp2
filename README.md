# api_yamdb 
# Проект YaMDb
## Описание
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

### Технологии
- Python 3.8
- Django 2.2.19
- DRF, JWT
### Установка

Создать и заполнить файл .env:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
Запустить docker-compose:
```
docker-compose up -d
```
Выполнить миграции:
```
docker-compose exec web python manage.py migrate
```
Создать суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Подгрузить статику:
```
docker-compose exec web python manage.py collectstatic --no-input 
```
Заполнить базу тестовыми данными:
```
docker-compose exec web python manage.py loaddata fixtures.json
```

### Распределение задач в команде

- Первый разработчик пишет всю часть, касающуюся управления пользователями (Auth и Users): систему регистрации и аутентификации, права доступа, работу с токеном, систему подтверждения через e-mail.
- Второй разработчик пишет категории (Categories), жанры (Genres) и произведения (Titles): модели, представления и эндпойнты для них.
- Третий разработчик занимается отзывами (Review) и комментариями (Comments): описывает модели, представления, настраивает эндпойнты, определяет права доступа для запросов. Рейтинги произведений тоже достаются третьему разработчику.
### Авторы:
- Александр Соловьёв - автор первой части. 
https://github.com/haus2100
- Дмитрий Кузнецов - автор второй части.
https://github.com/kuzdmv
- Лев Белов - автор третий части.
https://github.com/WhiteLev
