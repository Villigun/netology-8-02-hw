# Домашнее задание к занятию "`Что такое DevOps. СI/СD`" - `Колесин Владимир`

### Задание 1

1.  `Устанавливаем jenkins - sudo apt install jenkins`
2.  `Меняем пароль jenkins взяв временный пароль из /var/lib/jenkins/secrets/initialAdminPassword`
3.  `Устанавливаем go - sudo apt  install golang-go и проверяем командой go version, заходим через браузер`
4.  `Делаем форк репозитария`
5.  `Устанавливаем Nexus командой docker run -d -p 8081:8081 -p 8082:8082 --name nexus -e INSTALL4J_ADD_VM_PARAMS="-Xms512m -Xmx512m -XX:MaxDirectMemorySize=273m" sonatype/nexus3`
6.  `Получаем временный пароль, заходим в web-морду Nexus через браузер, меняем пароль`
7.  `Исправляем ошибки связанные с установкой go, тем что jenkins не в группе docker, прописываем ip адрес хоста в /etc/hosts`
8.  `Запускаем сборку проекта командой docker run -d -p 8081:8081 -p 8082:8082 --name nexus -e INSTALL4J_ADD_VM_PARAMS="-Xms512m -Xmx512m -XX:MaxDirectMemorySize=273m" sonatype/nexus3`

Результат выполнения:

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img1-01.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img1-02.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img1-03.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img1-04.png)

---

### Задание 2

1. `Создаем новый проект в Jenkins`
2. `Настраиваем pipeline, путем вписывания скрипта в поле Defination`
3. `Пытаемся собрать проект, и на 20 билд исправлений находим неочевидную ошибку в скрипте -`
   `на этапе Test криво задан путь к местоположению go. Указываем прямой путь и - победа!`

[Ссылка на скрипт](https://github.com/Villigun/netology-8-02-hw/blob/master/pipeline2.scr)

Результат выполнения:

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img2-01.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img2-02.png)

---

### Задание 3

1. `Создаем raw-hosted репозиторий в Nexus, который установили еще на первом задании`
2. `Скорее не переписываем, а создаем новый pipeline в Jenkins`
3. `Запускаем, исправляем ошибки, связанные с путем до директории с go и /app: Permission denied`
4. `Оптимизируем скрипт, чтобы основную массу параметров передавать через секцию environment`

[Ссылка на частично скопипастшенный из инторнэтов скрипт](https://github.com/Villigun/netology-8-02-hw/blob/master/pipeline3.scr)

Результат выполнения:

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img3-01.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img3-02.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img3-03.png)

### Задание 4

1. `Создаем новый репозиторий в Nexus, новый pipeline в Jenkins`
2. `Берем за основу скрипт из задания 2, вносим изменения в секции environment и stage('Upload to Nexus')`

[Ссылка на измененный скрипт](https://github.com/Villigun/netology-8-02-hw/blob/master/pipeline3.scr)

Результат выполнения:

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img4-01.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img4-02.png)

![alt text](https://github.com/Villigun/netology-8-02-hw/blob/master/img/img4-03.png)