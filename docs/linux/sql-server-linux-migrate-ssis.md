---
title: Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS
description: Сведения по запуску пакетов служб SQL Server Integration Services (SSIS) в Linux. Также из этой статьи вы узнаете, где найти дополнительные сведения о возможностях служб SSIS.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: e513f6783e827617a8c0cc4a1fa0ea4644dcb6e7
ms.sourcegitcommit: 22102f25db5ccca39aebf96bc861c92f2367c77a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2020
ms.locfileid: "92115847"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

В этой статье приводятся инструкции по запуску пакетов служб SQL Server Integration Services (SSIS) в Linux. Службы SSIS позволяют решать сложные проблемы интеграции данных путем извлечения данных из нескольких источников и форматов, преобразования и очистки данных, а также загрузки данных в несколько назначений. 

Пакеты SSIS, запущенные в Linux, могут подключаться к Microsoft SQL Server, работающему в локальной среде Windows или в облаке, в Linux или в Docker. Они также могут подключаться к Базе данных SQL Azure, Azure Synapse Analytics, источникам данных ODBC, неструктурированным файлам и другим источникам данных, включая источники ADO.NET, XML-файлы и службы OData.

Дополнительные сведения о возможностях служб SSIS см. в статье [Службы SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Предварительные требования

Для запуска пакетов SSIS на компьютере Linux сначала необходимо установить службы SQL Server Integration Services. Службы SSIS не входят в состав установки SQL Server для компьютеров Linux. Инструкции по установке см. в статье [Установка служб SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Вам также потребуется компьютер Windows для создания и обслуживания пакетов. Средства разработки и управления SSIS представляют собой приложения Windows, которые в настоящее время недоступны для компьютеров Linux. 

## <a name="run-an-ssis-package"></a>Запуск пакета SSIS

Чтобы запустить пакет SSIS на компьютере Linux, выполните следующие действия.

1.  Скопируйте пакет SSIS на компьютер Linux.
2.  Выполните следующую команду:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Запуск зашифрованного (защищенного паролем) пакета
Запустить пакет SSIS, зашифрованный с помощью пароля, можно тремя способами.

1.  Задайте значение переменной среды `SSIS_PACKAGE_DECRYPT`, как показано в следующем примере:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Укажите параметр `/de[crypt]` для интерактивного ввода пароля, как показано в следующем примере:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Укажите параметр `/de` для ввода пароля в командной строке, показано в следующем примере. Использовать этот метод не рекомендуется, так как он сохраняет пароль расшифровки с помощью команды в журнале команд.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Проектирование пакетов

**Подключение к источникам данных ODBC**. С помощью служб SSIS в Linux CTP 2.1 и более поздних версиях пакеты SSIS могут использовать подключения ODBC в Linux. Эта функция была протестирована с использованием SQL Server и драйверов ODBC для MySQL, но она также должна работать с любым драйвером ODBC для Юникода, который поддерживает спецификацию ODBC. Во время разработки можно указать либо имя DSN, либо строку подключения для подключения к данным ODBC. Кроме того, можно использовать проверку подлинности Windows. Дополнительные сведения см. в [записи блога с объявлением поддержки ODBC в Linux.](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

**Пути**. В пакетах SSIS пути следует указывать в формате Windows. Службы SSIS в Linux не поддерживают пути в формате Linux, но сопоставляют пути в формате Windows с путями в формате Linux во время выполнения. К примеру, службы SSIS в Linux сопоставляют путь в формате Windows `C:\test` с путем в формате Linux `/test`.

## <a name="deploy-packages"></a>Развертывание пакетов
В этом выпуске пакеты можно хранить только в файловой системе Linux. База данных каталога SSIS и устаревшая служба SSIS недоступны для развертывания и хранения пакетов в Linux.

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Планировать выполнение пакетов можно с помощью системных средств планирования Linux, таких как `cron`. В этом выпуске использовать агент SQL в Linux для этой задачи нельзя. Дополнительные сведения см. в статье [Планирование выполнения пакетов SSIS в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Ограничения и известные проблемы

Подробные сведения об ограничениях и известных проблемах служб SSIS в Linux см в статье [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Дополнительные сведения о службах SSIS в Linux

Дополнительные сведения о службах SSIS в Linux см. в следующих записях блога.

-   [SSIS on Linux is available in SQL Server CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/) (Доступность служб SSIS в Linux в SQL Server CTP 2.1)
-   [ODBC is supported in SSIS on Linux (SQL Server CTP 2.1 refresh)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/) (Поддержка ODBC в службах SSIS в Linux (обновление SQL Server CTP 2.1))

## <a name="more-info-about-ssis"></a>Дополнительные сведения о службах SSIS

Службы Microsoft SQL Server Integration Services (SSIS) представляют собой платформу для создания высокопроизводительных решений интеграции данных, включая пакеты ETL для хранения данных. Дополнительные сведения о службах SSIS см. в разделе [Службы SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

Службы SSIS включают в себя следующие компоненты.
- Графические инструменты и мастеры для создания и отладки пакетов в Windows
- Различные задачи для выполнения таких функций рабочих процессов, как FTP-операции, выполнение инструкций SQL и отправка сообщений электронной почты
- Разнообразные источники данных и назначения для извлечения и загрузки данных
- Различные преобразования для очистки, статистической обработки, слияния и копирования данных
- API-интерфейсы для расширения служб SSIS за счет пользовательских сценариев и компонентов

Чтобы начать работу со службами SSIS, скачайте последнюю версию [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Дополнительные сведения о службах SSIS см. в следующих статьях:
- [Службы SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Средства разработки и управления Integration Services (SSIS)](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Учебники по службам Integration Services](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Связанные материалы о службах SSIS в Linux
-   [Установка служб SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Планирование выполнения пакетов SQL Server Integration Services в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)