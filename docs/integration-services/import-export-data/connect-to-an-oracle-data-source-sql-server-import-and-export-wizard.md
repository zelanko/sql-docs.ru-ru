---
title: "Подключения к источнику данных Oracle (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0bd1f5a-34dd-4be3-9ac8-f9f87727781b
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e589e7f7a0262d258342bf887ec84c57d57dc978
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-oracle-data-source-sql-server-import-and-export-wizard"></a>Подключения к источнику данных Oracle (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **Oracle** из источника данных **выберите источник данных** или **Выбор назначения** страницы мастера экспорта и импорта SQL Server. Существует несколько поставщиков данных, которые можно использовать для подключения к базе данных Oracle.

> [!IMPORTANT]
> Подробные требования и необходимые условия для подключения к базе данных Oracle выходят за рамки данной статьи Microsoft. Предполагается наличие установленного клиентского программного обеспечения Oracle и что вы могут уже подключиться к целевой базе данных Oracle. Дополнительные сведения обратитесь к администратору базы данных Oracle или в документации Oracle.

## <a name="connect-to-oracle-with-the-net-framework-data-provider-for-oracle"></a>Подключиться к базе данных Oracle с .net Framework поставщик данных для Oracle
После выбора **поставщик данных .NET Framework для Oracle** на **выберите источник данных** или **Выбор назначения** странице мастера, на странице представлен Сгруппированный список параметров для поставщика. Многие из них являются чужим имена и неизвестные параметры. К счастью достаточно предоставляют два или три блока данных. Можно игнорировать значения по умолчанию для других параметров.

> [!NOTE]
> Параметры соединения для поставщика данных являются одинаковыми как для Oracle — источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

|Необходимые сведения|.NET framework поставщик данных для Oracle-свойство|
|---|---|
|Имя сервера|**Источник данных**|
|Сведения о проверке подлинности (имя входа)|**Идентификатор пользователя** и **пароль**; или, **встроенной безопасности**|

Не нужно ввести строку подключения в **ConnectionString** поле списка. После ввода имени сервера Oracle отдельных значений (**источника данных**) и информации о имени входа, мастер собирает строку подключения из отдельных свойств и их значения. 

![Подключение к базе данных Oracle с помощью поставщика .NET](../../integration-services/import-export-data/media/connect-to-oracle-with-net-provider.jpg)

## <a name="connect-to-oracle-with-the-microsoft-odbc-driver-for-oracle"></a>Подключиться к базе данных Oracle с помощью драйвера Microsoft ODBC для Oracle
Драйверы ODBC не перечислены в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, начинают с выбора **поставщик данных .NET Framework для ODBC** как источник данных на **выберите источник данных** или **Выбор назначения** страницы. Этот поставщик действует как оболочка для драйвера ODBC.

Вот универсального экран, появляется сразу после выбора поставщик данных .NET Framework для ODBC.

![Подключение к базе данных Oracle в ODBC до](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-odbc-driver-for-oracle"></a>Параметры, задающие (драйвер ODBC для Oracle)

> [!NOTE]
> Параметры соединения для этого поставщика данных и драйвера ODBC одинаковы ли Oracle источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

Чтобы подключиться к базе данных Oracle с помощью драйвера ODBC для Oracle, сформируйте строку подключения, которая включает следующие параметры и их значения. Формат полной строки соединения непосредственно после списка параметров.

> [!TIP]
> Получите справку по сборке выбрана правильная строка подключения. А не строку подключения, укажите существующего источника данных (имя источника данных) или создайте новую. Дополнительные сведения об этих параметрах см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC, **Microsoft ODBC для Oracle**.

**Server**  
Имя сервера Oracle. 

**UID** и **Pwd**   
Идентификатор пользователя и пароль для подключения.

### <a name="connection-string-format"></a>Формат строки соединения
Ниже приведен формат строки соединения.

    Driver={Microsoft ODBC for Oracle};Server=myServerAddress;Uid=myUsername;Pwd=myPassword;

### <a name="enter-the-connection-string"></a>Введите строку подключения
Введите строку подключения в **ConnectionString** , либо ввести имя DSN в **Dsn** в **выберите источник данных** или **Выбор назначения** страницы. Введите строку подключения, мастер анализирует строку и отображает отдельные свойства и их значения в списке.

Вот экрана, которое будет отображаться после ввода строки подключения.

![Подключение к базе данных Oracle с ODBC](../../integration-services/import-export-data/media/connect-to-oracle-with-odbc.jpg)

## <a name="whats-my-oracle-server-name"></a>Что такое имя сервера Oracle
Выполните одну из следующих запросов для получения имени сервера Oracle.

`SELECT host_name FROM v$instance`

либо

`SELECT sys_context('USERENV','SERVER_HOST') FROM dual`

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и Дополнительные сведения
Сведения о подключении к базе данных Oracle с помощью поставщика данных, не перечисленных здесь см. в разделе [строки подключения Oracle](https://www.connectionstrings.com/oracle/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметры подключения, описанных на этой странице.

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


