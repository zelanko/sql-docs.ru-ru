---
title: Домашняя страница для программирования клиента SQL | Документация Майкрософт
description: Страница центра с заметками ссылки на загружаемые файлы и документацию для множества комбинаций языков и операционных систем для подключения к SQL Server или к базе данных SQL Azure.
author: MightyPen
ms.date: 11/07/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: v-daveng
ms.author: genemi
ms.openlocfilehash: 6961f8c23b4acfd787958cc9a160faf88362b54c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451853"
---
# <a name="homepage-for-client-programming-to-microsoft-sql-server"></a>Главная страница для программирования клиента Microsoft SQL Server


Добро пожаловать на нашу домашнюю страницу о программировании клиента для взаимодействия с Microsoft SQL Server, а также с базой данных SQL Azure в облаке. Эта статья содержит следующие сведения.

- Содержит список и описание доступных сочетаний языков и драйверов.
    - Сведения предоставляются для операционных систем Linux (Ubuntu и другие), MacOS и Windows.
- Содержит ссылки на подробную документацию по каждому сочетанию.
- Отображает области и подобласти иерархической документации для определенных языков, где это необходимо.


#### <a name="azure-sql-database"></a>База данных SQL Azure

В любом конкретном языке код, который подключается к SQL Server, почти идентичен коду для подключения к базе данных SQL Azure.

Дополнительные сведения о строках подключения для подключения к базе данных SQL Azure см. в следующих статьях:

- [Используйте .NET Core (C#) для запроса к базе данных SQL Azure](/azure/sql-database/sql-database-connect-query-dotnet-core).
- Другая база данных SQL Azure, расположенная рядом с предыдущей статьей в содержании, о других языках. Например, см. статью [Использование PHP для запроса к базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php).


#### <a name="build-an-app-webpages"></a>Создание веб-страниц приложения

Наши веб *-страницы сборки — приложения* представляют примеры кода, а также сведения о конфигурации в альтернативном формате. Дополнительные сведения см. Далее в [разделе *сборка — веб-сайт*с подписью](#an-204-aka-ms-sqldev).



<a name="an-050-languages-clients" />

## <a name="languages-and-drivers-for-client-programs"></a>Языки и драйверы для клиентских программ


В следующей таблице каждый языковой образ является ссылкой на сведения об использовании языка с SQL Server. Каждая ссылка перейдет к более поздней части этой статьи.

| &nbsp; | &nbsp; | &nbsp; |
| :-- | :-- | :-- |
| &nbsp; [![C# логотип][image-ref-320-csharp]](#an-110-ado-net-docu) | &nbsp; [![ORM Entity Framework .NET Framework][image-ref-333-ef]](#an-116-csharp-ef-orm) | &nbsp; [![Логотип Java][image-ref-330-java]](#an-130-jdbc-docu) |
| [логотип &nbsp; ![Node. js][image-ref-340-node]](#an-140-node-js-docu) | &nbsp; [ **`ODBC for C++`** ](#an-160-odbc-cpp-docu)<br/>[![cpp-big-plus][image-ref-322-cpp]](#an-160-odbc-cpp-docu) | &nbsp; [![PHP логотип][image-ref-360-php]](#an-170-php-docu) |
| &nbsp; [![Логотип Python][image-ref-370-python]](#an-180-python-docu) | &nbsp; [![Ruby логотип][image-ref-380-ruby]](#an-190-ruby-docu) | &nbsp; ... |
| &nbsp; | &nbsp; | <br />|


#### <a name="downloads-and-installs"></a>Загрузки и установки

Следующая статья посвящена скачиванию и установке различных драйверов подключения SQL для использования в языках программирования:

- [Драйверы SQL Server](sql-server-drivers.md)



<a name="an-110-ado-net-docu" />

## <a name="c-logoimage-ref-320-csharp-c-using-adonet"></a>![C#совместимость][image-ref-320-csharp] C#Использование ADO.NET

Управляемые языки .NET, такие как C# и Visual Basic, являются наиболее распространенными пользователями ADO.NET. *ADO.NET* — это обычное имя подмножества классов .NET Framework.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью ADO.NET](./ado-net/step-3-connect-sql-ado-net.md) | Небольшой пример кода, посвященный соединению и запросу SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью ADO.NET](./ado-net/step-4-connect-resiliently-sql-ado-net.md) | Логика повторных попыток в примере кода, так как во время подключения могут возникать потери подключения.<br /><br />Логика повторных попыток применяется для подключений, обслуживаемых через Интернет, в любую облачную базу данных, например в базу данных SQL Azure. |
| [База данных SQL Azure. Демонстрация использования .NET Core в Windows, Linux и macOS для создания C# программы, подключения и запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-dotnet-core) | Пример базы данных SQL Azure. |
| [Сборка-an-App: C#, ADO.NET, Windows](https://www.microsoft.com/sql-server/developer-get-started/csharp/win/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

|||
| :-- | :-- |
| [C#Использование ADO.NET](./ado-net/index.md)| Корень нашей документации. |
| [Пространство имен: System. Data](https://docs.microsoft.com/dotnet/api/system.data) | Набор классов, используемых для ADO.NET. |
| [Пространство имен: System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.SqlClient) | Набор классов, которые наиболее непосредственно находятся в центре ADO.NET. |
| &nbsp; | <br /> |



<a name="an-116-csharp-ef-orm" />

## <a name="entity-framework-logoimage-ref-333-ef-entity-framework-ef-with-cx23"></a>![Логотип Entity Framework][image-ref-333-ef] Entity Framework (EF) с C&#x23;

Entity Framework (EF) предоставляет объектно-реляционное сопоставление (ORM). ORM упрощает исходный код объектно-ориентированного программирования (ООП) для работы с данными, полученными из реляционной базы данных SQL.

EF имеет прямые или косвенные связи со следующими технологиями:

- .NET Framework
- [LINQ to SQL](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/linq/)или [LINQ to Entities](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/linq-to-entities)
- Улучшения синтаксиса языка, такие как оператор **=>** в C#.
- Удобные программы, создающие исходный код для классов, которые сопоставляются с таблицами в базе данных SQL. Например, [EdmGen. exe](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/edm-generator-edmgen-exe).


#### <a name="original-ef-and-new-ef"></a>Исходный EF и New EF

[Начальная страница для Entity Framework](https://docs.microsoft.com/ef/) представляет EF с описанием, как показано ниже:

- Entity Framework — это объектно-реляционное средство сопоставления (O/RM), позволяющее разработчикам .NET работать с базой данных с помощью объектов .NET. Это устраняет необходимость в большей части исходного кода доступа к данным, который разработчикам обычно требуется писать.

*Entity Framework* — это имя, совместно используемое двумя отдельными ветвями исходного кода. Одна ветвь EF более старая, и ее исходный код теперь может поддерживаться общедоступным. Другая ссылка EF является новой. Ниже описаны две EFs.

|     |     |
| :-- | :-- |
| [EF 6.x](https://docs.microsoft.com/ef/ef6/) | Первая выпущенная ссылка корпорации Майкрософт в августе 2008 августа. В марте 2015 Корпорация Майкрософт объявила, что EF 6. x является окончательной версией, которая была разработана корпорацией Майкрософт. Корпорация Майкрософт выпустила исходный код в общедоступном домене.<br /><br />Изначально EF был частью .NET Framework. Но EF 6. x был удален из .NET Framework.<br /><br />[Исходный код EF 6. x в GitHub, в репозитории *ASPNET/EntityFramework6*](https://github.com/aspnet/EntityFramework6) |
| [EF Core](https://docs.microsoft.com/ef/core/) | Корпорация Майкрософт выпустила недавно разработанную EF Core в июне 2016. EF Core предназначен для повышения гибкости и переносимости. EF Core могут работать в операционных системах, не относящихся только к Microsoft Windows. И EF Core могут взаимодействовать с базами данных, помимо Microsoft SQL Server и других реляционных баз данных.<br /><br />**Примеры&#x23; кода C:**<br />[Приступая к работе с платформой Entity Framework Core](https://docs.microsoft.com/ef/core/get-started/index)<br />[Начало работы с EF Core на .NET Framework с существующей базой данных](https://docs.microsoft.com/ef/core/get-started/full-dotnet/existing-db) |
| &nbsp; | <br /> |

EF и родственные технологии являются мощными, и они очень полезны для разработчиков, желающих заглавную всю область.

&nbsp;



<a name="an-130-jdbc-docu" />

## <a name="java-logoimage-ref-330-java-java-and-jdbc"></a>![Логотип Java][image-ref-330-java] Java и JDBC

Корпорация Майкрософт предоставляет драйвер Java Database Connectivity (JDBC) для использования с SQL Server (или с базой данных SQL Azure). Это драйвер JDBC типа 4, который обеспечивает обмен данными с базами данных через стандартные интерфейсы API JDBC.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Примеры кода](./jdbc/code-samples/index.md) | Примеры кода, которые изучены о типах данных, результирующих наборах и больших данных. |
| [Пример URL-адреса подключения](./jdbc/connection-url-sample.md) | Описывает, как использовать URL-адрес подключения для подключения к SQL Server. Затем используйте его для получения данных с помощью инструкции SQL. |
| [Пример источника данных](./jdbc/data-source-sample.md) | Описывает, как использовать источник данных для подключения к SQL Server. Затем используйте хранимую процедуру для получения данных. |
| [Использование Java для запроса к базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java) | Пример базы данных SQL Azure. |
| [Создание приложений Java с помощью SQL Server в Ubuntu](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

Документация по JDBC включает в себя следующие основные области:

|||
| :-- | :-- |
| [Java Database Connectivity (JDBC)](./jdbc/index.md) | Корень документации по JDBC. |
| [Справочник](./jdbc/reference/index.md) | Интерфейсы, классы и элементы. |
| [Руководство по программированию для драйвера JDBC для SQL](./jdbc/programming-guide-for-jdbc-sql-driver.md) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-140-node-js-docu" />

## <a name="nodejs-logoimage-ref-340-node-nodejs"></a>![Логотип Node. js][image-ref-340-node] Node.js

С помощью Node. js можно подключаться к SQL Server из Windows, Linux или Mac. [Ниже](./node-js/index.md)приведена корневая папка документации по Node. js.

Драйвер подключения Node. js для SQL Server реализован в JavaScript. Драйвер использует протокол TDS, поддерживаемый всеми современными версиями SQL Server. Драйвер является проектом с открытым исходным кодом, [доступным на сайте GitHub](https://tediousjs.github.io/tedious/).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью Node.js](./node-js/step-3-proof-of-concept-connecting-to-sql-using-node-js.md) | Исходный код для исходного кода костей для подключения к SQL Server и выполнения запроса. |
| [База данных SQL Azure: использование Node. js для запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | Пример для базы данных SQL Azure в облаке. |
| [Создание приложений Node. js для использования SQL Server в macOS](https://www.microsoft.com/sql-server/developer-get-started/node/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-160-odbc-cpp-docu" />

## <a name="odbc-for-c"></a>ODBC дляC++ 

![Логотип ODBC][image-ref-350-odbc] ![cpp-big-plus][image-ref-322-cpp]

Открытая служба подключения к базе данных (ODBC) была разработана в 1990, а .NET Framework. ODBC разработан для того, чтобы быть независимым от какой-либо конкретной системы баз данных, независимо от операционной системы.

За годы многие драйверы ODBC были созданы и выпущены группами внутри и за пределами корпорации Майкрософт. Диапазон драйверов затрагивает несколько языков программирования клиента. Список целевых объектов данных хорошо выходит за пределы SQL Server.

Некоторые другие драйверы подключения используют ODBC внутренним образом.

#### <a name="code-example"></a>Пример кода

- [Пример кода C++ с использованием ODBC](../odbc/reference/sample-odbc-program.md)

#### <a name="documentation-outline"></a>Структура документации

Содержимое ODBC в этом разделе посвящено доступу к SQL Server или базе данных SQL Azure C++из. В следующей таблице приводится приблизительная структура основной документации по ODBC.


| Область | Подобласть | Описание |
| :--- | :------ | :---------- |
| [ODBC дляC++](./odbc/index.md) | Корень нашей документации. |
| [Linux-Mac](./odbc/linux-mac/index.md) | &nbsp; | Сведения об использовании ODBC в операционных системах Linux или MacOS. |
| [Windows](./odbc/windows/index.md)     | &nbsp; | Сведения об использовании ODBC в операционной системе Windows. |
| [Администрирование](../odbc/admin/index.md) | &nbsp; | Средство администрирования для управления источниками данных ODBC. |
| [Майкрософт](../odbc/microsoft/index.md)  | &nbsp; | Различные драйверы ODBC, создаваемые и предоставляемые корпорацией Майкрософт. |
| [Основные понятия и справочные материалы](../odbc/reference/index.md) | &nbsp; | Основные сведения об интерфейсе ODBC, а также традиционная ссылка. |
| &nbsp; " | [Приложения](../odbc/reference/appendixes/index.md)    | Таблицы смен состояния, Библиотека курсоров ODBC и многое другое. |
| &nbsp; " | [Разработка приложения](../odbc/reference/develop-app/index.md)  | Функции, дескрипторы и многое другое. |
| &nbsp; " | [Разработка драйверов](../odbc/reference/develop-driver/index.md) | Как разработать собственный драйвер ODBC, если у вас есть специализированный источник данных. |
| &nbsp; " | [Установка](../odbc/reference/install/index.md) | Установка ODBC, подразделы и многое другое. |
| &nbsp; " | [Синтаксис](../odbc/reference/syntax/index.md)   | API для установки, установщика, перевода и доступа к данным. |
| &nbsp; | &nbsp; | <br /> |



<a name="an-170-php-docu" />

## <a name="php-logoimage-ref-360-php-php"></a>![Логотип PHP][image-ref-360-php] PHP

Для взаимодействия с SQL Server можно использовать PHP. Корень документации по PHP находится [здесь](./php/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Подтверждение концепции, подразумевающее подключение к SQL с помощью PHP](./php/step-3-proof-of-concept-connecting-to-sql-using-php.md) | Небольшой пример кода, посвященный соединению и запросу SQL Server. |
| [Выполнение устойчивого подключения к SQL с помощью PHP](./php/step-4-connect-resiliently-to-sql-with-php.md) | Логика повторных попыток в примере кода, так как подключения через Интернет и облако могут иногда испытывать невозможность потери подключения. |
| [База данных SQL Azure: использование PHP для запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-php) | Пример базы данных SQL Azure. |
| [Создание приложений PHP для использования SQL Server в RHEL](https://www.microsoft.com/sql-server/developer-get-started/php/rhel/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-180-python-docu" />

## <a name="python-logoimage-ref-370-python-python"></a>![Логотип Python][image-ref-370-python] Python


Для взаимодействия с SQL Server можно использовать Python.

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Проверка концепции при подключении к SQL с помощью Python с использованием pyodbc](./python/pyodbc/step-3-proof-of-concept-connecting-to-sql-using-pyodbc.md) | Небольшой пример кода, посвященный соединению и запросу SQL Server. |
| [База данных SQL Azure: использование Python для запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-python) | Пример базы данных SQL Azure. |
| [Создание приложений PHP для использования SQL Server в SLES](https://www.microsoft.com/sql-server/developer-get-started/python/sles/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |

#### <a name="documentation"></a>Документация

| Область | Описание |
| :--- | :---------- |
| [SQL Server Python](./python/index.md) | Корень нашей документации. |
| [драйвер pymssql](./python/pymssql/index.md) | Корпорация Майкрософт не поддерживает и не тестирует драйвер pymssql.<br /><br />Драйвер подключения pymssql — это простой интерфейс для баз данных SQL, который используется в программах Python. Pymssql строится поверх FreeTDS, чтобы предоставить интерфейс Python DB-API (PEP-249) для Microsoft SQL Server. |
| [Драйвер pyodbc](./python/pyodbc/index.md)   | Драйвер подключения pyodbc — это модуль Python с открытым исходным кодом, который делает доступ к базам данных ODBC простым. Он реализует спецификацию API 2,0 в базе данных, но упакован с еще большим удобством Python. |
| &nbsp; | <br /> |


<a name="an-190-ruby-docu" />

## <a name="ruby-logoimage-ref-380-ruby-ruby"></a>![Эмблема Ruby][image-ref-380-ruby] Ruby

Ruby можно использовать для взаимодействия с SQL Server. Корень документации по Ruby находится [здесь](./ruby/index.md).

#### <a name="code-examples"></a>Примеры кода

|||
| :-- | :-- |
| [Эксперимент, подразумевающий подключение к SQL с помощью Ruby](./ruby/step-3-proof-of-concept-connecting-to-sql-using-ruby.md) | Небольшой пример кода, посвященный соединению и запросу SQL Server. |
| [База данных SQL Azure: использование Ruby для запроса](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ruby) | Пример базы данных SQL Azure. |
| [Создание приложений Ruby для использования SQL Server в MacOS](https://www.microsoft.com/sql-server/developer-get-started/ruby/mac/) | Сведения о конфигурации, а также примеры кода. |
| &nbsp; | <br /> |



<a name="an-204-aka-ms-sqldev" />

## <a name="build-an-app-website-for-sql-client-developmenthttpswwwmicrosoftcomsql-serverdeveloper-get-started"></a>[Сборка — веб-сайт на основе приложений, для разработки клиентов SQL](https://www.microsoft.com/sql-server/developer-get-started/)


На нашей веб-странице [*Сборка — приложение*](https://www.microsoft.com/sql-server/developer-get-started/) можно выбрать из длинного списка языков программирования для подключения к SQL Server. И клиентская программа может работать с различными операционными системами.

*Сборка — приложение* делает акцент на простоту и полноту для разработчика, который только приступ к работе. В этом разделе описаны следующие задачи.

1. Установка Microsoft SQL Server
2. Загрузка и установка средств и драйверов.
3. Как выполнить необходимые настройки в соответствии с выбранной операционной системой.
4. Как скомпилировать предоставленный исходный код.
5. Как запустить программу.

Далее представлено несколько приблизительных описаний на веб-сайте.

#### <a name="java-on-ubuntu"></a>Java в Ubuntu:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1,2. Установка Java
    - Шаг 1,3. Установка пакета средств разработки Java (JDK)
    - Шаг 1,4. установка Maven
2. Создание приложения Java с помощью SQL Server
    - Шаг 2,1. Создание приложения Java, которое подключается к SQL Server и выполняет запросы
    - Шаг 2,2. Создание приложения Java, которое подключается к SQL Server с помощью популярной среды в режиме гибернации
3. Ускорение работы приложения Java до 100X
    - Шаг 3,1. Создание приложения Java для демонстрации индексов columnstore

#### <a name="python-on-windows"></a>Python в Windows:

1. Настройка среды
    - Шаг 1.1. Установка SQL Server
    - Шаг 1,2. Установка Python
    - Шаг 1,3. Установка драйвера ODBC и служебной программы командной строки SQL для SQL Server
2. Создание приложения Python с помощью SQL Server
    - Шаг 2,1. Установка драйвера Python для SQL Server
    - Шаг 2,2. Создание базы данных для приложения
    - Шаг 2,3. Создание приложения Python, которое подключается к SQL Server и выполняет запросы
3. Быстрое создание приложения Python на 100 раз
    - Шаг 3,1. Создание новой таблицы с 5 000 000 с помощью программы sqlcmd
    - Шаг 3,2. Создание приложения Python, которое запрашивает эту таблицу и измеряет затраченное время
    - Шаг 3,3. Измерение времени, затрачиваемого на выполнение запроса
    - Шаг 3,4. Добавление индекса columnstore в таблицу
    - Шаг 3,5. Измерение времени, затрачиваемого на выполнение запроса с индексом columnstore

На следующих снимках экрана представлено представление о том, как выглядит наш веб-сайт документации по разработке SQL.

#### <a name="choose-a-language"></a>Выбор языка:

![Веб-сайт разработки SQL, начало работы][image-ref-390-aka-ms-sqldev-choose-language]

&nbsp;

#### <a name="choose-an-operating-system"></a>Выберите операционную систему:

![Веб-сайт разработки SQL, Java Ubuntu][image-ref-400-aka-ms-sqldev-java-ubuntu]

&nbsp;



## <a name="other-development"></a>Другая разработка


В этом разделе приводятся ссылки на другие варианты разработки. Они включают использование тех же языков для разработки Azure в целом. Эти сведения выходят за пределы выбора только базы данных SQL Azure и Microsoft SQL Server.

#### <a name="developer-hub-for-azure"></a>Центр разработчиков для Azure

- [Центр разработчиков для Azure](https://docs.microsoft.com/azure/)
- [Azure для разработчиков .NET](https://docs.microsoft.com/dotnet/azure/)
- [Azure для разработчиков Java](https://docs.microsoft.com/java/azure/)
- [Azure для разработчиков Node. js](https://docs.microsoft.com/nodejs/azure/)
- [Azure для разработчиков Python](https://docs.microsoft.com/python/azure/)
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

