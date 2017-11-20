---
title: "Подключения для источника данных SQL Server (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 386cedbb-fae5-45ce-9363-c4a417f80a2f
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 17910c8e30dee98f39e977896fb67774b54a798d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard"></a>Подключения для источника данных SQL Server (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **Microsoft SQL Server** из источника данных **выберите источник данных** или **Выбор назначения** страницы мастера экспорта и импорта SQL Server. Существует несколько поставщиков данных, которые можно использовать для подключения к SQL Server.

> [!TIP]
> Если вы в сети с несколькими серверами, он может быть проще введите имя сервера, а не разверните раскрывающегося списка серверов. Если нажать кнопку раскрывающегося списка, может занять много времени, чтобы запросить все доступные серверы в сети, результаты не и может даже необходимый сервер.

## <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Подключение к SQL Server через поставщик Microsoft OLE DB для SQL Server 
После выбора **поставщик данных .NET Framework для SQL Server** на **выберите источник данных** или **Выбор назначения** страницы мастера, на странице отображается список групп параметров для поставщика. Многие из них являются чужим имена и неизвестные параметры. К счастью Чтобы подключиться к любую базу данных, обычно необходимо предоставить несколько видов информации. Можно игнорировать значения по умолчанию для других параметров.

> [!NOTE]
> Параметры соединения для поставщика данных являются одинаковыми как для SQL Server не в источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

|Необходимые сведения|.NET framework поставщика данных для свойства SQL Server|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения о проверке подлинности (имя входа)|**Встроенная безопасность**; или, **идентификатор пользователя** и **пароль**<br/>Если вы хотите просмотреть список раскрывающегося списка баз данных на сервере, сначала необходимо ввести допустимое имя входа сведения.|
|Имя базы данных|**Исходный каталог**|

![Подключиться к SQL с помощью поставщика .NET](../../integration-services/import-export-data/media/connect-to-sql-with-net-provider.jpg)

### <a name="options-to-specify-net-framework-data-provider-for-sql-server"></a>Параметры, задающие (Framework поставщик данных .NET для SQL Server)

> [!NOTE]
> Параметры соединения для поставщика данных являются одинаковыми как для SQL Server не в источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

**Источник данных**  
 Введите имя или IP-адрес сервера-источника или назначения, или выберите сервер из раскрывающегося списка.  
 
 Чтобы указать нестандартный порт TCP, введите запятую после имени сервера или IP-адрес, а затем введите номер порта.
 
 **Исходный каталог**  
 Введите имя базы данных-источника или назначения, или выберите базу данных из раскрывающегося списка.  
  
 **Встроенные функции безопасности**  
 Укажите **True** для соединения со встроенной проверкой подлинности Windows (рекомендуется), или **False** соединяться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. При выборе **False**необходимо ввести идентификатор пользователя и пароль. Значение по умолчанию равно **False**.  
  
 **Идентификатор пользователя**  
 Введите имя пользователя, если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.  
  
 **Пароль**  
 Введите пароль, если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.  

## <a name="connect-to-sql-server-with-the-odbc-driver-for-sql-server"></a>Подключиться к SQL Server с помощью драйвера ODBC для SQL Server 
Драйверы ODBC не перечислены в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, начинают с выбора **поставщик данных .NET Framework для ODBC** как источник данных. Этот поставщик действует как оболочка для драйвера ODBC.

> [!TIP]
> **Получить последнюю версию драйвера**. Загрузить [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).

Вот универсального экран, появляется сразу после выбора поставщик данных .NET Framework для ODBC.

![Подключение к SQL с ODBC до](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-sql-server"></a>Параметры, задающие (драйвер ODBC для SQL Server)

> [!NOTE]
> Параметры соединения для драйвера ODBC одинаковы ли SQL Server не в источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

Чтобы подключиться к SQL Server с последнюю версию драйвера ODBC, сформируйте строку подключения, которая включает следующие параметры и их значения. Формат полной строки соединения непосредственно после списка параметров.

> [!TIP]
> Получите справку по сборке выбрана правильная строка подключения. А не строку подключения, укажите существующего источника данных (имя источника данных) или создайте новую. Дополнительные сведения об этих параметрах см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC. Имя отличается для различных версий драйвера.

**Server**  
Имя сервера SQL Server.

**База данных**  
Имя базы данных.  

**Trusted_Connection**; или, **Uid** и **Pwd**  
Укажите **Trusted_Connection = Yes** для соединения со встроенной проверкой подлинности Windows; также можно указать **Uid** (идентификатор пользователя) и **Pwd** (пароль) для подключения с проверкой подлинности SQL Server.

### <a name="connection-string-format"></a>Формат строки соединения
Ниже приведен формат строки соединения, использующего встроенную проверку подлинности Windows.

    `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;trusted_connection=Yes;`

Ниже приведен формат строки соединения, использующей проверку подлинности SQL Server вместо встроенной проверки подлинности Windows.

     `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;uid=<user id>;pwd=<password>;`

### <a name="enter-the-connection-string"></a>Введите строку подключения
Введите строку подключения в **ConnectionString** , либо ввести имя DSN в **Dsn** в **выберите источник данных** или **Выбор назначения** страницы. Введите строку подключения, мастер анализирует строку и отображает отдельные свойства и их значения в списке.

В следующем примере эта строка подключения.

    `Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;`

Вот экрана, которое будет отображаться после ввода строки подключения.

![Подключение к SQL с ODBC после](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="connect-to-sql-server-with-the-microsoft-ole-db-provider-for-sql-server-or-sql-server-native-client"></a>Подключение к SQL Server с помощью поставщика Microsoft OLE DB для SQL Server или собственный клиент SQL Server

> [!IMPORTANT]
> Поставщик Microsoft OLE DB для SQL Server и собственный клиент SQL Server не поддерживается в версиях SQL Server после выпуска SQL Server 2012. Вместо этого используйте драйвер ODBC. Дополнительные сведения о переходе к драйверу ODBC см. в следующих записях блога.
>   -   [Майкрософт переводит ODBC для собственного доступ к реляционным данным](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)
>   -   [Общие сведения о новых драйверов Microsoft ODBC для SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и Дополнительные сведения
Сведения о том, как подключиться к SQL Server с помощью поставщика данных, не указанного в этом разделе [строки подключения SQL Server](https://www.connectionstrings.com/sql-server/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметры подключения, описанных на этой странице.

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


