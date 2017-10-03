---
title: "Настройка служб SSIS в Linux с помощью служб ssis conf | Документы Microsoft"
description: "В этой статье показано, как настроить SQL Server Integration Services в Linux с помощью служебной программы conf служб ssis."
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 46327772e8c22f76770bc51f72817ceedffae469
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Настройка служб интеграции SQL Server в Linux с conf служб ssis

`ssis-conf`— Это сценарий конфигурации, при установке SQL Server Integration Services (SSIS) для Red Hat Enterprise Linux и Ubuntu. Эту программу можно использовать для настройки следующих свойств:

| Command | Description |
|-------------|---------------------------------------------------------------------|
| SET-edition | Выберите выпуск SQL Server                                       |
| Данные телеметрии   | Включение или отключение службы телеметрии SQL Server Integration Services |
| программа установки       | Инициализация и настройка Microsoft SQL Server Integration Services      |
|||

## <a name="how-to-run-ssis-conf"></a>Запуск conf служб ssis

Примеры в этой статье запуска `ssis-conf` , укажите полный путь: `/opt/ssis/bin/ssis-conf`. Если перейти к этому пути, перед запуском `ssis-conf`, программу можно запустить в контексте текущего каталога: `./ssis-conf`.

Убедитесь, что выполнение команд, описанных в этой статье, с привилегиями корневой. Например, запустите `sudo /opt/ssis/bin/ssis-conf setup` и не `/opt/ssis/bin/ssis-conf setup`.

Для запуска этих команд с помощью запросов на языке, который вы предпочитаете, можно указать языковой стандарт. Например чтобы просмотреть запросы на китайском языке, выполните следующую команду:

`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Используйте набор выпуск, чтобы установить выпуск SQL Server Integration Services

Выпуск служб SSIS выравнивается с выпуском SQL Server.

Введите следующую команду:

`$ sudo /opt/ssis/bin/ssis-conf set-edition`

После ввода команды вы видите следующее сообщение:

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at

https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409

Use of PAID editions of this software requires separate licensing through a

Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate

number of licenses in place to install and run this software.

Enter your edition(1-8):
```

Если ввести значение в диапазоне от 1 до 7, производится настройка бесплатным или платным выпуска. При вводе 8, программа предложит ввести ключ продукта, который вы приобрели:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Используйте данные телеметрии для настройки отзывов клиентов

`telemetry` Команда определяет, отправляет ли SSIS отзыв в корпорацию Майкрософт.

Службе телеметрии всегда включен для бесплатные выпуски (то есть выпуски Express, Developer и Evaluation). Если у вас есть бесплатный выпуск, нельзя использовать `telemetry` команду, чтобы отключить телеметрии.

Введите следующую команду:

`$ sudo /opt/ssis/bin/ssis-conf telemetry`

Для платных выпусков после выполнения команды, вы видите следующее сообщение:

```
Send feature usage data to Microsoft. Feature usage data includes information
about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Если выбрать **Да**, службе телеметрии включен и начинает выполнение. Служба авто начинается после каждой загрузки. Если выбрать **нет**, служба телеметрии останавливается и отключен.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Использовать программу установки, чтобы инициализировать и настроить Microsoft SQL Server Integration Services

Используйте `setup` команды всякий раз при установке служб SSIS.

Введите следующую команду:

`sudo /opt/ssis/bin/ssis-conf setup`

Программа предложит подтвердить или предоставить значения для следующих элементов:
-   Лицензии продукта
-   Лицензионное соглашение
-   Службе телеметрии
-   Язык, используемый службами Integration Services

Для запуска `setup` команды вывода сообщений на языке, что вы предпочитаете, можно указывать локаль. Например, чтобы просмотреть запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>Формат SSIS.conf

Следующие `/var/opt/ssis/ssis.conf` файл содержит пример для каждого параметра.

Для SQL Server, можно изменить параметры системы, изменив значения в `mssql.conf` файла. Для служб SSIS вы **не** изменить параметры системы путем изменения значения в `ssis.conf` файла. `ssis.conf` Файл отображаются только результаты установки. Если вы хотите изменить параметры для служб SSIS, можно удалить `ssis.conf` файл и запустите `setup` еще раз.

Ниже приведен пример `ssis.conf` файла. Каждое поле соответствует результат одного шага установки.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```
