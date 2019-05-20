---
title: Подключение к источнику данных PostgreSQL (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b7a75a72-b267-444f-9eb8-d23eb333fc35
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 168e53dde51641d79569eb3ef6a1930d0084d10f
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723985"
---
# <a name="connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard"></a>Подключение к источнику данных PostgreSQL (мастер импорта и экспорта SQL Server)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В этом разделе показано, как подключаться к источникам данных **PostgreSQL** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server. 

> [!IMPORTANT]
> Подробные требования и необходимые условия для подключения к базе данных PostgreSQL выходят за рамки этой статьи Майкрософт. В ней предполагается, что у вас уже установлено клиентское программное обеспечение PostgreSQL и вы можете успешно подключиться к целевой базе данных PostgreSQL. Для получения дополнительных сведений обратитесь к администратору базы данных PostgreSQL или к документации по PostgreSQL.

## <a name="get-the-postgresql-odbc-driver"></a>Получение драйвера ODBC для PostgreSQL

### <a name="install-the-odbc-driver-with-stack-builder"></a>Установка драйвера ODBC с помощью построителя стека
Запустите построитель стека, чтобы добавить драйвер ODBC для PostgreSQL (psqlODBC) в вашу установку PostgreSQL.

![Установка ODBC для PostgreSQL с помощью построителя стека](../../integration-services/import-export-data/media/install-postgresql-odbc-with-stack-builder.png)

### <a name="or-download-the-latest-odbc-driver"></a>Скачивание последней версии драйвера ODBC
Или скачайте установщик Windows для последней версии драйвера ODBC для PostgreSQL (psqlODBC) прямо с этого FTP-сайта — [https://www.postgresql.org/ftp/odbc/versions/msi/](https://www.postgresql.org/ftp/odbc/versions/msi/). Извлеките содержимое ZIP-файла и запустите файл MSI.

## <a name="connect-to-postgresql-with-the-postgresql-odbc-driver-psqlodbc"></a>Подключение к PostgreSQL с помощью драйвера ODBC для PostgreSQL (psqlODBC)
Драйверы ODBC не приводятся в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, сначала выберите **поставщик данных .NET Framework для ODBC** в качестве источника данных на странице **Выбор источника данных** или **Выбор назначения**. Этот поставщик служит оболочкой для драйвера ODBC.

Ниже показан экран, который появляется сразу после выбора поставщика данных .NET Framework для ODBC.

![Подключение к PostgreSQL с помощью ODBC ранее](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-postgresql-odbc-driver"></a>Указываемые параметры (драйвер ODBC для PostgreSQL)

> [!NOTE]
> Параметры подключения для этого поставщика данных и драйвера ODBC одинаковы независимо от того, является ли PostgreSQL источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

Чтобы подключиться к PostgreSQL с помощью драйвера ODBC для PostgreSQL, соберите строку подключения, используя указанные ниже параметры и их значения. Полный формат строки подключения приведен после списка параметров.

> [!TIP]
> Вы можете получить помощь в построении строки подключения. Кроме того, вместо указания строки подключения вы можете предоставить существующее имя DSN (имя источника данных) или создать новое. Дополнительные сведения об этих возможностях см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC — **PostgreSQL ODBC Driver(UNICODE)** или **PostgreSQL ODBC Driver(ANSI)**.

**Server**  
Имя сервера PostgreSQL. 

**Порт**  
Порт, используемый для подключения к серверу PostgreSQL.

**База данных**  
Имя базы данных PostgreSQL.

**Uid** и **Pwd**   
**Uid** (идентификатор пользователя) и **Pwd** (пароль) для подключения.

### <a name="connection-string-format"></a>Формат строки подключения
Ниже приведен формат типичной строки подключения. 

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=<server>;Port=<port>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Ввод строки подключения
Введите строку подключения в поле **ConnectionString** либо введите имя DSN в поле **Dsn** на странице **Выбор источника данных** или **Выбор назначения**. После того как вы введете строку подключения, мастер проанализирует ее и отобразит отдельные свойства и их значения в списке.

В приведенном ниже примере используется следующая строка подключения:

    ```
    Driver={PostgreSQL ODBC Driver(UNICODE)};Server=127.0.0.1;Port=5432;Database=postgres;UID=postgres;PWD=********
    ```

Ниже показан экран, который появляется после ввода строки подключения.

![Подключение к PostgreSQL с помощью ODBC](../../integration-services/import-export-data/media/connect-to-postgresql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и дополнительные сведения
Сведения о подключении к PostgreSQL с помощью поставщика данных, не представленного в этом списке, см. в разделе [Строки подключения PostgreSQL](https://www.connectionstrings.com/postgresql/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметрах подключения, описанных на этой странице.

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

