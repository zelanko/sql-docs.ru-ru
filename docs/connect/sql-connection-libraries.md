---
title: Библиотеки подключений для баз данных Microsoft SQL | Документация Майкрософт
description: Ссылки для загрузки модулей, которые обеспечивают подключение к Microsoft SQL Server и базе данных SQL Azure на различных языках программирования клиента.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 71254b937c4c0173af9e1549efb98a0b42f65e02
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632817"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Модули подключения для баз данных Microsoft SQL

В этой статье содержатся ссылки для загрузки модулей подключения или *драйверов* , которые клиентские программы могут использовать для взаимодействия с [Microsoft SQL Server](../relational-databases/database-features.md), а также с двойника в облачной [базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/). Драйверы доступны для различных языков программирования, работающих в следующих операционных системах:

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Несоответствие ООП-to-relation

*Реляционная*. клиентские программы, написанные на языке объектно-ориентированного программирования (ООП), часто используют драйверы SQL, возвращающие запрашиваемые данные в более реляционном формате, чем объектно-ориентированный. C#одним из примеров является использование ADO.NET. Несоответствие ООП-реляционного формата иногда делает код ООП труднее для написания и понимания.

*ORM*: другие драйверы или платформы возвращают запрашиваемые данные в формате ООП, избегая несоответствия. Эти драйверы работают, ожидая, что классы были определены для соответствия столбцам данных определенных таблиц SQL. Затем драйвер выполняет *объектно-реляционное сопоставление* (ORM) для возврата запрашиваемых данных в качестве экземпляра класса. Entity Framework Майкрософт (EF) для C#и перехода в режим гибернации для Java — это два примера.

В представленной статье рассматриваются отдельные разделы для этих двух типов драйверов подключения.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Драйверы для реляционного доступа


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Язык | Скачать драйвер SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[.NET Core, для Linux — Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET Core, для MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET Core, для Windows](https://www.microsoft.com/net/core) |
| C++ | [интерфейс ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Драйвер Node. js, инструкции по установке](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, инструкции по установке](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Скачать ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Драйвер Ruby, инструкции по установке](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Страница скачивания Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Драйверы для доступа к ORM


В следующей таблице приведены примеры платформ объектно-реляционного сопоставления (ORM), которые используются клиентскими приложениями для подключения к базам данных Microsoft SQL.


| Язык | Загрузка драйвера ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6. x или более поздней версии)](https://docs.microsoft.com/ef/) |
| Java | [Hibernate ORM](https://hibernate.org/orm)|
| PHP | [Милнером ORM, входящий в Laravel install](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Создание веб-страниц приложения
[https://aka.ms/sqldev](https://aka.ms/sqldev) выполняет переход к набору веб *-страниц "сборка — приложение* ". Веб-страницы содержат сведения о многочисленных сочетаниях языка программирования, операционной системы и драйвера подключения SQL. Ниже приведены сведения, предоставляемые веб-страницами «сборка — an-приложение».

- Сведения о том, как начать с самого начала, для каждого сочетания языка + операционная система + Driver.
    - Инструкции по установке последних версий драйверов для подключения к SQL.
- Примеры кода для каждого из следующих элементов:
    - Примеры объектно-реляционного кода.
    - Примеры кода ORM.
    - Демонстрации индекса columnstore для более быстрой производительности.

#### <a name="first-page-of-build-an-app-webpages"></a>Первая страница, из веб-страниц "сборка — приложение"
![Сборка — веб-страницы на основе приложения, снимок экрана первой страницы][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Меню для Java-Ubuntu — веб-страницы сборки и приложения
![Сборка — веб-страницы на основе приложений, меню Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Связанные ссылки
- [Примеры кода для подключения к базе данных SQL Azure в облаке с помощью Java и других языков](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
