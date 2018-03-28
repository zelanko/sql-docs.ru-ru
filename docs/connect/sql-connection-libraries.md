---
title: Библиотеки подключения для баз данных SQL Microsoft | Документы Microsoft
description: Предоставляет ссылки для загрузки модулей, которые обеспечивают подключение к Microsoft SQL Server и базы данных SQL Azure из различных языков программирования клиента.
author: MightyPen
ms.service: ''
ms.component: connect
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.technology: dbe-data-tier-apps
ms.custom: ''
ms.workload: data-management
ms.topic: article
ms.date: 08/09/2017
ms.author: genemi
ms.openlocfilehash: 33df5e13dcdeb205a1dbc9fa9c1a5dc7efc754c2
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Модули подключения для базы данных Microsoft SQL

Также приводятся ссылки для загрузки модули подключения или *драйверы* , его можно использовать для взаимодействия с [Microsoft SQL Server](../index.md)и с его двойных в облаке [Azure База данных SQL](http://docs.microsoft.com/azure/sql-database/). Драйверы предоставляются для различных языков программирования, в следующих операционных системах:

- Linux (Ubuntu)
- MacOS
- Windows


#### <a name="oop-to-relational-mismatch"></a>Объектно реляционные несоответствие

*Реляционные*: клиентские программы, записанные в объектно ориентированный язык программирования (OOP) часто использовать драйверы SQL, которые возвращают запрашиваемые данные в формате, несколько реляционных, чем объектно-ориентированной. С помощью ADO.NET в C# является одним из примеров. Объектно реляционного несоответствие формата иногда делает труднее писать и понимать код объектно-ориентированное Программирование.

*Объектно-реляционные Преобразователи*: других драйверов или платформы возврата запрошенных данных в формате объектно-ориентированное Программирование, как избежать несоответствия. Эти драйверы работать, ожидается, что классы были определены для сопоставления столбцов данных из отдельных таблиц SQL. Драйвер выполняет *объектно реляционное сопоставление* (ORM) для возврата результатов запроса в виде экземпляра класса. Корпорации Майкрософт Entity Framework (EF) для C# и режима гибернации для Java, приведены два примера.

Этой статье использует отдельные разделы для помещения в эти два вида драйверы соединения.


<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Драйверы для реляционный доступ


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->


| Язык | Загрузка драйвера SQL |
| :------- | :---------------------- |
| C#       | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[.NET core для Linux Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core для MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core для Windows](https://www.microsoft.com/net/core) |
| C++      | [ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Java     | [JDBC](http://www.microsoft.com/download/details.aspx?id=55539) |
| Node.js  | [Драйвер node.js, инструкции по установке](http://docs.microsoft.com/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development) |
| PHP      | *Операционная система:*<br /><br />[Драйвер PHP для Windows](https://www.microsoft.com/download/details.aspx?id=55642)<br />[Драйвер PHP Linux или macOS из Github](http://github.com/Microsoft/msphpsql/) |
| Python   | [pyodbc инструкции по установке](http://docs.microsoft.com/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development)<br />[Загрузите ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Ruby     | [Драйвер Ruby, инструкции по установке](https://docs.microsoft.com/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development)<br />[Страница загрузки Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |


<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Драйверы для ORM доступа


Ниже перечислены примеры объекта реляционного сопоставления (ORM) платформ, которые клиентские приложения используют для подключения к базам данных Microsoft SQL.


| Язык | Загрузка драйвера ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Платформа Entity Framework (версии 6.x или более поздней версии)](http://docs.microsoft.com/ef/) |
| Java | [Режим гибернации ORM](http://hibernate.org/orm)|
| PHP | [Eloquent ORM, входит в Laravel установки](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby на направляющие](http://rubyonrails.org/) |
| &nbsp; | <br /> |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Сборки в приложение веб-страниц


[http://aka.ms/sqldev](http://aka.ms/sqldev) Вы перейдете на набор *сборки в приложении* веб-страниц. Веб-страниц содержат сведения о многочисленные сочетания программирования языка, операционной системы и драйвера подключения SQL. Помимо сведений, предоставляемых сборки в приложение веб-страниц являются следующие элементы:

- Сведения о том, как приступить к работе с самого начала, для каждого сочетания языка + операционной системы и драйвера.
    - Инструкции по установке последние версии драйверов подключения SQL.
- Примеры кода для каждого из следующих элементов:
    - Примеры объектно реляционного кода.
    - Примеры кода ORM.
    - Демонстрации индекс ColumnStore для значительно повысить производительность.


#### <a name="first-page-of-build-an-app-webpages"></a>Первая страница сборки в приложение веб-страниц

![Сборки в приложение веб-страниц, первая страница экрана][image-ref-163-buildanapp-webpages-first-page]


#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Меню для Java - Ubuntu сборки в приложение веб-страниц

![Сборки в приложение веб-страниц, меню Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]


&nbsp;


## <a name="related-links"></a>Связанные ссылки

- [Примеры для подключения к базе данных SQL Azure в облаке, с использованием Java и других языков кода](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).


<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
