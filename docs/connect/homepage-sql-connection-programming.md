---
title: Домашняя страница для программирования клиента SQL | Документы Microsoft
description: Страница концентратора с заметками ссылки на файлы для загрузки и документации для различных сочетаний языков и операционных систем, для подключения к SQL Server, или к базе данных SQL Azure.
author: MightyPen
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: meetb
ms.author: genemi
ms.openlocfilehash: cfb1ac82894ef8fed001077d54665c9f89239787
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306223"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Домашняя страница для программирования для Microsoft SQL Server клиента


Добро пожаловать в нашей веб-странице о клиенте программирования для взаимодействия с Microsoft SQL Server и базы данных SQL Azure в облаке. Эта статья содержит следующие сведения:

- Перечислены и описаны все возможные комбинации языка и драйвера.
    - Информация предоставляется для операционных систем Linux (Ubuntu и др.), MacOS и Windows.
- Ссылки на подробную документацию для каждого сочетания.
- Отображает области и дочерние области иерархических документации для определенных языков уместно.


#### <a name="azure-sql-database"></a>База данных SQL Azure

На любом данном языке код, который подключается к SQL Server почти такой же код для подключения к базе данных SQL Azure.

Дополнительные сведения о строках подключения для подключения к базе данных SQL Azure см. в разделе:

- [Использовать .NET Core (C#) для запроса к базе данных Azure SQL](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core).
- Другие базы данных SQL Azure, которые ближайших предыдущей статьи в таблице содержимого с другими языками. Например, в разделе [использование PHP для запроса к базе данных Azure SQL](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Сборки в приложение веб-страниц

Наш *сборки в приложении* веб-страницах представлены примеры кода, вместе с информацией о конфигурации в альтернативный формат. Дополнительные сведения см. Далее в этой статье [раздел под названием *сборки в приложение веб-сайт*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Языки и драйверы для клиентских программ


В следующей таблице существует языка ссылку на подробные сведения о языке с SQL Server. Каждый канал перейдет в одном из следующих разделов этой статьи.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![Эмблема C#][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![Entity Framework ORM платформы .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Эмблема Java][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Эмблема node.js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [**`ODBC for C++`**](#an-160-odbc-cpp-docu)<br/>[![CPP big плюс][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![Эмблема PHP][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Эмблема Python][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Произносится эмблемы][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Загрузка и установка

Следующую статью предназначенного для загрузки и установки различных драйверов подключения SQL для использования в языках программирования:

- [Драйверы SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![Эмблема C#][image-ref-320-csharp] C# с помощью ADO.NET

В языках .NET управляемых, таких как C# и Visual Basic, будут ли наиболее распространенные пользователями ADO.NET. *ADO.NET* является именем случайного подмножества классов .NET Framework.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Пробная версия, подключение к SQL с помощью ADO.NET](./ado-net/step-3-proof-of-concept-connecting-to-sql-using-ado-net.md) | Пример, в небольших основное внимание уделено подключения и запросы к SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью ADO.NET](./ado-net/step-4-connect-resiliently-to-sql-with-ado-net.md) | Повторите логику в примере кода, поскольку подключений иногда могут возникать моменты потери подключения.<br /><br />Логика повторных попыток применяется также для соединения, поддерживаемые через Интернет в любой базе данных облака, такие как базы данных SQL Azure. |
| [База данных SQL Azure: Демонстрация использования .NET Core в Windows, Linux и macOS создание программы на C# для подключения и запроса](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Azure примера базы данных SQL. |
| [Сборки в приложении: C#, ADO.NET, Windows](http://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

|||
| :-- | :-- |
| [C# с помощью ADO.NET](./ado-net/index.md)| Корень нашей документации. |
| [Пространство имен: System.Data](http://docs.microsoft.com/dotnet/api/system.data) | Набор классов, используемых для ADO.NET. |
| [Пространство имен: System.Data.SqlClient](http://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Набор классов, которые являются наиболее полно center ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Эмблема Entity Framework][image-ref-333-ef] Entity Framework (EF) П &#x23;

Entity Framework (EF) предоставляет объектно-реляционного сопоставления (ORM). Объектно-реляционные Преобразователи упрощает об объектно-ориентированном программировании (OOP) исходного кода для работы с данными, которые были получены из реляционной базы данных SQL.

EF имеет прямой или косвенной связи со следующими технологиями:

- .NET Framework
- [LINQ to SQL](http://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/), или [LINQ to Entities](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Усовершенствования языка синтаксиса, такие как **=>** оператором в C#.
- Удобных программ, создающих исходный код для классов, которые сопоставляются с таблицами в базе данных SQL. Например [EdmGen.exe](http://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>EF исходные и новые EF

[Начальной страницы для Entity Framework](http://docs.microsoft.com/ef/) вводит EF с описанием примерно следующего содержания:

- Entity Framework является объектно реляционного сопоставления (O/надежный обмен Сообщениями), которая позволяет разработчикам .NET для работы с базой данных с помощью объектов .NET. Отпадает необходимость для большинства исходного кода доступа к данным, который разработчики обычно требуется записать.

*Платформа Entity Framework* является именем совместно используется два отдельных исходного кода. Одна ветвь EF старее, и его исходный код теперь может осуществляться из Интернета. Другие EF не использовался. Далее описаны два EFs:

|     |     |
| :-- | :-- |
| [EF 6.x](http://docs.microsoft.com/ef/ef6/) | Сначала Корпорация Майкрософт выпустила EF в август 2008 г. В март 2015 г. Корпорация Майкрософт объявила о, EF 6.x была окончательной версии, разрабатывать корпорации Майкрософт. Корпорация Майкрософт выпустила исходный код в общий домен.<br /><br />Изначально EF входил в состав .NET Framework. Но EF 6.x был удален из .NET Framework.<br /><br />[EF 6.x исходный код на Github в репозиторий *aspnet/EntityFramework6*](http://github.com/aspnet/EntityFramework6) |
| [EF Core](http://docs.microsoft.com/ef/core/) | Корпорация Майкрософт выпустила ядро недавно разработанную EF в июня 2016 г. EF Core разработана для большую гибкость и переносимость. EF Core можно запускать в операционных системах вне просто Microsoft Windows. И EF Core могут работать с базами данных, помимо только Microsoft SQL Server и другие реляционные базы данных.<br /><br />**П &#x23; Примеры кода.**<br />[Приступая к работе с Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Приступая к работе с EF Core в .NET Framework с существующей базы данных](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF и связанных технологиях мощных и много сведения для разработчика, который хочет главный всю область.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Эмблема Java][image-ref-330-java] Java и JDBC

Корпорация Майкрософт предоставляет драйвер Java Database Connectivity (JDBC) для использования с SQL Server (или с базой данных SQL Azure, разумеется,). Это драйвер JDBC типа 4, а также подключение к базе данных через стандартные интерфейсы JDBC (API).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Примеры кода](./jdbc/code-samples/index.md) | Примеры кода, в которых о типах данных, результирующие наборы и больших объемов данных. |
| [Пример URL-адреса подключения](./jdbc/connection-url-sample.md) | Описывает, как использовать URL-адрес подключения для подключения к SQL Server. Используйте его для использования инструкции SQL для получения данных. |
| [Пример источника данных](./jdbc/data-source-sample.md) | Описывает, как использовать источник данных для подключения к SQL Server. Затем можно используйте хранимую процедуру для извлечения данных. |
| [Используйте Java для запроса к базе данных Azure SQL](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Azure примера базы данных SQL. |
| [Создание приложений Java, с помощью SQL Server на Ubuntu](http://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

JDBC Документация включает следующие основные области:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Корень нашей документации JDBC. |
| [Справочник](./jdbc/reference/index.md) | Интерфейсы, классы и члены. |
| [Руководство по программированию для драйвера JDBC для SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Эмблема node.js][image-ref-340-node] Node.js

Node.js можно подключаться к серверу SQL Server с Windows, Linux или Mac. Корень нашей документации Node.js — [здесь](./node-js/index.md).

Драйвер Node.js соединения для SQL Server реализована в JavaScript. Драйвер использует протокол потока табличных данных, которую поддерживают все современные версии SQL Server. Драйвер является проекта с открытым кодом [на сайте Github](http://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Пробная версия, подключение к SQL с помощью Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Пустой исходный код для подключения к SQL Server и выполнения запроса. |
| [База данных SQL Azure: использование Node.js для запроса](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Пример базы данных SQL Azure в облаке. |
| [Для создания приложений Node.js для использования SQL Server на macOS](http://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC для C++ 

![Эмблема ODBC][image-ref-350-odbc] ![CPP big плюс][image-ref-322-cpp]

Интерфейс ODBC (ODBC) был разработан в 90-х, и эта реализация предшествовала .NET Framework. ODBC должен быть независимым от любой системе конкретной базы данных и зависит от операционной системы.

С годами многочисленные драйверы ODBC были созданы и выпускаемых группы внутри и вне корпорации Майкрософт. Диапазон драйверов включают в себя несколько языков программирования клиента. Список целевых объектов данных становится намного больше, чем SQL Server.

Некоторые другие драйверы соединения для внутреннего использования ODBC.

#### <a name="code-example"></a>Пример кода

- [Пример кода C++, с использованием ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Структура документации

ODBC содержимое этого раздела посвящена доступ к SQL Server или база данных SQL Azure из C++. В следующей таблице перечислены приблизительный контур в основной документации по ODBC.


| Область | Дочерних областей | Описание |
| :--- | :------ | :---------- |
| [ODBC для C++](./odbc/index.md) | Корень нашей документации. |
| [Linux Mac](./odbc/linux-mac/index.md) | &nbsp; | Сведения об использовании ODBC в операционных системах Linux и MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Сведения об использовании ODBC в операционной системе Windows. |
| [Администрирование](../odbc/admin/index.md) | &nbsp; | Средство администрирования для управления источников данных ODBC. |
| [Корпорация Майкрософт](../odbc/microsoft/index.md)  | &nbsp; | Различные драйверы ODBC, созданные и предоставляемые корпорацией Майкрософт. |
| [Концептуальная и справочная](../odbc/reference/index.md) | &nbsp; | Общие сведения об интерфейсе ODBC Помимо традиционных ссылки. |
| &nbsp; " | [Приложений](../odbc/reference/appendixes/index.md)    | Смена состояния таблиц, библиотека курсоров ODBC и многое другое. |
| &nbsp; " | [Разработка приложения](../odbc/reference/develop-app/index.md)  | Функции, дескрипторы и многое другое. |
| &nbsp; " | [Разработка драйвера](../odbc/reference/develop-driver/index.md) | Как для разработки собственного драйвера ODBC, если у вас есть специализированный источник данных. |
| &nbsp; " | [Установка](../odbc/reference/install/index.md) | Установка ODBC, подразделы и многое другое. |
| &nbsp; " | [Синтаксис](../odbc/reference/syntax/index.md)   | API-интерфейсы для программы установки, установщик, преобразования и доступ к данным. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Эмблема PHP][image-ref-360-php] PHP

PHP можно использовать для взаимодействия с SQL Server. Корень нашей документации Node.js — [здесь](./php/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Пробная версия, подключение к SQL с помощью PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Пример, в небольших основное внимание уделено подключения и запросы к SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | Повторите логику в примере кода, так как подключения через Интернет и облаком иногда могут возникать моменты потери подключения. |
| [База данных SQL Azure: использование PHP для запроса](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Azure примера базы данных SQL. |
| [Для создания приложений PHP для использования SQL Server на RHEL](http://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Эмблема Python][image-ref-370-python] Python


Python можно использовать для взаимодействия с SQL Server.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Пробная версия, подключение к SQL с помощью pyodbc Python](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Пример, в небольших основное внимание уделено подключения и запросы к SQL Server. |
| [База данных SQL Azure: использование Python для запроса](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Azure примера базы данных SQL. |
| [Для создания приложений PHP для использования SQL Server на SLES](http://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

| Область | Описание |
| :--- | :---------- |
| [Python в SQL Server](./python/index.md) | Корень нашей документации. |
| [драйвер pymssql](./python/pymssql/index.md) | Корпорация Майкрософт не поддерживать или проверить pymssql драйвер.<br /><br />Драйвер pymssql подключения — это простой интерфейс к базам данных SQL для использования в программах Python. Pymssql строится поверх FreeTDS для предоставления интерфейса Python DB-API (PEP 249) для Microsoft SQL Server. |
| [драйвер pyodbc](./python/pyodbc/index.md)   | Драйвер pyodbc подключения является модуль Python открытым исходным кодом, что упрощает доступ к базам данных ODBC. Реализует спецификацию API DB 2.0, но упакована с еще более удобным Pythonic. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Произносится эмблемы][image-ref-380-ruby] Ruby

Ruby можно использовать для взаимодействия с SQL Server. Корень Ruby документации [здесь](./ruby/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подключение к SQL с Ruby прототипа](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Пример, в небольших основное внимание уделено подключения и запросы к SQL Server. |
| [База данных SQL Azure: используйте Ruby для запроса](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Azure примера базы данных SQL. |
| [Создание приложений Ruby для использования SQL Server на MacOS](http://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpwwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Веб-сайта сборки в приложении, для разработки клиентских SQL](http://www.microsoft.com/sql-server/developer-get-started/)


На нашем [ *сборки в приложении* ](https://www.microsoft.com/sql-server/developer-get-started/) веб-страниц, можно выбрать из длинный список языков, для подключения к SQL Server программирования. Клиентскую программу можно запустить различных операционных систем.

*Сборки в приложении* обеспечивает простоту и полноту для разработчика, только начинающие работу. Шаги поясняют следующие задачи:

1. Установка Microsoft SQL Server
2. Как загрузить и установить средства и драйверы.
3. Как сделать все необходимые конфигурации, в соответствии с выбранной операционной системы.
4. Как скомпилировать предоставленного исходного кода.
5. Как для запуска программы.

Далее приведены несколько контуров приблизительное подробностей, обеспечиваемый веб-сайта.

#### <a name="java-on-ubuntu"></a>Java на Ubuntu:

1. Настройка среды
    - Шаг 1.1 Установка SQL Server
    - Шаг 1.2 установки Java
    - Шаг 1.3 Установка Java Development Kit (JDK)
    - Шаг 1.4 установки Maven
2. Создать приложение Java с SQL Server
    - Шаг 2.1. Создание приложения Java, которое подключается к SQL Server и выполняет запросы
    - Шаг 2.2. Создание приложения Java, которое подключается к SQL Server, используя платформу популярных спящий режим
3. Ускорить приложения Java не более 100 x
    - Шаг 3.1. Создание приложения Java для демонстрации индексов Columnstore

#### <a name="python-on-windows"></a>Python для Windows:

1. Настройка среды
    - Шаг 1.1 Установка SQL Server
    - Шаг 1.2 установки Python
    - В шаге 1.3 установить драйвер ODBC и программа командной строки SQL для SQL Server
2. Создание приложения Python с SQL Server
    - Шаг 2.1 установите драйвер Python для SQL Server
    - Шаг 2.2. Создание базы данных для приложения
    - Шаг 2.3. Создание приложения Python, который подключается к SQL Server и выполняет запросы
3. Ускорить приложения Python до 100 x
    - Шаг 3.1 Создание новой таблицы с 5 миллионов использование программы sqlcmd
    - Шаг 3.2. Создание приложения Python, который запрашивает эту таблицу и измеряет время, затраченное
    - Шаг 3.3 измерить время, необходимое для выполнения запроса
    - Добавить шаг 3.4 индекс columnstore в таблицу
    - Шаг 3.5 измерить время, необходимое для выполнения запроса с индексом columnstore

Следующие снимки экрана, дают представление того, как выглядит наш веб-сайт SQL разработки документации.

#### <a name="choose-a-language"></a>Выберите язык:

![Веб-сайт разработки SQL, приступить к работе][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Выберите операционную систему.

![Веб-сайт разработки SQL, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Другие разработки


Этот раздел содержит ссылки, о других вариантах разработки. К ним относятся, с помощью этих же языков для разработки Azure в целом. Данные можно не ограничиваться только базы данных SQL Azure и Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Центр разработчика для Azure

- [Центр разработчика для Azure](http://docs.microsoft.com/azure/)
- [Azure для разработчиков .NET](http://docs.microsoft.com/dotnet/azure/)
- [Azure для разработчиков Java](http://docs.microsoft.com/java/azure/)
- [Azure для разработчиков Node.js](http://docs.microsoft.com/nodejs/azure/)
- [Azure для разработчиков Python](http://docs.microsoft.com/python/azure/)
- [Создание веб-приложения PHP в Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Другие языки

- [Создание приложений перейдите с помощью SQL Server в Windows](http://www.microsoft.com/sql-server/developer-get-started/go/windows/)



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

