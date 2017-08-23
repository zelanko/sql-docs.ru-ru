---
title: "Подключения к источнику данных PostgreSQL (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4c82ae7eedc3e18e7591cf7ab30a507920695247
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>Подключения к источнику данных PostgreSQL (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **PostgreSQL** из источника данных **выберите источник данных** или **Выбор назначения** страницы мастера экспорта и импорта SQL Server. 

> [!IMPORTANT]
> Подробные требования и необходимые условия для подключения к базе данных PostgreSQL выходят за рамки данной статьи Microsoft. Предполагается, что у вас уже есть PostgreSQL клиентское программное обеспечение и что возможность уже установления подключения к целевой базе данных PostgreSQL. Дополнительные сведения обратитесь к администратору базы данных PostgreSQL или PostgreSQL документации.

## <a name="get-the-postgresql-odbc-driver"></a>Получить драйвер PostgreSQL ODBC

### <a name="install-the-odbc-driver-with-stack-builder"></a>Установка драйвера ODBC с помощью построителя стека
Запустите построитель стека для добавления драйверов PostgreSQL ODBC (psqlODBC) к установке PostgreSQL.

![Установите PostgreSQL ODBC с помощью построителя стека](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>Также загрузить последнюю версию драйвера ODBC
Или загрузка установщика Windows для последней версии драйвера PostgreSQL ODBC (psqlODBC) непосредственно из FTP-сайта — [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/). Извлеките файлы из ZIP-файл и запустите файл MSI.

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>Подключиться к PostgreSQL с помощью драйвера PostgreSQL ODBC (psqlODBC)
Драйверы ODBC не перечислены в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, начинают с выбора **поставщик данных .NET Framework для ODBC** как источник данных на **выберите источник данных** или **Выбор назначения** страницы. Этот поставщик действует как оболочка для драйвера ODBC.

Вот универсального экран, появляется сразу после выбора поставщик данных .NET Framework для ODBC.

![Подключиться к PostgreSQL с ODBC до](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>Параметры, задающие (драйвер PostgreSQL ODBC)

> [!NOTE]
> Параметры соединения для этого поставщика данных и драйвера ODBC одинаковы ли PostgreSQL источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

Чтобы подключиться с помощью драйвера PostgreSQL ODBC PostgreSQL, сформируйте строку подключения, которая включает следующие параметры и их значения. Формат полной строки соединения непосредственно после списка параметров.

> [!TIP]
> Получите справку по сборке выбрана правильная строка подключения. А не строку подключения, укажите существующего источника данных (имя источника данных) или создайте новую. Дополнительные сведения об этих параметрах см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC — либо **PostgreSQL ODBC Driver(UNICODE)** или **PostgreSQL ODBC Driver(ANSI)**.

**Server**  
Имя сервера, PostgreSQL. 

**Порт**  
Порт, используемый для подключения к серверу PostgreSQL.

**База данных**  
Имя базы данных PostgreSQL.

**UID** и **Pwd**   
**Uid** (идентификатор пользователя) и **Pwd** (пароль) для подключения.

### <a name="connection-string-format"></a>Формат строки соединения
Ниже приведен формат строки соединения. 

    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>

### <a name="enter-the-connection-string"></a>Введите строку подключения
Введите строку подключения в **ConnectionString** , либо ввести имя DSN в **Dsn** в **выберите источник данных** или **Выбор назначения** страницы. Введите строку подключения, мастер анализирует строку и отображает отдельные свойства и их значения в списке.

В следующем примере эта строка подключения.

    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********

Вот экрана, которое будет отображаться после ввода строки подключения.

![Подключиться к PostgreSQL с ODBC](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и Дополнительные сведения
Сведения о том, как подключиться к PostgreSQL с помощью поставщика данных, не указанного в этом разделе [строки подключения PostgreSQL](https://www.connectionstrings.com/postgresql/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметры подключения, описанных на этой странице.

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


