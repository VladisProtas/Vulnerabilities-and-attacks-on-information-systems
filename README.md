# Replication-and-scaling.-Part-2. Протасов Владислав

### Задание 1
Опишите основные преимущества использования масштабирования методами: 1) активный master-сервер и пассивный репликационный slave-сервер; 2) master-сервер и несколько slave-серверов. 
Дайте ответ в свободной форме.

---

1) Конфигурация master-slave обеспечивает отказоустойчивость, позволяя пассивному серверу (slave) быстро взять на себя функции активного сервера (master) в случае его сбоя, что минимизирует время простоя. Пассивный сервер также может выполнять задачи, такие как резервное копирование и создание отчетов, снижая нагрузку на основной сервер. Эта конфигурация проста в настройке и управлении, что делает её популярной среди малых и средних предприятий, а данные на slave-сервере обеспечивают дополнительную защиту и возможность восстановления информации.
2) Использование master-сервера и нескольких slave-серверов позволяет эффективно распределять нагрузку, увеличивая производительность системы. Каждый slave обрабатывает запросы на чтение, освобождая ресурсы master для операций записи. Это также повышает доступность: при сбое одного из slave-серверов другие продолжают работать. Запросы распределяются между slave-серверами, что оптимизирует использование ресурсов и снижает время отклика. Кроме того, slave-серверы могут быть настроены для работы с различными типами запросов, что улучшает управление данными и производительность при высоких нагрузках.

---

### Задание 2
Разработайте план для выполнения горизонтального и вертикального шаринга базы данных. База данных состоит из трёх таблиц: 1) пользователи. 2) книги. 3) магазины (столбцы произвольно).
Опишите принципы построения системы и их разграничение или разбивку между базами данных.
Пришлите блоксхему, где и что будет располагаться. Опишите, в каких режимах будут работать сервера.

---

Мы можем разделить общую базу данных на несколько отдельных баз данных, таких как DB Users, DB Books и DB Stores, что будет представлять собой вертикальный шардинг. На следующем этапе мы можем, например, разделить большую базу данных пользователей на два сервера (горизонтальный шардинг). На одном сервере мы будем хранить такие данные, как идентификатор, имя, пароль, электронная почта, адрес и телефон, а на другом — информацию о истории заказов, посещениях, любимых категориях, избранных книгах. Оба сервера будут функционировать как мастер-сервера.

![alt text](https://github.com/VladisProtas/Replication-and-scaling.-Part-2./blob/main/Снимок1.PNG)

---
