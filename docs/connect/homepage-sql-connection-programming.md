---
title: Главная страница для программирования клиента SQL | Документация Майкрософт
description: Страница концентратора с аннотированными ссылками на скачиваемые файлы и документацию (для различных комбинаций языков и операционных систем), позволяющие подключиться к SQL Server или Базе данных SQL Azure.
author: David-Engel
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: v-daenge
ms.openlocfilehash: df07130ea77578dd467add9d8a96cc331d5c127f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924885"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Главная страница для программирования клиента Microsoft SQL Server


Добро пожаловать на нашу главную страницу о программировании клиента для взаимодействия с Microsoft SQL Server, а также с Базой данных SQL Azure в облаке. Эта статья содержит следующие сведения.

- Список и описание доступных сочетаний языков и драйверов.
    - Сведения предоставляются для операционных систем Linux (Ubuntu и других), MacOS и Windows.
- Ссылки на подробную документацию по каждому сочетанию.
- Области и подобласти иерархической документации для определенных языков, где это необходимо.


#### <a name="azure-sql-database"></a>База данных SQL Azure

В любом языке код, который подключается к SQL Server, почти идентичен коду для подключения к Базе данных SQL Azure.

Дополнительные сведения о строках подключения для подключения к Базе данных SQL Azure см. в следующих статьях:

- [Краткое руководство. Использование .NET Core (C#) для создания запросов к базе данных SQL Azure](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Другая База данных SQL Azure, расположенная рядом с предыдущей статьей о других языках в содержании. Например, обратитесь к статье [Краткое руководство. Использование PHP для создания запросов к базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Веб-страницы для создания приложения

На веб-страницах для *создания приложения* представлены примеры кода, а также сведения о конфигурации в альтернативном формате. Дополнительные сведения см. далее в этой статье в [разделе *Веб-сайт для создания приложения*](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Языки и драйверы для клиентских программ


В следующей таблице каждое изображение с указанием языка является ссылкой на сведения об использовании языка с SQL Server. Каждая ссылка позволяет перейти к одному из следующих разделов этой статьи.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![Логотип C#][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM Entity Framework платформы .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Логотип Java][image-ref-330-java]](#an-130-jdbc-docu) |
| &nbsp; [![Логотип Node.js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![Логотип PHP][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Логотип Python][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Логотип Ruby][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Компоненты для скачивания и установки

Следующая статья посвящена скачиванию и установке различных драйверов подключения SQL для использования с языками программирования:

- [Драйверы SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![Логотип C#][image-ref-320-csharp] Использование ADO.NET в C#

ADO.NET наиболее часто используют управляемые языки .NET, такие как C# и Visual Basic. *ADO.NET* — это обычное имя подмножества классов .NET Framework.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью ADO.NET](./ado-net/step-3-connect-sql-ado-net.md) | Небольшой пример кода, позволяющий подключиться к SQL Server и отправить к нему запрос. |
| [Выполнение устойчивого подключения к SQL с помощью ADO.NET](./ado-net/step-4-connect-resiliently-sql-ado-net.md) | В примере кода реализуется логика повтора, потому что периодически могут возникать потери подключения.<br /><br />Логика повтора применяется для подключений, обслуживаемых через Интернет, к любой облачной базе данных, например к Базе данных SQL Azure. |
| [База данных SQL Azure. Демонстрация использования .NET Core в Windows, Linux и macOS для создания программы на C#, подключения и запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Пример Базы данных SQL Azure. |
| [Создание приложения: C#, ADO.NET, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

|||
| :-- | :-- |
| [Использование ADO.NET в C#](./ado-net/index.md)| Корневой раздел нашей документации. |
| [Пространство имен: System.Data](https://docs.microsoft.com/dotnet/api/system.data) | Набор классов, используемых для ADO.NET. |
| [Пространство имен: Microsoft.Data.SqlClient](https://docs.microsoft.com/dotnet/api/microsoft.data.SqlClient) | Набор классов, используемых для поставщика данных Microsoft .NET для SQL Server. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Логотип Entity Framework][image-ref-333-ef] Entity Framework (EF) с C&#x23;

Entity Framework (EF) предоставляет объектно-реляционное сопоставление (ОРС). ОРС упрощает работу с данными, полученными из реляционной базы данных SQL, в исходном коде объектно-ориентированного программирования (ООП).

Платформа EF прямо или косвенно связана со следующими технологиями:

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/) или [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities);
- улучшения синтаксиса языка, такие как оператор **=>** в C#;
- удобные программы, создающие исходный код для классов, которые сопоставляются с таблицами в базе данных SQL, например [EdmGen.exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>Исходная EF и новая EF

На начальной странице [Entity Framework](https://docs.microsoft.com/ef/) представлено такое описание:

- Механизм Entity Framework является модулем объектно-реляционного сопоставления, который позволяет разработчикам .NET работать с базой данных с помощью объектов .NET. Это исключает необходимость в большинстве вариантов исходного кода доступа к данным, который обычно требуется писать разработчикам.

*Entity Framework* — это имя, совместно используемое двумя отдельными ветвями исходного кода. Одна ветвь EF более старая, и ее исходный код теперь является общедоступным. Другая ветвь EF — новая. Ниже описаны две ветви EF.

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Первая платформа EF была выпущена корпорацией Майкрософт в августе 2008 года. В марте 2015 года корпорация Майкрософт объявила, что EF 6.x была окончательной разработанной ими версией. Корпорация Майкрософт опубликовала исходный код в общедоступном домене.<br /><br />Изначально EF была частью .NET Framework. В последствии EF 6.x была удалена из .NET Framework.<br /><br />[Исходный код EF 6.x на GitHub в репозитории *aspnet/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | Корпорация Майкрософт выпустила новую платформу EF Core в июне 2016 года. EF Core предназначена для повышения гибкости и переносимости. Эта платформа может работать в операционных системах не только под управлением Microsoft Windows. Платформа EF Core может взаимодействовать не только с базами данных Microsoft SQL Server и другими реляционными базами данных.<br /><br />**Примеры кода C#:**<br />[Приступая к работе с платформой Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Начало работы с EF Core в .NET Framework с существующей базой данных](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF и связанные с ней технологии являются сложными, и разработчикам предстоит многому научиться, чтобы освоить их полностью.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Логотип Java][image-ref-330-java] Java и JDBC

Корпорация Майкрософт предоставила драйвер Java Database Connectivity (JDBC), который можно использовать для работы с сервером SQL Server (или с Базой данных SQL Azure). Это драйвер JDBC типа 4, который обеспечивает обмен данными с базами данных через стандартные интерфейсы API JDBC.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Примеры кода](./jdbc/code-samples/index.md) | Примеры кода, которые демонстрируют типы данных, результирующие наборы и большие данные. |
| [Пример URL-адреса подключения](./jdbc/connection-url-sample.md) | Описывает, как использовать URL-адрес подключения для установки подключения к SQL Server. Затем его можно использовать для получения данных с помощью инструкции SQL. |
| [Пример источника данных](./jdbc/data-source-sample.md) | Описывает, как использовать источник данных для подключения к SQL Server. Затем можно использовать хранимую процедуру для получения данных. |
| [Использование Java для создания запросов к Базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Пример Базы данных SQL Azure. |
| [Создание приложений Java с помощью SQL Server в Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

Документация по JDBC включает в себя следующие основные области:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Корневой раздел нашей документации по JDBC. |
| [Справочные материалы](./jdbc/reference/index.md) | Интерфейсы, классы и элементы. |
| [Руководство по программированию для драйвера JDBC для SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Логотип Node.js][image-ref-340-node] Node.js

С помощью Node.js можно подключаться к SQL Server из Windows, Linux или Mac. Корневой элемент документации Node.js можно найти [здесь](./node-js/index.md).

Драйвер подключения Node.js для SQL Server реализован в JavaScript. Драйвер использует протокол TDS, который поддерживают все современные версии SQL Server. Драйвер является проектом с открытым исходным кодом и [доступен на сайте GitHub](https://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Простой исходный код для подключения к SQL Server и выполнения запроса. |
| [База данных SQL Azure. Использование Node.js для отправки запросов](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Пример для Базы данных SQL Azure в облаке. |
| [Создание приложений Node.js для использования SQL Server в macOS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC для C++ 

![Логотип ODBC][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

Открытый интерфейс доступа к базам данных (ODBC) был разработан в 1990 году. Он предшествовал .NET Framework. ODBC разработан для того, чтобы быть независимым от какой-либо конкретной системы баз данных и операционной системы.

За много лет разработчики в корпорации Майкрософт и других компаниях создали и выпустили множество драйверов ODBC. Набор драйверов включает в себя несколько клиентских языков программирования. Список целевых объектов данных выходит далеко за пределы SQL Server.

Некоторые другие драйверы подключения используют ODBC внутренним образом.

#### <a name="code-example"></a>Пример кода

- [Пример кода C++ с использованием ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Разделы документации

Содержимое ODBC в этом разделе посвящено доступу к SQL Server или Базе данных SQL Azure с помощью C++. В следующей таблице приведены приблизительные структурные разделы основной документации по ODBC.


| Область | Подобласть | Описание |
| :--- | :------ | :---------- |
| [ODBC для C++](./odbc/index.md) | Корневой раздел нашей документации. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Сведения об использовании ODBC в операционных системах Linux или MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Сведения об использовании ODBC в операционной системе Windows. |
| [Администрирование](../odbc/admin/index.md) | &nbsp; | Средство администрирования для управления источниками данных ODBC. |
| [Майкрософт](../odbc/microsoft/index.md)  | &nbsp; | Различные драйверы ODBC, создаваемые и предоставляемые корпорацией Майкрософт. |
| [Основные понятия и справочные материалы](../odbc/reference/index.md) | &nbsp; | Основные сведения об интерфейсе ODBC, а также обычная справочная информация. |
| &nbsp; " | [Приложения](../odbc/reference/appendixes/index.md)    | Таблицы переходов состояния, библиотека курсоров ODBC и многое другое. |
| &nbsp; " | [Разработка приложения](../odbc/reference/develop-app/index.md)  | Функции, дескрипторы и многое другое. |
| &nbsp; " | [Разработка драйверов](../odbc/reference/develop-driver/index.md) | Сведения о разработке собственного драйвера ODBC, если у вас есть специализированный источник данных. |
| &nbsp; " | [Установка](../odbc/reference/install/index.md) | Установка ODBC, подразделы и многое другое. |
| &nbsp; " | [Синтаксис](../odbc/reference/syntax/index.md)   | API для настройки, установки, перевода и доступа к данным. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Логотип PHP][image-ref-360-php] PHP

PHP можно использовать для взаимодействия с SQL Server. Корневой раздел документации PHP можно найти [здесь](./php/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Небольшой пример кода, позволяющий подключиться к SQL Server и отправить к нему запрос. |
| [Выполнение устойчивого подключения к SQL с помощью PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | В примере кода реализуется логика повтора, потому что периодически могут возникать потери интернет-подключения и подключения через облако. |
| [База данных SQL Azure. Использование PHP для отправки запросов](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Пример Базы данных SQL Azure. |
| [Создание приложений PHP для использования SQL Server в RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Логотип Python][image-ref-370-python] Python


Python можно использовать для взаимодействия с SQL Server.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL (Python) с помощью pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Небольшой пример кода, позволяющий подключиться к SQL Server и отправить к нему запрос. |
| [База данных SQL Azure. Использование Python для отправки запросов](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Пример Базы данных SQL Azure. |
| [Создание приложений PHP для использования SQL Server в SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

| Область | Описание |
| :--- | :---------- |
| [Python в SQL Server](./python/index.md) | Корневой раздел нашей документации. |
| [Драйвер pymssql](./python/pymssql/index.md) | Корпорация Майкрософт не поддерживает и не тестирует драйвер pymssql.<br /><br />Драйвер подключения pymssql — это простой интерфейс для баз данных SQL, который используется в программах Python. Pymssql создан на базе FreeTDS с целью предоставления интерфейса Python DB-API (PEP-249) для Microsoft SQL Server. |
| [Драйвер pyodbc](./python/pyodbc/index.md)   | Драйвер подключения pyodbc — это модуль Python с открытым исходным кодом, который упрощает доступ к базам данных ODBC. Он реализует спецификацию DB API 2.0, но сравним с Python по удобству. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Логотип Ruby][image-ref-380-ruby] Ruby

Ruby можно использовать для взаимодействия с SQL Server. Корневой раздел документации Ruby можно найти [здесь](./ruby/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Эксперимент, подразумевающий подключение к SQL с помощью Ruby](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Небольшой пример кода, позволяющий подключиться к SQL Server и отправить к нему запрос. |
| [База данных SQL Azure. Использование Ruby для отправки запросов](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Пример Базы данных SQL Azure. |
| [Создание приложений Ruby для использования SQL Server в macOS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-development"></a>[Веб-сайт для создания приложений (клиентских приложений SQL)](https://www.microsoft.com/sql-server/developer-get-started/)


На нашем веб-сайте для [*создания приложений*](https://www.microsoft.com/sql-server/developer-get-started/) можно выбрать из длинного списка языков программирования, используемых для подключения к SQL Server. Клиентская программа может работать с различными операционными системами.

Веб-сайт для *создания приложений* уделяет особое внимание простоте и доступности функций для начинающих разработчиков. Приведенные ниже шаги показывают, как это сделать.

1. Установка Microsoft SQL Server
2. Скачивание и установка средств и драйверов.
3. Осуществление необходимых настроек в соответствии с выбранной операционной системой.
4. Компиляция предоставленного исходного кода.
5. Как запустить программу.

Далее представлено несколько приблизительных разделов с описаниями, содержащихся на веб-сайте.

#### <a name="java-on-ubuntu"></a>Java в Ubuntu:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1.2. Установка Java.
    - Шаг 1.3. Установка пакета средств разработки Java (JDK).
    - Шаг 1.4. Установка Maven.
2. Создание приложения Java с помощью SQL Server.
    - Шаг 2.1. Создание приложения Java, которое подключается к SQL Server и выполняет запросы.
    - Шаг 2.2. Создание приложения Java, которое подключается к SQL Server с помощью популярной платформы Hibernate.
3. Ускорение работы приложения Java в 100 раз.
    - Шаг 3.1. Создание приложения Java для демонстрации индексов Columnstore.

#### <a name="python-on-windows"></a>Python в Windows:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1.2. Установка Python.
    - Шаг 1.3. Установка драйвера ODBC и служебной программы командной строки SQL для SQL Server.
2. Создание приложения Python с помощью SQL Server.
    - Шаг 2.1. Установка драйвера Python для SQL Server.
    - Шаг 2.2. Создание базы данных для приложения.
    - Шаг 2.3. Создание приложения Python, которое подключается к SQL Server и выполняет запросы.
3. Ускорение работы приложения Python в 100 раз.
    - Шаг 3.1. Создание новой таблицы с 5 млн записей с помощью программы sqlcmd.
    - Шаг 3.2. Создание приложения Python, которое запрашивает эту таблицу и измеряет затраченное время.
    - Шаг 3.3. Измерение времени, затрачиваемого на выполнение запроса.
    - Шаг 3.4. Добавление индекса columnstore в таблицу.
    - Шаг 3.5. Измерение времени, затрачиваемого на выполнение запроса с индексом columnstore.

На следующих снимках экрана показано, как выглядит наш веб-сайт документации по разработке SQL.

#### <a name="choose-a-language"></a>Выбор языка:

![Начало работы с веб-сайтом разработки SQL][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Выберите операционную систему:

![Веб-сайт разработки для SQL для Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Разработка на других языках


В этом разделе приводятся ссылки на другие варианты разработки. Тут описано использование тех же языков для разработки Azure в целом. В этой документации описывается не только целевая настройка для Базы данных SQL Azure и Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Центр разработчиков для Azure

- [Центр разработчиков для Azure](https://docs.microsoft.com/azure/)
- [Azure for .NET developers](https://docs.microsoft.com/dotnet/azure/) (Azure для разработчиков .NET);
- [Azure for Java developers](https://docs.microsoft.com/java/azure/) (Azure для разработчиков Java);
- [Azure for Node.js developers](https://docs.microsoft.com/nodejs/azure/) (Azure для разработчиков Node.js);
- [Azure for Python developers](https://docs.microsoft.com/python/azure/) (Azure для разработчиков Python).
- [Создание веб-приложения PHP в Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-php)

#### <a name="other-languages"></a>Другие языки

- [Создание приложений Go с помощью SQL Server в Windows](https://www.microsoft.com/sql-server/developer-get-started/go/windows/)



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

