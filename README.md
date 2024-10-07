# Домашнее задание к занятию «Уязвимости и атаки на информационные системы» - Протасов Владислав

### Задание 1.

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

Какие сетевые службы в ней разрешены?

Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

Приведите ответ в свободной форме.

---

Картинка

https://vulners.com/search?query=CVE-2023-2640

https://vulners.com/search?query=CVE-2023-3262

https://vulners.com/search?query=CVE-2024-28085

---

### Задание 2.

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?

Как отвечает сервер?

Приведите ответ в свободной форме.

---

При проведении сканирования Metasploitable в режимах SYN, FIN, Xmas и UDP, различия в сетевом трафике проявляются в типах отправляемых пакетов и их интерпретации. SYN сканирование использует пакеты с флагом SYN и не завершает "трёхкратное рукопожатие"; если хост отвечает SYN-ACK, порт считается открытым, а ответ RST — закрытым12. FIN сканирование отправляет пакеты с флагом FIN; ответ RST указывает на закрытый порт, отсутствие ответа — на открытый14. Xmas сканирование посылает пакеты с флагами FIN, PSH и URG; аналогично, ответ RST говорит о закрытом порте, а отсутствие ответа — об открытом25. UDP сканирование не устанавливает соединение и может быть менее точным; отсутствие ответа может означать открытый порт или фильтрацию4. Ответы сервера интерпретируются по флагам: RST указывает на закрытые порты, а отсутствие ответа может свидетельствовать о фильтрации или открытости порта.

---
