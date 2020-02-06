---
title: Настройка служб SSIS в Linux с помощью ssis-conf
description: В этой статье приводятся инструкции по настройке служб SQL Server Integration Services (SSIS) в Linux с помощью программы ssis-conf.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 51dc2ba27e346dea75f1bd347491d4932695fd43
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68077535"
---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Настройка SQL Server Integration Services в Linux с помощью ssis-conf

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Скрипт конфигурации `ssis-conf` запускается при установке служб SQL Server Integration Services (SSIS) для Red Hat Enterprise Linux и Ubuntu. Дополнительные сведения об установке служб SSIS см. в разделе [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md).

Кроме того, с помощью программы `ssis-conf` можно настроить следующие свойства.

| Get-Help | Description |
|-------------|---------------------------------------------------------------------|
| set-edition | Задает выпуск SQL Server.                                       |
| telemetry   | Включение или отключение службы телеметрии SQL Server Integration Services. |
| программа установки       | Инициализация и настройка служб Microsoft SQL Server Integration Services      |
|||

## <a name="run-ssis-conf"></a>Запуск ssis-conf

Примеры в этой статье выполняются в `ssis-conf` путем указания полного пути: `/opt/ssis/bin/ssis-conf`. Если вы перейдете к этому расположению перед запуском `ssis-conf`, программу можно запустить в контексте текущего каталога: `./ssis-conf`.

Выполнять команды, описанные в этой статье, следует с правами root. Например, `sudo /opt/ssis/bin/ssis-conf setup`, а не `/opt/ssis/bin/ssis-conf setup`.

Чтобы выполнить эти команды с запросом на предпочтительном языке, можно указать языковой стандарт. Например, чтобы получить запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Использование set-edition для установки выпуска SQL Server Integration Services

Выпуск служб SSIS соответствует выпуску SQL Server.

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

Если ввести значение от 1 до 7, система настроит бесплатную или платную версию. При вводе 8 программа предложит ввести ключ продукта, который вы приобрели:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Использование телеметрии для настройки отзывов клиентов

Команда `telemetry` определяет, отправляет ли SSIS отзыв в корпорацию Майкрософт.

Для бесплатных выпусков (Express, Developer и Evaluation) служба телеметрии всегда включена. Если у вас бесплатный выпуск, вы не сможете использовать команду `telemetry` для отключения телеметрии.

Введите следующую команду: `$ sudo /opt/ssis/bin/ssis-conf telemetry`.

После ввода команды в платных выпусках вы получите следующее сообщение:

```
Send feature usage data to Microsoft. Feature usage data includes information about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Если выбрать **да**, служба телеметрии будет включена и начнет работать. Служба запускается автоматически после каждой загрузки. Если выбрать **Нет**, служба телеметрии будет остановлена и отключена.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Инициализация и настройка служб Microsoft SQL Server Integration Services с помощью программы установки

Используйте команду `setup` при каждой установке служб SSIS.

Введите следующую команду: `sudo /opt/ssis/bin/ssis-conf setup`.

Программа предложит подтвердить или указать значения для следующих элементов:
-   Лицензия продукта
-   Условия лицензии
-   Служба телеметрии
-   Язык, используемый службами Integration Services

Чтобы выполнить команду `setup` с запросом на предпочтительном языке, можно указать языковой стандарт. Например, чтобы получить запросы на китайском языке, выполните следующую команду: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>Формат ssis.conf

В приведенном ниже файле `/var/opt/ssis/ssis.conf` представлен пример каждого параметра.

Для SQL Server можно изменить параметры системы, изменив значения в файле `mssql.conf`. В SSIS *невозможно* изменить параметры системы, изменив значения в файле `ssis.conf`. В файле `ssis.conf` отображаются только результаты установки. Если вы хотите изменить параметры служб SSIS, можно удалить файл `ssis.conf` и выполнить команду `setup` еще раз.

Пример файла `ssis.conf`. Каждое поле соответствует результату одного этапа установки.

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

## <a name="related-content-about-ssis-on-linux"></a>Связанные материалы о службах SSIS в Linux
-   [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md)
-   [Установка служб SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Планирование выполнения пакетов SQL Server Integration Services в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
