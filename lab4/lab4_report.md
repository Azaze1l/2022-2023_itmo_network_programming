University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2022/2023

Group: K34212

Author: Rusinov Vitaliy Dmitrievich

Lab: Lab4

Date of create: 14.02.2023

Date of finished: 

### Подготовка среды окружения:
   
1. Установим Vagrant и склонируем репозиторий с заданиями https://github.com/p4lang/tutorials. С помощью Vagrant 
развернем ВМ.
   
   ![OpenVPN UI](/lab4/lab_4_1.png)

   
2. Выполним вход под учетной записью p4/p4.

   ![OpenVPN UI](/lab4/lab_4_2.png)

### Конфигурация узлов

3. Убедимся в том что узлы не настроены выполнив инструкцию make run. Узлы действительно недоступны.
   
   ![OpenVPN UI](/lab4/lab_4_3.png)
   
   ![OpenVPN UI](/lab4/lab_4_4.png)
   
4. Изменим basic.p4:
   - Обновим код парсера, который позволяет заполнять заголовки ethernet_t, ipv4_t.
   
   ![OpenVPN UI](/lab4/lab_4_5.png)
   
   - В MyIngress дополнено action ip4_forward: определим выходной порт, обновим адрес назначения пакета, 
   источник отправления пакета, уменьшим значение TTL, обеспечим применение ipv4_lpm, если заголовок ipv4 верный.
   
   ![OpenVPN UI](/lab4/lab_4_6.png)
   
5. Выполним проверку доступности устройств.
   
   ![OpenVPN UI](/lab4/lab_4_7.png)
   
### Создание тунелирования
6. Изменим файл basic_tunnel.p4:

   - Обновим парсер myParser, а именно, добавим функцию заполненения заголовка myTunnel.
   
   ![OpenVPN UI](/lab4/lab_4_8.png)
   
   - Определим действие myTunnel_forward, которое назначает выходной порт, определим таблицу myTunnel_exact, 
   обновим выражение apply. Оно позволяет применять myTunnel_exact, если заголовок myTunell валидный.
   
   ![OpenVPN UI](/lab4/lab_4_9.png)
      
   - Обновим MyDeparser
   
   ![OpenVPN UI](/lab4/lab_4_10.png)

7. Проверим локальную связность.
   
   ![OpenVPN UI](/lab4/lab_4_11.png)

8. Выполним проверку скрипта: с h1 был оправлен пакет на h2 без туннелирования.
   
    ![OpenVPN UI](/lab4/lab_4_12.png)
   
9. Теперь проверим работу туннеля. Отправлен пакет с h1 на h2 через туннель. Как мы видим, пакет дошел до получателя с верным сообщением.
   
    ![OpenVPN UI](/lab4/lab_4_13.png)

## Выводы
Средствами языка P4 реализованы механизмы стандартного перенаправления пакетов, а также механизм туннелирования.

   ![OpenVPN UI](/lab4/lab_4_14.png)
