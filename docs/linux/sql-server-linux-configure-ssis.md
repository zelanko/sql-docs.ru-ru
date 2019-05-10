---
title: Настройка служб SSIS в Linux с помощью служб ssis-conf | Документация Майкрософт
description: В этой статье описывается настройка службы SQL Server Integration Services (SSIS) на платформе Linux с помощью служб ssis-conf служебной программы.
author: lrtoyou1223
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: c22fed22e4d2c8d2a903f72c9a28763efd491ee0
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488368"
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Настройка SQL Server Integration Services в Linux с помощью служб ssis-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Запуском `ssis-conf` сценарий конфигурации при установке служб SQL Server Integration Services (SSIS) для Red Hat Enterprise Linux и Ubuntu. Дополнительные сведения об установке служб SSIS см. в разделе [установить SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md).

Можно также использовать `ssis-conf` программу, чтобы настроить следующие свойства:

| Command | Описание |
|-------------|---------------------------------------------------------------------|
| SET-edition | Задает выпуск SQL Server                                       |
| Данные телеметрии   | Включить или отключить службу телеметрии SQL Server Integration Services |
| программа установки       | Инициализация и настройка Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Выполнения служб ssis-conf

В примерах в этой статье выполните `ssis-conf` , указав полный путь: `/opt/ssis/bin/ssis-conf`. Если перейти в это расположение, перед запуском `ssis-conf`, программу можно запустить в контексте текущего каталога: `./ssis-conf`.

Убедитесь в том, что для выполнения команд, описанных в этой статье с правами привилегированного пользователя. Например, запустите `sudo /opt/ssis/bin/ssis-conf setup` и не `/opt/ssis/bin/ssis-conf setup`.

Для выполнения этих команд с помощью запросов на языке, которое вы хотите использовать, можно указать языковой стандарт. Например, чтобы получать запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Использовать set-edition предназначен для указания выпуска SQL Server Integration Services

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

Если вы вводите значение от 1 до 7, система настраивает бесплатный или ПЛАТНЫЙ выпуск. При вводе 8, программа предложит ввести ключ продукта, который вы приобрели:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Используйте данные телеметрии, чтобы настроить отзывов пользователей

`telemetry` Команда определяет, отправляет ли SSIS отзыв в корпорацию Майкрософт.

Для бесплатных выпусков (то есть выпуски Express, Developer и Evaluation) всегда включен в службу телеметрии. Если у вас есть бесплатный выпуск, нельзя использовать `telemetry` команду, чтобы отключить сбор данных телеметрии.

Введите следующую команду: `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

Для ПЛАТНЫХ выпусков после ввода команды, вы получите следующее сообщение:

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

При выборе **Да**, служба телеметрии включена и запускает выполнение. Служба автоматически запускается после каждой загрузки. При выборе **нет**, службу телеметрии останавливается и она отключена.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Используйте программу установки для инициализации и настройка Microsoft SQL Server Integration Services

Используйте `setup` команды при каждой установке служб SSIS.

Введите следующую команду: `sudo /opt/ssis/bin/ssis-conf setup`.

Программа предложит подтвердить или указать значения для следующих элементов:
-   Лицензии на продукт
-   Лицензионное соглашение
-   Службе телеметрии
-   Язык, используемый службами Integration Services

Для запуска `setup` команды с помощью запросов на языке, что вы предпочитаете, можно указать языковой стандарт. Например, чтобы получать запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>Формат SSIS.conf

Следующие `/var/opt/ssis/ssis.conf` файл содержит пример для каждого параметра.

Для SQL Server, можно изменить параметры системы, изменив значения в `mssql.conf` файл. Для служб SSIS вы *невозможно* изменять системные параметры, изменив значения в `ssis.conf` файл. `ssis.conf` Файл отображает только результаты настройки. Если вы хотите изменить параметры для служб SSIS, можно удалить `ssis.conf` файл и запустите `setup` еще раз выполните команду.

Ниже приведен пример `ssis.conf` файл. Каждое поле соответствует результат одного этапа установки.

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

## <a name="related-content-about-ssis-on-linux"></a>См. также сведения о службах SSIS на платформе Linux
-   [Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Расписание SQL Server Integration Services выполнения пакета в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
