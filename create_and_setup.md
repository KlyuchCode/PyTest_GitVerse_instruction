# Инструкция по созданию и настройке организации, заданий и первого автотеста GITVERSE

**Автор: Ключиков Егор Владимирович 2025**

---

## Оглавление
1. [Начало](#начало)
2. [Создание и настройка организации и задания](#создание-и-настройка-организации-и-задания)
3. [Настройка репозитория задания](#настройка-репозитория-задания)
4. [Настройка и регистрация раннера](#настройка-и-регистрация-раннера)
5. [Завершение](#завершение)

---

## Начало:

Начнём с того, что нам потребуется, для того чтобы корректно настроить репозиторий-задание с автотестом:

1) Файл с автотестом `PyTest`, которого **название начинается с `test_`**. Это очень важно, так как во время запуска `PyTest` модуль ищет в репозитории файл по названию с таким началом. В противном случае автотест не запустится;
2) Файл с тестовым решением для проверки работоспособности автотеста;
3) Файл `.yml` или `.yaml`. Он обычно автоматически генерируется Гитвёрсом при создании репозитория-задания через `smartclass` и распологается в папке по данному пути `название_репозитория/.gitverse/workflows`. Это специальный файл конфигурации, который говорит, что именно нужно делать при `pull_request` или `push`. Про его правильное заполнение будет рассказано позже;
4) Сервер или виртуальная машина с операционной системой `Linux Ubuntu` с установленным `Docker`, в котом будет запущен runner при помощи бинарного файла, который позже будет установлен из `GitVerse`. 

---

## Создание и настройка организации и задания:

1) После регистрации в `GitVerse` и успешного входа нажимаем на аватарку в правом верхнем углу и в выдвинувшемся меню выбираем `SmartClass`. 

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/1.png)

2) В правом верхнем углу нажмите на кнопку `Новый класс` или `New class`, если до ещё до этого он не создавался.
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/2.png)

3) Соответственно дальше нужно создать организацию. В моём случае она уже есть.(Организация создается достаточно просто и интуитивно)

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/3.png)

4) После создания организации впишите название класса. В моем случае названием будет `pytest_curse`. Нажмите на кнопку `Создать класс` или `Create class`.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/4.png)

5) Наш класс создался теперь нужно пригласить в него учеников. Для этого нужно выбрать колонку участники и далее нажать на кнопку `Добавить участников`. 

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/5.png)

6) В списке участников пишем имена, фамилии или любую другую информацию, для того чтобы отличать пользователей. Также есть возможность загрузки имен и фамили из списка или `csv` файла. Далее нажимаем кнопку добавить.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/6.png)

7) Теперь мы видим, что наш новый участник появился, но у него статус `Не связанный пользователь`. Это обозначает что к добавленному нами пользователю не привязан аккаунт `GitVerse`. 

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/7.png)

8) Заходим в профиль организации и нажимаем на кнопку ННовая команда. Пишем название `Students` и проверяем настройки приватности.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/8.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/9.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/10.png)

9) Добавляем в нашу новую команду `Gitverse` профиль участника.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/11.png)

10) Далее создаем задание. Пишем название, оставляем приватным и выбираем шаблон. Везде используем рекомендованные настройки. Скрипт проверки пропускаем.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/12.png)

11) Копируем ссылку-приглашение и отправляем участнику. После того как он примет задание появится возможность привязать его аккаунт `Gitverse` к созданному нами ученику. Для этого заходим в класс во вкладку `Несвязанные аккаунты GitVerse` и нажимаем на кнопку `Cвязать аккаунт GitVErse с участником`.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/13.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/14.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/15.png)

12) Отлично! На данный момент мы создали репозиторий-задание и корректно добавили участника в нашу организацию и назначили задание. Теперь приступим к следующему этапу - а именно настройка самого задания.

---

## Настройка репозитория задания:

1) Заходим в наше задание и нажимаем на ссылку репозитория задания, которая находится в левом верхнем углу:

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/16.png)

2) Теперь мы видим, что находится внутри репозитория, а именно `README` файл. 

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/17.png)

3) Теперь нажимаем на кнопку меню `CI/CD`. Это автотест, который мы сейчас будем настраивать.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/18.png)

4) Нажимаем на кнопку `Перейти в настройки`, включаем тумблер на пункте `CI/CD` и нажимаем кнопку ООбновить.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/19.png)

5) Теперь заново переходим в пункт `CI/CD` и нажимаем кнопку попробовать. 

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/20.png)

6) Перед нами появится содержимое файла `demo.yaml`, который будет распологаться по пути обозначенном выше. В нем пока-что ничего не редактируем и просто нажимаем кнопку сохранить.

![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/21.png)

7) Теперь у нас в репозитории задания есть файл `README` и файл конфигурации. Переходим к настройке локального раннера.

---

## Настройка и регистрация раннера

Как было написано мною выше у нас должен быть сервер или виртуальная машина Linux Ubuntu c установленным докером. Дальше мы будем устанавливать и запускать бинарный файл. Делаем все пошагово:

- Установка `Docker` (если ещё не установлен):
```bash
# Обновляем пакеты
sudo apt update

# Устанавливаем зависимости
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Добавляем официальный GPG-ключ Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Добавляем репозиторий Docker
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Устанавливаем Docker
sudo apt update
sudo apt install -y docker-ce

# Проверяем, что Docker работает
sudo systemctl start docker
sudo docker --version  # Должна быть версия (например, 24.0.7)
sudo systemctl status docker  # Должен быть статус "active (running)"
```

- Скачивание и настройка бинарного раннера:
-  Скачиваем `act_runner` по ссылке https://gitverse.ru/api/packages/gitverse/generic/act_runner_linux_amd64/3.1.0/act_runner_linux_amd64 и помещаем файл в проект:

```bash
# Например, в папку проекта
mkdir ~/runner && cd ~/runner
wget https://gitverse.ru/gitverse/act_runner/releases/download/v0.1.0/act_runner_linux_amd64 -O act_runner
chmod +x act_runner  # Даём права на выполнение
```
	
- Соответственно проверяем, что раннер работает:

```bash
./act_runner --version
```
	
- Регистрация раннера. Переходим в `Настройки -> Раннеры -> Добавить раннер -> Скопировать токен`:
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/22.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/23.png)
![Image alt](https://github.com/KlyuchCode/PyTest_GitVerse_instruction/raw/main/images/24.png)
	
- Запускаем регистрацию:
```bash
./act_runner register
```

- Вводим токен, указываем имя раннера и пропускаем лейблы, нажав `Enter`. Видим успешную регистрацию раннера:
```bash
INFO Runner registered successfully.
```

- После этого в папке появится файл `.runner`. **Его удалять нельзя!**
- Запускаем раннер:
```bash
sudo ./act_runner daemon
```
- **Если система жалуется, что докер не запущен, то запускаем его:**
```bash
sudo systemctl start docker
sudo systemctl status docker
```

- Соответственно после `git push` в репозиторий во вкладке `CI/CD -> Задачи` задача будет обработана.

---

## Завершение:

Теперь у нас есть настроенная организация, класс, задание и автотест. Пришло время переходить к мини-документации по работе с `PyTest` и его добавлению и настройке в репозитории задания.
