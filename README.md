# **Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 2»**-***Вуколов Евгений***
 
### Цель задания
 
В тестовой среде Kubernetes необходимо обеспечить доступ к двум приложениям снаружи кластера по разным путям.
 
------
 
### Чеклист готовности к домашнему заданию
 
1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым Git-репозиторием.
 
------
 
### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания
 
1. [Инструкция](https://microk8s.io/docs/getting-started) по установке MicroK8S.
2. [Описание](https://kubernetes.io/docs/concepts/services-networking/service/) Service.
3. [Описание](https://kubernetes.io/docs/concepts/services-networking/ingress/) Ingress.
4. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.
 
------
 
### Задание 1. Создать Deployment приложений backend и frontend
 
1. Создать Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт.
2. Создать Deployment приложения _backend_ из образа multitool. 
3. Добавить Service, которые обеспечат доступ к обоим приложениям внутри кластера. 
4. Продемонстрировать, что приложения видят друг друга с помощью Service.
5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.
 
------
 
### Задание 2. Создать Ingress и обеспечить доступ к приложениям снаружи кластера
 
1. Включить Ingress-controller в MicroK8S.
2. Создать Ingress, обеспечивающий доступ снаружи по IP-адресу кластера MicroK8S так, чтобы при запросе только по адресу открывался _frontend_ а при добавлении /api - _backend_.
3. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.
4. Предоставить манифесты и скриншоты или вывод команды п.2.
 
------
 
### Правила приема работы
 
1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl` и скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.



# **Решение**

## **Задание 1**

- Создал namespace netology-net:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20163033.png)

1. Создаю Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20163621.png)
- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20163437.png)

2. Создаю Deployment приложения _backend_ из образа multitool:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20164117.png)
- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20164130.png)

3. Добавляю Service, которые обеспечат доступ к обоим приложениям внутри кластера и запускаю:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20164651.png)
- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20164638.png)

4. Демонстрация, что приложения видят друг друга с помощью Service при помощи команды создающий временный pod с контейнером:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20214928.png)

## **Задание 2**

1. Включаю Ingress-controller в MicroK8S:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20224713.png)

2. Далее создаю файл ingress.yaml
- В файле /etc/hosts прописал внешний IP сервера и название evgenii.ru

3. Демонстрация доступа с помощью `curl` с локального компьютера:

- ![scrin](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/Снимок%20экрана%202025-03-17%20234152.png)


- Ссылки манифестов:

[backend-deployment.yaml](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/config.yml/backend-deployment.yaml)

[frontend-deployment.yaml](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/config.yml/frontend-deployment.yaml)

[ingress.yaml](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/config.yml/ingress.yaml)

[services.yaml](https://github.com/Evgenii-379/1.5-1.5.md/blob/main/config.yml/services.yaml)








