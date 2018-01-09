---
title: "Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS | Документы Microsoft"
description: "В этой статье описывается SQL Server Integration Services (SSIS) для компьютеров Linux."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 2ecd66763b0fbcdff8eb0d776b9c7b7df98e60b0
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Извлечения, преобразования и загрузки данных в Linux с помощью служб SSIS

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

В этой статье описывается выполнение пакетов служб SQL Server Integration Services (SSIS) для Linux. Служб SSIS позволяет решить проблемы с интегрированием сложных данных путем извлечения данных из нескольких источников и форматов, преобразования и очистки данных и загрузку данных в несколько назначений. 

Пакеты служб SSIS, выполняемым на платформе Linux можно подключиться к Microsoft SQL Server запущен на Windows локально или в облаке, в Linux или в Docker. Они также могут подключаться к базе данных SQL Azure, хранилище данных SQL Azure, источники данных ODBC, неструктурированные файлы и других источников данных, включая источники ADO.NET, XML-файлы и службы OData.

Дополнительные сведения о возможностях служб SSIS см. в разделе [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>предварительные требования

Для запуска пакетов служб SSIS на компьютере Linux, сначала необходимо установить SQL Server Integration Services. Служб SSIS не включается в установке SQL Server на компьютерах Linux. Инструкции по установке см. в разделе [установить SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Также необходимо иметь компьютер Windows для создания и обслуживания пакетов. Средства проектирования и управления служб SSIS будут приложений Windows, которые в настоящее время недоступны для компьютеров Linux. 

## <a name="run-an-ssis-package"></a>Запустить пакет служб SSIS

Чтобы запустить пакет служб SSIS на компьютере Linux, выполните следующие действия:

1.  Скопируйте пакет служб SSIS на компьютере Linux.
2.  Выполните следующую команду:
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Запустите зашифрованный пакет (защищенный паролем)
Существует три способа выполнения пакета служб SSIS, который зашифрован с паролем:

1.  Задать значение переменной среды `SSIS_PACKAGE_DECRYPT`, как показано в следующем примере:

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Укажите `/de[crypt]` параметр и введите пароль в интерактивном режиме, как показано в следующем примере:

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Укажите `/de` параметр, чтобы предоставить пароль в командной строке, как показано в следующем примере. Этот метод не рекомендуется, поскольку она сохраняет пароль для дешифрования с помощью команды в журнале команд.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Проектировать пакеты

**Подключения к источникам данных ODBC**. С помощью служб SSIS на Linux CTP-версии 2.1 обновления и более поздних версий пакетов служб SSIS можно использовать подключения ODBC в Linux. Эта функциональность была протестирована с SQL Server и драйверы MySQL ODBC, но также требуются для работы с любой драйвер ODBC Юникода, отслеживающее спецификации ODBC. Во время разработки укажите имя источника данных или строку подключения для подключения к данным ODBC; Можно также использовать проверку подлинности Windows. Дополнительные сведения см. в разделе [записи блога Представляем поддержка ODBC в Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Пути**. Предоставляют пути стиль Windows в пакеты служб SSIS. Служб SSIS в Linux не поддерживает пути стиле Linux, но сопоставляет пути стиль Windows в стиле Linux пути во время выполнения. Затем, например, служб SSIS в Linux сопоставляет путь стиль Windows `C:\test` в стиле Linux путь `/test`.

## <a name="deploy-packages"></a>Развертывание пакетов
Пакеты можно сохранить только в файловой системе на платформе Linux в этом выпуске. База данных каталога служб SSIS и устаревшие службы SSIS недоступны в Linux для хранения и развертывания пакетов.

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Можно использовать системы Linux, таких как средства планирования `cron` планирования пакетов. Для планирования выполнения пакетов в этом выпуске нельзя использовать агента SQL Server в Linux. Дополнительные сведения см. в разделе [пакетов служб SSIS расписания в Linux с cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Ограничения и известные проблемы

Подробные сведения о ограничения и известные проблемы служб SSIS в Linux см. в разделе [ограничения и известные проблемы для служб SSIS в Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Дополнительные сведения о служб SSIS в Linux

Дополнительные сведения о служб SSIS в Linux см. в следующих записях блога:

-   [Служб SSIS для Linux доступна в SQL Server CTP2.1 2017 г.](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC поддерживается в службах SSIS в Linux (обновить SQL Server 2017 г CTP-версия 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Дополнительные сведения о служб SSIS

Microsoft SQL Server Integration Services (SSIS) — это платформа для создания решений интеграции данных высокой производительности, включая извлечения, преобразования и загрузки (ETL) пакетов для хранилищ данных. Дополнительные сведения о службах SSIS см. в разделе [Службы SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

Службы SSIS включает следующие компоненты:
- графические средства и мастера для построения и отладки пакетов в Windows
- широкий набор задач для выполнения функций потока операций, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты
- различные источники данных и назначения для извлечения и загрузки данных
- разнообразие преобразований для очистки, статистической обработки, слияния и копирования данных
- программные интерфейсы (API) для расширения служб SSIS с помощью собственных пользовательских сценариев и компоненты

Чтобы приступить к работе со службами SSIS, загрузите последнюю версию [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

## <a name="see-also"></a>См. также раздел
- [Дополнительные сведения о SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) разработки и средства управления](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [SQL Server Integration Services, учебники](../integration-services/integration-services-tutorials.md)
