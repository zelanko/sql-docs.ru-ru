---
title: Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS | Документация Майкрософт
description: В этой статье описывается SQL Server Integration Services (SSIS) для компьютеров Linux
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: d01a53524bf03e0ea8318c41b05b9cc59499de33
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713226"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается, как для запуска пакетов служб SQL Server Integration Services (SSIS) в Linux. SSIS решает проблемы интеграции сложных данных путем извлечения данных из нескольких источников и форматов, преобразования и очистки данных и загрузки данных в несколько назначений. 

Пакеты служб SSIS, под управлением Linux можно подключиться к Microsoft SQL Server под управлением Windows в локальной или в облаке, в Linux или в Docker. Они также могут подключаться к базе данных SQL Azure, хранилище данных SQL Azure, источники данных ODBC, неструктурированные файлы и других источников данных, включая источники ADO.NET, XML-файлов и служб OData.

Дополнительные сведения о возможностях служб SSIS см. в разделе [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>предварительные требования

Для запуска пакетов служб SSIS на компьютер под управлением Linux, сначала необходимо установить SQL Server Integration Services. Службы SSIS не включается в установку SQL Server для компьютеров Linux. Инструкции по установке см. в разделе [установить SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Также необходимо иметь компьютер Windows для создания и обслуживания пакетов. Средства проектирования и управления служб SSIS, приложения Windows, которые в настоящее время недоступны для компьютеров Linux. 

## <a name="run-an-ssis-package"></a>Запустить пакет служб SSIS

Чтобы запустить пакет служб SSIS на компьютере Linux, выполните указанные ниже действия:

1.  Скопируйте пакет служб SSIS на компьютер Linux.
2.  Выполните следующую команду:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Выполнение зашифрованного пакета (паролем)
Существует три способа, чтобы запустить пакет служб SSIS, который зашифрован с паролем:

1.  Задайте значение переменной среды `SSIS_PACKAGE_DECRYPT`, как показано в следующем примере:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Укажите `/de[crypt]` параметр, чтобы ввести пароль в интерактивном режиме, как показано в следующем примере:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Укажите `/de` параметр, чтобы указать пароль в командной строке, как показано в следующем примере. Этот метод не рекомендуется, поскольку он хранит пароль для дешифрования с помощью команды в журнале команд.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Проектирование пакетов

**Подключение к источникам данных ODBC**. С помощью служб SSIS на Linux CTP 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также должен работать с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки можно предоставить имя DSN или строки подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога о выходе поддержки ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Пути**. Укажите пути в формате Windows в пакетах SSIS. Службы SSIS в Linux не поддерживает пути в формате Linux, но сопоставляется пути в формате Linux пути в формате Windows во время выполнения. Затем, в том случае, например, служб SSIS в Linux сопоставляет путь Windows стиля `C:\test` в стиле Linux путь `/test`.

## <a name="deploy-packages"></a>Развертывание пакетов
Пакеты можно сохранять только в файловой системе на платформе Linux в этом выпуске. База данных каталога служб SSIS и устаревшие службы SSIS недоступны в Linux для развертывания пакета и хранилища.

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Можно использовать систему Linux, таких как средства планирования `cron` планирования пакетов. Агент SQL в Linux нельзя использовать для планирования выполнения пакетов в этом выпуске. Дополнительные сведения см. в разделе [пакетов служб SSIS расписание на платформе Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Ограничения и известные проблемы

Подробные сведения об ограничениях и известных проблем служб SSIS в Linux см. в разделе [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Дополнительные сведения о службах SSIS на платформе Linux

Дополнительные сведения о службах SSIS на платформе Linux см. в следующих записях блога:

-   [SSIS на платформе Linux доступна в SQL Server CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC поддерживается в службах SSIS на платформе Linux (обновить SQL Server CTP 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Дополнительные сведения о службах SSIS

Microsoft SQL Server Integration Services (SSIS) — это платформа для создания решений интеграции данных высокой производительности, включая извлечение, преобразование и загрузку (ETL) пакетов для хранилищ данных. Дополнительные сведения о службах SSIS см. в разделе [Службы SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS включает следующие компоненты:
- Графические средства и мастера для построения и отладки пакетов на Windows
- Широкий набор задач для выполнения функций потока операций, таких как операции FTP, выполнение инструкций SQL и отправки сообщений электронной почты
- Широкий набор источников данных и мест назначения для извлечения и загрузки данных
- Разнообразие преобразований для очистки, статистической обработки, слияния и копирования данных
- Прикладные программные интерфейсы (API) для расширения служб SSIS с помощью собственных пользовательских сценариев и компоненты

Чтобы приступить к работе со службами SSIS, загрузите последнюю версию [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Дополнительные сведения о службах SSIS см. в разделе со следующими статьями:
- [Дополнительные сведения о SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) разработки и средства управления](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Руководства по службам интеграции SQL Server](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>См. также сведения о службах SSIS на платформе Linux
-   [Установка SQL Server Integration Services (SSIS) в Linux](sql-server-linux-setup-ssis.md)
-   [Настройка SQL Server Integration Services в Linux с помощью служб ssis-conf](sql-server-linux-configure-ssis.md)
-   [Ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md)
-   [Расписание SQL Server Integration Services выполнения пакета в Linux с помощью cron](sql-server-linux-schedule-ssis-packages.md)
