# Рекомендательная система для социальной сети

### В стадии оформление в GitHub. Ниже описаны основные этапы работы

В текущем финальном строится рекомендательная систему постов в социальной сети.

Часть №1:
Создадим endpoint `GET /post/recommendations/` в Python с использованием FastAPI, который принимает параметры запроса `id` и `limit` и возвращает топ `limit` постов, отсортированных по количеству лайков. Этот endpoint будет реализован в файле `app.py`.

Часть №2
В данной части строим рекомендательную систему постов в социальной сети для студентов Karpov Courses. Разрабатываю сервис, который будет для каждого пользователя возвращать посты, которые будут отображаться в его ленте социальной сети.

Оценка качества модели будет проводиться по метрике hitrate@5, которая будет проверяться в чекере на скрытых данных.

Учитываем следующие моменты:

Алгоритм должен работать быстро и не занимать большое количество памяти.
Набор пользователей фиксирован и новые пользователи не будут добавляться.
Чекер будет проверять модель в рамках того же временного периода, что и в БД.
Модели не обучаются заново при использовании сервиса. Ожидается, что ваш код будет импортировать уже обученную модель и применять ее.
Предоставляется окружение с набором необходимых библиотек, которое может быть пополнено по мере выполнения задания.
Пример пайплайна, который будет реализован:

Загрузка данных из БД и их обзор.
Создание признаков и обучающей выборки.
Тренировка модели и оценка ее качества на валидационной выборке.
Сохранение модели.
Написание сервиса: загрузка модели, получение признаков для модели по user_id, предсказание постов, которые будут лайкнуты, и возвращение ответа.
Вам также необходимо будет загрузить и сервис, и модель одновременно для работы чекера.

Часть №3
Дополняю рекомендательную систему с помощью моделей глубокого обучения.  

Часть №4
Реализуем функцию для проведения A/B эксперимента с рекомендациями постов.

1. Реализую функцию `get_exp_group`, которая по `user_id` пользователя будет определять, в какую группу попал пользователь. Для этого используйте хэш-функцию (например, `md5` из библиотеки `hashlib`) с использованием соли. Значения соли и проценты разбиения (50 на 50) выношу в константы.

2. Выношу в две отдельные функции построение рекомендаций двумя моделями (`model_control` и `model_test`).

3. В эндпоинте для построения рекомендаций использую функцию для определения группы пользователя и вызываю соответствующую функцию для построения рекомендаций. Записываю в логи информацию о примененной модели. В ответе эндпоинта указывать группу, в которую попал пользователь ("control" или "test").
 
