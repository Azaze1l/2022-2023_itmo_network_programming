University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2022/2023

Group: K34212

Author: Rusinov Vitaliy Dmitrievich

Lab: Lab3

Date of create: 10.02.2023

Date of finished: 
 
### Развертывание Netbox на Ubuntu ###
   1. Был установлен Netbox при помощи клонирования репозитория по официальной документации, и выполнено подключение 
к его веб интерфейсу.

![image](/lab3/lab_3_1.png)

 
   2. В NetBox были созданы site, devices type, manufactures, добавлены роутеры R1 и R2 и заполнена информация о них.

![image](/lab3/lab_3_2.png)
![image](/lab3/lab_3_3.png)
![image](/lab3/lab_3_4.png)
![image](/lab3/lab_3_5.png)

   3. Из NetBox экспортирован файл netbox_devices.csv с данными об устройствах. Файл скопирован на сервер.

```
scp /Users/aleksejkomarov/Downloads/netbox_devices.csv rsos@158.160.23.129:~/ 
```

   4. Далее при помощи ansible из файла netbox_devices.csv получены имена роутеров. 
На CHR, которые были созданы в прошлых работах, имена были заменены.

![image](/lab3/lab_3_6.png)
![image](/lab3/lab_3_7.png)

   5. Теперь задача обратная предыдущей - с помощью ansible playbook нужно передать информацию о роутере в NetBox.

![image](/lab3/lab_3_8.png)
![image](/lab3/lab_3_9.png)
![image](/lab3/lab_3_10.png)

   6. Был создан playbook, при помощи которого достаем информацию о серийном номере из микротика и отправляем в NetBox

![image](/lab3/lab_3_11.png)
![image](/lab3/lab_3_12.png)
![image](/lab3/lab_3_13.png)


## Выводы:
   В процессе выполнения лабораторной работы я ознакомился с инструментом NetBox, были созданы сценарии Ansible для 
   работы с NetBox. Выполнена проверка локальной связности между роутерами и NetBox.
   
![image](/lab3/lab_3_14.png)
![image](/lab3/lab_3_15.png)
![image](/lab3/lab_3_16.png)

  Схема связи
  
![image](/lab3/drawio-3.png)
