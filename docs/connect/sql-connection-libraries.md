---
title: Библиотеки подключений для базы данных Microsoft SQL | Документация Майкрософт
description: Ссылки для скачивания модулей, которые обеспечивают подключение к Microsoft SQL Server и базе данных SQL Azure с использованием разных языков программирования клиента.
author: RothJa
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 03/05/2020
ms.author: JRoth
ms.openlocfilehash: 88fbd0e3fd01492b8e7d920eb132196f8a005478
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79434121"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Модули подключения для баз данных Microsoft SQL

В этой статье содержатся ссылки для загрузки модулей подключения или *драйверов*, которые клиентские программы могут использовать для взаимодействия с [Microsoft SQL Server](../relational-databases/database-features.md), а также с двойником в облаке [Базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/). Драйверы доступны для различных языков, работающих в следующих операционных системах:

- Linux
- macOS
- Windows

**Несоответствие ООП и реляционных баз данных**

*Реляционные базы данных*. Клиентские программы, написанные на языке объектно-ориентированного программирования (ООП), часто используют драйверы SQL, возвращающие запрашиваемые данные в формате, больше подходящем для реляционных, чем объектно-ориентированных баз данных. Примером является использование C# в ADO.NET. Несоответствие ООП и реляционного формата иногда делает код ООП труднее для написания и понимания.

*ОРС*. Другие драйверы или платформы возвращают запрашиваемые данные в формате ООП, чтобы избежать несоответствия. Эти драйверы работают, ожидая, что классы были определены для соответствия столбцам данных определенных таблиц SQL. Затем драйвер выполняет *объектно-реляционное сопоставление* (ОРС) для возврата запрашиваемых данных в качестве экземпляра класса. Например, Entity Framework Майкрософт (EF) для C# и Hibernate для Java.

В этой статье приведены отдельные разделы для этих двух типов драйверов подключения.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Драйверы для реляционного доступа

| Язык | Скачать драйвер SQL |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[.NET Core для: Linux-Ubuntu, macOS, Windows](https://dotnet.microsoft.com/download) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Драйвер Node.js, инструкции по установке](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, инструкции по установке](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Скачать ODBC](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Драйвер Ruby, инструкции по установке](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Страница скачивания Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br/> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Драйверы для доступа к ОРС

В следующей таблице приведены примеры платформ объектно-реляционного сопоставления (ОРС), которые используются клиентскими приложениями для подключения к базам данных Microsoft SQL.

| Язык | Скачать драйвер ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework 6 или более поздняя версия](https://docs.microsoft.com/ef/) |
| Java | [Hibernate ORM](https://hibernate.org/orm)|
| PHP | [Eloquent ORM, входящая в установку Laravel](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |
| &nbsp; | <br/> |

<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Веб-страницы для создания приложения

**[https://aka.ms/sqldev](https://aka.ms/sqldev)** позволяет перейти к набору веб-страниц для *создания приложения*. Веб-страницы содержат сведения о многочисленных сочетаниях языков программирования, операционных систем и драйверов подключения SQL. На веб-страницах для создания приложения содержатся следующие сведения:

- Сведения о том, как начать с азов, для каждого сочетания языков, операционных систем и драйверов подключения SQL.
  - Инструкции по установке последних версий драйверов для подключения к SQL.
- Примеры кода для каждого из следующих элементов:
  - Примеры объектно-реляционного кода.
  - Примеры кода ORM.
  - Демонстрации индекса columnstore для повышения производительности.

**Первая страница из веб-страниц для создания приложений.**  
![Снимок экрана первой веб-страницы для создания приложений](media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png)

**Меню для Java Ubuntu на веб-страницах для создания приложений**  
![Веб-страницы для создания приложений, меню Java Ubuntu](media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png)

&nbsp;

## <a name="related-links"></a>Связанные ссылки

- [Примеры кода для подключения к Базе данных SQL Azure в облаке с использованием Java и других языков](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).

<!--
Image references, **obsolete** markdown syntax alternative:

![Build-an-app webpages, first page screenshot][image-ref-163-buildanapp-webpages-first-page]
![Build-an-app webpages, menu Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
-->
