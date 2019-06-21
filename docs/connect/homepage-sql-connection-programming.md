---
title: Домашняя страница для программирования клиента SQL | Документация Майкрософт
description: Страница концентратора с заметками ссылки на файлы для загрузки и документации для различных комбинаций языков и операционных систем, для подключения к SQL Server или базу данных SQL Azure.
author: MightyPen
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: genemi
ms.openlocfilehash: d773e05a3ed953e5210c0ade3226b4a32e82aeab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63182174"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Главная страница для программирования клиента Microsoft SQL Server


Добро пожаловать в нашей веб-странице о клиенте, программирование для взаимодействия с Microsoft SQL Server и базы данных SQL Azure в облаке. Эта статья содержит следующие сведения:

- Перечисляются и описываются все возможные комбинации языка и драйвера.
    - Информация предоставляется для операционных систем Windows, MacOS и Linux (Ubuntu и др.).
- Ссылки на подробную документацию для каждого сочетания.
- Отображает области и дочерние области иерархических документации для некоторых языков, где это необходимо.


#### <a name="azure-sql-database"></a>База данных SQL Azure

На любом данном языке код, который подключается к SQL Server почти такой же код для подключения к базе данных SQL Azure.

Дополнительные сведения о строках подключения для подключения к базе данных SQL Azure см. в разделе:

- [Использование .NET Core (C#) для создания запросов к базе данных Azure SQL](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Другие базы данных SQL Azure, которые ближайших точек в предыдущей статье в таблице содержимого, относительно других языков. Например, см. в разделе [запросов к базе данных Azure SQL с помощью PHP](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Сборки в приложение веб-страниц

Наши *-an app* веб-страницах представлены примеры кода, вместе с информацией о конфигурации, в альтернативный формат. Дополнительные сведения см. Далее в этой статье [раздел под названием *веб-сайт сборки приложения*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Языки и драйверы для клиентских программ


В следующей таблице каждый образ язык представляет собой ссылку сведений об использовании языка с SQL Server. Каждая связь перейдет к следующем разделе этой статьи.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![Логотип C#][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM Entity Framework, платформы .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Логотип Java][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Логотип node.js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![Логотип PHP][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Логотип Python][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Логотип Ruby][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Загрузка и установка

В следующей статье, предназначенного для загрузки и установки различных драйверов подключения SQL, для использования с языками программирования:

- [Драйверы SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![Логотип C#][image-ref-320-csharp] C# с помощью ADO.NET

Наиболее распространенные пользователями ADO.NET являются управляемого .NET языков, например C# и Visual Basic. *ADO.NET* представляет собой обычное подмножество классов .NET Framework.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью ADO.NET](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | Пример небольшого кода уделено подключение и запросы к SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью ADO.NET](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | Логика повторных попыток в пример кода, так как подключения иногда может происходить секунд потери подключения.<br /><br />Логика повторных попыток применяется также для соединения, поддерживаемые через Интернет в любой облачной базы данных, например к базе данных SQL Azure. |
| [База данных SQL Azure: Демонстрация того, как использовать .NET Core в Windows, Linux и Mac OS для создания программы C#, подключение и запрос](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Пример базы данных SQL Azure. |
| [Сборки в приложение: C#, ADO.NET, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

|||
| :-- | :-- |
| [C# с помощью ADO.NET](./ado-net/index.md)| Корень нашей документации. |
| [Пространство имен: System.Data](https://docs.microsoft.com/dotnet/api/system.data) | Набор классов, используемых для ADO.NET. |
| [Пространство имен: System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Набор классов, которые являются наиболее полно center ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Логотип Entity Framework][image-ref-333-ef] Платформа Entity Framework (EF) с помощью c#&#x23;

Entity Framework (EF) предоставляет объектно-реляционного сопоставления (ORM). ORM упрощает для объектно-ориентированное программирование (ООП) исходного кода для работы с данными, который был извлечен из реляционной базы данных SQL.

EF имеет прямых или косвенных связей со следующими технологиями:

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/), или [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Усовершенствования синтаксис языка, такие как **=>** оператор в C#.
- Удобных программ, которые создают исходный код для классов, которые сопоставляются с таблицами в базе данных SQL. Например [EdmGen.exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>Исходный EF и новый EF

[Начальной страницы для платформы Entity Framework](https://docs.microsoft.com/ef/) вводит EF с описанием, аналогичную следующей:

- Entity Framework является объектно реляционного сопоставления (O/RM), которая позволяет разработчикам .NET работать с базой данных, используя объекты .NET. Это устраняет необходимость в большей исходного кода доступа к данным, который разработчикам обычно приходится писать.

*Платформа Entity Framework* — это имя, совместно используется два отдельных исходного кода. Старше одной ветви работы с EF и ее исходный код теперь можно поддерживать открытым. Другие EF является новым. Далее описаны два файловая система EFs:

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Во-первых, корпорация Майкрософт выпустила EF в августе 2008 г. В марте 2015 года корпорация Майкрософт объявила о, EF 6.x была окончательной версии, как разрабатывать Microsoft. Корпорация Microsoft выпустила исходный код в общедоступном домене.<br /><br />Изначально EF входил в состав .NET Framework. Но EF 6.x был удален из .NET Framework.<br /><br />[EF 6.x исходный код на Github в репозитории *aspnet/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | В июне 2016 г. Корпорация Майкрософт выпустила недавно разработанную EF Core. EF Core предназначена для более высокую гибкость и переносимость. EF Core можно запустить в операционных системах, помимо просто Microsoft Windows. И EF Core может взаимодействовать с базами данных за пределы просто Microsoft SQL Server и других реляционных баз данных.<br /><br />**C&#x23; примеры кода:**<br />[Начало работы с Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Начало работы с EF Core в .NET Framework с существующей базы данных](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF и связанных технологий являются мощными и многие дополнительные сведения для разработчика, желающего освоить, всю область.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Логотип Java][image-ref-330-java] Java и JDBC

Корпорация Майкрософт предоставляет драйвер Java Database Connectivity (JDBC) для использования с SQL Server (или с базой данных SQL Azure, конечно). Это драйвер JDBC типа 4, который обеспечивает обмен данными с базами данных через стандартные интерфейсы API JDBC.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Примеры кода](./jdbc/code-samples/index.md) | Примеры кода, в которых о типах данных, результирующие наборы и большого объема данных. |
| [Пример URL-адреса подключения](./jdbc/connection-url-sample.md) | В этой статье описывается использование URL-адрес подключения для подключения к SQL Server. Затем используйте его для использования инструкции SQL для извлечения данных. |
| [Пример источника данных](./jdbc/data-source-sample.md) | В этой статье описывается использование источника данных для подключения к SQL Server. Затем можно используйте хранимую процедуру для извлечения данных. |
| [Использование Java для создания запросов к базе данных Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Пример базы данных SQL Azure. |
| [Создание приложений Java с помощью SQL Server в Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

В документации по JDBC включает следующие основные области:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Корень документации по JDBC. |
| [Справочник](./jdbc/reference/index.md) | Интерфейсы, классы и члены. |
| [Руководство по программированию для драйвера JDBC для SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Логотип node.js][image-ref-340-node] Node.js

С помощью Node.js можно подключиться к SQL Server из Windows, Linux или Mac. Корень нашей документации Node.js — [здесь](./node-js/index.md).

Драйвер подключений Node.js для SQL Server реализованы в JavaScript. Драйвер использует протокол потока табличных данных, который поддерживается все современные версии SQL Server. Драйвер — это проект с открытым исходным кодом, [на сайте Github](https://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Пустой исходный код для подключения к SQL Server и выполнения запроса. |
| [База данных SQL Azure: запрос с помощью Node.js](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Пример базы данных SQL Azure в облаке. |
| [Создание приложений Node.js, чтобы использовать SQL Server в Mac OS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC для C++ 

![Логотип ODBC][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

Open database connectivity (ODBC) был разработан в 90-х, и эта реализация предшествовала .NET Framework. ODBC должен быть независимым от любой конкретной базы данных системы и зависит от операционной системы.

С годами созданных многочисленные драйверы ODBC и выпущен по группам в пределах и за пределами Microsoft. Диапазон драйверов включают в себя несколько языков программирования клиента. Список целевых объектов данных выходит далеко за пределы SQL Server.

Некоторые драйверы внутренним образом используют ODBC.

#### <a name="code-example"></a>Пример кода

- [Пример кода C++ с использованием ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Структура документации

ODBC содержимое этого раздела посвящена доступ к SQL Server или базы данных SQL Azure, из C++. В следующей таблице перечислены приблизительное контур в основной документации по ODBC.


| Область | Дочерних областей | Описание |
| :--- | :------ | :---------- |
| [ODBC для C++](./odbc/index.md) | Корень нашей документации. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Сведения об использовании ODBC в операционных системах Linux или MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Сведения об использовании ODBC в операционной системе Windows. |
| [Администрирование](../odbc/admin/index.md) | &nbsp; | Средство администрирования для управления источников данных ODBC. |
| [Майкрософт](../odbc/microsoft/index.md)  | &nbsp; | Различные драйверы ODBC, которые создаются и предоставляемые корпорацией Майкрософт. |
| [Концептуальная и справочная](../odbc/reference/index.md) | &nbsp; | Общие сведения об интерфейсе ODBC, кроме традиционных ссылки. |
| &nbsp; " | [Приложения](../odbc/reference/appendixes/index.md)    | Таблицы перехода состояния, библиотека курсоров ODBC и многое другое. |
| &nbsp; " | [Разработка приложения](../odbc/reference/develop-app/index.md)  | Функции, дескрипторы и многое другое. |
| &nbsp; " | [Разработка драйверов](../odbc/reference/develop-driver/index.md) | Как разрабатывать собственные драйвер ODBC при наличии специализированный источник данных. |
| &nbsp; " | [Установка](../odbc/reference/install/index.md) | Установка ODBC, подразделы и многое другое. |
| &nbsp; " | [Синтаксис](../odbc/reference/syntax/index.md)   | API-интерфейсы для установки, установщик, перевод и доступ к данным. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Логотип PHP][image-ref-360-php] PHP

PHP можно использовать для взаимодействия с SQL Server. Корень нашей документации по PHP — [здесь](./php/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Пример небольшого кода уделено подключение и запросы к SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | Логика повторных попыток в пример кода, так как подключения через Интернет и облако иногда может происходить секунд потери подключения. |
| [База данных SQL Azure: с помощью PHP запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Пример базы данных SQL Azure. |
| [Создание приложения PHP для использования SQL Server на RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Логотип Python][image-ref-370-python] Python


Python можно использовать для взаимодействия с SQL Server.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции путем подключения к SQL с помощью Python с использованием pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Пример небольшого кода уделено подключение и запросы к SQL Server. |
| [База данных SQL Azure: запрос с помощью Python](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Пример базы данных SQL Azure. |
| [Создание приложения PHP для использования SQL Server на SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

| Область | Описание |
| :--- | :---------- |
| [Python для SQL Server](./python/index.md) | Корень нашей документации. |
| [драйвер pymssql](./python/pymssql/index.md) | Майкрософт не поддерживают или протестируйте драйвер pymssql.<br /><br />Драйвер pymssql подключения — это простой интерфейс к базам данных SQL, для использования в программах Python. Pymssql подключает FreeTDS для обеспечения интерфейса API Python для DB-(PEP 249) для Microsoft SQL Server. |
| [Драйвер pyodbc](./python/pyodbc/index.md)   | Драйвер pyodbc для подключения — это модуль Python открытым исходным кодом, который упрощает доступ к базам данных ODBC. Он реализует спецификацию API DB 2.0, но содержит более привычные для Python удобства. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Логотип Ruby][image-ref-380-ruby] Ruby

Ruby можно использовать для взаимодействия с SQL Server. Корень документации Ruby — [здесь](./ruby/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Эксперимент, подразумевающий подключение к SQL с помощью Ruby](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Пример небольшого кода уделено подключение и запросы к SQL Server. |
| [База данных SQL Azure: запрос с помощью Ruby](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Пример базы данных SQL Azure. |
| [Создание приложения Ruby использовать SQL Server в Mac OS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpswwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Веб-сайта — это приложение, для разработки клиентских SQL](https://www.microsoft.com/sql-server/developer-get-started/)


На нашем [ *-an app* ](https://www.microsoft.com/sql-server/developer-get-started/) веб-страниц, можно выбрать длинный список языков для подключения к SQL Server. Клиентская программа может запустить широкий набор операционных систем.

*Сборки приложение* особое внимание уделяется простоты и «полнота» для разработчиков, которым просто Приступая к работе. В шагах объясняется следующие задачи:

1. Установка Microsoft SQL Server
2. Как скачать и установить средства и драйверы.
3. Как внести все необходимые конфигурации, в зависимости от выбранной операционной системе.
4. Способы компиляции указанного исходного кода.
5. Сведения о выполнении программы.

Далее приведены несколько контуров приблизительное подробностей, обеспечиваемый веб-сайта.

#### <a name="java-on-ubuntu"></a>Java в Ubuntu:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1.2 Установка Java
    - Шаг 1.3 Установка Java Development Kit (JDK)
    - Шаг 1.4 установки Maven
2. Создание приложения Java с помощью SQL Server
    - Шаг 2.1. Создание приложения Java, которое подключается к SQL Server и выполняет запросы
    - Шаг 2.2. Создание приложения Java, которое подключается к SQL Server с помощью популярная платформа спящий режим
3. Сделать ваше приложение Java до 100 раз быстрее
    - Шаг 3.1. Создание приложения Java для демонстрации индексов Columnstore

#### <a name="python-on-windows"></a>Python в Windows:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1.2 установите Python
    - Шаг 1.3 Установка драйвера ODBC и программа командной строки SQL для SQL Server
2. Создание приложения Python с помощью SQL Server
    - Шаг 2.1 установите драйвер Python для SQL Server
    - Шаг 2.2. Создание базы данных для приложения
    - Шаг 2.3. Создание приложения Python, который подключается к SQL Server и выполняет запросы
3. Сделайте приложение Python до 100 раз быстрее
    - Шаг 3.1. Создание новой таблицы с 5 миллионов использование программы sqlcmd
    - Шаг 3.2. Создание приложения Python, которое запрашивает этой таблицы и измеряет время, затраченное
    - Шаг 3.3 измерить время, необходимое для выполнения запроса
    - Шаг 3.4 добавить индекс columnstore в таблицу
    - Шаг 3.5 измерить время, необходимое для выполнения запроса с индексом columnstore

Далее на снимках экрана дают представление о том, как выглядит наш веб-сайт документации по разработке для SQL.

#### <a name="choose-a-language"></a>Выбор языка:

![Веб-сайт разработки SQL, приступить к работе][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Выберите операционную систему:

![Веб-сайт разработки SQL, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Другие разработки


Этот раздел содержит ссылки на информацию о других возможностях разработки приложений. К ним относятся, в целом с помощью этих же языков для разработки в Azure. Данные не только базы данных SQL Azure и Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Центр разработчиков для Azure

- [Центр разработчиков для Azure](https://docs.microsoft.com/azure/)
- [Azure для разработчиков .NET](https://docs.microsoft.com/dotnet/azure/)
- [Azure для разработчиков Java](https://docs.microsoft.com/java/azure/)
- [Azure для разработчиков Node.js](https://docs.microsoft.com/nodejs/azure/)
- [Azure для разработчиков Python](https://docs.microsoft.com/python/azure/)
- [Создание веб-приложения PHP в Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Другие языки

- [Создание приложения Go, используя SQL Server на Windows](https://www.microsoft.com/sql-server/developer-get-started/go/windows/)



<!-- Image references. -->

[image-ref-322-cpp]: ./media/homepage-sql-connection-drivers/gm-cpp-4point-p61f.png
[image-ref-320-csharp]: ./media/homepage-sql-connection-drivers/gm-csharp-c10c.png
[image-ref-333-ef]: ./media/homepage-sql-connection-drivers/gm-entity-framework-ef20d.png
[image-ref-330-java]: ./media/homepage-sql-connection-drivers/gm-java-j18c.png
[image-ref-340-node]: ./media/homepage-sql-connection-drivers/gm-node-n30.png
[image-ref-350-odbc]: ./media/homepage-sql-connection-drivers/gm-odbc-ic55826-o35.png
[image-ref-360-php]: ./media/homepage-sql-connection-drivers/gm-php-php60.png
[image-ref-370-python]: ./media/homepage-sql-connection-drivers/gm-python-py72.png
[image-ref-380-ruby]: ./media/homepage-sql-connection-drivers/gm-ruby-un-r82.png
[image-ref-390-aka-ms-sqldev-choose-language]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-400-aka-ms-sqldev-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png

