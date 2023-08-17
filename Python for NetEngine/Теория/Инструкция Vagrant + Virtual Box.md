
## Если Vagrant и VirtualBox не установлены:

Установить [Virtualbox](https://www.virtualbox.org/wiki/Downloads) и [Vagrant](https://www.vagrantup.com/downloads.html)

Скачать [подготовленный образ Vagrant vagrant-pyneng-11-python3-78-gns3.box](https://drive.google.com/file/d/1xxVXIKut5R2lTHBxJtY6SAy0yKj5_TZs/view?usp=sharing)

Vagrant, Virtualbox и образ должны находится в каталоге, в пути к которому нет кириллицы. Подробнее этот аспект описан в [статье](https://habrahabr.ru/post/251529/) в разделе "Предварительная настройка".

## После установки Vagrant и VirtualBox

1. Создать произвольный каталог, например, pyneng_course
2. Переместить в каталог pyneng_course образ vagrant-pyneng-11-python3-78-gns3.box
3. Открыть командную строку
4. Перейти в каталог pyneng_course и выполнить команды ниже

Добавить образ в Vagrant (при условии, что файл vagrant-pyneng-11-python3-78-gns3.box находится в текущем каталоге):

vagrant box add gns3-pyneng vagrant-pyneng-11-python3-78-gns3.box  
vagrant init gns3-pyneng  
  

После этого в текущем каталоге создался файл Vagrantfile.

В нем необходимо раскомментировать несколько строк. Найдите соответствующую секцию в файле и удалите символ решетки перед строками, как в выводе:

|   |
|---|
|config.vm.provider "virtualbox" do \|vb\|<br><br>  #   # Display the VirtualBox GUI when booting the machine<br><br>    vb.gui = true<br><br>  <br><br>  #   # Customize the amount of memory on the VM:<br><br>     vb.memory = "2048"<br><br>  end|

Объем памяти можно указать любым, но с включением виртуального оборудования, лучше выделить хотя бы 2Г.

После этого:

vagrant up  

Виртуальная машина должна запуститься.
В ней есть предустановленный пользователь:

- Username: vagrant
- Password: vagrant

В виртуальной машине:

- настроена сеть и по IP доступна хостовая система.
- установлены и настроены редакторы: vim, geany и Mu.
- установлен Python 3.7

Все модули, которые нужны в курсе, установлены в [виртуальном окружении](https://pyneng.github.io/docs/venv/) pyneng-py3-7. Перейти в него можно с помощью команды (при открытии shell переход выполняется автоматически):

workon pyneng-py3-7

## Возможные проблемы с Vagrant:

Ошибка:
URL using bad/illegal format or missing URL
Решение:
использовать другую версию vagrant - 2.15.

  
Ошибка: 
Virtual box не запустила виртуальную машину, выдав ошибку
5644 too many regions

Решение: 
Перед выполнением vagrant up необходимо убедиться, что все процессы DeviceLock в диспетчере задач выключены.

  

## Запуск GNS3

Для начала работы с оборудованием, в командной строке надо набрать gns3:
$ gns3

В открывшемся окне надо выбрать "open recent project" и там выбрать проект python.

![Capture2.PNG](https://lh4.googleusercontent.com/3zyVGHYSKfhXvP_r68fwjODrLoZpdF0zQpdP9nCObzo6p_dc5UD_4PL4flnx6WAbuFwx3VE9U868Uk6lcTUvpHgY73JImqALJPvsDUPA7Iboa6ovnz3RF0PtKI5jn-rFE7zZLS23RbOG6uT4NSqBrw)

Откроется схема.

![topology.PNG](https://lh4.googleusercontent.com/kbV7eOXliESg2SxhNPepS632S-iQUDySPBW_9vZcFC6bX9O6MkPEKF5YbX_kVw3TX7dAGPEzCxCtvcVqa-ezn8J5Wrm8zMuMblq93QdV4iy-R5yfsCQmeMmg-Fti3J02o0KUrrSunb1qnaEas_7hcg)

Для включения всех устройств надо нажать зеленую кнопку:

![InkedCapture3_LI.jpg](https://lh4.googleusercontent.com/JBX5TE1IA8uMIUOv4e4Jh8QChVhr8WYL9h_WHkvVjgmpoz_cjC7kNBXUzXyqIUdH3jjVRS3tXEDLaeJO16UlZFkn955tVhI10nRUDUfnabH0Xt5L39Vap_uiLp5_mDvZRWdh5TPrGDJqzJQ6mFD33w)

После этого можно подключаться к устройствам, нажав правой кнопкой мыши на устройстве и выбрав Console:

![Capture4.PNG](https://lh5.googleusercontent.com/4GvJJrmbguf4jdkr6NRa-TySNZJ7KTr99N6jGsAvValBHhatNOfPhGZsE6iU2r9LJpP4UPRRbNTYe4gTGy6PjSbnXnwUhxH-A7EIKC_0vwDKpgeii-t8B7ZLX9qqt0p8pPSQV1uL__YJSFLvdxtEeA)

Консоль откроется в терминале.

На всех устройствах есть базовый конфиг. И настроены IP-адреса:  
  
- R1 - 192.168.100.1
- R2 - 192.168.100.2  
- R3 - 192.168.100.3
   
На виртуалке настроен IP 192.168.100.100.
Логин/пароль на маршрутизаторах cisco/cisco, enable: cisco