---
title: Библиотеки подключений и платформы | Документация Майкрософт
description: Список драйверов подключения клиентских приложений можно использовать для подключения к Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker, а также базу данных SQL Azure и хранилище данных SQL Azure из различных языков.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: 7a2f02323a3fb02cb74da3112c084609c5fe2b34
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085016"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Библиотеки подключений и платформы для Microsoft SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ознакомьтесь с [руководства по началу работы](http://aka.ms/sqldev) быстро приступить к программированию языков, таких как C#, Java, Node.js, PHP и Python, и построение приложения с помощью SQL Server в Linux или Windows либо Docker в macOS.

В следующей таблице перечислены библиотеки подключений или *драйверы* что клиентские приложения могут использовать из различных языков для подключения и использования Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker и также база данных SQL в Azure и хранилище данных Azure SQL. 

| Язык | Платформа | Дополнительные ресурсы | Загрузить | Приступая к работе |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET для SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Загрузить](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Драйвер Microsoft JDBC для SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Загрузить](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Драйвера PHP SQL для SQL Server](http://msdn.microsoft.com/library/dn865013.aspx) | Операционная система: <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Драйвер Node.js для SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Драйвер SQL Python](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Драйвер Ruby для SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Начало работы](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Драйвер Microsoft ODBC для SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [Загрузить](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

В следующей таблице перечислены примеры платформ объектно-реляционного сопоставления (ORM) и веб-платформ, которые клиентские приложения могут использовать с Microsoft SQL Server локально или в облаке, в Linux, Windows или Docker, а также к базе данных SQL Azure и Хранилище данных Azure SQL. 

| Язык | Платформа | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Платформа Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows, Linux, macOS |[Режим гибернации ORM](http://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Милнером)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on Rails](http://rubyonrails.org/) |

## <a name="related-links"></a>Связанные ссылки
- [Драйверы SQL Server](http://msdn.microsoft.com/library/mt654049.aspx) для подключения из клиентских приложений
