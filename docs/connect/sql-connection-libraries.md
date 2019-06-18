---
title: Библиотеки подключений для базы данных SQL Microsoft | Документация Майкрософт
description: Ссылки для скачивания модулей, которые обеспечивают подключение к Microsoft SQL Server и базы данных SQL Azure, с разных языков программирования клиента.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 7f759dbe9022cff557461d900a35b3ccc91d2c4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62862431"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Модули подключения для базы данных Microsoft SQL

В этой статье ссылками на загрузку модулей подключения или *драйверы* , клиентские программы можно использовать для взаимодействия с [Microsoft SQL Server](../relational-databases/database-features.md)и с его двойником в облаке [Azure База данных SQL](https://docs.microsoft.com/azure/sql-database/). Драйверы доступны для различных языков программирования, работающих под управлением следующих ОС:

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Объектно реляционные несоответствие

*Реляционные*: клиентские программы, написанные в языках объектно ориентированного программирования (OOP), часто использовать драйверы SQL, которые возвращают запрашиваемые данные в формате, который является более реляционной, чем объектно-ориентированного программирования. С помощью ADO.NET в C# — один из примеров. Объектно реляционного несоответствие формата иногда делает труднее писать и понимать код ООП.

*ORM*: другие драйверы или платформ возврата запрошенных данных в формате ООП, как избежать несоответствия. Эти драйверы работают, ожидается, что классы были определены для сопоставления столбцы данных отдельные таблицы SQL. Драйвер выполняет *объектно реляционного сопоставления* (ORM) для возврата запрошенных данных в виде экземпляра класса. Microsoft Entity Framework (EF) для C#, а также спящий режим для Java, приведены два примера.

Этой статье использует отдельными разделами для помещения в эти два типа драйверов подключения.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Драйверы на доступ к реляционным


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Язык | Скачайте драйвер Microsoft SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br /><br />[.NET core для Linux Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET core для MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core для Windows](https://www.microsoft.com/net/core) |
| C++ | [интерфейс ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Драйвер node.js, инструкции по установке](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, инструкции по установке](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Скачайте ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Драйвер Ruby, инструкции по установке](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Страница загрузки Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Драйверы для доступа к ORM


Ниже перечислены примеры платформ объектно-реляционного сопоставления (ORM), которые клиентские приложения используют для подключения к базам данных Microsoft SQL.


| Язык | Загрузка драйвера ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Платформа Entity Framework (6.x или более поздней версии)](https://docs.microsoft.com/ef/) |
| Java | [Режим гибернации ORM](https://hibernate.org/orm)|
| PHP | [Милнером ORM, входит в состав установки Laravel](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Сборки в приложение веб-страниц
[https://aka.ms/sqldev](https://aka.ms/sqldev) Вы перейдете к набору *-an app* веб-страниц. Веб-страниц содержат сведения о многочисленных комбинации языка программирования, операционной системы и драйвер подключения SQL. Сведения, предоставляемые веб-страниц-an app относятся следующие элементы:

- Сведения о том, как приступить к работе с самого начала, для каждой комбинации языка + операционной системы и драйвера.
    - Инструкции по установке последних версий драйверов подключения SQL.
- Примеры кода для каждого из следующих элементов:
    - Примеры объектно реляционного кода.
    - Примеры кода ORM.
    - Демонстрации индекса ColumnStore значительно повысить производительность.

#### <a name="first-page-of-build-an-app-webpages"></a>Первая страница, сборки приложение веб-страниц
![Сборки в приложение веб-страниц, первый снимок экрана страницы][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Меню для Java - Ubuntu — это приложение веб-страниц
![Сборки в приложение веб-страниц, меню Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Связанные ссылки
- [Примеры кода для подключения к базе данных SQL Azure в облаке, с помощью Java и других языках](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
