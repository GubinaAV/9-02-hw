# Домашнее задание к занятию "`GitLab`" - `Gubina Angela Vital'evna`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/8-03-gitlab-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

Что нужно сделать:
1.	Разверните GitLab локально, используя Vagrantfile и инструкцию, описанные в этом репозитории.
2.	Создайте новый проект и пустой репозиторий в нём.
3.	Зарегистрируйте gitlab-runner для этого проекта и запустите его в режиме Docker. Раннер можно регистрировать и запускать на той же виртуальной машине, на которой запущен GitLab.
В качестве ответа в репозиторий шаблона с решением добавьте скриншоты с настройками раннера в проекте.

### Решение 1
![alt text](https://github.com/GubinaAV/8-03-hw/blob/main/img/01.png)
---

### Задание 2

Что нужно сделать:
1.	Запушьте репозиторий на GitLab, изменив origin. Это изучалось на занятии по Git.
2.	Создайте .gitlab-ci.yml, описав в нём все необходимые, на ваш взгляд, этапы.
В качестве ответа в шаблон с решением добавьте:
·	файл gitlab-ci.yml для своего проекта или вставьте код в соответствующее поле в шаблоне;
·	скриншоты с успешно собранными сборками.

### Решение 2
![alt text](https://github.com/GubinaAV/8-03-hw/blob/main/img/02.png)
|
![alt text](https://github.com/GubinaAV/8-03-hw/blob/main/img/03.png)
|
![alt text](https://github.com/GubinaAV/8-03-hw/blob/main/img/04.png)
|
![alt text](https://github.com/GubinaAV/8-03-hw/blob/main/img/05.png)
_
##### #.gitlab-ci.yml
image: docker/compose:latest

services:
  - docker:dind

before_script:
  - docker info
  - docker-compose --version

buildJob:
  stage: build
  tags:
    - docker
  script:
    - docker-compose -f docker-compose.yaml up
