---
title: "Подключения к источнику данных MySQL (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d7c5a38-18d3-4cc9-a241-04422cb250d3
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3df56fcda5b39c2895de83feac4f302686b1adf3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-a-mysql-data-source-sql-server-import-and-export-wizard"></a>Подключения к источнику данных MySQL (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **MySQL** из источника данных **выберите источник данных** или **Выбор назначения** страницы мастера экспорта и импорта SQL Server. Существует несколько поставщиков данных, которые можно использовать для подключения к MySQL.

> [!IMPORTANT]
> Подробные требования и необходимые условия для подключения к базе данных MySQL выходят за рамки данной статьи Microsoft. В этой статье предполагается уже установлено клиентское программное обеспечение MySQL и что вы могут уже подключиться к целевой базе данных MySQL. Дополнительные сведения обратитесь к администратору базы данных MySQL или документация по MySQL.

## <a name="get-the-mysql-connectors"></a>Получение соединителей MySQL
Загрузить поставщики и драйверы, описанные в этом разделе из [соединители MySQL](https://dev.mysql.com/downloads/connector/) страницы.

## <a name="connect-to-mysql-with-the-net-framework-data-provider-for-mysql"></a>Подключение к MySQL с .net Framework поставщик данных для MySQL
После выбора **поставщик данных .NET Framework для MySQL** на **выберите источник данных** или **Выбор назначения** странице мастера, на странице представлен Сгруппированный список параметров для поставщика. Многие из них являются чужим имена и неизвестные параметры. К счастью имеется только для предоставления несколько фрагментов данных. Можно игнорировать значения по умолчанию для других параметров.

> [!NOTE]
> Параметры соединения для поставщика данных одинаковы ли MySQL источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

|Необходимые сведения|.NET framework поставщика данных для свойства MySQL|
|---|---|
|Имя сервера|**Server**|
|Имя базы данных|**База данных**|
|Сведения о проверке подлинности (имя входа)|**Идентификатор пользователя** и **пароль**|

Не нужно ввести строку подключения в **ConnectionString** поле списка. После ввода имени сервера MySQL отдельных значений (**сервера**) и информации о имени входа, мастер собирает строку подключения из отдельных свойств и их значения. 

![Подключение к MySQL с помощью поставщика .NET, 1 из 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-1-of-2.png)

![Подключение к MySQL с помощью поставщика .NET, часть 2 из 2](../../integration-services/import-export-data/media/connect-to-mysql-with-the-net-provider-2-of-2.png)

## <a name="connect-to-mysql-with-the-mysql-odbc-driver"></a>Подключение к MySQL с помощью драйвера MySQL ODBC
Драйверы ODBC не перечислены в раскрывающемся списке источников данных. Чтобы подключиться с помощью драйвера ODBC, начинают с выбора **поставщик данных .NET Framework для ODBC** как источник данных на **выберите источник данных** или **Выбор назначения** страницы. Этот поставщик действует как оболочка для драйвера ODBC.

Вот универсального экран, появляется сразу после выбора поставщик данных .NET Framework для ODBC.

![Подключение к SQL с ODBC до](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

### <a name="options-to-specify-mysql-odbc-driver"></a>Параметры, задающие (драйвер ODBC MySQL)

> [!NOTE]
> Параметры соединения для этого поставщика данных и драйвера ODBC одинаковы ли MySQL источнике или месте назначения. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

Подключение к MySQL с помощью драйвера MySQL ODBC, сформируйте строку подключения, которая включает следующие параметры и их значения. Формат полной строки соединения непосредственно после списка параметров.

> [!TIP]
> Получите справку по сборке выбрана правильная строка подключения. А не строку подключения, укажите существующего источника данных (имя источника данных) или создайте новую. Дополнительные сведения об этих параметрах см. в разделе [подключение к источнику данных ODBC](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md).

**Драйвер**  
Имя драйвера ODBC.

**Server**  
Имя сервера MySQL. 

**База данных**  
Имя базы данных MySQL.

**UID** и **PWD**   
Идентификатор пользователя и пароль для подключения.

### <a name="connection-string-format"></a>Формат строки соединения
Ниже приведен формат строки соединения.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=<server>;Database=<database>;UID=<user id>;PWD=<password>
    ```

### <a name="enter-the-connection-string"></a>Введите строку подключения
Введите строку подключения в **ConnectionString** , либо ввести имя DSN в **Dsn** в **выберите источник данных** или **Выбор назначения** страницы. Введите строку подключения, мастер анализирует строку и отображает отдельные свойства и их значения в списке.

В следующем примере эта строка подключения.

    ```
    Driver={MySQL ODBC 5.3 Unicode Driver};Server=127.0.0.1;Database=world;UID=root;PWD=********
    ```

Вот экрана, которое будет отображаться после ввода строки подключения.

![Подключение к MySQL с ODBC](../../integration-services/import-export-data/media/connect-to-mysql-with-odbc.png)

## <a name="other-data-providers-and-more-info"></a>Другие поставщики данных и Дополнительные сведения
Сведения о том, как подключиться к MySQL с помощью поставщика данных, нет в списке в разделе [строки подключения MySQL](https://www.connectionstrings.com/mysql/). Этот сторонний сайт также содержит дополнительные сведения о поставщиках данных и параметры подключения, описанных на этой странице.

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


