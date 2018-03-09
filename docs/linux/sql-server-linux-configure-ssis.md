---
title: "Настройка служб SSIS в Linux с помощью служб ssis conf | Документы Microsoft"
description: "В этой статье описывается настройка SQL Server Integration Services (SSIS) для Linux с помощью служебной программы conf служб ssis."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: d71490df718bfcb6f8ce35c7d087bac4d5961aff
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Настройка служб интеграции SQL Server в Linux с conf служб ssis

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Запуском `ssis-conf` сценарий настройки при установке SQL Server Integration Services (SSIS) для Red Hat Enterprise Linux и Ubuntu. Дополнительные сведения об установке служб SSIS см. в разделе [установить SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md).

Можно также использовать `ssis-conf` программу, чтобы настроить следующие свойства:

| Command | Описание |
|-------------|---------------------------------------------------------------------|
| SET-edition | Выберите выпуск SQL Server                                       |
| Данные телеметрии   | Включение или отключение службы телеметрии SQL Server Integration Services |
| программа установки       | Инициализация и настройка Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Запустите conf служб ssis

Примеры в этой статье запуска `ssis-conf` , указав полный путь: `/opt/ssis/bin/ssis-conf`. Если перейти в это расположение, прежде чем запускать `ssis-conf`, программу можно запустить в контексте текущего каталога: `./ssis-conf`.

Убедитесь, что для выполнения команд, описанных в этой статье, с привилегиями root. Например, запустите `sudo /opt/ssis/bin/ssis-conf setup` и не `/opt/ssis/bin/ssis-conf setup`.

Для запуска этих команд с помощью запросов на языке, который вы предпочитаете, можно указать языковой стандарт. Например, чтобы получать запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Используйте набор выпуск, чтобы установить выпуск SQL Server Integration Services

Выпуск служб SSIS выравнивается с выпуском SQL Server.

Введите следующую команду: `$ sudo /opt/ssis/bin/ssis-conf set-edition`.

После ввода команды вы получите следующее сообщение:

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

Details about editions can be found at https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409.

Use of PAID editions of this software requires separate licensing through a Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate number of licenses in place to install and run this software.

Enter your edition (1-8):
```

Если ввести значение от 1 до 7, производится настройка бесплатным или ПЛАТНЫМ выпуска. При вводе 8, программа предложит ввести ключ продукта, который вы приобрели:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Используйте данные телеметрии для настройки отзывов клиентов

`telemetry` Команда определяет, отправляет ли SSIS отзыв в корпорацию Майкрософт.

Службе телеметрии всегда включен для бесплатные выпуски (то есть выпуски Express, Developer и Evaluation). Если у вас есть бесплатный выпуск, нельзя использовать `telemetry` команду, чтобы отключить телеметрии.

Введите следующую команду: `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

Для выпусков ОПЛАЧЕНО после выполнения команды, вы получите следующее сообщение:

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

При выборе **Да**, службе телеметрии включен и начинает выполнение. Служба запускается автоматически после каждой загрузки. При выборе **нет**, служба телеметрии останавливается и отключен.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Использовать программу установки, чтобы инициализировать и настроить Microsoft SQL Server Integration Services

Используйте `setup` команды всякий раз при установке служб SSIS.

Введите следующую команду: `sudo /opt/ssis/bin/ssis-conf setup`.

Программа предложит подтвердить или предоставить значения для следующих элементов:
-   Лицензии продукта
-   Лицензионное соглашение
-   Службе телеметрии
-   Язык, используемый службами Integration Services

Для запуска `setup` команды вывода сообщений на языке, что вы предпочитаете, можно указывать локаль. Например, чтобы получать запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>Формат SSIS.conf

Следующие `/var/opt/ssis/ssis.conf` файл содержит пример для каждого параметра.

Для SQL Server, можно изменить параметры системы, изменив значения в `mssql.conf` файла. Для служб SSIS вы *не* изменить параметры системы путем изменения значения в `ssis.conf` файла. `ssis.conf` Файле отображаются только результаты установки. Если вы хотите изменить параметры для служб SSIS, можно удалить `ssis.conf` файл и запустите `setup` еще раз.

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

## <a name="related-content-about-ssis-on-linux"></a>См. также о служб SSIS в Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка SQL Server Integration Services (SSIS) для Linux](sql-server-linux-setup-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Выполнение в Linux с cron пакетов служб интеграции SQL Server расписание](sql-server-linux-schedule-ssis-packages.md)
