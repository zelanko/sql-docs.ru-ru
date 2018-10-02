---
title: Подключение к источнику данных SQL Server (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 386cedbb-fae5-45ce-9363-c4a417f80a2f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b49d5a4bee30a8fc5b225bf12e15c29bf942631b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750562"
---
# <a name="connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard"></a>Подключение к источнику данных SQL Server (мастер импорта и экспорта SQL Server)
В этом разделе показано, как подключаться к источникам данных **Microsoft SQL Server** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server. Для подключения к SQL Server можно использовать ряд поставщиков данных.

> [!TIP]
> В сети с несколькими серверами может быть проще ввести имя сервера, а не разворачивать раскрывающийся список серверов. Если вы щелкнете раскрывающийся список, запрос всех доступных серверов может потребовать много времени, причем нужного сервера может не оказаться в списке.

## <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Подключение к SQL Server через поставщик Microsoft OLE DB для SQL Server 
После выбора элемента **Поставщик данных .NET Framework для SQL Server** на странице **Выбор источника данных** или **Выбор назначения** мастера появится сгруппированный список параметров для поставщика. Многие из них могут быть вам незнакомы или иметь непонятные имена. К счастью, для подключения к любой корпоративной базе данных, как правило, необходимо указать лишь некоторые данные. Остальные параметры можно пропустить.

> [!NOTE]
> Параметры подключения для этого поставщика данных одинаковы независимо от того, является ли сервер SQL Server источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

|Необходимые сведения|Свойство "Поставщик данных .NET Framework для SQL Server"|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения для проверки подлинности (имя входа)|**Встроенная система безопасности** или **Идентификатор пользователя** и **Пароль**<br/>Чтобы открыть раскрывающийся список баз данных на сервере, сначала нужно указать действительные данные для входа.|
|Имя базы данных|**Исходный каталог**|

![Подключение к SQL с помощью поставщика .NET](../../integration-services/import-export-data/media/connect-to-sql-with-net-provider.jpg)

### <a name="options-to-specify-net-framework-data-provider-for-sql-server"></a>Указываемые параметры (поставщик данных .NET Framework для SQL Server)

> [!NOTE]
> Параметры подключения для этого поставщика данных одинаковы независимо от того, является ли сервер SQL Server источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

**Источник данных**  
 Введите имя или IP-адрес исходного или конечного сервера либо выберите сервер в раскрывающемся списке.  
 
 Чтобы указать нестандартный TCP-порт, введите запятую после имени или IP-адреса сервера, а затем введите номер порта.
 
 **Исходный каталог**  
 Введите имя исходной или конечной базы данных либо выберите базу данных в раскрывающемся списке.  
  
 **Встроенные функции безопасности**  
 Выберите значение **True**, чтобы использовать встроенную проверку подлинности Windows (рекомендуется), или **False** для подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе **False**необходимо ввести идентификатор пользователя и пароль. Значение по умолчанию равно **False**.  
  
 **Идентификатор пользователя**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите пароль.  

## <a name="connect-to-sql-server-with-the-odbc-driver-for-sql-server"></a>Подключение к SQL Server с помощью драйвера ODBC для SQL Server 
Драйверы ODBC не приводятся в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, сначала выберите **поставщик данных .NET Framework для ODBC** в качестве источника данных. Этот поставщик служит оболочкой для драйвера ODBC.

> [!TIP]
> **Получите последнюю версию драйвера**. Скачайте [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339).

Ниже показан экран, который появляется сразу после выбора поставщика данных .NET Framework для ODBC.

![Подключение к SQL с помощью ODBC ранее](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-sql-server"></a>Указываемые параметры (драйвер ODBC для SQL Server)

> [!NOTE]
> Параметры подключения для этого драйвера ODBC одинаковы независимо от того, является ли сервер SQL Server источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

Чтобы подключиться к SQL Server с помощью последней версии драйвера ODBC, постройте строку подключения, используя указанные ниже параметры и их значения. Полный формат строки подключения приведен после списка параметров.

> [!TIP]
> Вы можете получить помощь в построении строки подключения. Кроме того, вместо указания строки подключения вы можете предоставить существующее имя DSN (имя источника данных) или создать новое. Дополнительные сведения об этих возможностях см. в разделе [Подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC. Для разных версий драйвера имена различаются.

**Server**  
Имя сервера SQL Server.

**База данных**  
Имя базы данных.  

**Trusted_Connection** либо **Uid** и **Pwd**  
Укажите параметр **Trusted_Connection=Yes** для подключения с использованием встроенной проверки подлинности Windows либо укажите **Uid** (идентификатор пользователя) и **Pwd** (пароль) для подключения с использованием проверки подлинности SQL Server.

### <a name="connection-string-format"></a>Формат строки подключения
Ниже приведен формат строки подключения с использованием встроенной проверки подлинности Windows.

    `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;trusted_connection=Yes;`

Ниже приведен формат строки подключения с использованием проверки подлинности SQL Server вместо встроенной проверки подлинности Windows.

     `Driver={ODBC Driver 13 for SQL Server};server=<server>;database=<database>;uid=<user id>;pwd=<password>;`

### <a name="enter-the-connection-string"></a>Ввод строки подключения
Введите строку подключения в поле **ConnectionString** либо введите имя DSN в поле **Dsn** на странице **Выбор источника данных** или **Выбор назначения**. После того как вы введете строку подключения, мастер проанализирует ее и отобразит отдельные свойства и их значения в списке.

В приведенном ниже примере используется следующая строка подключения:

    `Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;`

Ниже показан экран, который появляется после ввода строки подключения.

![Подключение к SQL с помощью ODBC позднее](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="connect-to-sql-server-with-the-microsoft-ole-db-provider-for-sql-server-or-sql-server-native-client"></a>Подключение к SQL Server с помощью поставщика OLE DB для SQL Server (Майкрософт) или SQL Server Native Client

> [!IMPORTANT]
> Поставщик OLE DB для SQL Server (Майкрософт) и клиент SQL Server Native Client не поддерживаются в версиях SQL Server после SQL Server 2012. Используйте вместо этого драйвер ODBC. Дополнительные сведения о переходе на драйвер ODBC см. в следующих записях блога:
>   -   [Майкрософт переводит ODBC на собственный доступ к реляционным данным](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/)
>   -   [Общие сведения о драйверах Microsoft ODBC Driver for SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/)

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и дополнительные сведения
Сведения о подключении к SQL Server с помощью поставщика данных, который не указан в этой статье, см. на странице [Строки подключения к SQL Server](https://www.connectionstrings.com/sql-server/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметрах подключения, описанных на этой странице.

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

